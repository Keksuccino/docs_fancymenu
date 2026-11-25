---
title: Visibilidade dos elementos
description: >-
  Como mostrar e ocultar elementos com requisitos, atrasos, efeitos de
  desvanecimento e opacidade, e como alterná-los com um botão.
sourceBlobSha: 819fbc2639734fc8658f6fb65e9df6b1234e9cc5
---

# Visibilidade dos elementos

Os elementos não precisam ficar visíveis o tempo todo. Eles podem aparecer apenas em determinadas situações, surgir um pouco depois, aparecer e desaparecer gradualmente ou ser ativados e desativados com um botão.

<img width="800" alt="Um texto de boas-vindas aparece gradualmente alguns segundos após a tela abrir; em seguida, um botão Regras do servidor faz um painel de regras aparecer e desaparecer gradualmente" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_visibility_toggle.gif?raw=true">

No editor de layout, os elementos estão sempre visíveis para que você ainda possa editá-los. Tudo nesta página funciona fora do editor.

> [!TIP]
> Todos os requisitos estão listados em [Requisitos](/conditions).

# Mostrar elementos apenas às vezes

Clique com o botão direito em um elemento e clique em **Requisitos de carregamento**. O elemento só aparece enquanto todos os seus [requisitos](/conditions) forem atendidos, como "o mouse está sobre este botão", "é dezembro" ou "uma variável tem este valor". O FancyMenu verifica os requisitos o tempo todo, então o elemento aparece ou desaparece imediatamente.

- **Modo do requisito** Inverte um requisito, como "NÃO é dezembro".
- Os grupos permitem combinar requisitos com "isto OU aquilo".
- Elementos do jogo base também têm **Requisitos de carregamento**. Para remover um elemento completamente, consulte [Elementos do jogo base removidos](/deleted-vanilla-elements).

