---
title: Posicionamento e dimensionamento avançados
description: Como usar o posicionamento e o dimensionamento avançados de elementos.
sourceBlobSha: 205b887e844f770856bfd4836ea791e0acdca4b8
---
# Posicionamento e dimensionamento avançados

O posicionamento e o dimensionamento avançados oferecem controle direto sobre as coordenadas e as dimensões dos elementos.

> [!WARNING]
> Para adaptar a escala da interface gráfica, experimente primeiro o **Dimensionamento automático** em todo o layout. Clique com o botão direito no plano de fundo do editor, force uma escala da interface gráfica e, em seguida, ative o **Dimensionamento automático** no mesmo menu.


# Ativar o modo de posicionamento/dimensionamento avançado

Para ativar o posicionamento ou o dimensionamento avançado de um elemento, clique nele com o **botão direito** e selecione **Posicionamento avançado** ou **Dimensionamento avançado**.
O elemento mudará automaticamente para o modo avançado quando você definir um valor avançado de posição ou tamanho.

Para **desativar** o modo e voltar ao posicionamento/dimensionamento normal, **limpe todos os valores de posicionamento/dimensionamento**.

> [!WARNING]
> Enquanto um elemento estiver no modo de dimensionamento/posicionamento avançado, o redimensionamento e/ou a movimentação do elemento poderão ser desativados ou restritos.

# Cálculo de posições/tamanhos

Os valores de posição e tamanho avançados aceitam [marcadores](/placeholders).

Isso permite combinar o marcador [**Calculadora**](/placeholders#calculator) com marcadores da interface gráfica, como [**Largura da tela**](/placeholders#screen-width), [**Escala da interface gráfica**](/placeholders#gui-scale) e [**Largura do elemento**](/placeholders#element-width).

> [!NOTE]
> Você pode adicionar marcadores clicando no botão **Marcadores**, no canto superior direito do editor de texto. Se esse botão não aparecer, o conteúdo que você quer editar **não é compatível** com marcadores.

Para calcular algo com o [marcador **Calculadora**](/placeholders#calculator), substitua a expressão de exemplo pela sua. Marcadores aninhados podem fornecer as dimensões da tela ou do elemento.

Este exemplo retorna `2`:

`{"placeholder":"calc","values":{"expression":"1 + 1","decimal":"false"}}`

Mantenha `decimal` definido como `false` para que os cálculos de posição e tamanho resultem em pixels inteiros.

A calculadora a seguir usa o marcador [**Largura da tela**](/placeholders#screen-width) e divide seu valor por `2`:

`{"placeholder":"calc","values":{"expression":"{"placeholder":"guiwidth"} / 2","decimal":"false"}}`

> [!IMPORTANT]
> O **Posicionamento avançado** ignora a âncora do elemento e usa o canto superior esquerdo da tela (`X0 Y0`) como origem. A opção **Permanecer na tela** continua sendo aplicada.
