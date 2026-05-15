---
title: Cabeças de Jogador
description: Como exibir a cabeça de um jogador como uma imagem 2D ou 3D em um menu.
---

# Cabeças de Jogador em Menus

Para exibir a cabeça de um jogador como uma imagem 2D ou 3D usando um elemento de imagem, você pode usar uma API web de terceiros chamada "Minotar".

## Imagem 2D

### 1. Adicione um Elemento de Imagem

No editor do FancyMenu, clique com o botão direito no fundo, selecione "Novo Elemento" e depois escolha "Imagem" (ou "Picture").

### 2. Defina a Fonte Web

Clique com o botão direito no elemento de imagem para acessar suas propriedades. Para o tipo de fonte, selecione "Web".

### 3. Monte a URL com o Placeholder Correto

No campo "Source", você deve inserir a seguinte URL:
`https://minotar.net/avatar/{"placeholder":"playername"}.png`

O FancyMenu usará `{"placeholder":"playername"}` para inserir dinamicamente o nome de usuário atual do jogador na URL, permitindo que o elemento de imagem busque e exiba sua cabeça no Minotar.

## Imagem 3D

Esta é bem parecida com a versão 2D, mas aqui precisamos usar uma URL diferente:

`https://minotar.net/cube/{"placeholder":"playername"}/200.png`

O `200` é o tamanho em pixels neste caso, então, se você quiser uma versão menor, basta substituí-lo por `100`, por exemplo; ou, para uma versão maior, use `300` e assim por diante.
