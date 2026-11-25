---
title: GLSL 着色器 API
description: 编写用于背景、元素和装饰叠加层的 FancyMenu GLSL 着色器。
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# FancyMenu GLSL 着色器 API

本文档介绍 FancyMenu 以下功能使用的 GLSL 运行时：

- `GLSL` 菜单背景
- `GLSL` 元素
- `GLSL` 装饰叠加层

内容涵盖编译模式、多通道路由、支持的 uniform，以及实用的着色器编写模式。

## 1. 运行时概述

FancyMenu 使用内部 OpenGL 管线（`#version 150`）渲染着色器，并支持：

- 单通道着色器（仅 `Image` 通道）
- 多通道着色器（`Buffer A` / `B` / `C` / `D` + `Image`）
- Shadertoy 风格的入口点（`mainImage`）
- 直接片段着色器入口点（`main`）

着色器源代码以内联文本形式提供：

- `Shader Source`（Image 通道，渲染所必需）
- `Buffer A Source`（可选）
- `Buffer B Source`（可选）
- `Buffer C Source`（可选）
- `Buffer D Source`（可选）

如果 Image 源代码为空，渲染会失败，并显示“no source”错误。

## 2. 编译模式

FancyMenu 支持三种编译模式：

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoy 模式

预期的入口点：

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu 会将其包装在 `main()` 中，并传入相对于区域的局部坐标：

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

包装器会将输出 alpha 乘以 `fmOpacity`。

### 2.2 Direct 模式

预期的入口点：

```glsl
void main()
```

兼容性处理：

- 会尝试使用 `gl_FragColor` 兼容版本。
- 也会尝试不带兼容处理的版本（适用于使用现代显式 `out vec4` 的着色器）。

在 Direct 模式下，`fmOpacity` 不会自动应用到输出。若有需要，请手动应用。

### 2.3 Auto 模式

Auto 会依次尝试兼容的版本（Shadertoy/Direct），并使用第一个成功编译的版本。

## 3. 源代码预处理和内置宏

编译前，FancyMenu 会规范化源代码：

- 移除 UTF-8 BOM
- 将 CRLF/CR 转换为 LF
- 移除 `#version ...` 行
- 移除 `precision ...;` 行

运行时注入的前置代码包括：

- `#version 150`
- `in vec2 fmUv_FancyMenu`（范围为 `[0,1]` 的全屏 UV，原点位于左下角）
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

注意：

- 如果源代码中已声明已知 uniform 名称（例如 `iTime`），FancyMenu 会避免重复注入声明。
- FancyMenu 仍会在运行时尝试向该名称上传数值。
- 此处的 `textureCube` 只是别名宏；`iChannel0..3` 是 `sampler2D` uniform。

## 4. 通道系统（Image + Buffer A-D）

FancyMenu 有 5 个通道槽位：

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image`（最终屏幕渲染通道）

行为说明：

- 仅当缓冲区源代码非空时，才会运行对应的缓冲区通道。
- 必须提供 Image 通道，才能渲染输出。
- 缓冲区会渲染到浮点纹理（`GL_RGBA16F`），然后通过乒乓缓冲进行读写（每帧交换读写目标）。

### 4.1 每个通道的输入路由

每个通道都可以为 `iChannel0..3` 配置路由。每个输入通道可选择：

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

资源通道的输入来自 `iChannel# Resource` 设置。

默认值：

- 所有 `iChannel` 路由默认为 `None`
- 缓冲区源代码非空之前，不会启用对应的缓冲区通道

重要说明：

- 路由到同一个缓冲区通道（反馈）时，读取的是上一帧的数据（乒乓缓冲的读纹理）。
- 如果路由的源缺失或未激活，则会绑定备用纹理，并将 `iChannelResolution[n].z` 设为 `0.0`。

## 5. 坐标和区域语义

着色器在一个矩形区域内运行：

- 菜单背景：全屏区域
- GLSL 元素：元素矩形区域

坐标约定：

- 像素类 uniform 使用区域内的局部像素坐标。
- 面向着色器的像素坐标以左下角为 Y 轴原点。
- 鼠标坐标不会被限制在区域内；当光标位于区域外时，坐标值也可能超出区域范围。

特殊字段：

- `fmAreaOffset`：区域左下角在屏幕像素坐标中的位置
- `fmAreaTopLeft`：区域左上角在屏幕像素坐标中的位置
- `fmAreaSize`：区域的像素尺寸

## 6. Uniform API 参考

以下 uniform 均可用于背景和元素着色器。

## 6.1 兼容 Shadertoy 的 uniform

