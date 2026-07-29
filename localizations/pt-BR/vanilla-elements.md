---
title: Elementos Vanilla
description: Como personalizar elementos que fazem parte das telas por padrão.
---
# Elementos Vanilla

O FancyMenu não apenas permite adicionar novos elementos às telas, como também possibilita personalizar elementos existentes do jogo base (Vanilla) e até de outros mods.

## Botões e Sliders Vanilla (Widgets)

Para personalizar widgets Vanilla/mod existentes, basta criar um novo layout **"para a tela atual"** (NÃO universal!) e **clicar com o botão direito** nos elementos no editor, assim como você faria com elementos personalizados.

Você pode personalizar seus **rótulos e texturas** da mesma forma que faria com botões e sliders personalizados.

A única coisa que você **não pode** fazer com widgets Vanilla/mod é personalizar o **script de ação** deles (como alterar o que eles fazem ao interagir com eles). Isso só é possível com botões e sliders personalizados.

## Cliques Automatizados

Widgets Vanilla e de mods têm a propriedade **Cliques Automatizados**. Defina-a como um inteiro maior que `0` para acionar o comportamento original de clique com o botão esquerdo do widget esse número de vezes quando a tela carregar. Por exemplo, definir como `2` clica no widget duas vezes durante a primeira atualização de cada tela recém-aberta. O valor padrão `0` desativa os cliques automatizados.

Esses são cliques reais em widgets: cada clique pode alterar o valor de um slider ou de um botão de ciclo, executar o callback normal do widget ou até abrir outra tela. Teste o resultado com cuidado, especialmente ao configurar mais de um clique.

Para **mover** e **redimensionar** widgets Vanilla/mod, primeiro você precisa definir um ponto de ancoragem para eles. Para isso, **clique com o botão direito** neles e clique em **Ponto de Ancoragem**. Defina qualquer opção diferente de **Original**, pois esse é o âncora padrão dos elementos Vanilla/mod.

Você também pode **ocultar** widgets Vanilla/mod simplesmente **clicando com o botão direito** neles e clicando em **Delete**. Eles não são realmente excluídos, mas ficam ocultos, e você pode restaurá-los clicando em **barra de menu -> Elemento -> Elementos Vanilla Excluídos** e **clicando com o botão esquerdo** no(s) elemento(s) que deseja tornar visível(is) novamente.

> [!WARNING]
> O widget **Copyright** na tela de Título é o único que você **NÃO PODE** ocultar/excluir. Isso é intencional. Por favor, não remova avisos de direitos autorais.

## Elementos da Tela de Título

A tela de Título tem elementos que não são widgets normais (como o logo, o texto aleatório, etc.) e que não podem ser movidos ou personalizados. Eles foram feitos para serem excluídos e substituídos por elementos personalizados (como um elemento de Imagem para o logo ou um elemento personalizado de Texto Aleatório para o texto aleatório Vanilla).

Para excluí-los, basta clicar com o botão direito neles. Se quiser restaurá-los depois, basta clicar em **barra de menu -> Elemento -> Elementos Vanilla Excluídos** e **clicar com o botão esquerdo** no elemento que deseja tornar visível novamente.

## Solução de problemas: Elementos Vanilla não ficam visíveis no editor

Se você não consegue ver os elementos Vanilla no editor, provavelmente isso é causado pelo uso de um **layout universal** em vez de um **para a tela atual**. Certifique-se de criar um layout para a tela atual. Você só pode criar layouts para a tela atual quando as personalizações estiverem ativadas para essa tela.

## Solução de problemas: As personalizações não são aplicadas

Se as personalizações em elementos Vanilla não forem aplicadas fora do editor, isso geralmente é causado por outro mod sobrescrevendo ou alterando o menu pai dos elementos Vanilla.

Um bom exemplo de mod que sobrescreve uma tela/menu é **Ice and Fire**, que substitui a tela de Título.

Personalizações que não são aplicadas aos menus não se limitam apenas a elementos Vanilla. Elementos personalizados adicionados às telas provavelmente também não serão aplicados aos menus se um mod estiver sobrescrevendo ou alterando-os.
