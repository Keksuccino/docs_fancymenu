---
title: Posicionamento e Dimensionamento Avançados
description: Como usar o Posicionamento e Dimensionamento Avançados dos elementos.
---
# Posicionamento e Dimensionamento Avançados

O posicionamento/dimensionamento avançado permite que você tenha **controle total sobre a posição e o tamanho dos seus elementos**. Isso é muito poderoso, mas também **bem mais demorado** do que usar o dimensionamento e posicionamento automáticos do FancyMenu.

> Se você só quer que os elementos se ajustem melhor à **escala da GUI** do Minecraft, é recomendado usar o **autoescalonamento** em nível de layout. Ele pode ser ativado primeiro forçando uma escala de GUI no menu que abre ao clicar com o botão direito no fundo do editor e depois habilitando **Auto-Scaling** no mesmo menu.
{.is-warning}


# Ativando o Modo de Posicionamento/Dimensionamento Avançado

Para **ativar** o posicionamento/dimensionamento avançado de um elemento, **clique com o botão direito** nele e clique em **Advanced Positioning** ou **Advanced Sizing**.
O elemento mudará automaticamente para o modo avançado quando você definir um valor avançado de posição ou tamanho.

Para **desativá-lo** e voltar ao posicionamento/dimensionamento normal, **limpe todos os valores de posicionamento/dimensionamento**.

> Enquanto um elemento estiver no modo de Dimensionamento/Posicionamento Avançado, redimensionar e/ou mover o elemento pode ser desativado ou ter restrições.
{.is-warning}

# Calculando Posições/Tamanhos

A razão pela qual o posicionamento/dimensionamento avançado é tão poderoso é que você pode usar **placeholders** nos valores de posição/tamanho.

Isso permite usar o placeholder **Calculator** (localizado na categoria de placeholders **Advanced**) em combinação com placeholders da categoria **GUI**, como **Screen Width**, **GUI Scale**, **Element Width** e outros.

> Você pode adicionar placeholders clicando no botão **Placeholders** no canto superior direito do editor de texto. Se você não vir esse botão, o conteúdo que deseja editar **não suporta** placeholders.
{.is-info}

Para calcular algo com o placeholder **Calculator**, substitua a expressão de exemplo pela sua própria. Você pode usar placeholders aninhados na expressão, então pode aproveitar ali os placeholders de tamanho da tela, tamanho do elemento etc.

Por exemplo, este placeholder simplesmente resolverá `1 + 1` e depois será exibido como `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

A variável `decimal` está definida como `false`, o que é importante para a maioria dos cálculos de dimensionamento/posicionamento, então deixe isso sempre como `false` ao trabalhar com posicionamento/dimensionamento avançado.

O seguinte cálculo usa o placeholder **Screen Width** e o divide por `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> Enquanto **Advanced Positioning** estiver ativado, a **âncora** e quaisquer outros tipos de recursos relacionados à posição do elemento serão **ignorados**. O Posicionamento Avançado sempre usará o canto superior esquerdo (X0 Y0) como origem, assim como a lógica padrão da GUI do Minecraft faz. A única configuração que o Posicionamento Avançado respeita é **Stay on Screen**.
