---
title: Áreas roláveis
description: >-
  Como colocar elementos em uma Área rolável, organizá-los e alterar a forma
  como a área rola.
sourceBlobSha: a424c5e8680ece5f25846de0399fc8e78f375e15
---
# Áreas roláveis

Uma **Área rolável** contém outros elementos e permite que os jogadores rolem por eles. Ela é ótima para listas longas de botões, seletores de mundos ou servidores, vitrines de itens, painéis de notícias e tudo mais que não caiba em uma única tela.

Tudo o que estiver na área rola junto com ela e é recortado nas bordas.

<img width="800" alt="Colocando botões em uma Área rolável e empilhando-os" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_showcase.gif?raw=true">

> [!NOTE]
> Somente elementos adicionados ao layout podem ser colocados em uma área. [Elementos vanilla](/vanilla-elements) não podem, pois fazem parte do próprio menu.

# Adicionando uma Área rolável

1. Abra um layout no editor de layout.
2. Clique com o botão direito no plano de fundo do editor e selecione **Novo elemento -> Área rolável**.
3. Arraste os elementos para a área.

# Colocando elementos dentro e fora

- Arraste um elemento para a área para colocá-lo nela. A área se ilumina quando aceita o elemento. O elemento só é colocado nela se uma parte dele estiver dentro da área.
- Para arrastar vários elementos selecionados de uma vez, mantenha `Ctrl` (`Cmd` no macOS) pressionado ao começar a arrastar.
- Enquanto você arrasta um elemento perto da borda da área, ela rola para que você possa alcançar todas as partes. Você também pode rolá-la com a roda do mouse no editor.
- Para tirar um elemento da área, arraste-o para fora ou clique nele com o botão direito e selecione **Mover para fora da Área rolável**. Ele permanece na mesma posição na tela.
- Também é possível colocar áreas dentro de outras áreas.

## Camadas