| Uniform | 类型 | 含义 |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | 累积的着色器运行时间，单位为秒 |
| `iTimeDelta` | `float` | 上次渲染的时间间隔，受冻结/时间缩放影响 |
| `iFrameRate` | `float` | Minecraft FPS；无法获取时使用运行时 FPS 作为备用值 |
| `iFrame` | `int` | 运行时帧计数器 |
| `iMouse` | `vec4` | 详见下文 |
| `iDate` | `vec4` | `(年, 月, 日, 含小数部分的当天秒数)` |
| `iSampleRate` | `float` | 固定值 `44100.0` |
| `iChannelTime[4]` | `float[4]` | 当前全部设为 `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | 每个输入通道的 `(宽度, 高度, 有效标志)` |
| `iChannel0..3` | `sampler2D` | 路由的纹理输入 |

### `iMouse` 详细说明

`iMouse = vec4(x, y, z, w)`

- `x`、`y`：当前区域内的局部鼠标像素位置；如果启用了相关切换选项，则会采用保持/冻结行为
- `z`、`w`：鼠标左键的按下起始位置
  - 按住鼠标左键时为正值
  - 松开后为负值

由切换选项控制的行为：

- `Update iMouse Position Only While Holding LMB = Off`：
  - `iMouse.xy` 持续更新
- `... = On`：
  - 仅在按住鼠标左键时更新 `iMouse.xy`，随后保持在最后一次按住时的位置

默认值：

- `Off`（持续更新）

## 6.2 FancyMenu 专用 uniform

| Uniform | 类型 | 含义 |
|---|---|---|
| `fmAreaOffset` | `vec2` | 区域左下角在屏幕空间中的像素偏移 |
| `fmAreaSize` | `vec2` | 区域的像素尺寸 |
| `fmAreaPosition` | `vec2` | 与 `fmAreaOffset` 相同 |
| `fmAreaTopLeft` | `vec2` | 区域左上角在屏幕空间中的像素偏移 |
| `fmScreenSize` | `vec2` | 全屏尺寸，单位为像素 |
| `fmGuiScale` | `float` | 当前 GUI 缩放比例 |
| `fmMouse` | `vec4` | `(局部像素X, 局部像素Y（原点在底部）, 局部归一化X, 局部归一化Y)` |
| `fmMouseDelta` | `vec2` | 区域内的鼠标移动量（Y 轴方向已反转为着色器向上） |
| `fmMouseButtons` | `ivec4` | 按钮 `0..3` 的按下状态 |
| `fmMouseClickCount` | `ivec4` | 按钮 `0..3` 的累计按下次数 |
| `fmMouseReleaseCount` | `ivec4` | 按钮 `0..3` 的累计释放次数 |
| `fmMouseScroll` | `vec2` | 自该运行时上次渲染以来的滚动增量 |
| `fmMouseScrollTotal` | `vec2` | 累计滚动总量 |
| `fmKeyEvent` | `ivec4` | `(上次按键代码, 上次扫描码, 上次修饰键, 上次操作)` |
| `fmKeyEventCount` | `int` | 累计键盘事件计数 |
| `fmCharEvent` | `ivec4` | `(上次字符代码点, 上次修饰键, 0, 0)` |
| `fmCharEventCount` | `int` | 累计字符输入事件计数 |
| `fmDateParts` | `ivec4` | `(年, 月, 日, 星期几（ISO 1 到 7）)` |
| `fmTimeParts` | `ivec4` | `(小时, 分钟, 秒, 毫秒部分（0 到 999）)` |
| `fmDayOfYear` | `int` | 一年中的第几天 |
| `fmWeekOfYear` | `int` | ISO 年周数 |
| `fmUnixTimeSeconds` | `int` | Unix 时间戳秒数 |
| `fmUnixTimeMilliseconds` | `int` | 当前时间的毫秒部分（`0..999`） |
| `fmPartialTick` | `float` | 当前部分刻（partial tick） |
| `fmGameDeltaTicks` | `float` | Minecraft 游戏刻增量 |
| `fmRealtimeDeltaTicks` | `float` | Minecraft 实时时间刻增量 |
| `fmInWorld` | `int` | 在世界中时为 `1`，否则为 `0` |
| `fmIsPaused` | `int` | 游戏暂停时为 `1`，否则为 `0` |
| `fmOpacity` | `float` | 实际不透明度乘数（`0..1`） |
| `fmVariableCount` | `int` | 当前 FancyMenu 变量数量 |

按键操作值（`fmKeyEvent.w`）：

- `0` = 释放
- `1` = 按下
- `2` = 重复

## 6.3 FancyMenu 变量 Uniform API

FancyMenu 变量会直接作为运行时 uniform 提供给背景、元素和装饰叠加层着色器；变量值变化时，无需重新编译着色器。

### 命名

对于每个变量 `<name>`，FancyMenu 会提供：

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>`（`1` = 变量当前存在，`0` = 不存在/已移除）

`<name>` 的 uniform 后缀会按以下规则规范化：

- 允许的字符为 `[A-Za-z0-9_]`
- 其他所有字符都会转换为 `_`
- 如果首字符是数字，则会在前面加上 `_`

示例：

