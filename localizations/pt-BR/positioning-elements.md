---
title: Posicionando Elementos
description: Como usar corretamente os pontos de ancoragem.
---

# Posicionando Elementos no FancyMenu

No FancyMenu, a posição de cada elemento é determinada por **pontos de ancoragem**. Esses pontos são necessários para calcular onde um elemento deve aparecer na tela, garantindo que os elementos não se sobreponham, não saiam da tela nem se movam incorretamente quando a janela é redimensionada.

## Entendendo os Pontos de Ancoragem

Os pontos de ancoragem servem como a origem a partir da qual a posição de um elemento é calculada. Por padrão, os elementos que você adiciona aos layouts são vinculados ao ponto de ancoragem **"Center of Screen"**. Esse ancoradouro é exatamente o centro da tela, independentemente do tamanho da janela.

Por exemplo, se um elemento estiver a 2 centímetros do centro da tela enquanto estiver vinculado ao ancoradouro **"Center of Screen"**, ele manterá essa distância independentemente de quaisquer mudanças no tamanho da janela.

## Interagindo com os Pontos de Ancoragem

Quando você arrasta um elemento no editor, o ponto de ancoragem ao qual ele está conectado é destacado. Por padrão, essa ação também exibe todos os outros pontos de ancoragem disponíveis. Você pode alterar a âncora de um elemento arrastando-o sobre outro ponto de ancoragem e aguardando até que a barra de carregamento seja preenchida.

![Illustration of anchor points](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Ancorando Elementos em Outros Elementos

Os elementos também podem servir como pontos de ancoragem para outros elementos. Esse recurso é particularmente útil para integrar elementos personalizados de forma fluida aos designs de menus Vanilla, sem precisar ajustar cada elemento Vanilla.

Para ancorar um elemento a outro, basta arrastá-lo até o elemento desejado. Quando o elemento que você está arrastando passa por cima de outro, seu ponto de ancoragem é alterado para o elemento sobrevoado, assim como acontece ao passar o mouse sobre um ponto de ancoragem real.

Isso permite que o elemento se mova junto com seu elemento pai.

## Exemplo de Como Ancorar Elementos

A captura de tela a seguir mostra como você deve escolher âncoras para os elementos.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos os elementos que devem permanecer no centro da tela (botões e a entidade do jogador) estão ancorados ao ponto de ancoragem **Center of Screen**.

Os botões no canto superior esquerdo estão ancorados ao ancoradouro **Top-Left Corner**, porque devem permanecer no canto superior esquerdo.

O elemento de texto no canto inferior esquerdo está ancorado ao ponto de ancoragem **Bottom-Left Corner**, porque deve permanecer no canto inferior esquerdo.

O elemento de imagem no canto inferior direito está ancorado ao ponto de ancoragem **Bottom-Right Corner**, porque deve permanecer no canto inferior direito.

## Movendo Elementos para Fora da Tela

Por padrão, não é possível mover elementos para fora da tela, o que funciona como uma proteção caso um layout seja carregado em uma janela muito pequena ou incomum, para que os elementos ainda fiquem visíveis e possam ser interagidos.

Eles sempre permanecerão na tela e manterão um pequeno espaço entre eles e as bordas da tela.

Você pode **desativar** isso para elementos individuais **clicando com o botão direito** neles e depois desativando **Stay On Screen**.

> [!WARNING]
> Desativar isso pode, às vezes, fazer o elemento desaparecer, porque sua posição real estava fora da tela, mas o recurso o mantinha visível. Se isso acontecer, **desfaça** a última ação (desativar **Stay On Screen**) pelo atalho de desfazer ou em **barra de menu -> Edit -> Undo**, depois mova manualmente o elemento para o centro da tela e desative **Stay On Screen** novamente. Agora ele deve permanecer visível mesmo com o recurso desativado.

## Centralizando Elementos

Enquanto os elementos tiverem um tamanho fixo, centralizá-los é tão fácil quanto ancorá-los em um ponto de ancoragem baseado no centro.

Se o elemento mudar dinamicamente de tamanho com base em condições ou em qualquer outra coisa, isso fica um pouco mais complicado, mas o FancyMenu tem um ótimo recurso para isso! Nesse caso, primeiro ancore o elemento em um ponto de ancoragem baseado no centro e então clique com o botão direito nele. No menu de contexto, ative **Sticky Anchors**. Esse recurso altera a forma como o FancyMenu calcula a posição do elemento, fazendo com que ele sempre mantenha a mesma distância em relação ao seu ponto de ancoragem, independentemente de o tamanho mudar. Para âncoras baseadas no centro, ele sempre manterá a mesma distância da âncora até o centro absoluto do elemento, o que faz com que ele permaneça sempre centralizado ao usar âncoras baseadas no centro. (Para âncoras baseadas à esquerda, ele sempre manterá a mesma distância da âncora até o lado esquerdo do elemento, e para âncoras baseadas à direita, manterá a mesma distância a partir do lado direito do elemento.)

## Mais Maneiras de Melhorar o Posicionamento dos Elementos

Se **todos os pontos de ancoragem estiverem corretos**, mas seus elementos ainda estiverem se sobrepondo quando a janela fica pequena demais, é possível que seu layout simplesmente esteja muito cheio para a lógica normal de escala da GUI do Minecraft.

### Escala de GUI Forçada

Uma forma de melhorar o posicionamento dos elementos do layout é forçar uma escala de GUI no menu, **clicando com o botão direito no plano de fundo do editor** e selecionando **Force GUI Scale**. Isso fará com que o menu sempre tenha a mesma escala de GUI, independentemente da escala definida nas opções do Minecraft.

### Auto-Scaling

A última opção para corrigir sobreposições é usar **auto-scaling**.
Essa configuração dimensionará automaticamente o menu com base no tamanho da janela, tentando preservar a posição dos elementos da melhor forma possível ao redimensionar a janela. Para ativar o auto-scaling, **clique com o botão direito no plano de fundo do editor** e então clique em **Auto-Scaling**.

> [!WARNING]
> **Auto-scaling** pode fazer com que o **texto** renderizado pelo Minecraft **fique com aparência ruim**. Isso não é um bug, é apenas como a renderização de texto do Minecraft funciona. No caso de botões, uma boa alternativa é fazer com que os rótulos dos botões façam parte da textura de fundo do botão e definir um rótulo normal em branco para o botão.
