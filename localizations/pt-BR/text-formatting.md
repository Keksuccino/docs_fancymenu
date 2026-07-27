---
title: Formatação de Texto
description: Como formatar texto com Markdown e os códigos de formatação do Minecraft.
---

# Formatação de Texto

[Elementos de texto](./elements#text) suportam Markdown. Outros campos de texto usam a formatação do Minecraft, e os rótulos de botões podem usar componentes de texto do Minecraft.

# Markdown

Os **elementos de texto** do FancyMenu têm suporte completo a Markdown, o que significa que você pode formatar o conteúdo adicionando caracteres especiais a ele.

Por exemplo, para deixar o texto em negrito, você adiciona `**` antes e depois do texto em negrito, então `**Algum texto em negrito que é muito em negrito.**` ficará assim:
**Algum texto em negrito que é muito em negrito.**

O FancyMenu também suporta as extensões documentadas abaixo.

> [!CAUTION]
> O Markdown funciona apenas em **elementos de texto**. Para rótulos de botões e outros campos de texto, use [os códigos de formatação do Minecraft](#minecraft-text-formatting).

## Fontes

Você pode exibir texto em uma fonte personalizada carregada via pacote de recursos adicionando `%!!<nome_da_fonte>%` antes do texto e `%!!%` depois.

Uma fonte válida incluída no jogo base é `uniform`, então, para exibir texto na fonte `uniform`, faça assim:
`%!!uniform%este é um tipo de fonte personalizado%!!%`

Isso exibirá `este é um tipo de fonte personalizado` na fonte `uniform`.

## Cor do Texto (HEX)

É possível exibir texto em uma cor HEX específica adicionando `%<cor_HEX>%` antes do texto e `%#%` depois.

Uma cor HEX válida para verde é `#77fc03`, então, para mostrar texto nessa cor, faça assim:
`%#77fc03%este texto é verde!%#%`

Isso mostrará `este texto é verde!` como `#77fc03` (verde).

Certifique-se de que a cor HEX começa com `#`!

Nomes de cores comuns semelhantes aos do HTML são suportados no mesmo código de formatação de cor:

```
%#red%Este texto é vermelho!%#%
```

Nomes suportados: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` e `transparent`.

## Alinhamento de Texto

Você pode alinhar linhas de texto começando uma linha com o código de formatação de alinhamento específico, sem mais nada, depois as linhas de texto que deseja mostrar com esse alinhamento e, em seguida, o código de alinhamento novamente em uma linha extra.

Todo o conteúdo de texto é **alinhado à esquerda por padrão**, então só existem códigos de formatação para **centralizado** e **alinhado à direita**.

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

Adicione `~` antes e depois do texto para deixá-lo ~~riscado~~.

Exemplo:
`~conteúdo de texto tachado~`

## Hiperlinks

Você pode adicionar hiperlinks ao conteúdo de texto que abrem um site quando clicados.

O texto que deve aparecer como [hiperlink](https://google.com) precisa estar envolvido por `[ ]`, seguido do link real envolvido por `( )`.

Então, se você quiser tornar `exemplo de conteúdo de texto` clicável e abrir `https://example-website.net`, faça assim:
`[exemplo de conteúdo de texto](https://example-website.net)`

## Eventos de Clique e Hover

Eventos Markdown de clique e hover estão disponíveis para [elementos de texto](./elements#text) e outros textos em Markdown. Use [**Ao Clicar no Texto Markdown**](./listeners#on-markdown-text-clicked-text_clicked) e [**Ao Passar o Mouse sobre o Texto Markdown**](./listeners#on-markdown-text-hovered-text_hovered) para reagir a eles.

Eventos de clique usam o prefixo `click:`:

```
[algum texto clicável](click:unique_text_click_event_id)
```

Eventos de hover usam o prefixo `hover:`:

```
[algum texto com hover](hover:unique_text_hover_event_id)
```

Ambos os listeners expõem o ID do evento como `$$text_event_id`.

## Imagens

O Markdown suporta a exibição de imagens no conteúdo de texto.

O FancyMenu suporta recursos do Minecraft, recursos locais e recursos da web em Markdown.

Para adicionar uma imagem, comece uma linha de texto com `![](`, depois [a URL, a Localização do Recurso ou o Caminho para o recurso](./resources) e então `)`.

Então, para mostrar o recurso da web `https://example-website.net/image.png`, faça assim:
`![](https://example-website.net/image.png)`

Imagens também podem ser **hiperlinks** envolvendo toda a linha de texto da imagem em um **hiperlink** assim:
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> Recursos locais precisam estar em `<game-directory>/config/fancymenu/assets/`!

## Citação

Para formatar texto como citação, comece uma linha de texto com `> `.
Isso formatará todas as linhas seguintes como citação até encontrar uma linha **em branco**.

Exemplo:
```
Isto não parecerá uma citação.

> Isto parecerá uma citação.
Esta também parecerá uma citação.

Isto não parecerá mais uma citação.
```

## Listas com Marcadores

Para exibir texto como uma lista com marcadores como esta:
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

Para adicionar uma linha de separação ao seu texto com a largura de uma linha inteira de texto, basta começar uma linha com `---` e não adicionar mais nada.

Ela ficará algo assim:

---

## Blocos de Código

Blocos de código podem ajudar a exibir texto como `texto simples` sem que o Markdown tente formatá-lo, ou simplesmente para exibir texto em um estilo semelhante a código sem quebra automática das linhas de texto.

Um bloco de código de uma única linha (entre outros textos) começa e termina com \` , o que é na verdade bem difícil de mostrar em um texto Markdown..

Uma linha de texto contendo um bloco de código de uma única linha tem esta aparência:

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Blocos de código com várias linhas envolvem várias linhas em um único bloco grande e começam com uma linha que contém apenas \`\`\` depois o conteúdo do texto e então \`\`\` novamente:

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texto Simples

O código de formatação de texto simples ignora todos os outros códigos de formatação dentro dele.

Ele funciona de forma parecida com blocos de código, mas não o formata como um bloco de código. Em vez disso, ele aparece como texto normal, mas sem nenhuma formatação.

Para envolver uma parte do texto dentro de uma linha em um código de formatação de texto simples, você precisa adicionar `;;` antes e depois da parte do texto que deseja mostrar como texto simples, assim:

```
Esta é uma linha de texto com ;;**esta parte**;; aparecendo como texto sem formatação, com o código de formatação ** (negrito) visível e _esta parte_ como texto itálico formatado normalmente.
```

Texto simples também funciona como um código envolvente de várias linhas. Para envolver linhas inteiras, adicione `;;;` antes e depois da(s) linha(s) que deseja mostrar como texto simples, assim:

```
;;;
Esta linha será exibida **sem formatação** com os códigos de formatação ** (negrito) visíveis.
Esta linha também será exibida _sem formatação_ com os códigos de formatação _ (itálico) visíveis.
;;;

Esta linha voltará a parecer **normal** com "normal" formatado como texto em negrito.
```

# Formatação de Texto do Minecraft

Os códigos de formatação do Minecraft funcionam em campos de texto formatados compatíveis em todo o FancyMenu. Use `&` no lugar do prefixo `§` do Minecraft; por exemplo, `&cAviso` exibe texto em vermelho.

Veja a [referência de códigos de formatação da Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes) para conhecer as cores e estilos disponíveis.

> [!CAUTION]
> Os códigos de formatação do Minecraft são pouco confiáveis em **elementos de texto** porque esses elementos interpretam Markdown. Em vez disso, use a formatação Markdown descrita acima.

# Componentes de Texto do Minecraft (Sistema de Componentes Brutos)

O sistema de componentes de texto do Minecraft é bem poderoso para conteúdo de texto de **uma única linha**, como **rótulos de botões**.

No Minecraft Vanilla, você pode usá-lo nos comandos `/tellraw` e `/title` (e provavelmente em outros lugares).
Ele é texto formatado serializado em JSON, então você pode adicionar atributos de formatação ao conteúdo de texto.

Para saber mais sobre componentes de texto em detalhes, consulte [esta página da Minecraft Wiki](https://minecraft.wiki/w/Raw_JSON_text_format).
Para saber mais sobre fontes no Minecraft, consulte [esta página da Minecraft Wiki](https://minecraft.wiki/w/Resource_pack#Fonts).

Para fazer o FancyMenu detectar um rótulo de botão como **componente de texto**, não defina nada além do texto serializado do componente como rótulo, assim:
`{"text":"Texto do rótulo do botão","font":"uniform"}`

O exemplo acima mostrará o rótulo do botão `Texto do rótulo do botão` na fonte `uniform`.

> [!NOTE]
> Você pode usar os placeholders do FancyMenu no valor `text` dos componentes.
