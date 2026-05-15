---
title: Dragger
description: Como arrastar elementos em menus usando o elemento Dragger.
---

# Dragger

O elemento Dragger é um elemento no FancyMenu que permite tornar menus interativos de uma forma um tanto incomum. O Dragger é um elemento que pode ser arrastado com o mouse FORA do editor, o que significa que os usuários basicamente podem pegar o elemento e movê-lo.

Isso é legal e tudo mais, mas mover um elemento que não faz mais nada é meio inútil, certo? Bem, não, porque você pode anexar outros elementos a ele definindo o elemento Dragger como ponto de ancoragem para os outros elementos que devem se mover junto com o Dragger.

O deslocamento de posição dos elementos Dragger é persistente e é salvo entre reinicializações do jogo, o que basicamente significa que, quando um usuário move o Dragger, ele permanece nessa posição "personalizada", mesmo ao reiniciar o jogo.

O elemento Dragger só fica visível no editor e invisível fora dele, então certifique-se de usar outro elemento como "corpo" para ele, se quiser que o usuário veja onde fica a área arrastável.
