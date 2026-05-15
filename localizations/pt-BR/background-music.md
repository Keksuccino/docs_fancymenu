---
title: Música de Fundo do Menu
description: Como personalizar a música reproduzida nos menus.
---

# Música de Fundo do Menu

É possível substituir a música padrão de fundo dos menus do Minecraft por faixas personalizadas ou simplesmente desativar a música Vanilla normal que toca nos menus.

# Desativando a Música Vanilla

O FancyMenu oferece várias maneiras de desativar a música de menu Vanilla. Isso pode ser útil se você planeja reproduzir outras faixas de áudio nas telas ou se simplesmente não quer que nenhuma música toque em algumas telas.

## Globalmente

Se você não quiser música em nenhum menu, esta é a maneira mais fácil de fazer isso.

Para desativar ou substituir globalmente a música de menu Vanilla no FancyMenu 3.9.0+, vá até a barra de menus do FancyMenu no topo das telas e clique em **Customization -> Global Customizations**. As Global Customizations podem substituir a música do menu sem exigir um resource pack e sem precisar habilitar personalizações para cada tela.

<br>
<img width="600" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/d829a35e-f23f-42a9-ad79-193de73b499b">

> Desativar a música padrão do Minecraft irá desativá-la em todas as telas, não apenas na atual.
{.is-info}

## Por Tela

Se você quiser mais controle sobre onde a música dos menus Vanilla deve tocar, você deve usar o elemento **Music Controller**. Esse elemento é adicionado aos layouts como qualquer outro, clicando com o **botão direito no fundo do editor** e depois em **New Element -> Music Controller**.

Ao **clicar com o botão direito** no elemento, você pode personalizar quais tipos de música tocada nos menus devem ser desativados (música normal de menu e música do mundo que continua tocando em telas que não pausam o jogo, como a tela do Inventário).

> Esse elemento oferece suporte a **requisitos de carregamento**, então você tem ainda mais controle sobre quando a música Vanilla deve tocar!
{.is-info}


# Adicionando Música Personalizada

Agora podemos adicionar a música de fundo personalizada de fato.

Se você quiser tocar a mesma música personalizada em todas as telas e precisar de controle no nível do layout, você deve usar um **layout universal**, que é carregado em todas as telas que têm personalizações habilitadas. Para uma substituição global simples da música do menu, use [Global Customizations](/global-customizations) em vez disso.

Ao usar um layout universal, a música irá **continuar tocando** ao ir de um menu com o layout habilitado para outro com o mesmo layout habilitado.

Se você quiser tocar músicas diferentes por tela, use layouts normais.

Neste exemplo, usaremos **layouts universais**.

Adicione um novo elemento **Audio** ao layout universal, que funcionará como nosso tocador de música de fundo.

<br>
<img width="400" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/bddf8f46-47c5-4a00-a6f7-b5ca1df8ae67">

Agora adicione a ele as faixas que devem tocar ao fundo.

<br>
<img width="300" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/824dcb90-3bd5-4c0b-96d0-e581a7c2f9f7">

Basicamente, é isso.
Você também pode definir o elemento Audio para o modo aleatório e alterar seu canal de som, se necessário.

Salve o layout e saia do editor.

# Habilitando Personalizações para Todos os Menus

Usamos um **layout universal** neste exemplo, porque queremos que nossa música de fundo toque em várias telas.

Como os layouts só são carregados em telas que têm **personalizações habilitadas**, agora precisamos habilitá-las para todas as telas em que queremos que a música toque.

Para fazer isso, clique em **Customization** e habilite **Current Screen Customization**.

<br>
<img width="320" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/2f6527b7-ae14-4e82-abc6-3572cc6490b2">

Repita isso para todas as telas em que você quer que sua música de fundo personalizada toque.

E é isso! Agora você tem música de fundo personalizada nos menus do Minecraft!
