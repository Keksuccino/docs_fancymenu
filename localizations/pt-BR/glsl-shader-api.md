---
title: API de shaders GLSL
description: >-
  Crie shaders GLSL do FancyMenu para planos de fundo, elementos e sobreposições
  decorativas.
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# API de shaders GLSL do FancyMenu

Este documento descreve o runtime GLSL usado nos seguintes recursos do FancyMenu:

- plano de fundo de menu `GLSL`
- elemento `GLSL`
- sobreposição decorativa `GLSL`

Ele aborda modos de compilação, roteamento multipass, uniforms compatíveis e padrões práticos para criação de shaders.

## 1. Visão geral do runtime

O FancyMenu renderiza shaders com um pipeline OpenGL interno (`#version 150`) e oferece suporte a:

- shaders de passagem única (somente passagem `Image`)
- shaders multipass (`Buffer A` / `B` / `C` / `D` + `Image`)
- pontos de entrada no estilo Shadertoy (`mainImage`)
- pontos de entrada de fragmento diretos (`main`)

As fontes dos shaders são campos de texto embutidos:

- `Shader Source` (passagem Image, obrigatório para renderizar)
- `Buffer A Source` (opcional)
- `Buffer B Source` (opcional)
- `Buffer C Source` (opcional)
- `Buffer D Source` (opcional)

Se a fonte de Image estiver vazia, a renderização falhará com um erro de "no source".

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

O FancyMenu o envolve em `main()` e passa as coordenadas locais da área:

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

O wrapper multiplica o alfa da saída por `fmOpacity`.

### 2.2 Modo direto

Ponto de entrada esperado:

```glsl
void main()
```

Comportamento de compatibilidade:

- É testada uma variante de compatibilidade com `gl_FragColor`.
- Também é testada uma variante sem compatibilidade (para shaders modernos com `out vec4` explícito).

No modo direto, `fmOpacity` não é aplicado automaticamente à saída. Aplique-o manualmente, se necessário.

### 2.3 Modo automático

O modo Auto tenta variantes compatíveis em sequência (Shadertoy/direto) e usa a primeira que compilar.

## 3. Pré-processamento da fonte e macros integradas

Antes da compilação, o FancyMenu normaliza a fonte:

- remove o BOM UTF-8
- converte CRLF/CR em LF
- remove linhas `#version ...`
- remove linhas `precision ...;`

O preâmbulo injetado pelo runtime inclui:

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV de tela cheia no intervalo `[0,1]`, origem no canto inferior esquerdo)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Observação:

- Se sua fonte já declarar um nome de uniform conhecido (por exemplo, `iTime`), o FancyMenu evita injetar uma declaração duplicada.
- Mesmo assim, o FancyMenu tenta enviar valores para esse nome durante o runtime.
- `textureCube` é apenas um alias de macro; `iChannel0..3` são uniforms `sampler2D`.

## 4. Sistema de passagens (Image + Buffer A-D)

O FancyMenu tem 5 slots de passagem:

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (passagem final exibida na tela)

Comportamento:

- As passagens de buffer só são executadas se a fonte não estiver vazia.
- A passagem Image precisa estar presente para renderizar a saída.
- Os buffers são renderizados em texturas de ponto flutuante (`GL_RGBA16F`) e, em seguida, alternados por pingue-pongue (troca de leitura/gravação a cada quadro).

### 4.1 Roteamento de canais por passagem

Cada passagem oferece opções de roteamento para `iChannel0..3`. Para cada canal, você pode selecionar:

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

- todos os roteamentos de `iChannel` são definidos como `None` por padrão
- nenhuma passagem de buffer fica ativa até que a fonte desse buffer não esteja vazia

Importante:

- O roteamento para a mesma passagem de buffer (feedback) lê os dados do quadro anterior (textura de leitura do pingue-pongue).
- Se a origem roteada estiver ausente/inativa, uma textura alternativa será vinculada e `iChannelResolution[n].z` será definido como `0.0`.

## 5. Coordenadas e semântica da área

Os shaders são executados em uma área retangular:

- Plano de fundo do menu: área de tela inteira
- Elemento GLSL: retângulo do elemento

Convenções de coordenadas:

- Os uniforms de pixel usam pixels locais à área.
- A origem Y das coordenadas de pixel usadas pelo shader fica no canto inferior esquerdo.
- As coordenadas do mouse não são limitadas; os valores podem ficar fora da área se o cursor estiver fora dela.

Campos especiais:

- `fmAreaOffset`: posição do canto inferior esquerdo da área no espaço de pixels da tela
- `fmAreaTopLeft`: posição do canto superior esquerdo da área no espaço de pixels da tela
- `fmAreaSize`: tamanho da área em pixels

## 6. Referência da API de uniforms

Todos os uniforms abaixo estão disponíveis para shaders de plano de fundo e de elemento.

