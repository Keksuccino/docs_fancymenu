---
title: GLSL 着色器 API
description: 为背景、元素和装饰覆盖层编写 FancyMenu GLSL 着色器。
---

# FancyMenu GLSL 着色器 API

本文档介绍 FancyMenu 使用的 GLSL 运行时，适用于以下内容：

- `GLSL` 菜单背景
- `GLSL` 元素
- `GLSL` 装饰覆盖层

本文涵盖编译模式、多通道路由、受支持的 uniform，以及实用的着色器编写模式。

## 1. 运行时概览

FancyMenu 使用内部 OpenGL 管线（`#version 150`）渲染着色器，并支持：

- 单通道着色器（仅 `Image` 通道）
- 多通道着色器（`Buffer A` / `B` / `C` / `D` + `Image`）
- Shadertoy 风格入口点（`mainImage`）
- 直接片段着色器入口点（`main`）

着色器源码为内联文本字段：

- `Shader Source`（`Image` 通道，渲染必需）
- `Buffer A Source`（可选）
- `Buffer B Source`（可选）
- `Buffer C Source`（可选）
- `Buffer D Source`（可选）

如果 Image 源为空，渲染会因“no source”错误而失败。

## 2. 编译模式

FancyMenu 支持三种编译模式：

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Shadertoy 模式

期望的入口点：

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu 会将其封装到 `main()` 中，并传入局部区域坐标：

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

该封装会将输出 alpha 乘以 `fmOpacity`。

### 2.2 直接模式

期望的入口点：

```glsl
void main()
```

兼容性行为：

- 会尝试 `gl_FragColor` 兼容版本。
- 也会尝试不兼容版本（用于现代的显式 `out vec4` 着色器）。

在直接模式下，`fmOpacity` 不会自动应用到你的输出。若需要，请手动应用。

### 2.3 自动模式

Auto 会按顺序尝试兼容变体（Shadertoy/直接），并使用第一个编译成功的版本。

## 3. 源码预处理与内置宏

编译前，FancyMenu 会对源码进行规范化处理：

- 移除 UTF-8 BOM
- 将 CRLF/CR 转换为 LF
- 删除 `#version ...` 行
- 删除 `precision ...;` 行

运行时注入的前导内容包括：

- `#version 150`
- `in vec2 fmUv_FancyMenu`（全屏 UV，范围 `[0,1]`，左下角为原点）
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

注意：

- 如果你的源码已经声明了某个已知 uniform 名称（例如 `iTime`），FancyMenu 会避免注入重复声明。
- FancyMenu 仍会尝试在运行时向该名称上传值。
- `textureCube` 在此仅是别名宏；`iChannel0..3` 是 `sampler2D` uniform。

## 4. 通道系统（Image + Buffer A-D）

FancyMenu 有 5 个通道槽位：

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image`（最终屏幕输出通道）

行为：

- 只有当缓冲通道的源码非空时才会运行。
- `Image` 通道必须存在，才能渲染输出。
- 缓冲区会渲染到浮点纹理（`GL_RGBA16F`），然后进行乒乓交换（每帧读/写交换）。

### 4.1 每个通道的通道路由

每个通道都支持 `iChannel0..3` 的路由设置。每个通道可选：

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

资源通道来自 `iChannel# Resource` 设置。

默认值：

- 所有 `iChannel` 路由默认都是 `None`
- 在对应缓冲区源码非空之前，任何缓冲通道都不会激活

重要：

- 路由到同一个缓冲通道（反馈）时，读取的是上一帧的数据（乒乓读纹理）。
- 如果路由源缺失/未激活，会绑定一个回退纹理，并且 `iChannelResolution[n].z` 会变为 `0.0`。

## 5. 坐标与区域语义

着色器运行在一个区域矩形中：

- 菜单背景：全屏区域
- GLSL 元素：元素矩形

坐标约定：

- 像素 uniform 使用的是区域局部像素坐标。
- 面向着色器的像素坐标中，Y 轴原点在左下角。
- 鼠标坐标不会被裁剪；当鼠标在区域外时，值可能超出区域范围。

