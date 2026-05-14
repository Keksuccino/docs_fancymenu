---
title: Posicionamento e Dimensionamento Avançados
description: Como usar o Posicionamento e Dimensionamento Avançados de elementos.
---

# Posicionamento e Dimensionamento Avançados

O posicionamento/dimensionamento avançado permite que você tenha **controle total sobre a posição e o tamanho dos seus elementos**. Isso é muito poderoso, mas também **muito mais demorado** do que usar o dimensionamento e posicionamento automatizados do FancyMenu.

> Se você só quer que os elementos se ajustem melhor à **escala da GUI** do Minecraft, é recomendado usar o **auto-dimensionamento** em nível de layout. Ele pode ser ativado primeiro forçando uma escala de GUI no menu que abre ao clicar com o botão direito no plano de fundo do editor e, em seguida, habilitando **Auto-Scaling** no mesmo menu.
{.is-warning}


# Alternando o Modo de Posicionamento/Dimensionamento Avançado

Para **ativar** o posicionamento/dimensionamento avançado de um elemento, **clique com o botão direito** nele e clique em **Advanced Positioning** ou **Advanced Sizing**.
O elemento mudará automaticamente para o modo avançado quando você definir um valor avançado de posição ou tamanho.

Para **desativá-lo** e voltar ao posicionamento/dimensionamento normal, **limpe todos os valores de posicionamento/dimensionamento**.

> Enquanto um elemento estiver no modo de Dimensionamento/Posicionamento Avançado, o redimensionamento e/ou movimentação do elemento pode ser desativado ou restrito.
{.is-warning}

# Calculando Posições/Tamanhos

O motivo pelo qual o posicionamento/dimensionamento avançado é tão poderoso é que você pode usar **placeholders** nos valores de posição/tamanho.

Isso permite usar o placeholder **Calculator** (localizado na categoria de placeholders **Advanced**) em combinação com placeholders da categoria **GUI**, como **Screen Width**, **GUI Scale**, **Element Width** e outros.

> Você pode adicionar placeholders clicando no botão **Placeholders** no canto superior direito do editor de texto. Se você não vir esse botão, o conteúdo que deseja editar **não suporta** placeholders.
{.is-info}

Para calcular algo com o placeholder **Calculator**, substitua a expressão de exemplo pela sua própria. Você pode usar placeholders aninhados na expressão, então pode aproveitar ali os placeholders de tamanho da tela, tamanho do elemento etc.

Por exemplo, este placeholder simplesmente resolverá `1 + 1` e depois aparecerá como `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

A variável `decimal` está definida como `false`, o que é importante para a maioria dos cálculos de dimensionamento/posicionamento, então mantenha isso sempre como `false` ao trabalhar com posicionamento/dimensionamento avançado.

O seguinte calculador usa o placeholder **Screen Width** e o divide por `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`
