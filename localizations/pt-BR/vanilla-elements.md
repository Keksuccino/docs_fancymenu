---
title: Elementos Vanilla
description: Como personalizar elementos que fazem parte das telas por padrão.
---

# Elementos Vanilla

O FancyMenu não permite apenas adicionar coisas novas às telas, ele também possibilita personalizar elementos existentes do jogo base (Vanilla) e até de outros mods.

## Botões e Sliders Vanilla (Widgets)

Para personalizar widgets Vanilla/de mod existentes, basta criar um novo layout **"para a tela atual"** (NÃO universal!) e **clicar com o botão direito** nos elementos no editor, assim como você faria com os elementos personalizados.

Você pode personalizar seus **rótulos e texturas** da mesma forma que faria com botões e sliders personalizados.

A única coisa que você **não pode** fazer com widgets Vanilla/de mod é personalizar o **script de ação** deles (como alterar o que eles fazem ao interagir com eles). Isso só é possível com botões e sliders personalizados.

Para **mover** e **redimensionar** widgets Vanilla/de mod, primeiro você precisa definir um ponto de ancoragem. Para isso, **clique com o botão direito** neles e clique em **Ponto de ancoragem**. Defina qualquer opção diferente de **Original**, porque esse é o ponto de ancoragem padrão dos elementos Vanilla/de mod.

Você também pode **ocultar** widgets Vanilla/de mod simplesmente **clicando com o botão direito** neles e clicando em **Excluir**. Eles não são realmente excluídos, mas ocultados, e você pode restaurá-los clicando em **barra de menu -> Elemento -> Elementos Vanilla Excluídos** e **clicando com o botão esquerdo** no(s) elemento(s) que deseja tornar visível(is) novamente.

> O widget **Copyright** na tela inicial é o único que você **NÃO PODE** ocultar/excluir. Isso é intencional. Por favor, não remova avisos de copyright.
{.is-warning}

## Elementos da Tela Inicial

A tela inicial possui elementos que não são widgets normais (como o logo, o texto aleatório, etc.) e que não podem ser movidos ou personalizados. Eles devem ser excluídos e substituídos por elementos personalizados (como um elemento de Imagem para o logo ou um elemento personalizado de Texto Aleatório para o texto aleatório Vanilla).

Para excluí-los, basta clicar com o botão direito neles. Se quiser restaurá-los depois, basta clicar em **barra de menu -> Elemento -> Elementos Vanilla Excluídos** e **clicar com o botão esquerdo** no elemento que deseja tornar visível novamente.

## Solução de problemas: Elementos Vanilla não estão visíveis no editor

Se você não consegue ver elementos Vanilla no editor, isso provavelmente é causado por você estar usando um **layout universal** em vez de um **para a tela atual**. Certifique-se de criar um layout para a tela atual. Você só pode criar layouts para a tela atual quando as personalizações estão habilitadas para essa tela.

## Solução de problemas: As personalizações não são aplicadas

Se as personalizações em elementos Vanilla não forem aplicadas fora do editor, isso geralmente é causado por outro mod substituindo ou alterando o menu pai dos elementos Vanilla.

Um bom exemplo de mod que substitui uma tela/menu é **Ice and Fire**, que substitui a tela inicial.

Personalizações que não são aplicadas aos menus não se limitam aos elementos Vanilla. Elementos personalizados adicionados às telas provavelmente também não serão aplicados aos menus se um mod estiver substituindo ou alterando esses menus.
