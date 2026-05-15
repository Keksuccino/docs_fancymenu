---
title: Primeiros Passos
description: O mundo do FancyMenu espera por você! Este é o começo de algo bonito!
---

# Para Desenvolvedores

Se você é desenvolvedor e quer criar um addon para o FancyMenu ou integrar o FancyMenu ao seu mod, vale a pena dar uma olhada na [documentação para desenvolvedores](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki).

# Primeiros Passos

Usar o FancyMenu pela primeira vez pode parecer um pouco intimidador, mas não se preocupe: a maior parte é bem autoexplicativa assim que você começar a mexer com ele!

> Por favor, **lembre-se** de que esta página serve apenas para apresentar o FancyMenu e ajudar você nos seus **primeiros passos**.
Não deixe de conferir também o restante da documentação para informações mais detalhadas sobre os recursos do FancyMenu!
{.is-info}

# A Barra de Menu

Uma das primeiras coisas que você notará ao iniciar o jogo é a **barra de menu** no topo de cada menu.

A **barra de menu** é a sua porta de entrada para praticamente todos os recursos do FancyMenu, como **criar layouts** para **personalizar menus**, alterar o **título e o ícone da janela** e muito mais.

> Se você apertou algumas teclas sem querer e a **barra de menu desapareceu**, pode trazê-la de volta pressionando **CTRL + ALT + C**.
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# Seu Primeiro Layout

Como você provavelmente quer personalizar os menus do Minecraft, deixa eu te contar uma coisa sobre **layouts**!

Layouts funcionam como camadas de personalização para menus e permitem adicionar novos elementos e personalizar os existentes.

Para criar um novo layout para um **menu específico**:
1. Abra o menu para o qual você quer criar um layout (a Tela Inicial, por exemplo)
2. Abra a aba **Personalização** na **barra de menu**

As personalizações vêm desativadas por padrão para todos os menus, e você precisa ativá-las para cada menu que quiser personalizar. Então vamos clicar primeiro na entrada **"Personalização da Tela Atual: Desativada"**, o que vai alternar para **Ativada**.

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

Depois disso, clique em **Layouts -> Novo -> Para a Tela Atual**.

Isso abrirá o **editor de layout**, onde você pode adicionar elementos ao layout e personalizar elementos da Vanilla e de mods (como botões).

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## Editando o Layout

A maioria das opções de personalização pode ser acessada clicando com o **botão direito no fundo do editor**.

Isso abrirá um menu de contexto com várias opções, como personalizar o **fundo do menu** ou **adicionar elementos** ao layout.

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## Adicionando Elementos aos Layouts

Para adicionar um novo elemento ao seu layout, **clique com o botão direito** no fundo do editor.

No menu de contexto que abrir, clique em **Novo Elemento** e escolha um dos vários tipos de elementos.

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## Personalizando Elementos

Para personalizar um elemento, **clique com o botão direito** nele, o que abrirá um menu de contexto com tudo o que você pode personalizar para aquele tipo de elemento.

Além dos elementos que você adicionou, também é possível personalizar elementos da Vanilla (embora, às vezes, haja menos opções para eles)

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> Alguns menus de contexto como este são **roláveis**!

## Posicionando Elementos

Todo elemento no FancyMenu está conectado a um **ponto de ancoragem**.

Os pontos de ancoragem são necessários para calcular a posição de um elemento e, quando usados corretamente, evitam que os elementos se sobreponham, saiam da tela ou vão para o lugar errado quando a janela é redimensionada.

Eles são o ponto de origem a partir do qual a posição do elemento é calculada.

Por padrão, os elementos estão conectados ao ponto de ancoragem **"Centro da Tela"**, que basicamente é apenas o centro exato da tela, independentemente do tamanho da janela.
Então, digamos que um elemento esteja a 2 centímetros do centro da tela enquanto estiver conectado à âncora **"Centro da Tela"**. Nesse caso, o elemento estará **sempre** a 2 centímetros do centro da tela, não importa o tamanho da janela.

Você pode ver a qual ponto de ancoragem um elemento está conectado ao arrastá-lo. Isso também exibirá, por padrão, todos os outros pontos de ancoragem. Você pode passar o mouse sobre um ponto de ancoragem enquanto arrasta um elemento para alterar a âncora do elemento para o ponto sobre o qual o mouse estiver.

Você até pode usar um elemento como ponto de ancoragem para outros elementos! Basta passar o mouse sobre um elemento enquanto arrasta outro, e o ponto de ancoragem do elemento arrastado será alterado para o elemento sob o cursor.

**[Saiba mais sobre como posicionar seus elementos.](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## Salvando Seu Trabalho

Não se esqueça de salvar sua obra-prima!

Você verá um indicador de "Alterações não salvas" no canto superior direito do editor se precisar salvar suas alterações antes de fechar.

Salve seu trabalho clicando em **Layout -> Salvar**!

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> Você também pode salvar seu trabalho usando o atalho de teclado **CTRL + S**

*Parabéns! Agora você pode fazer os menus do Minecraft parecerem muito mais bonitos!*