- 变量 `player_hp` -> 后缀 `player_hp`
- 变量 `player-hp` -> 后缀 `player_hp`
- 变量 `2nd_phase` -> 后缀 `_2nd_phase`

重要说明：

- 这些动态变量 uniform **不会在着色器源代码中自动声明**（请手动声明所需变量）
- 避免使用规范化后得到相同后缀的变量名称，因为它们会映射到相同的 GLSL uniform 名称

### 值转换

给定变量文本值 `v`：

- `fmVarFloat_*`：解析为浮点数（失败时默认为 `0.0`）
- `fmVarInt_*`：解析为整数（失败时默认为 `0`）
- `fmVarBool_*`：按布尔值/整数解释（`true/yes/on/enabled` => `1`，`false/no/off/disabled` => `0`，其他情况下数值非零则为 `1`）
- 向量解析支持以下分隔符：空格、`,`, `;`, `|`
  - `fmVarVec2_*`：取解析出的前 2 个分量
  - `fmVarVec3_*`：取解析出的前 3 个分量
  - `fmVarVec4_*`：取解析出的前 4 个分量
  - 如果分量不足，则将最后一个已解析的分量重复用于缺少的分量
  - 如果没有可解析的数值分量，则所有向量分量都使用标量备用值

[列表变量](/variables#text-and-list-variables)提供的是条目数量，而不是文本内容：

- `fmVarFloat_*` 和 `fmVarInt_*`：条目数量，例如含 3 个条目的列表返回 `3`
- `fmVarBool_*`：列表有条目时为 `1`，为空时为 `0`
- `fmVarVec2_*`、`fmVarVec3_*` 和 `fmVarVec4_*`：每个分量都返回条目数量

如果变量被移除：

- `fmVarExists_*` 变为 `0`
- 所有对应的 `fmVar*_*` 值都会重置为 `0`

### 声明和用法示例

```glsl
uniform float fmVarFloat_player_hp;
uniform int fmVarBool_is_boss_phase;
uniform vec3 fmVarVec3_theme_color;
uniform int fmVarExists_player_hp;

void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;

    float hp = clamp(fmVarFloat_player_hp / 100.0, 0.0, 1.0);
    vec3 theme = fmVarVec3_theme_color;
    float boss = float(fmVarBool_is_boss_phase);

    vec3 col = mix(theme * 0.25, theme, hp);
    col += vec3(0.2, 0.0, 0.0) * boss;

    if (fmVarExists_player_hp == 0) {
        col = vec3(0.15);
    }

    fragColor = vec4(col, 1.0);
}
```

## 7. 输入跟踪模型

FancyMenu 会全局跟踪输入，并在每次渲染时创建快照：

- 鼠标移动/拖动
- 鼠标按下/释放
- 滚动
- 按键按下/释放/重复
- 字符输入

鼠标状态保障：

- 运行时会在每帧通过 GLFW 轮询来校准按钮状态，避免按钮状态卡住。

如果禁用了 `Pass Input Events To Shader`：

- 每帧都会将输入 uniform 重置为中性值
- 着色器可见数据中的计数器和事件都会清零

## 8. 纹理输入详情

资源通道（`iChannel# Resource`）需要使用 2D 纹理。

每个通道的纹理状态：

- 资源有效：绑定对应纹理，使用真实宽高，`iChannelResolution[n].z = 1.0`
- 资源缺失/未激活/为 None：使用备用纹理，`iChannelResolution[n].xyz = (0,0,0)`

缓冲区纹理：

- 内部格式：`RGBA16F`（浮点）
- 过滤方式：线性
- 环绕方式：边缘钳制

这适用于多通道数据处理（包括 `[0,1]` 范围之外的值）。

## 9. 渲染和混合说明

- 缓冲区通道在屏幕外渲染，不进行混合。
- 最终 Image 通道使用 `Enable Blending` 设置进行合成。
- Shadertoy 包装器会自动将 `fmOpacity` 应用到 alpha。
- 如有需要，Direct 着色器应手动应用 `fmOpacity`。

## 10. 实用模板

## 10.1 最简 Shadertoy 风格着色器

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 最简直接片段着色器

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 最简反馈式多通道

### Buffer A 源代码

路由：`Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Image 源代码

路由：`Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. 故障排查清单

- 没有输出：
  - 确认 Image 源代码非空
  - 确认编译模式与入口点相匹配（`mainImage` 或 `main`）
- 纹理呈紫色/无效：
  - 确认资源绑定和通道路由
  - 检查 `iChannelResolution[n].z`（`0.0` 表示无效/不可用）
- Direct 着色器中的坐标不正确：
  - 使用 `gl_FragCoord.xy - fmAreaOffset` 获取区域内的局部坐标
- 拖动行为不正确：
  - 使用 `Update iMouse Position Only While Holding LMB` 切换选项
- Direct 着色器中未应用不透明度：
  - 手动将 alpha 乘以 `fmOpacity`
