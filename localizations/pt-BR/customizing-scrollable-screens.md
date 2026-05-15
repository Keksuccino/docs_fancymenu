---
title: Telas Roláveis
description: Como personalizar telas roláveis.
---

# Personalizando Telas Roláveis

Personalizar telas roláveis, como as telas de Opções, pode ser um pouco complicado, já que o FancyMenu não consegue "ver" nem personalizar o conteúdo dentro de áreas roláveis.

Desde o FancyMenu v3.6.0+, é possível tornar ALGUMAS dessas telas personalizáveis expondo automaticamente os widgets dentro das áreas roláveis de uma tela específica. Isso é bastante poderoso, mas também bastante experimental, então não funcionará em todas as telas.

Para habilitar o recurso de exposição para uma tela específica, clique em **menu bar -> Customization -> Expose Scroll Area Content Of Current Screen**. Não é possível habilitar esse recurso para todas as telas de uma vez, e algumas telas não permitirão ativá-lo de forma alguma, como os menus de Singleplayer e Multiplayer.

Ativar esse recurso empilhará todos os widgets encontrados em áreas roláveis no canto superior esquerdo da tela. Isso é intencional e não é um bug. Então você pode abrir um layout **para a tela atual** e deverá conseguir ver e editar (mover, redimensionar etc.) esses widgets no editor.

A coisa mais importante a lembrar ao usar esse recurso é que expor widgets de áreas roláveis REMOVERÁ a área rolável original da tela, e tudo dentro da área rolável que não for um widget normal (widgets são botões e sliders) será PERDIDO, então não ficará visível nem interagível enquanto o recurso de exposição estiver ativado.