## 6.1 Uniforms compatíveis com Shadertoy

| Uniform | Tipo | Significado |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Tempo acumulado do shader em segundos |
| `iTimeDelta` | `float` | Intervalo desde a última renderização, afetado pelo congelamento/escala de tempo |
| `iFrameRate` | `float` | FPS do runtime, com o FPS do Minecraft como alternativa |
| `iFrame` | `int` | Contador de quadros por runtime |
| `iMouse` | `vec4` | Consulte os detalhes abaixo |
| `iDate` | `vec4` | `(ano, mês, dia, segundosDoDiaComFração)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Atualmente, todos são definidos como `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(largura, altura, indicadorDeValidade)` por canal |
| `iChannel0..3` | `sampler2D` | Entradas de textura roteadas |

### Detalhes de `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y`: posição atual do mouse em pixels locais à área, ou comportamento de retenção/congelamento se a opção estiver ativada
- `z`, `w`: origem do clique com o botão esquerdo
  - positivo enquanto o botão esquerdo do mouse estiver pressionado
  - negativo após soltar

Comportamento controlado pela opção:

- `Atualizar a posição de iMouse somente enquanto o botão esquerdo estiver pressionado = Desativado`:
  - `iMouse.xy` é atualizado continuamente
- `... = Ativado`:
  - `iMouse.xy` é atualizado somente enquanto o botão esquerdo estiver pressionado; depois, mantém a última posição registrada enquanto estava pressionado

Valor padrão:

- `Desativado` (atualizações contínuas)

## 6.2 Uniforms específicos do FancyMenu

| Uniform | Tipo | Significado |
|---|---|---|
| `fmAreaOffset` | `vec2` | Deslocamento em pixels do canto inferior esquerdo da área no espaço da tela |
| `fmAreaSize` | `vec2` | Tamanho da área em pixels |
| `fmAreaPosition` | `vec2` | Igual a `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Deslocamento em pixels do canto superior esquerdo da área no espaço da tela |
| `fmScreenSize` | `vec2` | Tamanho total da tela em pixels |
| `fmGuiScale` | `float` | Escala atual da interface |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Variação do mouse em pixels da área (Y é invertido para cima no espaço do shader) |
| `fmMouseButtons` | `ivec4` | Estados de pressionamento dos botões `0..3` |
| `fmMouseClickCount` | `ivec4` | Contagem acumulada de pressionamentos dos botões `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Contagem acumulada de solturas dos botões `0..3` |
| `fmMouseScroll` | `vec2` | Variação da rolagem desde a renderização anterior deste runtime |
| `fmMouseScrollTotal` | `vec2` | Totais acumulados da rolagem |
| `fmKeyEvent` | `ivec4` | `(últimoCódigoDaTecla, últimoCódigoDeVarredura, últimosModificadores, últimaAção)` |
| `fmKeyEventCount` | `int` | Contador acumulado de eventos de tecla |
| `fmCharEvent` | `ivec4` | `(últimoPontoDeCódigo, últimosModificadores, 0, 0)` |
| `fmCharEventCount` | `int` | Contador acumulado de eventos de caracteres digitados |
| `fmDateParts` | `ivec4` | `(ano, mês, dia, diaDaSemanaIso1A7)` |
| `fmTimeParts` | `ivec4` | `(hora, minuto, segundo, milissegundos0A999)` |
| `fmDayOfYear` | `int` | Dia do ano |
| `fmWeekOfYear` | `int` | Semana ISO do ano |
| `fmUnixTimeSeconds` | `int` | Segundos desde a época Unix |
| `fmUnixTimeMilliseconds` | `int` | Parte dos milissegundos do horário atual (`0..999`) |
| `fmPartialTick` | `float` | Tick parcial atual |
| `fmGameDeltaTicks` | `float` | Ticks de variação do jogo do Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Ticks de variação em tempo real do Minecraft |
| `fmInWorld` | `int` | `1` quando estiver em um mundo; caso contrário, `0` |
| `fmIsPaused` | `int` | `1` quando estiver pausado; caso contrário, `0` |
| `fmOpacity` | `float` | Multiplicador efetivo de opacidade (`0..1`) |
| `fmVariableCount` | `int` | Quantidade atual de variáveis do FancyMenu |

Valores de ação de tecla (`fmKeyEvent.w`):

- `0` = soltura
- `1` = pressionamento
- `2` = repetição

## 6.3 API de uniforms de variáveis do FancyMenu

As variáveis do FancyMenu são disponibilizadas diretamente como uniforms de runtime (para shaders de plano de fundo, elementos e sobreposições decorativas), sem recompilar o shader quando os valores mudam.

### Nomenclatura

Para cada variável `<name>`, o FancyMenu disponibiliza:

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = a variável existe no momento; `0` = não está presente/foi removida)

Normalização do sufixo do uniform para `<name>`:

- os caracteres permitidos são `[A-Za-z0-9_]`
- todos os outros caracteres são convertidos em `_`
- se o primeiro caractere for um dígito, `_` será adicionado no início

Exemplos:

- variável `player_hp` -> sufixo `player_hp`
- variável `player-hp` -> sufixo `player_hp`
- variável `2nd_phase` -> sufixo `_2nd_phase`

Importante:

- esses uniforms dinâmicos de variáveis **não são declarados automaticamente** no código-fonte do shader (declare manualmente os que usar)
- evite nomes de variáveis que sejam normalizados para o mesmo sufixo, pois eles correspondem ao mesmo nome de uniform GLSL

### Conversão de valores

Dado o valor de texto da variável `v`:

- `fmVarFloat_*`: número de ponto flutuante analisado (valor alternativo `0.0`)
- `fmVarInt_*`: número inteiro analisado (valor alternativo `0`)
- `fmVarBool_*`: interpretação booleana/inteira (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`; caso contrário, valor numérico diferente de zero => `1`)
- a análise de vetores aceita os separadores: espaço em branco, `,`, `;`, `|`
  - `fmVarVec2_*`: os 2 primeiros componentes analisados
  - `fmVarVec3_*`: os 3 primeiros componentes analisados
  - `fmVarVec4_*`: os 4 primeiros componentes analisados
  - se houver menos componentes, o último componente analisado será repetido nos espaços restantes
  - se não houver componentes numéricos, todos os componentes do vetor usarão o valor escalar alternativo

