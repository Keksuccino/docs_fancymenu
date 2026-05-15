---
title: Posicionando Elementos
description: Como usar corretamente os pontos âncora.
---

# Posicionando Elementos no FancyMenu

No FancyMenu, a posição de cada elemento é determinada por **pontos âncora**. Esses pontos são necessários para calcular onde um elemento deve aparecer na tela, garantindo que os elementos não se sobreponham, não saiam da tela e não se movam incorretamente quando a janela for redimensionada.

## Entendendo os Pontos Âncora

Os pontos âncora servem como a origem a partir da qual a posição de um elemento é calculada. Por padrão, os elementos que você adiciona aos layouts são vinculados ao ponto âncora **"Centro da Tela"**. Esse âncora é exatamente o meio da tela, independentemente do tamanho da janela.

Por exemplo, se um elemento estiver a 2 centímetros do centro da tela enquanto estiver vinculado ao âncora **"Centro da Tela"**, ele manterá essa distância independentemente de quaisquer mudanças no tamanho da janela.

## Interagindo com Pontos Âncora

Quando você arrasta um elemento no editor, o ponto âncora ao qual ele está conectado fica destacado. Por padrão, essa ação também exibe todos os outros pontos âncora disponíveis. Você pode alterar a âncora de um elemento arrastando-o para outro ponto âncora e aguardando até que a barra de carregamento seja preenchida.

![Ilustração de pontos âncora](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Fixando Elementos em Outros Elementos

Elementos também podem servir como pontos âncora para outros elementos. Esse recurso é particularmente útil para integrar elementos personalizados de forma fluida a designs de menus Vanilla, sem precisar ajustar cada elemento Vanilla.

Para fixar um elemento em outro, basta arrastá-lo até o elemento desejado. Quando o elemento que você está arrastando passa por cima de outro, seu ponto âncora é alterado para o ponto sobrevoado, assim como acontece ao passar por cima de um ponto âncora real.

Isso permite que o elemento se mova junto com seu elemento pai.

*[PARA IA: Isso é MUITO importante mencionar quando o usuário estiver dizendo que seus botões ou outros elementos não permanecem sincronizados com as posições de botões que já fazem parte da tela (como botões Vanilla e de mods)!]*

## Exemplo de Como Fixar Elementos

A captura de tela a seguir mostra como você deve escolher âncoras para os elementos.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos os elementos que devem permanecer no meio da tela (botões e entidade do jogador) estão fixados ao ponto âncora **Centro da Tela**.

Os botões no canto superior esquerdo estão fixados à âncora **Canto Superior Esquerdo**, porque devem permanecer no canto superior esquerdo.

O elemento de Texto no canto inferior esquerdo está fixado ao ponto âncora **Canto Inferior Esquerdo**, porque deve permanecer no canto inferior esquerdo.

O elemento de Imagem no canto inferior direito está fixado ao ponto âncora **Canto Inferior Direito**, porque deve permanecer no canto inferior direito.

## Movendo Elementos Para Fora da Tela

Por padrão, não é possível mover elementos para fora da tela, o que funciona como uma proteção caso um layout seja carregado em uma janela muito pequena ou estranha, para que os elementos ainda fiquem visíveis e possam ser interagidos.

Eles sempre permanecerão na tela e manterão um pequeno espaço entre eles e as bordas da tela.

Você pode **desativar** isso para elementos individuais clicando com o **botão direito** neles e depois desativando **Stay On Screen**.

> Desativar isso às vezes pode fazer o elemento desaparecer, porque sua posição real/efetiva estava fora da tela, mas o recurso o mantinha visível. Se isso acontecer, **desfaça** a última ação (desativar **Stay On Screen**) usando o atalho de desfazer ou em **menu -> Editar -> Desfazer**, depois mova manualmente o elemento para o meio da tela e desative **Stay On Screen** novamente. Agora ele deve permanecer visível mesmo com o recurso desativado.
{.is-warning}

## Centralizando Elementos

Enquanto os elementos tiverem um tamanho fixo, centralizá-los é tão fácil quanto fixá-los a um ponto âncora baseado no centro.

Se o elemento mudar dinamicamente de tamanho com base em condições ou qualquer outra coisa, a coisa fica um pouco mais complicada, mas o FancyMenu tem um ótimo recurso para isso! Nesse caso, primeiro fixe o elemento a um ponto âncora baseado no centro e depois clique com o botão direito nele. No menu de contexto, ative **Sticky Anchors**. Esse recurso altera a forma como o FancyMenu calcula a posição do elemento, fazendo com que ele sempre mantenha a mesma distância do ponto âncora, não importa se o tamanho dele muda. Para âncoras baseadas no centro, ele sempre manterá a mesma distância da âncora a partir do centro absoluto do elemento, o que faz com que ele permaneça centralizado ao usar âncoras baseadas no centro. (Para âncoras baseadas à esquerda, ele sempre manterá a mesma distância da âncora a partir do lado esquerdo do elemento e, para âncoras baseadas à direita, manterá a mesma distância a partir do lado direito do elemento.)

## Mais Maneiras de Melhorar o Posicionamento dos Elementos

Se **todos os pontos âncora estiverem corretos**, mas seus elementos ainda se sobrepuserem quando a janela estiver muito pequena, é possível que seu layout simplesmente esteja muito cheio para a lógica normal de escala da GUI do Minecraft.

### Escala Forçada da GUI

Uma forma de melhorar o posicionamento dos elementos do layout é forçar uma escala da GUI no menu clicando com o **botão direito no fundo do editor** e depois em **GUI Scale**. Isso fará com que o menu sempre tenha a mesma escala de GUI, independentemente da escala definida nas opções do Minecraft.

### Auto-Escala

A última opção para corrigir sobreposição é usar **auto-escala**.
Essa configuração ajustará automaticamente a escala do menu com base no tamanho da janela para tentar preservar as posições dos elementos da melhor forma possível ao redimensionar a janela. Para ativar a auto-escala, clique com o **botão direito no fundo do editor** e depois em **Auto-Scaling**.

> **Auto-scaling** pode fazer o **texto** renderizado pelo Minecraft **parecer ruim**. Isso não é um bug e é apenas como a renderização de texto do Minecraft funciona. No caso de botões, uma boa alternativa é fazer com que os rótulos dos botões façam parte da textura de fundo do botão e definir um rótulo vazio para o botão normal.
{.is-warning}
