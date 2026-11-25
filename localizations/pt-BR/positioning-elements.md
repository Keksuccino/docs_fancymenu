---
title: Posicionamento de elementos
description: Como usar corretamente os pontos de ancoragem.
sourceBlobSha: c6c6b53374ed720fcdc32a3a0fbc1784f202cc5a
---

# Posicionando elementos no FancyMenu

No FancyMenu, a posição de cada elemento é determinada por **pontos de ancoragem**. Esses pontos são necessários para calcular onde um elemento deve aparecer na tela e garantir que os elementos não se sobreponham, saiam da tela ou se movam incorretamente quando a janela for redimensionada.

## Entendendo os pontos de ancoragem

Os pontos de ancoragem servem como origem para o cálculo da posição de um elemento. Por padrão, os elementos adicionados aos layouts são vinculados ao ponto de ancoragem **"Centro da tela"**. Esse ponto fica exatamente no meio da tela, independentemente do tamanho da janela.

Por exemplo, se um elemento estiver a 2 centímetros do centro da tela e estiver vinculado ao ponto de ancoragem **"Centro da tela"**, ele manterá essa distância mesmo que o tamanho da janela mude.

## Interagindo com pontos de ancoragem

Ao arrastar um elemento no editor, o ponto de ancoragem ao qual ele está conectado é destacado. Por padrão, essa ação também exibe todos os outros pontos de ancoragem disponíveis. Você pode mudar o ponto de ancoragem de um elemento arrastando-o sobre outro ponto e aguardando até que a barra de carregamento seja preenchida.

