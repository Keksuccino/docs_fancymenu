---
title: Randomizar Layouts
description: Como randomizar layouts completos ou partes deles.
---

# Randomização

O FancyMenu tem vários recursos que ajudam você a randomizar layouts ou partes deles.

Isso pode ser útil, por exemplo, se você quiser que os usuários vejam diferentes fundos de tela toda vez que abrirem uma tela ou dicas aleatórias na tela de carregamento.

# Randomizando Layouts

Há um recurso no FancyMenu que permite criar um grupo de layouts e o sistema escolherá automaticamente um layout aleatório desse grupo. Fazendo isso, você basicamente pode exibir um design de menu completamente diferente e aleatório toda vez que o usuário iniciar o jogo ou abrir uma tela, mas isso também pode ser usado para alterar apenas partes da tela, por exemplo, o fundo.

## Modo Aleatório

Para randomizar layouts, você precisa habilitar o **Modo Aleatório** para cada layout que deve ser uma possível escolha na randomização. Para fazer isso, **clique com o botão direito** no **fundo do editor** e procure a entrada **Modo Aleatório**.

<br>

<img width="351" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/ef0f22d5-2f48-47cd-b526-d12415d8e099">

## Identificador do Grupo Aleatório

Depois de ativar o modo aleatório, você precisa definir o **Identificador do Grupo Aleatório**.
Esse número precisa ser **o mesmo** para todos os layouts que devem fazer parte do **mesmo grupo**.

<br>

<img width="301" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/dde0c94e-9729-4251-9aca-32a55c3dfd02">

<br>

<img width="377" alt="Screenshot_8" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/25e7777c-0503-4e54-b866-e85647241eee">

## Comportamento da Randomização

Se você quiser que o sistema escolha um layout aleatório do grupo **apenas uma vez por sessão de jogo**, habilite **Randomizar Apenas na Primeira Vez**. Isso fará com que ele escolha um layout na primeira vez que a tela for aberta e depois sempre use o layout escolhido na primeira vez. Se essa opção estiver desativada, um layout aleatório será escolhido toda vez que a tela for aberta.

<br>

<img width="305" alt="Screenshot_9" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/355e49eb-73b0-4646-aeb2-c6f113f6ce3b">

# Cenário de Exemplo 1: Fundo

Vamos supor que você queira randomizar o fundo da Tela Inicial.

Para isso, você precisa criar **um layout por fundo** e _**APENAS**_ alterar o fundo desses layouts e habilitar o modo aleatório com o identificador correto do grupo aleatório.

Neste exemplo, usamos o identificador de grupo aleatório **10**. Esse identificador precisa ser definido para cada layout desse grupo de layouts aleatórios.

A maneira mais fácil de fazer isso é preparar um layout com o identificador correto do grupo aleatório e então usar **Salvar Como**. Altere o fundo toda vez que salvar o layout com um novo nome; assim, você acabará com vários layouts com fundos diferentes, e um desses layouts será escolhido toda vez que você abrir a tela ou uma vez por sessão de jogo.

# Cenário de Exemplo 2: Elemento

Outro caso de uso comum é randomizar um elemento de texto ou imagem.

Assim como no caso do fundo, crie um layout para cada versão do elemento que você quer selecionar aleatoriamente. Adicione apenas o elemento aos layouts e nada mais. Não personalize mais nada e não adicione outros elementos.

Depois, basta salvar todos os layouts com o mesmo identificador de grupo aleatório, e um layout do grupo será escolhido quando você abrir a tela ou iniciar o jogo.
