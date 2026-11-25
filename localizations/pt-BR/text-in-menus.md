---
title: Texto em Menus
description: >-
  Como exibir texto em menus com os elementos Text e Tooltip, além de estilizar
  e rolar esse conteúdo.
sourceBlobSha: 557734a5ca4e53d75045d7086642e9c561805b29
---
# Texto em Menus

O FancyMenu tem dois elementos para texto:

- **Text** exibe texto diretamente no menu, desde uma única linha até páginas longas e roláveis, como changelogs, regras ou notícias.
- **Tooltip** exibe uma caixa de texto em um local fixo ou ao lado do mouse, por exemplo, quando o cursor está sobre um botão.

Ambos oferecem suporte a [Markdown](/text-formatting) e [placeholders](/placeholders), além de compartilharem as mesmas opções de aparência e estilo.

<img width="800" alt="Editing a Text element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/text_editor_showcase.gif?raw=true">

> [!TIP]
> Esta página explica os elementos e suas configurações. Para saber tudo o que você pode escrever no texto, como títulos, listas, links e cores, consulte [Formatação de Texto](/text-formatting).

# Adicionando texto

1. Abra um layout no editor de layouts.
2. Clique com o botão direito no fundo do editor e selecione **New Element -> Text**.
3. Clique com o botão direito no novo elemento e selecione **Text Content**.
4. Escreva seu texto e clique em **Done**.

# Conteúdo do texto

## Modo de origem

Clique com o botão direito no elemento e defina **Source Mode**:

- **Direct**: você mesmo digita o texto no editor de texto.
- **Resource**: o texto vem de um arquivo de texto. Clique em **Text Source** para escolher um arquivo local em `<game-directory>/config/fancymenu/assets/`, um URL da web ou um arquivo de pacote de recursos. Consulte [Recursos](/resources).

Fontes da web são ótimas para conteúdo como changelogs ou notícias que precisam estar sempre atualizados, sem que você tenha que atualizar seu modpack.

O FancyMenu mantém na memória o texto de arquivos e fontes da web até o jogo ser fechado. Para carregá-lo novamente, recarregue o FancyMenu usando **menu bar -> Customization -> Reload FancyMenu**.

## Texto dinâmico

O texto pode exibir valores atualizados em tempo real usando [placeholders](/placeholders), por exemplo, `Boas-vindas, {"placeholder":"playername"}!`. Também pode exibir os valores de [variáveis](/variables). O texto é atualizado automaticamente quando esses valores mudam.

## O editor de texto

Ao clicar em **Text Content**, o editor de texto é aberto. Clique em **Placeholders**, no canto superior direito, para procurar todos os placeholders e adicioná-los ao texto.

### Atalhos de formatação

O editor de texto dos elementos Text e Tooltip tem atalhos para formatações comuns. No macOS, use `Cmd` em vez de `Ctrl`.

| Atalho | O que faz |
|---|---|
| `Ctrl + B` | Negrito |
| `Ctrl + I` | Itálico |
| `Ctrl + U` | Sublinhado |
| `Ctrl + L` | Alinhar à esquerda |
| `Ctrl + E` | Centralizar |
| `Ctrl + R` | Alinhar à direita |

- Primeiro, selecione o texto que deseja formatar. Pressione o mesmo atalho novamente para remover a formatação.
- Sem uma seleção, o atalho adiciona os caracteres de formatação e posiciona o cursor entre eles, para que você possa continuar digitando.
- Os atalhos de alinhamento funcionam nas linhas selecionadas ou na linha onde está o cursor. Usar `Ctrl + E` ou `Ctrl + R` em linhas que já têm esse alinhamento volta a alinhá-las à esquerda.
- Clique com o botão direito no editor e abra **Formatting** para ver todos esses atalhos em um menu.

### Outros atalhos

O mesmo editor de texto é aberto para a maioria dos textos no FancyMenu, como valores de ações e muitas configurações de elementos. Estes atalhos funcionam em todos eles. No macOS, use `Cmd` em vez de `Ctrl`.

