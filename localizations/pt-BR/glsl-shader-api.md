---
title: API de Shader GLSL
description: >-
  Escreva shaders GLSL do FancyMenu para fundos, elementos e sobreposições de
  decoração.
---

# API de Shader GLSL do FancyMenu

Este documento descreve o runtime GLSL usado por:

- plano de fundo de menu `GLSL`
- elemento `GLSL`
- sobreposição de decoração `GLSL`

Ele cobre modos de compilação, roteamento multipass, uniforms suportados e padrões práticos de autoria de shaders.

## 1. Visão geral do runtime

O FancyMenu renderiza shaders com um pipeline interno de OpenGL (`#version 150`) e oferece suporte a:

- shaders de passagem única (`apenas pass Image`)
- shaders multipass (`Buffer A` / `B` / `C` / `D` + `Image`)
- pontos de entrada no estilo Shadertoy (`mainImage`)
- pontos de entrada fragmentados diretos (`main`)

As fontes dos shaders são campos de texto inline:

- `Shader Source` (pass Image, obrigatório para renderizar)
- `Buffer A Source` (opcional)
- `Buffer B Source` (opcional)
- `Buffer C Source` (opcional)
- `Buffer D Source` (opcional)

Se a fonte do Image estiver vazia, a renderização falha com um erro de "no source".

## 2. Modos de compilação

O FancyMenu oferece três modos de compilação:

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Modo Shadertoy

Ponto de entrada esperado:

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

O FancyMenu o envolve em `main()` e passa as coordenadas da área local:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

O wrapper multiplica a alpha de saída por `fmOpacity`.

### 2.2 Modo direto

Ponto de entrada esperado:

```glsl
void main()
```

Comportamento de compatibilidade:

- Uma variante de compatibilidade com `gl_FragColor` é tentada.
- Uma variante sem compatibilidade também é tentada (para shaders modernos com `out vec4` explícito).

No modo direto, `fmOpacity` não é aplicado automaticamente à sua saída. Aplique manualmente, se necessário.

### 2.3 Modo automático

O Auto tenta variantes compatíveis em sequência (Shadertoy/direto) e usa a primeira que compilar.

## 3. Pré-processamento da fonte e macros embutidas

Antes da compilação, o FancyMenu normaliza a fonte:

- remove BOM UTF-8
- converte CRLF/CR para LF
- remove linhas `#version ...`
- remove linhas `precision ...;`

O preâmbulo injetado em tempo de execução inclui:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV de tela cheia em `[0,1]`, origem no canto inferior esquerdo)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Observação:

- Se sua fonte já declara um nome de uniform conhecido (por exemplo, `iTime`), o FancyMenu evita injetar uma declaração duplicada.
- O FancyMenu ainda tenta enviar valores para esse nome em tempo de execução.
- `textureCube` é apenas um macro de alias aqui; `iChannel0..3` são uniforms `sampler2D`.

## 4. Sistema de passes (Image + Buffer A-D)

O FancyMenu possui 5 slots de pass:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (pass final exibido na tela)

Comportamento:

- Os passes de Buffer só executam se sua fonte não estiver vazia.
- O pass Image precisa estar presente para renderizar a saída.
- Os buffers são renderizados em texturas de ponto flutuante (`GL_RGBA16F`) e depois fazem ping-pong (troca de leitura/escrita a cada frame).

### 4.1 Roteamento de canais por pass

Cada pass expõe roteamento para `iChannel0..3`. Por canal, você pode selecionar:

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Os canais de recurso vêm das configurações `iChannel# Resource`.

Padrões:

- todos os roteamentos `iChannel` começam como `None`
- nenhum pass de buffer fica ativo até que a fonte desse buffer não esteja vazia

Importante:

- Roteamento para o mesmo pass de buffer (feedback) lê dados do frame anterior (textura de leitura ping-pong).
- Se uma origem roteada estiver ausente/inativa, uma textura de fallback é vinculada e `iChannelResolution[n].z` passa a ser `0.0`.

## 5. Semântica de coordenadas e área

Os shaders são executados em um retângulo de área:

- Fundo do menu: área de tela cheia
- Elemento GLSL: retângulo do elemento

Convenções de coordenadas:

- Uniforms de pixel usam pixels locais da área.
- A origem do Y é no canto inferior esquerdo para coordenadas de pixel expostas ao shader.
- As coordenadas do mouse não são limitadas; os valores podem ficar fora da área se o cursor estiver fora dela.

