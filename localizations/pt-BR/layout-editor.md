---
title: Editor de Layout
description: >-
  Como abrir o editor de layout, selecionar, mover e redimensionar elementos,
  organizá-los com camadas e grupos, salvar seu layout e conhecer todos os
  atalhos do editor.
sourceBlobSha: c247d44a67ac209f2a0b638cb4748b408c7e7b13
---

# Editor de Layout

O editor de layout é onde você cria [layouts](/home#your-first-layout): adiciona elementos, move e redimensiona cada um e altera o menu ao redor deles. Ele mostra o menu como os jogadores o veem, para que você confira na hora como ficou.

<img width="800" alt="Movendo, alargando e ajustando um título, depois selecionando dois botões, copiando e colando, arrastando as cópias para baixo e desfazendo a ação" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_basics.gif?raw=true">

# Abrir o Editor

1. Abra o menu que deseja alterar, como a tela inicial.
2. Clique em **barra de menu -> Customização -> Customização da Tela Atual**, para que apareça **Ativado**.
3. Clique em **barra de menu -> Customização -> Layouts -> Novo -> Para a Tela Atual**.

- **Para Todas as Telas [Universal]** cria um [Layout Universal](/universal-layouts), que aparece em todos os menus.
- Os layouts que você já tem também aparecem em **Layouts**. Passe o cursor sobre um deles e clique em **Editar Layout**.
- Em qualquer menu, `Ctrl + Alt + L` abre o último layout que você editou. Veja [os atalhos da barra de menu](/home#menu-bar-shortcuts).

# Visão Geral do Editor

<img width="800" alt="O editor de layout com o botão Entrar no Servidor selecionado, a barra de menu na parte superior e o widget Camadas à direita" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Clique com o botão direito no plano de fundo para acessar as configurações do layout inteiro e adicionar elementos com **Novo Elemento**.
- Clique com o botão direito em um elemento para acessar suas configurações. Veja [Elementos](/elements#settings-of-all-elements).
- **Camadas**, à direita, lista todos os elementos do layout. Veja [Camadas e Grupos](#layers-and-groups).
- A barra de menu na parte superior:

| Menu | O que contém |
|---|---|
| **Layout** | **Novo**, **Abrir**, **Salvar**, **Salvar Como**, **Exportar Layout para IA**, **Propriedades do Layout** (o mesmo que o menu do botão direito no plano de fundo), **Configurações** e **Fechar Editor** |
| **Editar** | **Desfazer**, **Refazer**, **Copiar**, **Colar** e **Selecionar Tudo** |
| **Elemento** | **Novo** para adicionar elementos e **Elementos Vanilla Excluídos** para restaurar [elementos vanilla que você excluiu](/deleted-vanilla-elements) |
| **Janela** | **Widgets do Editor**, a [grade](#grid-and-anchor-overlay), a [sobreposição de âncoras](#grid-and-anchor-overlay), **Controles de Rotação do Elemento** e **Controles de Inclinação do Elemento** |

## Configurações do Layout

O menu do botão direito no plano de fundo reúne tudo o que diz respeito ao layout, como:

- [**Planos de Fundo do Menu**](/menu-backgrounds) e [**Sobreposições Decorativas**](/decoration-overlays)
- **Título Personalizado da Tela** para o texto na parte superior de alguns menus, como "Opções". Você pode usar [marcadores de posição](/placeholders).
- **Personalizações do Cabeçalho/Rodapé** para [telas com rolagem](/customizing-scrollable-screens)
- **Índice do Layout [Ordenação de Vários Layouts]** e **Modo Aleatório** para [usar vários layouts em um menu](/randomize-layouts)
- **Requisitos de Carregamento [Para Todo o Layout]**. Veja [Requisitos](/conditions#layout-wide-requirements).
- **Editar Script de Ação 'Abrir Tela'** e **Editar Script de Ação 'Fechar Tela'**. Veja [Scripts de Ação](/action-scripts).
- **Opções de Layout Universal**, disponíveis apenas em [Layouts Universais](/universal-layouts)

# Trabalhar com Elementos

## Selecionar

- Clique em um elemento para selecioná-lo. Clique no plano de fundo para desmarcar tudo.
- Arraste sobre o plano de fundo para selecionar todos os elementos dentro do retângulo.
- `Ctrl` + clique adiciona um elemento à seleção ou remove dela um elemento selecionado.
- `Ctrl + A` seleciona todos os elementos.

Cliques, seleções retangulares e `Ctrl + A` ignoram os elementos que você [ocultou em Camadas](#hiding-and-renaming).

## Mover

- Arraste um elemento para movê-lo. Para mover vários elementos selecionados, mantenha `Ctrl` pressionado enquanto começa a arrastá-los. Sem `Ctrl`, o clique seleciona apenas o elemento clicado.
- As teclas de seta movem os elementos selecionados um pixel.
- Enquanto arrasta, os pontos de ancoragem aparecem. Mantenha o elemento sobre outro ponto de ancoragem ou elemento para ancorá-lo ali. Veja [Posicionar Elementos](/positioning-elements).
- Solte um elemento em uma [Área com Rolagem](/scrollable-areas) para colocá-lo dentro dela.

## Redimensionar

Arraste uma borda ou um canto de um elemento selecionado. Mantenha `Shift` pressionado para preservar a proporção.

Só é possível redimensionar um elemento quando há apenas um elemento selecionado.

## Girar e Inclinar

Os elementos selecionados que aceitam esse recurso exibem controles para [girálos e incliná-los](/rotating-elements). Mantenha `Shift` pressionado enquanto arrasta para ajustar em incrementos: 45° para rotação e 15° para inclinação.

**Janela -> Controles de Rotação do Elemento** e **Controles de Inclinação do Elemento** ocultam os controles.

## Copiar, Colar e Excluir

- `Ctrl + C` copia os elementos selecionados; `Ctrl + V` cola. As cópias aparecem sobre os originais e ficam selecionadas, para que você possa arrastá-las logo em seguida.
- Você também pode colar em outro layout, até o jogo ser fechado.
- `Delete` exclui os elementos selecionados. Os elementos vanilla são apenas ocultados: restaure-os com **Elemento -> Elementos Vanilla Excluídos**.
- Ao excluir uma Área com Rolagem, você pode escolher se o conteúdo dela também será excluído ou permanecerá no layout.

## Desfazer e Refazer

`Ctrl + Z` desfaz a última alteração; `Ctrl + Y` a refaz. Os dois comandos também estão no menu **Editar**.

## Elementos Invisíveis

Os jogadores não conseguem ver os elementos [Áudio](/elements#audio), [Arrastador](/dragger), [Animador de Elemento](/element-animator), [Controlador de Música](/elements#music-controller) e [Ticker](/elements#ticker). No editor, eles aparecem como caixas coloridas com seus nomes, para que você possa encontrá-los, movê-los e redimensioná-los.

- **Cor no Editor** no menu do botão direito altera a cor da caixa, por exemplo, para diferenciar vários Tickers. As cores usam o formato `#RRGGBB` ou `#RRGGBBAA`, com transparência: uma cor translúcida, como `#E30E2366`, deixa visível o que está atrás da caixa.
- O nome dentro da caixa é o nome da camada do elemento. Veja [Ocultar e Renomear](#hiding-and-renaming).

Os jogadores nunca veem a caixa, sua cor ou seu nome.

# Camadas e Grupos

**Camadas** lista todos os elementos do layout, começando pelo que está no topo: um elemento aparece na frente de tudo o que estiver abaixo dele na lista. **Janela -> Widgets do Editor -> Camadas** mostra ou oculta essa lista.

<img width="800" alt="Arrastando a camada Plano de Fundo das Notícias para baixo de Texto das Notícias, para que as notas da atualização apareçam após desmarcar o elemento; depois, adicionando um grupo, colocando as duas camadas nele, ocultando e mostrando o grupo com o ícone de olho e recolhendo-o" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_layers.gif?raw=true">

## Alterar a Ordem

- Clique em uma camada para selecionar o elemento correspondente e arraste-a para cima ou para baixo. Uma linha indica onde ela será colocada. Todas as camadas selecionadas se movem juntas.
- Ou clique com o botão direito em um elemento ou em sua camada e selecione **Mover Uma Camada Para Cima** ou **Mover Uma Camada Para Baixo**.

No editor, os elementos selecionados sempre aparecem na frente dos demais. Desmarque-os para ver a ordem real.

Em algumas versões do Minecraft, elementos [Entidade do Jogador](/elements#player-entity) e [Item](/elements#item) aparecem na frente de tudo, independentemente da camada. Veja [Problemas Conhecidos](/known-issues#1-player-entity--item-elements-are-always-in-front-of-everything).

## Elementos Vanilla

A linha **Elementos Vanilla** representa todos os elementos do próprio menu, como os botões. Não é possível alterar a ordem deles, mas o botão à direita da linha coloca todos os seus elementos atrás ou na frente deles. Ele faz o mesmo que **Elementos Personalizados Atrás dos Vanilla**, no menu do botão direito no plano de fundo.

## Ocultar e Renomear

- O ícone de olho de uma camada oculta o elemento no editor, tirando-o do caminho enquanto você trabalha nos demais. Clique nele novamente para mostrar o elemento.
- Não é possível clicar, mover, copiar ou excluir elementos ocultos. Os jogadores ainda os veem; eles ficam ocultos apenas no editor. O layout memoriza quais elementos você ocultou.
- Clique com o botão direito em uma camada e selecione **Renomear Camada** para dar a ela um nome mais fácil de encontrar, como `Painel de Notícias`. Essa opção equivale a **Nome de Exibição no Editor** do elemento, e os jogadores não veem o nome.

## Grupos

Os grupos organizam camadas relacionadas sob um mesmo nome, como todas as partes de um painel de notícias. Eles apenas organizam a lista: os elementos continuam aparecendo e funcionando como antes.

- Clique com o botão direito dentro de Camadas e selecione **Adicionar Grupo**. O grupo aparece abaixo das camadas.
- Arraste camadas para o grupo para adicioná-las a ele. Arraste-as para fora para removê-las.
- Clique em um grupo para selecionar todos os elementos dele. Arraste-o para mover todos esses elementos para cima ou para baixo de uma só vez.
- A seta do grupo recolhe ou expande suas camadas, e o ícone de olho oculta ou mostra todas elas.
- Clique com o botão direito em um grupo para renomeá-lo, movê-lo uma camada para cima ou para baixo ou excluí-lo. **Excluir Grupo** mantém os elementos do grupo.

**Mover Uma Camada Para Cima** e **Mover Uma Camada Para Baixo** mantêm o elemento dentro do grupo. Para removê-lo, arraste a camada para fora do grupo.

O layout salva os grupos e quais deles estão recolhidos.

## Áreas com Rolagem

Os elementos de uma [Área com Rolagem](/scrollable-areas) aparecem abaixo da camada da área, com recuo.

- Arraste uma camada para a metade inferior da camada de uma área para colocar o elemento dentro dela. Arraste-a para fora, entre outras camadas, para removê-la. O elemento permanece na mesma posição na tela.
- A seta da camada de uma área recolhe ou expande seus elementos.
- Os elementos de uma área não pertencem a nenhum grupo. Eles se movem junto com a área.

# Grade e Sobreposição de Âncoras

O menu **Janela** reúne as configurações das ferramentas auxiliares do editor:

- **Grade** mostra as linhas da grade; `Ctrl + G` ativa ou desativa a exibição. **Tamanho da Grade** define o espaçamento entre as linhas.
- **Ajuste à Grade** faz com que um elemento arrastado se alinhe às linhas da grade enquanto ela estiver visível. **Intensidade do Ajuste à Grade** define a força do alinhamento.
- **Visibilidade da Sobreposição de Âncoras** define quando os pontos de ancoragem aparecem:
  - **Mostrar ao Arrastar Elementos**: enquanto você arrasta elementos.
  - **Sempre Visível**: o tempo todo.
  - **Mostrar ao Pressionar Tecla (Tecla "O")**: enquanto você mantém `O` pressionado.
  - **Desativado**: nunca.
- **Ativar Âncora ao Passar o Cursor sobre a Área** define se manter um elemento sobre um ponto de ancoragem altera sua âncora. **Ativar Âncora ao Passar o Cursor sobre Elementos** adiciona outros elementos aos pontos de ancoragem; essa opção só funciona quando **Ativar Âncora ao Passar o Cursor sobre a Área** também está ativada.

# Salvar e Fechar

- `Ctrl + S` ou **Layout -> Salvar** salva o layout. Na primeira vez, o FancyMenu pede um nome de arquivo.
- **Layout -> Salvar Como** salva o layout em um novo arquivo.
- Quando há alterações não salvas, a barra de menu mostra **\* Alterações Não Salvas! \***.
- O X à direita da barra de menu ou **Layout -> Fechar Editor** fecha o editor. Se houver alterações não salvas, o editor perguntará se você deseja continuar.

# Atalhos

No macOS, use `Cmd` em vez de `Ctrl`.

| Atalho | O que faz |
|---|---|
| `Ctrl + S` | Salvar |
| `Ctrl + Z` | Desfazer |
| `Ctrl + Y` | Refazer |
| `Ctrl + C` | Copiar os elementos selecionados |
| `Ctrl + V` | Colar |
| `Ctrl + A` | Selecionar todos os elementos |
| `Delete` | Excluir os elementos selecionados |
| Teclas de seta | Mover os elementos selecionados um pixel |
| `Ctrl` + clique | Adicionar um elemento à seleção ou removê-lo dela |
| `Ctrl` + arrastar | Mover vários elementos selecionados |
| `Shift` + redimensionar | Preservar a proporção |
| `Shift` + girar ou inclinar | Ajustar em incrementos |
| `Ctrl + G` | Ativar ou desativar a grade |
| Manter `O` pressionado | Mostrar os pontos de ancoragem, com **Mostrar ao Pressionar Tecla (Tecla "O")** |

> [!TIP]
> O editor de texto tem seus próprios atalhos. Veja [Texto nos Menus](/text-in-menus#the-text-editor). Janelas como [Scripts de Ação](/action-scripts#shortcuts) listam seus atalhos nas respectivas páginas.