![Ilustração dos pontos de ancoragem](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Ancorando elementos a outros elementos

Um elemento pode usar outro elemento como ponto de ancoragem. Assim, ele se move junto com o outro elemento e mantém a distância em relação ao canto superior esquerdo dele. Isso é útil para painéis compostos por vários elementos, para um rótulo ao lado de um botão padrão do jogo e para [Arrastadores](/dragger).

Há duas maneiras de fazer isso. Em ambas, o elemento permanece no mesmo lugar.

### Arrastando

1. Arraste o elemento e mantenha o cursor sobre o outro elemento.
2. Aguarde até que a barra esteja cheia e solte o elemento.

Se o cursor já estiver sobre o outro elemento quando você começar a arrastar, mova-o para fora do elemento e depois de volta. Elementos que já estiverem sob o cursor no início não serão considerados.

As opções **Pairar sobre áreas de ancoragem** e **Pairar sobre elementos de ancoragem**, no menu **Janela**, precisam estar ativadas — ambas vêm ativadas por padrão. A primeira ativa e desativa a ancoragem ao manter o cursor sobre um elemento; a segunda adiciona outros elementos aos pontos de ancoragem. A opção **Tempo de espera para carregar ao pairar sobre áreas/elementos de ancoragem (segundos)**, no mesmo menu, define por quanto tempo você precisa manter o cursor sobre o elemento. O padrão é 2 segundos.

### Por ID

1. Clique com o botão direito no outro elemento e selecione **Copiar ID do elemento**.
2. Clique com o botão direito no elemento e selecione **Ponto de ancoragem -> Outro elemento**.
3. Cole o ID em **ID do elemento** e clique em **Concluído**.

Se vários elementos estiverem selecionados, as etapas 2 e 3 os ancoram todos de uma vez. Consulte [Identificadores de elementos](/element-identifiers) para saber mais sobre IDs.

## Pontos de ancoragem em áreas roláveis

Os elementos em uma [área rolável](/scrollable-areas) também têm pontos de ancoragem, mas eles pertencem ao conteúdo da área, e não à tela:

- **Canto superior esquerdo** corresponde ao canto superior esquerdo do conteúdo; **Centro da tela**, ao meio do conteúdo; e os pontos de ancoragem inferiores ficam no fim do conteúdo. Assim, um elemento pode ficar no final de uma lista longa e permanecer ali quando a lista aumentar.
- Os elementos de uma área só podem usar outros elementos dessa mesma área como ponto de ancoragem.
- Ao mover um elemento para dentro ou para fora de uma área, os elementos que estavam ancorados do outro lado da borda dela passam a usar o ponto de ancoragem **Canto superior esquerdo** e permanecem no mesmo lugar.

Isso funciona no modo **Pontos de ancoragem** da área. Nos outros modos, a própria área posiciona os elementos. Consulte [Áreas roláveis](/scrollable-areas#anchors-mode).

## Exemplo de como ancorar elementos

A captura de tela a seguir mostra como escolher os pontos de ancoragem dos elementos.

<br>
<img width="571" alt="Captura de tela_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos os elementos que devem permanecer no meio da tela (os botões e a entidade do jogador) estão ancorados ao ponto **Centro da tela**.

Os botões no canto superior esquerdo estão ancorados ao ponto **Canto superior esquerdo**, pois devem permanecer nesse canto.

O elemento de texto no canto inferior esquerdo está ancorado ao ponto **Canto inferior esquerdo**, pois deve permanecer nesse canto.

O elemento de imagem no canto inferior direito está ancorado ao ponto **Canto inferior direito**, pois deve permanecer nesse canto.

## Movendo elementos para fora da tela

Por padrão, não é possível mover elementos para fora da tela. Isso funciona como uma proteção caso um layout seja carregado em uma janela muito pequena ou com dimensões incomuns, garantindo que os elementos continuem visíveis e possam ser usados.

Eles sempre permanecerão na tela, mantendo uma pequena distância das bordas.

Você pode **desativar** esse recurso para elementos específicos clicando neles com o **botão direito** e desativando **Permanecer na tela**.

> [!WARNING]
> Desativar esse recurso pode fazer com que o elemento desapareça, pois a posição real dele estava fora da tela, mas o recurso o mantinha visível. Se isso acontecer, **desfaça** a última ação (desativar **Permanecer na tela**) usando o atalho para desfazer ou acessando **barra de menus -> Editar -> Desfazer**. Em seguida, mova manualmente o elemento para o meio da tela e desative **Permanecer na tela** novamente. Agora, ele deve continuar visível mesmo com o recurso desativado.

## Centralizando elementos

Se os elementos tiverem tamanho fixo, centralizá-los é simples: basta ancorá-los a um ponto de ancoragem baseado no centro.

Se o tamanho do elemento mudar dinamicamente de acordo com determinadas condições ou por outros motivos, o processo é um pouco mais complicado — mas o FancyMenu tem um ótimo recurso para isso! Nesse caso, primeiro ancore o elemento a um ponto de ancoragem baseado no centro e depois clique nele com o botão direito. No menu de contexto, ative **Ancoragem fixa**. Esse recurso muda a forma como o FancyMenu calcula a posição do elemento, fazendo com que ele mantenha sempre a mesma distância em relação ao ponto de ancoragem, independentemente de mudanças no tamanho. Com pontos de ancoragem baseados no centro, o elemento sempre manterá a mesma distância em relação ao ponto usando seu centro absoluto como referência, o que o manterá centralizado. (Com pontos de ancoragem à esquerda, ele manterá sempre a mesma distância em relação ao ponto usando o lado esquerdo do elemento como referência; com pontos de ancoragem à direita, usará o lado direito.)

## Outras maneiras de melhorar o posicionamento dos elementos

Se **todos os pontos de ancoragem estiverem corretos**, mas os elementos ainda se sobrepuserem quando a janela ficar pequena demais, é possível que o layout simplesmente esteja cheio demais para a lógica normal de escala da interface do Minecraft.

### Escala forçada da interface

Uma maneira de melhorar o posicionamento dos elementos no layout é forçar uma escala da interface no menu. Para isso, **clique com o botão direito no plano de fundo do editor** e selecione **Forçar escala da interface**. Assim, o menu sempre terá a mesma escala, independentemente da escala definida nas opções do Minecraft.

### Escala automática

A última opção para corrigir sobreposições é usar a **escala automática**.
Essa opção ajusta automaticamente a escala do menu com base no tamanho da janela para tentar preservar ao máximo as posições dos elementos quando ela for redimensionada. Para ativar a escala automática, **clique com o botão direito no plano de fundo do editor** e selecione **Escala automática**.

> [!WARNING]
> A **escala automática** pode fazer com que o **texto** renderizado pelo Minecraft **fique com aparência ruim**. Isso não é um erro; é simplesmente a forma como a renderização de texto do Minecraft funciona. Para botões, uma boa solução alternativa é incluir os rótulos na textura de fundo do botão e deixar em branco o rótulo normal do botão.