Como adicionar e combinar requisitos: [Requisitos](/conditions#adding-a-requirement).

## Carregar apenas uma vez por sessão

Clique com o botão direito em um elemento e ative **Carregar apenas uma vez por sessão**. O elemento aparece na primeira vez que a tela é aberta. Depois que o jogador for para outra tela, o elemento permanecerá oculto até o jogo ser reiniciado.

Útil para dicas que devem aparecer apenas uma vez por início do jogo, como "Pressione F1 para ver os controles". Para usar a mesma ideia em scripts de ação, há o requisito [**Apenas uma vez por sessão**](/conditions#only-once-per-session).

# Atrasar elementos

## Atrasar a aparição

Clique com o botão direito em um elemento e clique em **Atrasar aparição**:

- **Atraso**:
  - **Sem atraso**: aparece imediatamente.
  - **Na primeira vez**: aguarda apenas na primeira vez que o elemento aparece após o início do jogo.
  - **Todas as vezes**: aguarda sempre que a tela é aberta e sempre que os requisitos voltam a ser atendidos.
- **Atraso em segundos**: por quanto tempo aguardar, como `1.5`.

Redimensionar a janela não reinicia o atraso.

## Atrasar o desaparecimento

Clique com o botão direito em um elemento e clique em **Atrasar desaparecimento**. Quando os requisitos deixam de ser atendidos, o elemento permanece por **Atraso em segundos** antes de desaparecer. **Atraso** tem as mesmas opções descritas acima.

Por exemplo, uma caixa de informações com o requisito [**O elemento está sob o cursor**](/conditions#is-element-hovered) de um botão permanece por 1 segundo depois que o mouse sai do botão.

# Aparecer e desaparecer gradualmente

Clique com o botão direito em um elemento e clique em **Aparecer/desaparecer gradualmente**:

- **Aparecimento gradual** e **Desaparecimento gradual**:
  - **Sem efeito gradual**: aparece ou desaparece imediatamente.
  - **Apenas uma vez**: o efeito ocorre apenas na primeira vez após o início do jogo.
  - **Todas as vezes**: o efeito ocorre todas as vezes.
- **Velocidade do aparecimento gradual** e **Velocidade do desaparecimento gradual**: em `1`, o efeito leva 2.5 segundos. `2` é duas vezes mais rápido.

Os elementos aparecem gradualmente quando a tela é aberta e quando seus requisitos são atendidos. Com **Atrasar aparição**, o efeito começa após o atraso.

O desaparecimento gradual só ocorre quando os requisitos ocultam o elemento, não quando a tela é fechada.

# Opacidade

Clique com o botão direito em um elemento e clique em **Opacidade**: `1.0` é totalmente visível, `0.5` é semitransparente e `0.0` é invisível. A maioria dos elementos tem essa opção.

A opacidade aceita [marcadores](/placeholders) e [variáveis](/variables), como `$$panel_opacity`. Os efeitos de aparecimento gradual param na opacidade definida para o elemento.

# Alternar elementos com um botão

Um botão pode mostrar e ocultar elementos, como o painel de regras no GIF acima. Uma [variável](/variables) registra se o painel está visível.

1. Clique com o botão direito no painel e clique em **Requisitos de carregamento**. Adicione [**O valor da variável (variável FM) é**](/conditions#is-variable-value-fm-variable) com a variável `show_rules` e o valor `true`.
2. Clique com o botão direito no botão e clique em **Editar script de ação**.
3. Clique com o botão direito na área do script e clique em **Adicionar instrução IF**. Defina o mesmo requisito do painel.
4. Adicione [**Definir valor da variável (variável FM)**](/action-scripts#set-variable-value-fm-variable) dentro do IF, com este valor:

   ```
   show_rules:false
   ```

5. Clique com o botão direito no IF e clique em **Adicionar instrução ELSE**. Adicione **Definir valor da variável (variável FM)** dentro do ELSE, com este valor:

   ```
   show_rules:true
   ```

Assim, cada clique inverte o valor da variável: painéis visíveis são ocultados e painéis ocultos são exibidos. Todos os elementos com o mesmo requisito aparecem e desaparecem juntos. Para um efeito suave, defina **Aparecimento gradual** e **Desaparecimento gradual** do painel como **Todas as vezes**.

Saiba mais sobre IF e ELSE em [Scripts de ação](/action-scripts#if-else-if-and-else).

> [!NOTE]
> As variáveis são mantidas depois que o jogo é fechado, então o painel continuará aberto na próxima inicialização. Para fechá-lo a cada inicialização, clique com o botão direito na variável em **Gerenciar variáveis** e ative **Limpar variável ao iniciar o jogo**.

## Alternar entre versões

Um botão também pode alternar entre mais de duas versões, como três planos de fundo:

1. Em **barra de menu -> Personalização -> Gerenciar variáveis**, adicione a variável de texto `background` com o valor `0`.
2. Defina o requisito **O valor da variável (variável FM) é** para os três [elementos de imagem](/elements#image), usando `background` com os valores `0`, `1` e `2`.
3. Defina **Definir valor da variável (variável FM)** para o botão com este valor. Ele conta `0`, `1`, `2` e recomeça em `0`:

   ```
   background:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"getvariable","values":{"name":"background"}} + 1) % 3"}}
   ```

Para adicionar mais versões, altere o `3` no final. Consulte [**Calculadora**](/placeholders#calculator) para ver como funciona a matemática.

# Ativar e desativar layouts

Para mostrar ou ocultar um layout inteiro:

- **Requisitos de carregamento [para todo o layout]** no menu exibido ao clicar com o botão direito no plano de fundo do editor funciona como os requisitos dos elementos. Consulte [Requisitos para todo o layout](/conditions#layout-wide-requirements).
- As ações [**Alternar layout**](/action-scripts#toggle-layout), [**Ativar layout**](/action-scripts#enable-layout) e [**Desativar layout**](/action-scripts#disable-layout) ativam e desativam um layout pelo nome.

Coloque o botão em um layout diferente daquele que ele desativa. Caso contrário, o botão desaparecerá junto com ele, e nada poderá reativar o layout.