特殊字段：

- `fmAreaOffset`：区域左下角在屏幕像素空间中的位置
- `fmAreaTopLeft`：区域左上角在屏幕像素空间中的位置
- `fmAreaSize`：区域大小（像素）

## 6. Uniform API 参考

以下所有 uniform 都适用于背景和元素着色器。

## 6.1 Shadertoy 兼容 uniform

| Uniform | 类型 | 含义 |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | 累积的着色器时间（秒） |
| `iTimeDelta` | `float` | 上一次渲染的时间增量，受冻结/时间缩放影响 |
| `iFrameRate` | `float` | Minecraft FPS 备用运行时 FPS |
| `iFrame` | `int` | 每个运行时的帧计数器 |
| `iMouse` | `vec4` | 详见下方 |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | 固定为 `44100.0` |
| `iChannelTime[4]` | `float[4]` | 当前全部设为 `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | 每个通道的 `(width, height, validFlag)` |
| `iChannel0..3` | `sampler2D` | 已路由的纹理输入 |

### `iMouse` 详情

`iMouse = vec4(x, y, z, w)`

- `x`、`y`：当前区域局部鼠标像素位置；如果启用了切换项，则为按住/冻结行为
- `z`、`w`：左键点击起点
  - 按住左键时为正
  - 释放后为负

切换项控制的行为：

- `Update iMouse Position Only While Holding LMB = Off`：
  - `iMouse.xy` 持续更新
- `... = On`：
  - `iMouse.xy` 仅在按住 LMB 时更新，然后保持在最后一次按住的位置

默认值：

- `Off`（持续更新）

## 6.2 FancyMenu 专用 uniform

| Uniform | 类型 | 含义 |
|---|---|---|
| `fmAreaOffset` | `vec2` | 区域左下角在屏幕空间中的像素偏移 |
| `fmAreaSize` | `vec2` | 区域大小（像素） |
| `fmAreaPosition` | `vec2` | 与 `fmAreaOffset` 相同 |
| `fmAreaTopLeft` | `vec2` | 区域左上角在屏幕空间中的像素偏移 |
| `fmScreenSize` | `vec2` | 整个屏幕大小（像素） |
| `fmGuiScale` | `float` | 当前 GUI 缩放 |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | 区域像素中的鼠标增量（Y 方向已反转为着色器向上） |
| `fmMouseButtons` | `ivec4` | 按钮 `0..3` 的按下状态 |
| `fmMouseClickCount` | `ivec4` | 按钮 `0..3` 的累计按下次数 |
| `fmMouseReleaseCount` | `ivec4` | 按钮 `0..3` 的累计释放次数 |
| `fmMouseScroll` | `vec2` | 自本运行时上一次渲染以来的滚轮增量 |
| `fmMouseScrollTotal` | `vec2` | 累计滚轮总量 |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | 累计按键事件计数器 |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | 累计字符输入事件计数器 |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | 一年中的第几天 |
| `fmWeekOfYear` | `int` | ISO 年周数 |
| `fmUnixTimeSeconds` | `int` | Unix 纪元秒数 |
| `fmUnixTimeMilliseconds` | `int` | 当前时间的毫秒部分（`0..999`） |
| `fmPartialTick` | `float` | 当前部分 tick |
| `fmGameDeltaTicks` | `float` | Minecraft 游戏 delta ticks |
| `fmRealtimeDeltaTicks` | `float` | Minecraft 实时 delta ticks |
| `fmInWorld` | `int` | 在世界中时为 `1`，否则为 `0` |
| `fmIsPaused` | `int` | 暂停时为 `1`，否则为 `0` |
| `fmOpacity` | `float` | 实际不透明度乘数（`0..1`） |
| `fmVariableCount` | `int` | 当前 FancyMenu 变量数量 |

按键动作值（`fmKeyEvent.w`）：

- `0` = 释放
- `1` = 按下
- `2` = 重复

## 6.3 FancyMenu 变量 Uniform API

FancyMenu 变量会作为运行时 uniform 直接暴露给背景、元素和装饰覆盖层着色器，并且在值变化时无需重新编译着色器。

### 命名

对于每个变量 `<name>`，FancyMenu 会暴露：

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>`（`1` = 变量当前存在，`0` = 不存在/已移除）