Campos especiais:

- `fmAreaOffset`: posição do canto inferior esquerdo da área no espaço de pixels da tela
- `fmAreaTopLeft`: posição do canto superior esquerdo da área no espaço de pixels da tela
- `fmAreaSize`: tamanho da área em pixels

## 6. Referência da API de uniforms

Todos os uniforms abaixo estão disponíveis tanto para shaders de fundo quanto para shaders de elemento.

## 6.1 Uniforms compatíveis com Shadertoy

| Uniform | Type | Meaning |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Tempo acumulado do shader em segundos |
| `iTimeDelta` | `float` | Delta de tempo do último render, afetado por freeze/escala de tempo |
| `iFrameRate` | `float` | FPS de fallback do runtime do Minecraft |
| `iFrame` | `int` | Contador de frames por runtime |
| `iMouse` | `vec4` | Veja os detalhes abaixo |
| `iDate` | `vec4` | `(year, month, day, secondsOfDayWithFraction)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Atualmente todos definidos como `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(width, height, validFlag)` por canal |
| `iChannel0..3` | `sampler2D` | Entradas de textura roteadas |

### Detalhes de `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: posição atual do mouse em pixels locais da área, ou comportamento de retenção/congelamento se a opção estiver ativada
- `z`, `w`: origem do clique esquerdo
  - positivo enquanto o botão esquerdo do mouse estiver pressionado
  - negativo após a liberação

Comportamento controlado por toggle:

- `Update iMouse Position Only While Holding LMB = Off`:
  - `iMouse.xy` é atualizado continuamente
- `... = On`:
  - `iMouse.xy` é atualizado somente enquanto o LMB estiver pressionado, então permanece na última posição mantida

Valor padrão:

- `Off` (atualizações contínuas)

## 6.2 Uniforms específicos do FancyMenu

| Uniform | Type | Meaning |
|---|---|---|
| `fmAreaOffset` | `vec2` | Deslocamento em pixels do canto inferior esquerdo da área no espaço da tela |
| `fmAreaSize` | `vec2` | Tamanho da área em pixels |
| `fmAreaPosition` | `vec2` | Igual a `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Deslocamento em pixels do canto superior esquerdo da área no espaço da tela |
| `fmScreenSize` | `vec2` | Tamanho total da tela em pixels |
| `fmGuiScale` | `float` | Escala atual da GUI |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Delta do mouse em pixels da área (o Y é invertido para cima no shader) |
| `fmMouseButtons` | `ivec4` | Estados pressionados dos botões `0..3` |
| `fmMouseClickCount` | `ivec4` | Contagens acumuladas de pressionamento dos botões `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Contagens acumuladas de liberação dos botões `0..3` |
| `fmMouseScroll` | `vec2` | Delta de rolagem desde o render anterior deste runtime |
| `fmMouseScrollTotal` | `vec2` | Totais acumulados de rolagem |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | Contador acumulado de eventos de teclado |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | Contador acumulado de eventos de caractere digitado |
| `fmDateParts` | `ivec4` | `(year, month, day, dayOfWeekIso1To7)` |
| `fmTimeParts` | `ivec4` | `(hour, minute, second, millisecondPart0To999)` |
| `fmDayOfYear` | `int` | Dia do ano |
| `fmWeekOfYear` | `int` | Semana ISO do ano |
| `fmUnixTimeSeconds` | `int` | Segundos da época Unix |
| `fmUnixTimeMilliseconds` | `int` | Parte em milissegundos do tempo atual (`0..999`) |
| `fmPartialTick` | `float` | Partial tick atual |
| `fmGameDeltaTicks` | `float` | Delta ticks de jogo do Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Delta ticks de tempo real do Minecraft |
| `fmInWorld` | `int` | `1` quando estiver em um mundo, caso contrário `0` |
| `fmIsPaused` | `int` | `1` quando pausado, caso contrário `0` |
| `fmOpacity` | `float` | Multiplicador efetivo de opacidade (`0..1`) |
| `fmVariableCount` | `int` | Quantidade atual de variáveis do FancyMenu |

Valores de ação de tecla (`fmKeyEvent.w`):

- `0` = release
- `1` = press
- `2` = repeat

## 6.3 API de uniforms de variáveis do FancyMenu

As variáveis do FancyMenu são expostas diretamente como uniforms em tempo de execução (para shaders de fundo, elemento e sobreposição de decoração) sem recompilação do shader quando os valores mudam.

