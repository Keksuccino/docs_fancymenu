---
title: Posicionamento e Dimensionamento Avançados
description: Como usar o Posicionamento e Dimensionamento Avançados de elementos.
---
# Posicionamento e Dimensionamento Avançados

O posicionamento e o dimensionamento avançados oferecem controle direto sobre as coordenadas e dimensões dos elementos.

> [!WARNING]
> Para adaptação a diferentes escalas de GUI, experimente primeiro o **Auto-Scaling** em nível de layout. Clique com o botão direito no fundo do editor, force uma escala de GUI e, em seguida, ative **Auto-Scaling** no mesmo menu.


# Alternando o Modo de Posicionamento/Dimensionamento Avançado

Para ativar o posicionamento ou dimensionamento avançado de um elemento, **clique com o botão direito** nele e selecione **Advanced Positioning** ou **Advanced Sizing**.
O elemento alternará automaticamente para o modo avançado quando você definir um valor avançado de posição ou tamanho.

Para **desativá-lo** e voltar ao posicionamento/dimensionamento normal, **limpe todos os valores de posicionamento/dimensionamento**.

> [!WARNING]
> Enquanto um elemento estiver no modo de Dimensionamento/Posicionamento Avançado, redimensioná-lo e/ou movê-lo pode ser desativado ou restrito.

# Calculando Posições/Tamanhos

Os valores avançados de posição e tamanho suportam [placeholders](./placeholders).

Isso permite combinar o placeholder [**Calculator**](./placeholders#calculator-calc) com placeholders de GUI, como [**Screen Width**](./placeholders#screen-width-guiwidth), [**GUI Scale**](./placeholders#gui-scale-guiscale) e [**Element Width**](./placeholders#element-width-elementwidth).

> [!NOTE]
> Você pode adicionar placeholders clicando no botão **Placeholders** no canto superior direito do editor de texto. Se você não vir esse botão, o conteúdo que deseja editar **não** suporta placeholders.

Para calcular algo com o [**placeholder Calculator**](./placeholders#calculator-calc), substitua a expressão de exemplo pela sua própria. Placeholders aninhados podem fornecer dimensões da tela ou do elemento.

Este exemplo retorna `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Mantenha `decimal` definido como `false` para cálculos de posição e tamanho em pixels inteiros.

O seguinte cálculo usa o [**placeholder Screen Width**](./placeholders#screen-width-guiwidth) e o divide por `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> **Advanced Positioning** ignora a âncora do elemento e usa o canto superior esquerdo da tela (`X0 Y0`) como origem. **Stay on Screen** ainda se aplica.