No widget [Camadas](/layout-editor#scrollable-areas), os elementos de uma área aparecem abaixo dela. Arraste as camadas para colocá-las dentro ou fora de uma área, ou para alterar a ordem. O botão de recolher da camada de uma área oculta os elementos dela na lista.

## Copiar e excluir

- Ao copiar uma área, tudo o que estiver dentro dela também será copiado.
- Ao excluir uma área que ainda contém elementos, você poderá escolher o que fazer com eles: **Excluir elementos** também os exclui; **Manter elementos** os deixa na mesma posição na tela.

# Organizando elementos

Clique com o botão direito na área e abra **Organização**. **Modo** define como a área posiciona os elementos:

- **Âncoras**: você posiciona os elementos manualmente, como no restante do layout. As novas áreas usam esse modo.
- **Pilha**: os elementos ficam alinhados um após o outro.
- **Grade**: os elementos ficam alinhados em células do mesmo tamanho.
- **Fluxo**: os elementos ficam alinhados lado a lado e começam uma nova linha quando a linha atual fica cheia.

<img width="800" alt="Áreas roláveis nos modos Pilha, Grade e Fluxo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

## Modo Âncoras

Os elementos em uma área têm suas próprias âncoras, que fazem referência ao conteúdo da área, e não à tela. Por exemplo, a âncora **Canto superior esquerdo** corresponde ao canto superior esquerdo do conteúdo, e as âncoras inferiores se fixam no final do conteúdo. Consulte [Posicionamento de elementos](/positioning-elements) para saber como as âncoras funcionam.

- **Esticar horizontalmente** e **Esticar verticalmente** ajustam a largura ou a altura de um elemento ao tamanho do conteúdo.
- Os elementos só podem ser ancorados a outros elementos na mesma área. Ao mover um elemento para dentro ou para fora de uma área, os elementos que estavam ancorados do outro lado da borda da área recebem a âncora **Canto superior esquerdo** e permanecem na mesma posição.

### Tamanho do conteúdo

No modo Âncoras, você define o tamanho do conteúdo e, assim, o quanto a área pode rolar.

Selecione a área e arraste a alça no final do conteúdo. Arraste-a para além da borda da área para continuar; a área rolará junto.

<img width="698" alt="A alça de conteúdo de uma Área rolável selecionada" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_content_handle.png?raw=true">

Você também pode clicar com o botão direito na área e abrir **Tamanho do conteúdo**:

- **Largura do conteúdo** e **Altura do conteúdo** definem o tamanho por valor numérico. Elas aceitam [placeholders](/placeholders). Ao usar um placeholder, não é possível arrastar a alça.
- **Ajustar ao conteúdo** faz o conteúdo terminar exatamente onde termina o último elemento. Os elementos ancorados ao meio ou ao final do conteúdo se movem junto com ele e, por isso, não são considerados.

O conteúdo nunca fica menor que a área e só aumenta nas direções em que a área rola.

## Pilha, Grade e Fluxo

- A área posiciona os elementos para você, e o conteúdo aumenta automaticamente para acomodá-los.
- Arraste um elemento para alterar sua ordem. Uma linha indica onde ele será colocado.
- Ao mudar de Âncoras para um desses modos, os elementos mantêm a ordem em que estavam na tela. Ao voltar para Âncoras, cada elemento permanece na posição em que estava.
- Os elementos ocultos por seus [requisitos](/conditions) não deixam espaços vazios.
- O esticamento não funciona nesses modos.
- Esses modos só rolam em uma direção. Uma área definida como **Ambos** rola verticalmente.

Abra **Organização** para ajustar as configurações:

| Configuração | O que faz |
|---|---|
| **Alinhamento** | Define onde os elementos ficam na direção perpendicular ao alinhamento: **Início**, **Centro**, **Fim** ou **Preencher**. Com **Preencher**, eles ocupam toda a largura disponível (ou toda a altura, em áreas que rolam horizontalmente). O modo Fluxo não tem a opção **Preencher**. |
| **Espaçamento** | Define o espaço entre os elementos. |
| **Margem interna** | Define o espaço entre os elementos e as bordas do conteúdo. |
| **Elementos por linha** | Somente no modo Grade. Define quantos elementos cabem em uma linha. |
| **Ajustar o máximo possível** | Somente no modo Grade. Coloca o máximo de elementos possível em cada linha, em vez de usar uma quantidade fixa. **Tamanho mínimo da célula** determina quantos elementos cabem. |

# Rolagem

Os jogadores rolam a área com a roda do mouse. Mantenha `Shift` pressionado para rolar horizontalmente.

- **Direção da rolagem** define se a área rola **Verticalmente**, **Horizontalmente** ou em **Ambas as direções**. Na direção em que não rola, o conteúdo tem exatamente o mesmo tamanho da área.
- Os elementos de texto em uma área rolam primeiro. Quando chegam ao fim, a área continua rolando.
- Quando os jogadores navegam entre botões com `Tab`, a área rola até o botão selecionado.

Os menus **Rolagem**, **Rolagem automática** e **Barras de rolagem** têm as mesmas configurações que os elementos de texto. Consulte [Texto em menus](/text-in-menus#scrolling-settings) para ver todas. As diferenças são:

- Em **Ajustar**, o conteúdo pode se alinhar **Aos elementos**, para que um elemento fique sempre no início da área, ou **Às páginas**.
- Os botões e todos os demais elementos da área continuam funcionando com **Arrastar para rolar** ativado.
- Os puxadores de rolagem são alças de pixel, a menos que você defina suas próprias **Texturas do puxador de rolagem** ou uma **Cor do puxador de rolagem [HEX]**.

# Plano de fundo

As áreas desenham um painel atrás do conteúdo. Abra **Plano de fundo** para alterá-lo. Ele funciona como o [plano de fundo dos elementos de texto](/text-in-menus#background): desative-o com **Exibir plano de fundo**, use sua própria textura com [divisão em nove partes](/nine-slicing-and-tiling) ou ladrilhamento e altere até onde ele se estende com **Margem interna**.

# Rolagem com ações

Você também pode controlar e acompanhar as áreas em outras partes do FancyMenu:

- A [ação](/action-scripts) **Rolar um elemento** rola uma área até o início, o fim, uma posição ou um dos elementos dentro dela.
- Os [placeholders](/placeholders) **Posição de rolagem do elemento**, **Porcentagem de rolagem do elemento** e **Tamanho do conteúdo da rolagem do elemento** informam o quanto a área rolou e qual é o tamanho do conteúdo.
- O [requisito](/conditions) **O elemento está rolado até o fim** verifica se a área chegou ao final da rolagem.
- Os [listeners](/listeners) **Ao rolar um elemento**, **Ao rolar um elemento até o início** e **Ao rolar um elemento até o fim** executam ações enquanto a área rola.

Todos eles precisam do [identificador do elemento](/element-identifiers) da área. Por exemplo, este placeholder mostra o quanto uma área rolou, de 0 a 100:

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"3f2a9c1e-7b4d-4e8a-9c2f-1d5e6a7b8c9d-1763950000000","axis":"vertical"}}
```

# Bom saber

- Ocultar uma área oculta tudo o que estiver dentro dela, e a opacidade da área também se aplica a esses elementos.
- Não é possível girar ou inclinar áreas, e a paralaxe não funciona nelas nem nos elementos dentro delas.
- Os elementos de dica de ferramenta em uma área são recortados nas bordas dela, a menos que acompanhem o mouse.