### Nomeação

Para cada variável `<name>`, o FancyMenu expõe:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = a variável existe no momento, `0` = ausente/removida)

Sanitização do sufixo do uniform para `<name>`:

- caracteres permitidos são `[A-Za-z0-9_]`
- todos os outros caracteres são convertidos para `_`
- se o primeiro caractere for um dígito, `_` é prefixado

Exemplos:

- variável `player_hp` -> sufixo `player_hp`
- variável `player-hp` -> sufixo `player_hp`
- variável `2nd_phase` -> sufixo `_2nd_phase`

Importante:

- esses uniforms dinâmicos de variáveis **não são declarados automaticamente** na fonte do shader (declare manualmente os que você usar)
- evite nomes de variáveis que se sanitizem para o mesmo sufixo, porque elas mapearão para o mesmo nome de uniform GLSL

### Conversão de valores

Dado o valor textual da variável `v`:

- `fmVarFloat_*`: float analisado (`0.0` como fallback)
- `fmVarInt_*`: int analisado (`0` como fallback)
- `fmVarBool_*`: interpretação booleana/integer (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, caso contrário numérico diferente de zero => `1`)
- a análise de vetores aceita separadores: espaço em branco, `,`, `;`, `|`
  - `fmVarVec2_*`: primeiros 2 componentes analisados
  - `fmVarVec3_*`: primeiros 3 componentes analisados
  - `fmVarVec4_*`: primeiros 4 componentes analisados
  - se houver menos componentes, o último componente analisado é repetido nas posições ausentes
  - se não houver componentes numéricos, todos os componentes do vetor usam o fallback escalar

Se uma variável for removida:

- `fmVarExists_*` passa a ser `0`
- todos os valores correspondentes `fmVar*_*` são redefinidos para `0`

### Exemplo de declaração e uso

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

## 7. Modelo de rastreamento de entrada

O FancyMenu rastreia a entrada globalmente e cria um snapshot dela a cada render:

- movimento/arrasto do mouse
- pressionar/liberar do mouse
- rolagem
- pressionar/liberar/repetir tecla
- caractere digitado

Robustez do mouse:

- O runtime reconcilia os estados dos botões com a leitura do GLFW a cada frame para evitar estados de botão travado.

Se `Pass Input Events To Shader` estiver desativado:

- os uniforms de entrada são redefinidos para valores neutros a cada frame
- contadores e eventos são zerados nos dados visíveis pelo shader

## 8. Detalhes de entrada de textura

Os canais de recurso (`iChannel# Resource`) esperam texturas 2D.

Estado da textura por canal:

- recurso válido: textura vinculada, largura/altura reais, `iChannelResolution[n].z = 1.0`
- ausente/inativo/None: textura de fallback, `iChannelResolution[n].xyz = (0,0,0)`

Texturas de buffer:

- formato interno: `RGBA16F` (ponto flutuante)
- filtragem: linear
- wrap: clamp-to-edge

Isso é adequado para dados multipass (incluindo valores fora de `[0,1]`).

## 9. Observações sobre renderização e blending

- Os passes de Buffer renderizam fora da tela sem blending.
- O pass Image final usa a configuração `Enable Blending` para composição.
- O wrapper Shadertoy aplica `fmOpacity` automaticamente à alpha.
- Shaders diretos devem aplicar `fmOpacity` manualmente, se necessário.

## 10. Modelos práticos

## 10.1 Shader mínimo no estilo Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Shader fragmentado direto mínimo

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Multipass de feedback mínimo

### Fonte do Buffer A

Roteamento: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Fonte do Image

Roteamento: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Lista de verificação para solução de problemas

- Sem saída:
  - verifique se a fonte do Image não está vazia
  - verifique se o modo de compilação corresponde ao seu ponto de entrada (`mainImage` vs `main`)
- Texturas roxas/inválidas:
  - verifique os bindings de recurso e o roteamento de canal
  - confira `iChannelResolution[n].z` (`0.0` significa inválido/indisponível)
- Coordenadas incorretas no shader direto:
  - use `gl_FragCoord.xy - fmAreaOffset` para coordenadas locais da área
- Comportamento de arrasto incorreto:
  - use o toggle `Update iMouse Position Only While Holding LMB`
- Opacidade não aplicada no shader direto:
  - multiplique a alpha por `fmOpacity` manualmente