`<name>` 的 uniform 后缀清理规则：

- 允许的字符为 `[A-Za-z0-9_]`
- 其他所有字符都会转换为 `_`
- 如果首字符是数字，则会在前面加上 `_`

示例：

- 变量 `player_hp` -> 后缀 `player_hp`
- 变量 `player-hp` -> 后缀 `player_hp`
- 变量 `2nd_phase` -> 后缀 `_2nd_phase`

重要：

- 这些动态变量 uniform **不会**自动声明在着色器源码中（请手动声明你会用到的那些）
- 避免使用清理后会变成相同后缀的变量名，因为它们会映射到同一个 GLSL uniform 名称

### 值转换

给定变量文本值 `v`：

- `fmVarFloat_*`：解析为浮点数（默认回退 `0.0`）
- `fmVarInt_*`：解析为整数（默认回退 `0`）
- `fmVarBool_*`：布尔/整数解释（`true/yes/on/enabled` => `1`，`false/no/off/disabled` => `0`，否则数值非零 => `1`）
- 向量解析支持以下分隔符：空白、`,`、`;`、`|`
  - `fmVarVec2_*`：前 2 个解析出的分量
  - `fmVarVec3_*`：前 3 个解析出的分量
  - `fmVarVec4_*`：前 4 个解析出的分量
  - 如果分量不足，则用最后一个已解析分量重复填充缺失项
  - 如果没有任何数值分量，则所有向量分量都使用标量回退值

如果某个变量被移除：

- `fmVarExists_*` 变为 `0`
- 所有对应的 `fmVar*_*` 值都会重置为 `0`

### 示例声明与使用

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

FancyMenu 会全局跟踪输入，并在每次渲染时生成快照：

- 鼠标移动/拖拽
- 鼠标按下/释放
- 滚轮
- 按键按下/释放/重复
- 字符输入

鼠标鲁棒性：

- 运行时会每帧将按钮状态与 GLFW 轮询结果进行校正，以防止按钮卡住。

如果 `Pass Input Events To Shader` 被禁用：

- 每帧都会将输入 uniform 重置为中性值
- 着色器可见数据中的计数器和事件都会清零

## 8. 纹理输入详情

资源通道（`iChannel# Resource`）期望使用 2D 纹理。

每个通道的纹理状态：

- 有效资源：已绑定纹理，真实宽高，`iChannelResolution[n].z = 1.0`
- 缺失/未激活/None：回退纹理，`iChannelResolution[n].xyz = (0,0,0)`

缓冲区纹理：

- 内部格式：`RGBA16F`（浮点）
- 过滤：线性
- 环绕：clamp-to-edge

这适合多通道数据（包括超出 `[0,1]` 的值）。

## 9. 渲染与混合说明

- 缓冲通道在屏幕外渲染，不使用混合。
- 最终 `Image` 通道会使用 `Enable Blending` 设置进行合成。
- Shadertoy 封装会自动将 `fmOpacity` 应用到 alpha。
- 直接着色器如有需要，应手动应用 `fmOpacity`。

## 10. 实用模板

## 10.1 最小 Shadertoy 风格着色器

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 最小直接片段着色器

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 最小反馈多通道示例

### Buffer A 源码

路由：`Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Image 源码

路由：`Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. 故障排查清单

- 没有输出：
  - 确认 Image 源码非空
  - 确认编译模式与入口点匹配（`mainImage` vs `main`）
- 紫色/无效纹理：
  - 检查资源绑定和通道路由
  - 查看 `iChannelResolution[n].z`（`0.0` 表示无效/不可用）
- 直接着色器坐标不正确：
  - 使用 `gl_FragCoord.xy - fmAreaOffset` 获取局部区域坐标
- 拖拽行为不正确：
  - 使用 `Update iMouse Position Only While Holding LMB` 切换项
- 直接着色器中未应用不透明度：
  - 自行将 alpha 乘以 `fmOpacity`