| Atalho | O que faz |
|---|---|
| `Ctrl + C` | Copiar o texto selecionado |
| `Ctrl + X` | Recortar o texto selecionado |
| `Ctrl + V` | Colar |
| `Ctrl + A` | Selecionar todo o texto |
| `Ctrl + Z` | Desfazer |
| `Ctrl + Y` | Refazer |
| `Ctrl + D` | Duplicar a linha onde está o cursor |
| `Alt + Seta para cima` / `Alt + Seta para baixo` | Mover a linha onde está o cursor para cima ou para baixo |
| `Shift + Teclas de seta` | Selecionar texto |
| `Ctrl + Home` / `Ctrl + End` | Ir para o início ou o fim do texto |
| `Ctrl + G` | Ir para uma linha: digite o número dela e pressione `Enter` |
| `Ctrl + S` | Equivale a **Done** |

Para ver os atalhos do editor de layouts, consulte [Editor de Layouts](/layout-editor#shortcuts).

# Aparência e estilos

Clique com o botão direito no elemento e abra **Markdown** para alterar a aparência do texto.

## Aparência

Uma **Look** define de uma só vez todas as opções de estilo do texto:

- **Pixel**: arte em pixel criada para a fonte do Minecraft, com cores quentes, detalhes dourados e marcadores desenhados à mão.
- **Classic**: a aparência clássica do FancyMenu, com texto branco, caixas cinzas e linhas cinzas.
- **Neutral**: uma aparência limpa, com as cores do tema atual da interface do FancyMenu. As cores são salvas junto com o elemento, então permanecem iguais quando você troca de tema depois.

<img width="800" alt="The three Markdown looks" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_looks.png?raw=true">

Os novos elementos começam com a aparência Pixel. Os elementos de layouts antigos mantêm a aparência Classic que já tinham.

> [!NOTE]
> Escolher uma aparência substitui as alterações de estilo que você fez. Mudou de ideia? É só desfazer com `Ctrl + Z`.

## Opções de estilo

Depois de escolher uma aparência, você ainda pode ajustar cada parte dela. O menu **Markdown** tem opções para **Text**, **Headlines**, **Lists**, **Links**, **Code**, **Quotes**, **Callouts**, **Tables**, **Images** e **Separators**. Passe o cursor sobre uma opção para ver o que ela faz.

**Markdown -> Text** reúne as opções básicas, como a cor e a sombra do texto, o espaçamento entre linhas e o espaço entre o texto e as bordas do elemento.

## Desativando o Markdown

Se você não precisa de Markdown, desative **Markdown -> Markdown Parser**. Assim, o texto aparece exatamente como você o digitou, e o processamento também fica um pouco mais rápido em textos muito longos.

## Outras configurações de texto

Clique com o botão direito no elemento para encontrar também estas opções:

- **Text Scale** aumenta ou diminui o texto.
- **Case Mode** exibe o texto normalmente, todo em maiúsculas ou todo em minúsculas.
- **Auto Line Wrapping** quebra linhas que são longas demais para o elemento. Quando desativada, as linhas longas continuam sem quebra.
- **Remove HTML Line Breaks** remove as quebras de linha HTML (`<br>`) do texto, o que é útil para textos de sites.

# Fundo

Os elementos Text podem desenhar um painel atrás do texto. Abra **Background** no menu de contexto do elemento:

- **Show Background** ativa ou desativa o painel. Essa opção vem ativada nos novos elementos Text.
- Por padrão, é usado um painel escuro integrado. Você pode usar sua própria textura, com [divisão em nove partes](/nine-slicing-and-tiling) e repetição para manter as bordas no formato correto.
- **Padding** define a distância que o fundo se estende além do texto.
- **Reach Behind Scroll Bars** permite que o fundo cubra também as barras de rolagem. Quando desativada, as barras ficam ao lado do fundo.

Os Tooltips têm seu próprio menu **Background**, onde você pode definir uma textura e sua divisão em nove partes.

# Rolagem

Um elemento Text permite rolar quando o texto não cabe nele. Use a roda do mouse para rolar. Segure `Shift` para rolar na horizontal.

**Scroll Direction** define se o texto rola **Vertical**, **Horizontal** ou em **Both** as direções. Nas direções em que não há rolagem, tudo o que não couber será cortado.

## Configurações de rolagem

Abra **Scrolling** no menu de contexto do elemento:

| Configuração | O que faz |
|---|---|
| **Let Players Scroll** | Define se os jogadores podem rolar o texto. Quando desativada, o texto só rola automaticamente ou por meio de ações. |
| **Scroll Speed** | Define o quanto uma etapa da roda do mouse rola. |
| **Smooth Scrolling** | Faz o texto deslizar em vez de pular. |
| **Drag to Scroll** | Permite que os jogadores arrastem o texto com o mouse, como em uma tela sensível ao toque. |
| **Scroll with Keyboard** | Quando o cursor está sobre o texto, `Page Up` e `Page Down` rolam uma página, e `Home` e `End` vão para o início e o fim. |
| **Snap** | Define onde o texto para: em qualquer lugar (**Off**), com uma linha inteira no topo (**To Lines**), com um título no topo (**To Headlines**) ou avançando uma página inteira de cada vez (**To Pages**). |
| **Start At** | Define se o texto começa no **Start** ou no **End**. O fim é útil para coisas como logs, em que as informações mais recentes aparecem por último. |
| **Reset When Screen Opens** | Faz o texto voltar ao início sempre que a tela é aberta. Quando desativada, a posição da rolagem é mantida até o jogo ser fechado. |

## Rolagem automática

Abra **Auto-Scroll** para fazer o texto rolar devagar por conta própria, como em créditos ou em um letreiro de notícias:

- **Scroll on Its Own** ativa a rolagem automática.
- **Speed [Pixels per Second]** define a velocidade da rolagem.
- **Start Over at the End** reinicia o texto no início quando ele chega ao fim.
- **Pause While Hovered** interrompe a rolagem enquanto o cursor está sobre o texto, para que os jogadores possam ler com calma.

## Barras de rolagem

Abra **Scroll Bars** para alterar as barras:

- **Show** define quando as barras aparecem: **Always**, somente **While Scrolling** ou **Never**. Mesmo com **Never**, a roda do mouse continua rolando o texto.
- **Thickness** define a espessura das barras.
- **Vertical Bar on the Left** e **Horizontal Bar on Top** movem as barras para o lado oposto.
- **Scroll Grabber Style** escolhe a aparência dos controles deslizantes: **Theme Bar** (nas cores do tema atual da interface do FancyMenu) ou **Pixel Handle** (arte em pixel que combina muito bem com a aparência Pixel).
- **Scroll Grabber Textures** e **Scroll Grabber Color [HEX]** substituem os controles deslizantes por texturas ou cores personalizadas.
- **Scroll Bar Backgrounds** adiciona texturas atrás dos controles deslizantes, ao longo do caminho percorrido por eles.

## Rolagem com ações

Você também pode controlar e acompanhar a rolagem em outras partes do FancyMenu:

- A [ação](/action-scripts) **Scroll an Element** rola um elemento Text até o início, o fim, uma posição, um número de linha ou a primeira linha que contém um determinado texto.
- Os [placeholders](/placeholders) **Element Scroll Position**, **Element Scroll Percent** e **Element Scroll Content Size** informam o quanto o texto foi rolado e qual é o tamanho dele.
- O [requisito](/conditions) **Is Element Scrolled to End** verifica se o texto chegou ao fim, por exemplo, para só habilitar um botão "Aceitar" depois que as regras forem lidas.
- Os [listeners](/listeners) **On Element Scrolled**, **On Element Scrolled to Start** e **On Element Scrolled to End** executam ações enquanto o texto rola.

Todos eles precisam do [identificador do elemento](/element-identifiers) Text.

# Interação com elementos Text

Os elementos Text reagem ao mouse para que seus links e barras de rolagem funcionem. Isso também significa que eles capturam os cliques, e os botões que estiverem atrás ou na frente de um elemento Text podem não recebê-los.

Se isso for um problema, clique com o botão direito no elemento Text e desative **Interactable**. O texto não poderá mais ser rolado e seus links não poderão mais ser clicados.

# Tooltips

Os elementos Tooltip funcionam como os elementos Text, mas sem rolagem:

- As configurações de texto, aparência e estilo são as mesmas dos elementos Text.
- **Follow Mouse** faz o tooltip acompanhar o mouse.
- Use [requisitos](/conditions) para decidir quando o tooltip aparece, como o requisito [**Is Element Hovered**](/conditions#is-element-hovered), que o exibe quando o cursor está sobre um botão.
