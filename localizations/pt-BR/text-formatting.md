---
title: Formatação de Texto
description: Como formatar texto com Markdown e os códigos de formatação do Minecraft.
---

# Formatação de Texto

O FancyMenu tem vários recursos para deixar o conteúdo de texto nos layouts *mais sofisticado*!

Elementos de texto têm suporte completo a **Markdown**, com alguns extras interessantes, e a maior parte dos outros conteúdos de texto também suporta o sistema de **formatação de texto do Minecraft**. Até os rótulos de botões têm suporte a **componentes de texto do Minecraft**, que permitem usar fontes personalizadas e muito mais.

# Markdown

Os **elementos de texto** do FancyMenu têm suporte total a Markdown, o que significa que você pode formatar o conteúdo de texto adicionando caracteres especiais a ele.

Por exemplo, para deixar um texto em negrito, você adiciona `**` antes e depois do texto em negrito, então `**Algum texto em negrito que é bem negrito.**` ficará assim:
**Algum texto em negrito que é bem negrito.**

O Markdown do FancyMenu até tem algumas coisas especiais que o tornam ainda mais poderoso!

> Markdown **NÃO FUNCIONA** para outros textos, como rótulos de botões. Ele funciona apenas em **ELEMENTOS DE TEXTO**. Para todo o resto, use [os códigos de formatação do Minecraft](/text-formatting#minecraft-text-formatting).
{.is-danger}

## Fontes

Você pode mostrar texto em uma fonte personalizada carregada via pacote de recursos adicionando `%!!<font_name>%` antes do texto e `%!!%` depois.

Uma fonte válida incluída no jogo base é `uniform`, então para exibir texto na fonte `uniform`, faça assim:
`%!!uniform%este é uma fonte personalizada%!!%`

Isso exibirá `este é uma fonte personalizada` na fonte `uniform`.

## Cor do Texto (HEX)

É possível mostrar texto em uma cor HEX específica adicionando `%<HEX_color>%` antes do texto e `%#%` depois.

Uma cor HEX válida para verde é `#77fc03`, então para mostrar texto nessa cor, faça assim:
`%#77fc03%este texto é verde!%#%`

Isso mostrará `este texto é verde!` em `#77fc03` (verde).

Certifique-se de que a cor HEX comece com `#`!

O FancyMenu 3.9.0 também suporta nomes de cores comuns no estilo HTML nesse mesmo código de formatação de cor:

```
%#red%Este texto é vermelho!%#%
```

Nomes suportados: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` e `transparent`.

## Alinhamento de Texto

Você pode alinhar linhas de texto começando uma linha com o código de formatação de alinhamento específico, não adicionando mais nada, depois as linhas de texto que deseja mostrar com esse alinhamento e então o código de alinhamento novamente em uma linha extra.

Todo o conteúdo de texto é **alinhado à esquerda por padrão**, então só existem códigos de formatação para texto **centralizado** e **alinhado à direita**.

### Centralizado

Para centralizar linhas de texto, use o código de formatação `^^^`.

Exemplo:
```
Este texto não está centralizado.

^^^
Este texto está centralizado.
Este texto também está centralizado.
^^^

Este texto não está mais centralizado.
```

### Alinhado à Direita

Para mostrar linhas de texto alinhadas à direita, use o código de formatação `|||`.

Exemplo:
```
Este texto não está alinhado à direita.

|||
Este texto está alinhado à direita.
Este texto também está alinhado à direita.
|||

Este texto não está mais alinhado à direita.
```

## Títulos

Para mostrar **uma linha de texto** como título (maior e sublinhado), adicione `# ` (muito grande), `## ` (grande) ou `### ` (pequeno) antes da linha de texto.

Exemplo:
`## Título Grande`

## Negrito

Adicione `**` antes e depois do texto para deixá-lo em **negrito**.

Exemplo:
`**conteúdo de texto em negrito**`

## Itálico

Adicione `_` OU `*` antes e depois do texto para deixá-lo em *itálico*.

Exemplo:
`*conteúdo de texto em itálico*`

## Tachado

Adicione `~` antes e depois do texto para deixá-lo ~~tachado~~.

Exemplo:
`~conteúdo de texto tachado~`

## Links

Você pode adicionar hyperlinks ao conteúdo de texto para abrir um site quando clicados.

O texto que deve aparecer como [hyperlink](https://google.com) precisa ser colocado entre `[ ]`, seguido do link real entre `( )`.

Então, se você quiser tornar `conteúdo de texto de exemplo` clicável e abrir `https://example-website.net`, faça assim:
`[conteúdo de texto de exemplo](https://example-website.net)`

## Eventos de Clique e Hover

O FancyMenu 3.9.0 adiciona eventos de clique e hover em Markdown para Elementos de Texto e outros textos em Markdown.

Eventos de clique usam o prefixo `click:`:

```
[algum texto clicável](click:unique_text_click_event_id)
```

Eventos de hover usam o prefixo `hover:`:

```
[algum texto com hover](hover:unique_text_hover_event_id)
```

Use os listeners **On Markdown Text Clicked** e **On Markdown Text Hovered** para reagir a esses eventos. Ambos expõem o ID do evento como `$$text_event_id`.

## Imagens

Markdown suporta exibir imagens em conteúdo de texto.

O FancyMenu suporta recursos do Minecraft, recursos locais e recursos da web em Markdown.

Para adicionar uma imagem, comece uma linha de texto com `![](`, depois [a URL, o Resource Location ou o caminho para o recurso](/resources) e então `)`.

Então, para mostrar o recurso da web `https://example-website.net/image.png`, faça assim:
`![](https://example-website.net/image.png)`

Imagens também podem ser **hyperlinks** envolvendo a linha inteira da imagem em um **hyperlink** assim:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> Recursos locais precisam estar em `/config/fancymenu/assets/` !
{.is-warning}

## Citação

Para formatar texto como citação, comece uma linha com `> `.
Isso formatará todas as linhas seguintes como citação até encontrar uma linha **em branco**.

Exemplo:
```
Este texto não ficará como citação.

> Este texto ficará como citação.
Este texto também ficará como citação.

Este texto não ficará mais como citação.
```

## Listas com Marcadores

Para mostrar texto como uma lista com marcadores assim:
- Entrada 1
- Entrada 2
  - Subentrada

Você só precisa começar uma linha com `- `.

Exemplo:
```
- Entrada 1
- Entrada 2
  - Subentrada
```

## Linha de Separação

Para adicionar uma linha de separação ao seu texto com a largura de uma linha inteira, basta começar uma linha com `---` e não adicionar mais nada.

Isso ficará mais ou menos assim:

---

## Blocos de Código

Blocos de código podem ajudar você a exibir texto como `texto simples` sem que o Markdown tente formatá-lo, ou simplesmente para exibir texto em um estilo semelhante a código sem quebra automática de linhas.

Um bloco de código de uma linha (entre outros textos) começa e termina com \` , o que na verdade é bem difícil de mostrar em um texto Markdown..

Uma linha de texto contendo um bloco de código de uma linha se parece com isto:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Blocos de código de várias linhas envolvem várias linhas em um bloco grande e começam com uma linha que contém apenas \`\`\` então o conteúdo de texto e depois \`\`\` novamente:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texto Simples

O código de formatação de texto simples ignora todos os outros códigos de formatação dentro dele.

Ele funciona de forma parecida com blocos de código, mas não o formata como um bloco de código. Em vez disso, ele aparece como texto normal, porém sem nenhuma formatação.

Para envolver uma parte do texto dentro de uma linha em um código de formatação de texto simples, você precisa adicionar `;;` antes e depois da parte do texto que deseja mostrar como texto simples, assim:

```
Esta é uma linha de texto com ;;**esta parte**;; aparecendo como texto sem formatação, com o código de formatação ** (negrito) visível, e _esta parte_ como texto itálico normalmente formatado.
```

Texto simples também funciona como um código envolvente de várias linhas. Para envolver linhas inteiras, adicione `;;;` antes e depois da(s) linha(s) que deseja mostrar como texto simples, assim:

```
;;;
Esta linha será mostrada **sem formatação** com os códigos de formatação ** (negrito) visíveis.
Esta linha também será mostrada _sem formatação_ com os códigos de formatação _ (itálico) visíveis.
;;;

Esta linha voltará a parecer **normal** com "normal" formatado como texto em negrito.
```

# Formatação de Texto do Minecraft

O próprio Minecraft tem um sistema de formatação bem bom que funciona de forma parecida com Markdown, no qual você adiciona caracteres especiais ao conteúdo de texto para formatá-lo.

Para saber mais sobre o sistema de formatação do Minecraft, confira [esta página da wiki do Minecraft](https://minecraft.wiki/w/Formatting_codes).

> A wiki vai dizer que o prefixo do código de formatação é `§`, mas no FancyMenu você precisa substituí-lo por `&`. Todo o resto permanece igual.
{.is-warning}

> Os **elementos de texto** são muito complexos e, para oferecer suporte ao Markdown, o compromisso foi **quebrar os códigos de formatação Vanilla do Minecraft**, então esses códigos não funcionarão bem em Elementos de Texto (apenas a primeira palavra é formatada após o código de formatação, etc.). Em vez disso, você deve usar os códigos de formatação do Markdown nos Elementos de Texto.
{.is-danger}

# Componentes de Texto do Minecraft (Sistema de Componentes Brutos)

O sistema de componentes de texto do Minecraft é bem poderoso para conteúdo de texto de **uma única linha**, como **rótulos de botões**.

No Minecraft Vanilla, você pode usá-lo nos comandos `/tellraw` e `/title` (e provavelmente em outros lugares).
Ele formata texto serializado em JSON, então você pode adicionar atributos de formatação ao conteúdo de texto.

Para saber mais sobre componentes de texto em detalhes, confira [esta página da wiki do Minecraft](https://minecraft.wiki/w/Raw_JSON_text_format).
Para saber mais sobre fontes no Minecraft, confira [esta página da wiki do Minecraft](https://minecraft.wiki/w/Resource_pack#Fonts).

Para fazer o FancyMenu detectar um rótulo de botão como **componente de texto**, não coloque nada além do texto do componente serializado como rótulo, assim:
`{"text":"Texto do Rótulo do Botão","font":"uniform"}`

O exemplo acima mostrará o rótulo do botão `Texto do Rótulo do Botão` na fonte `uniform`.

> Você pode usar os placeholders do FancyMenu no valor `text` dos componentes.
{.is-info}
