---
title: Elementos Vanilla
description: Como personalizar elementos que já fazem parte das telas por padrão.
sourceBlobSha: 3943106d1e4f0722aad0d1578908262b7c8d92ec
---

# Elementos Vanilla

O FancyMenu não permite apenas adicionar novos elementos às telas: ele também possibilita personalizar elementos existentes do jogo base (Vanilla) e até mesmo de outros mods.

## Botões e controles deslizantes Vanilla (widgets)

Para personalizar os botões e controles deslizantes de uma tela, crie um layout para a tela atual (não um [layout universal](/universal-layouts)) e clique neles com o botão direito no editor.

Eles têm as mesmas configurações que seus próprios [botões](/elements#button) e [controles deslizantes](/elements#slider), como texturas, sons e dicas de ferramentas. Apenas o script de ação deles não pode ser alterado: eles continuam fazendo o que faziam antes.

Elementos Vanilla não podem ser colocados em [Áreas Roláveis](/scrollable-areas), pois pertencem ao próprio menu.

### Rótulos

- **Label** e **Hover Label** substituem o texto de um botão. Em outros widgets, como controles deslizantes, eles são chamados de **Widget Text** e **Hover Widget Text**. Sem eles, o widget mantém o próprio texto.
- **Label Alignment** posiciona o rótulo à **Left** (esquerda), **Centered** (centralizado) ou à **Right** (direita) do widget. Rótulos largos demais para o widget rolam de um lado para o outro, independentemente do alinhamento.
- **Label Scale**, **Label Base Color**, **Label Hover Color**, **Label Shadow** e **Underline Label On Hover** alteram o tamanho, as cores e a sombra do rótulo.

Para alinhar os rótulos de vários botões de uma só vez, selecione-os usando `Ctrl` + clique (consulte [Seleção](/layout-editor#selecting)), clique com o botão direito em um deles e defina **Label Alignment** para todos. Para os rótulos de todos os menus, use **Label Alignment** em [Personalizações Globais](/global-customizations#labels). Um [modelo](/button-slider-templates) também pode aplicar o estilo de rótulo a todos os botões de uma tela.

## Cliques automatizados

Widgets Vanilla e de mods têm a propriedade **Automated Clicks**. Defina-a como um número inteiro maior que `0` para acionar o comportamento original de clique com o botão esquerdo do widget esse número de vezes quando a tela carregar. Por exemplo, definir o valor como `2` clica no widget duas vezes durante a primeira atualização de cada tela recém-aberta. O valor padrão `0` desativa os cliques automatizados.

Esses são cliques reais no widget: cada clique pode alterar o valor de um controle deslizante ou botão de alternância, executar a função de retorno de chamada normal do widget ou até abrir outra tela. Teste o resultado com atenção, especialmente ao configurar mais de um clique.

Para **mover** e **redimensionar** widgets Vanilla/de mods, primeiro é necessário atribuir um ponto de ancoragem a eles. Para isso, clique neles com o **botão direito** e selecione **Anchor Point**. Defina qualquer opção diferente de **Original**, pois essa é a âncora padrão dos elementos Vanilla/de mods.

Você também pode **ocultar** widgets Vanilla/de mods: basta clicar neles com o **botão direito** e selecionar **Delete**. Eles não são realmente excluídos, apenas ocultados. Para restaurá-los, clique em **barra de menu -> Element -> Deleted Vanilla Elements** e clique com o **botão esquerdo** nos elementos que deseja tornar visíveis novamente.

> [!WARNING]
> O widget **Copyright** na tela de título é o único que **NÃO PODE** ser ocultado/excluído. Isso é intencional. Não remova avisos de direitos autorais.

## Elementos da tela de título

A tela de título tem elementos que não são widgets comuns (como o logotipo, o texto de abertura etc.) e que não podem ser movidos nem personalizados. A ideia é excluí-los e substituí-los por elementos personalizados (como um elemento Image para o logotipo ou um elemento Splash Text personalizado para o texto de abertura Vanilla).

Para excluí-los, basta clicar neles com o botão direito. Se quiser restaurá-los mais tarde, clique em **barra de menu -> Element -> Deleted Vanilla Elements** e clique com o **botão esquerdo** no elemento que deseja tornar visível novamente.

## Solução de problemas: elementos Vanilla não aparecem no editor

Se você não consegue ver elementos Vanilla no editor, provavelmente está usando um **layout universal** em vez de um layout **para a tela atual**. Crie um layout para a tela atual. Só é possível criar layouts para a tela atual quando as personalizações estão habilitadas para essa tela.

## Solução de problemas: as personalizações não são aplicadas

Se as personalizações de elementos Vanilla não forem aplicadas fora do editor, geralmente isso acontece porque outro mod substitui ou altera o menu pai dos elementos Vanilla.

Um bom exemplo de mod que substitui uma tela/menu é o **Ice and Fire**, que substitui a tela de título.

O problema de as personalizações não serem aplicadas aos menus não se limita aos elementos Vanilla. Elementos personalizados adicionados às telas provavelmente também não serão aplicados aos menus se um mod os estiver substituindo ou alterando.
