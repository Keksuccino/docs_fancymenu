---
title: Rotacionar e inclinar elementos
description: >-
  Rotacione e incline elementos e suas alças no editor de layout, usando valores
  exatos ou placeholders.
sourceBlobSha: e36d9f5b6a1f4253312e5eee56e1facc1551dcd3
---

# Rotacionar e inclinar elementos

A maioria dos elementos pode ser rotacionada e inclinada. Ambas as transformações acontecem em torno do centro do elemento, que mantém sua posição e seu tamanho.

- **Rotação** gira o elemento, como o ponteiro de um relógio.
- **Inclinação vertical** inclina o elemento para trás, e a **Inclinação horizontal** o vira para o lado. Elementos inclinados são exibidos sem perspectiva, então ficam apenas mais baixos ou mais estreitos. Com as duas inclinações, eles também ficam oblíquos.

<img width="800" alt="Quatro elementos de texto sobre um fundo de menu: um rotacionado em 15 graus, um com inclinação vertical de 45 graus que fica mais baixo, um com inclinação horizontal de 45 graus que fica mais estreito e um com as duas inclinações, que fica oblíquo. Caixas claras atrás deles mostram como seriam sem rotação e inclinação." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_axes.png?raw=true">

# No editor de layout

<img width="800" alt="No editor de layout, um adesivo da Temporada 3 é rotacionado com a alça no círculo ao redor dele; em seguida, um painel de notas da atualização é inclinado com as alças nas linhas à direita e abaixo dele" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_editor.gif?raw=true">

Selecione um elemento no [editor de layout](/layout-editor) e arraste suas alças:

- A alça no círculo ao redor do elemento o rotaciona.
- A alça na linha à direita define a **Inclinação vertical**; a alça na linha abaixo define a **Inclinação horizontal**. O meio da linha corresponde a nenhuma inclinação.

Enquanto arrasta:

- Segure `Shift` para ajustar aos incrementos: 45 graus para a rotação e 15 graus para a inclinação.
- Quando estiver perto de 0, as alças se ajustam a 0, facilitando deixar o elemento reto novamente.
- O canto superior esquerdo do elemento mostra sua rotação e inclinação.

É bom saber:

- A moldura de seleção permanece reta. Clique dentro dela para selecionar ou mover o elemento.
- As alças só aparecem quando um elemento está selecionado.
- Um elemento sem círculo ou linhas não pode ser rotacionado nem inclinado. Consulte [Elementos sem rotação ou inclinação](#elementos-sem-rotação-ou-inclinação).
- **barra de menu -> Janela -> Controles de rotação do elemento** e **Controles de inclinação do elemento** ocultam as alças de todos os elementos.

# Valores exatos

Clique com o botão direito no elemento para acessar estas configurações. Cada uma delas tem as opções **Definir usando seletor numérico**, **Definir como texto simples** e **Redefinir para o padrão**.

| Configuração | O que faz |
|---|---|
| **Rotação** | Os graus que o elemento gira no sentido horário, como `90` para um quarto de volta. Valores negativos giram no sentido anti-horário. |
| **Inclinação vertical** | O quanto o elemento inclina para trás, de `-60` a `60` graus. |
| **Inclinação horizontal** | O quanto o elemento vira para o lado, de `-60` a `60` graus. |

Uma única inclinação tem a mesma aparência com valores positivos e negativos. Quando as duas inclinações são usadas, os sinais determinam para que lado o elemento fica oblíquo.

## Com placeholders

Para rotacionar ou inclinar um elemento usando uma [variável](/variables) ou outro [placeholder](/placeholders):

1. Clique com o botão direito no elemento e ative **Modo avançado de rotação**, **Modo avançado de inclinação vertical** ou **Modo avançado de inclinação horizontal**.
2. Clique em **Rotação**, **Inclinação vertical** ou **Inclinação horizontal**, depois em **Definir como texto simples** e insira o placeholder.

Os modos avançados mantêm seu próprio valor e ocultam a alça, para que arrastá-la não substitua o placeholder. Ao desativar um deles, o elemento volta ao valor anterior.

Um logotipo que dá uma volta a cada 3,6 segundos, usando esta **Rotação** no **Modo avançado de rotação**. Divida por um valor maior que `10` para deixá-lo mais lento:

```
{"placeholder":"calc","values":{"expression":"{"placeholder":"unix_time"} / 10 % 360"}}
```

Uma agulha que aponta para o ângulo indicado pela variável `needle_angle`, que pode ser definida por botões ou por um [controle deslizante](/elements#slider):

```
{"placeholder":"getvariable","values":{"name":"needle_angle"}}
```

# Cliques e o mouse

<img width="800" alt="O ponteiro sobre um botão Entrar no servidor rotacionado: nos pontos em que ficariam os cantos do botão reto, nada acontece; nas extremidades do botão rotacionado, ele acende" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/rotating_tilting_hover.gif?raw=true">

Botões, controles deslizantes, links e barras de rolagem de elementos de texto respondem ao mouse onde aparecem, inclusive quando estão rotacionados ou inclinados. O mesmo vale para os requisitos [**O elemento está sob o cursor**](/conditions#is-element-hovered), [**Algum elemento está sob o cursor**](/conditions#is-any-element-hovered) e [**Algum botão está sob o cursor**](/conditions#is-any-button-hovered).

> [!NOTE]
> Caixas de seleção, campos de entrada de texto, elementos arrastáveis e navegadores continuam respondendo dentro da área que ocupariam sem rotação ou inclinação. Mantenha-os retos.

# Elementos sem rotação ou inclinação

- Sem rotação nem inclinação: [Áreas roláveis](/scrollable-areas), [Shaders GLSL](/elements#glsl-shader), [Modelos JSON de blocos/itens](/elements#blockitem-json-model), [Entidades de jogador](/player-entities) e [elementos vanilla](/vanilla-elements), como os botões da própria tela.
- Com rotação, mas sem inclinação: [Dicas de ferramenta](/elements#tooltip) e [Itens](/elements#item).

Os elementos dentro de uma área rolável podem ser rotacionados e inclinados; somente a própria área não pode.

Os elementos de [Texto de abertura](/splash-text) também têm uma **Rotação** própria, mais abaixo no menu aberto com o botão direito, para criar sua inclinação característica. Ela funciona em conjunto com a rotação descrita nesta página.