As [variáveis de lista](/variables#text-and-list-variables) fornecem a quantidade de entradas em vez do texto:

- `fmVarFloat_*` e `fmVarInt_*`: quantidade de entradas, como `3` para uma lista com 3 entradas
- `fmVarBool_*`: `1` se a lista tiver entradas; `0` se estiver vazia
- `fmVarVec2_*`, `fmVarVec3_*` e `fmVarVec4_*`: quantidade de entradas em cada componente

Se uma variável for removida:

- `fmVarExists_*` passa a ser `0`
- todos os valores `fmVar*_*` correspondentes são redefinidos como `0`

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

## 7. Modelo de rastreamento de entradas

O FancyMenu rastreia as entradas globalmente e registra um instantâneo delas a cada renderização:

- movimento/arrasto do mouse
- pressionamento/soltura do mouse
- rolagem
- pressionamento/soltura/repetição de tecla
- caractere digitado

Confiabilidade do mouse:

- O runtime concilia os estados dos botões com a consulta de estado do GLFW a cada quadro para evitar que botões fiquem presos.

Se `Pass Input Events To Shader` estiver desativado:

- os uniforms de entrada são redefinidos para valores neutros a cada quadro
- os contadores e eventos são zerados nos dados visíveis ao shader

## 8. Detalhes das entradas de textura

Os canais de recurso (`iChannel# Resource`) esperam texturas 2D.

Estado da textura por canal:

- recurso válido: textura vinculada, largura/altura reais, `iChannelResolution[n].z = 1.0`
- ausente/inativo/None: textura alternativa, `iChannelResolution[n].xyz = (0,0,0)`

Texturas de buffer:

- formato interno: `RGBA16F` (ponto flutuante)
- filtragem: linear
- modo de repetição: limitar às bordas

Isso é adequado para dados multipass (incluindo valores fora do intervalo `[0,1]`).

## 9. Observações sobre renderização e mesclagem

- As passagens de buffer são renderizadas fora da tela, sem mesclagem.
- A passagem final Image usa a configuração `Enable Blending` para composição.
- O wrapper Shadertoy aplica automaticamente `fmOpacity` ao alfa.
- Se necessário, shaders diretos devem aplicar `fmOpacity` manualmente.

## 10. Modelos práticos

## 10.1 Shader mínimo no estilo Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Shader de fragmento direto mínimo

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Feedback multipass mínimo

### Fonte de Buffer A

Roteamento: `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Fonte de Image

Roteamento: `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Lista de verificação para solução de problemas

- Sem saída:
  - verifique se a fonte de Image não está vazia
  - verifique se o modo de compilação corresponde ao seu ponto de entrada (`mainImage` ou `main`)
- Texturas roxas/inválidas:
  - verifique as vinculações de recursos e o roteamento de canais
  - confira `iChannelResolution[n].z` (`0.0` significa inválido/indisponível)
- Coordenadas incorretas no shader direto:
  - use `gl_FragCoord.xy - fmAreaOffset` para obter coordenadas locais à área
- Comportamento de arrasto incorreto:
  - use a opção `Atualizar a posição de iMouse somente enquanto o botão esquerdo estiver pressionado`
- Opacidade não aplicada no shader direto:
  - multiplique o alfa por `fmOpacity` manualmente
