---
title: Formatação de texto
description: >-
  Como formatar texto com Markdown, códigos de formatação do Minecraft e
  componentes de texto.
sourceBlobSha: c6ddde5939e929b3d4c04541f0b104ee6ee795bc
---
# Formatação de texto

O FancyMenu oferece três maneiras de formatar texto:

- **Markdown** para [elementos de Texto e Dica](/text-in-menus): títulos, listas, cores, imagens, tabelas e muito mais.
- **Códigos de formatação do Minecraft**, como `&c`, para aplicar cores rapidamente. Eles funcionam em quase todos os campos de texto, inclusive em textos Markdown.
- **Componentes de texto do Minecraft** para rótulos de botões e controles deslizantes.

> [!TIP]
> Esta página explica *como escrever* texto formatado. Para aprender a adicionar texto aos seus menus, mudar sua aparência ou fazê-lo rolar, consulte [Texto nos menus](/text-in-menus).

<img width="800" alt="Markdown em um elemento de Texto" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_showcase.png?raw=true">

# Markdown

O Markdown formata o texto com alguns caracteres especiais ao redor dele. Por exemplo, `**negrito**` vira texto em **negrito**.

O Markdown funciona em [elementos de Texto](/elements#text) e [elementos de Dica](/elements#tooltip). Os caracteres que você escreve determinam *o que* algo é (um título, uma lista, uma citação). A [aparência](/text-in-menus#looks-and-styles) do elemento define como ele fica, como suas cores e seus tamanhos.

## Visão geral rápida

| Você escreve | O resultado |
|---|---|
| `**negrito**` ou `__negrito__` | Texto em negrito |
| `*itálico*` ou `_itálico_` | Texto em itálico |
| `++sublinhado++` | Texto sublinhado |
| `~~riscado~~` | Texto riscado |
| `` `código` `` | Código em linha |
| `[Abrir site](https://example.com)` | Um link clicável |
| `%#ff5555%texto vermelho%#%` | Texto colorido |
| `# Título` | Um título |
| `- Item` | Uma lista com marcadores |
| `1. Item` | Uma lista numerada |
| `> Texto` | Uma citação |
| `> [!TIP]` | Uma caixa de destaque |
| `---` | Uma linha separadora |

## Estilos de texto

| Estilo | Como escrever |
|---|---|
| **Negrito** | `**texto**` ou `__texto__` |
| **Itálico** | `*texto*` ou `_texto_` |
| **Sublinhado** | `++texto++` |
| **Tachado** | `~~texto~~` (também funciona usar um único `~` de cada lado) |

Você pode combinar estilos, como em `***negrito e itálico***`.

Sublinhados únicos dentro de palavras continuam sendo sublinhados normais; assim, `meu_layout_legal` não fica em itálico. Nomes como `C++` também permanecem como estão.

> [!TIP]
> No editor de texto, selecione um trecho e pressione `Ctrl + B`, `Ctrl + I` ou `Ctrl + U` (`Cmd` no macOS) para deixá-lo em negrito, itálico ou sublinhado. Consulte [Atalhos de formatação](/text-in-menus#formatting-shortcuts).

## Cor do texto (HEX)

Coloque `%<cor HEX>%` antes do texto e `%#%` depois dele:

```
%#77fc03%Este texto é verde!%#%
```

A cor HEX precisa começar com `#`. Você também pode usar nomes de cores:

```
%#red%Este texto é vermelho!%#%
```

Nomes aceitos: `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` e `transparent`.

## Fontes

Para exibir o texto em outra fonte, coloque `%!!<nome da fonte>%` antes dele e `%!!%` depois. A fonte pode ser do Minecraft ou de um pacote de recursos.

```
%!!uniform%Este texto usa a fonte uniform%!!%
```

## Alinhamento do texto

Por padrão, o texto fica alinhado à esquerda. Para centralizar as linhas ou alinhá-las à direita, coloque o código de alinhamento em uma linha separada antes e depois delas:

- `^^^` centraliza as linhas.
- `|||` alinha as linhas à direita.

```
Esta linha fica alinhada à esquerda.

^^^
Esta linha fica centralizada.
Esta também.
^^^

|||
Esta linha fica alinhada à direita.
|||
```

> [!TIP]
> No editor de texto, `Ctrl + L`, `Ctrl + E` e `Ctrl + R` (`Cmd` no macOS) alinham as linhas selecionadas à esquerda, ao centro ou à direita.

## Títulos

Comece uma linha com `# ` (maior), `## ` (grande) ou `### ` (pequeno):

```
# Boas-vindas!
## Novidades
### Título pequeno
```

## Listas

<img width="460" alt="Listas em Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_lists.png?raw=true">

### Listas com marcadores

Comece uma linha com `- `. Adicione dois espaços antes do marcador para cada nível de aninhamento:

```
- Primeiro item
- Segundo item
  - Item aninhado
    - Mais um nível
```

### Listas numeradas

Comece uma linha com um número e um ponto ou parêntese:

```
1. Abra a barra de menus
2. Clique em Personalização
3) Isto também funciona
```

### Marcadores de notas de atualização

As linhas também podem começar com `+`, `-`, `~` ou `*`. Cada um deles recebe seu próprio marcador, o que é perfeito para notas de atualização e registros de alterações:

```
+ Novo menu principal adicionado
- Logotipo antigo removido
~ Cores dos botões alteradas
* Falha na inicialização corrigida
```

| Marcador | Significado |
|---|---|
| `+` | Algo foi adicionado |
| `-` | Algo foi removido |
| `~` | Algo foi alterado |
| `*` | Algo que merece destaque |

Um item com `-` só recebe o marcador de “removido” quando a lista também tem um item com `+`. Caso contrário, ele é um item normal de uma lista com marcadores. Você pode alterar isso em **Markdown -> Listas -> Marcadores extras (+ - ~ \*) -> Marcador - usado**.

> [!NOTE]
> Novos elementos de Texto e Dica vêm com listas numeradas, marcadores de notas de atualização e [destaques](#callouts) ativados. Eles ficam desativados em elementos de layouts antigos para que o texto não mude de repente. Ative-os no menu **Markdown** do elemento: **Listas -> Listas numeradas**, **Listas -> Marcadores extras (+ - ~ \*)** e **Destaques**.

## Citações

Comece uma linha com `> ` para criar uma citação. Ela continua até a próxima linha vazia:

```
> Isto é uma citação.
Esta linha também faz parte dela.

Esta linha já é texto normal novamente.
```

As linhas dentro de uma citação também podem começar com `>`, e uma linha contendo apenas `>` adiciona uma linha vazia à citação:

```
> Primeiro parágrafo da citação.
>
> Segundo parágrafo da citação.
```

## Destaques

Destaques são caixas coloridas com um ícone e um rótulo, ótimas para dicas e avisos. Escreva uma citação cuja primeira linha indique o tipo de destaque:

```
> [!WARNING]
> Não se esqueça de salvar seu layout!
```

<img width="640" alt="Destaques em Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_callouts.png?raw=true">

Há cinco tipos: `[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]` e `[!CAUTION]`.

## Hiperlinks

Coloque o texto entre `[ ]` e o link, logo depois, entre `( )`:

```
[Visite nosso site](https://example.com)
```

Os links podem conter parênteses, como `https://en.wikipedia.org/wiki/Minecraft_(video_game)`. Para exibir colchetes no texto do link, coloque um `\` antes deles: `[Clique \[aqui\]](https://example.com)`.

## Eventos de clique e de foco

O texto também pode acionar [listeners](/listeners) em vez de abrir um site. Use o prefixo `click:` ou `hover:` com um ID de sua escolha:

```
[algum texto clicável](click:unique_text_click_event_id)
[algum texto com evento de foco](hover:unique_text_hover_event_id)
```

Reaja a esses eventos usando os listeners [**Ao clicar no texto Markdown**](/listeners#on-markdown-text-clicked) e [**Ao passar o cursor sobre o texto Markdown**](/listeners#on-markdown-text-hovered). Ambos fornecem o ID como `$$text_event_id`.

## Imagens

Coloque uma imagem em uma linha própria com `![](` + a origem da imagem + `)`:

```
![](https://example.com/image.png)
```

A origem pode ser um URL da web, um arquivo local como `/config/fancymenu/assets/image.png` ou uma imagem de um pacote de recursos. Consulte [Recursos](/resources) para ver todos os tipos de origem.

O texto entre colchetes vira a legenda da imagem:

```
![Minha captura de tela legal](/config/fancymenu/assets/screenshot.png)
```

As legendas aparecem abaixo da imagem se a opção **Markdown -> Imagens -> Legenda** do elemento estiver ativada.

Para tornar uma imagem clicável, coloque-a dentro de um link:

```
[![](https://example.com/image.png)](https://example.com)
```

## Tabelas

Separe as células com `|`. A primeira linha é o cabeçalho, e a segunda linha contém `---` para cada coluna:

```
| Item | Preço |
|:---|---:|
| Espada de diamante | 10 |
| Maçã dourada | 5 |
```

Os dois-pontos na segunda linha alinham a coluna: `:---` à esquerda, `:---:` ao centro e `---:` à direita. Para exibir um `|` dentro de uma célula, escreva `\|`.

<img width="640" alt="Tabela e código em Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_table_code.png?raw=true">

## Separadores

Uma linha contendo apenas `---` desenha um separador ao longo do texto.

## Código

O código exibe o texto como está, sem formatá-lo.

- **Código em linha:** coloque um trecho da linha entre `` ` ``, como `` `/spawn` ``.
- **Blocos de código:** coloque uma linha com `` ``` `` antes e depois das linhas. As linhas dos blocos de código não quebram.

````
```
/give @p minecraft:diamond 64
```
````

Você pode escrever o nome de uma linguagem depois dos primeiros `` ``` ``, como em `` ```json ``. O FancyMenu aceita isso, mas não altera a aparência do código.

[Placeholders](/placeholders) ainda são substituídos dentro do código.

## Texto simples

O texto simples exibe os caracteres de formatação como estão, mas sem a aparência de código. Coloque um trecho da linha entre `;;`:

```
Isto exibe ;;**asteriscos**;; em vez de texto em negrito.
```

Para fazer isso em linhas inteiras, coloque `;;;` em uma linha própria antes e depois delas:

```
;;;
**Sem negrito**, _sem itálico_.
;;;
```

## Escape de caracteres

Para exibir um caractere de formatação como texto normal, coloque um `\` antes dele. Por exemplo, `\*sem itálico\*` exibe `*sem itálico*`.

Isso funciona para `\` `` ` `` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `.` `!` `|` `>` `~` e `^`.

# Formatação de texto do Minecraft

Os códigos de formatação do Minecraft funcionam na maioria dos campos de texto do FancyMenu. Use `&` no lugar de `§`, usado pelo Minecraft. Por exemplo, `&cAviso` exibe texto vermelho e `&l` deixa o texto em negrito. `&r` redefine a formatação.

Consulte a [Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes) para ver todos os códigos.

Os códigos de formatação também funcionam em textos Markdown, exceto dentro de código e texto simples. Para estilos como negrito e itálico, o Markdown costuma ser mais fácil de ler, mas os códigos são práticos para aplicar cores rapidamente.

# Componentes de texto do Minecraft (sistema de componentes brutos)

Os componentes de texto do Minecraft são textos formatados escritos em JSON. Eles funcionam em textos de **uma única linha**, como **rótulos de botões e controles deslizantes**, mas não em elementos de Texto.

Para usar um componente, defina o rótulo apenas com ele:

```
{"text":"Texto do rótulo do botão","font":"uniform"}
```

Isso exibe `Texto do rótulo do botão` com a fonte `uniform`. Você pode usar [placeholders](/placeholders) no valor de `text`.

Para saber mais, consulte as páginas da Minecraft Wiki sobre o [formato dos componentes de texto](https://minecraft.wiki/w/Raw_JSON_text_format) e [fontes](https://minecraft.wiki/w/Resource_pack#Fonts).
