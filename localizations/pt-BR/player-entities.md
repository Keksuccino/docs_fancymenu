---
title: Entidades do Jogador
description: >-
  Como o elemento "Entidade do Jogador" do FancyMenu funciona e como usá-lo
  corretamente.
---
# Entidades do Jogador

O FancyMenu permite adicionar entidades de jogador às telas, para que você possa exibir o jogador do cliente ou outros jogadores, incluindo entidades personalizadas que não representam um jogador real de forma alguma, com skin, nome, capa e muito mais personalizados.

# Jogador do Cliente

Para mostrar um "espelho" do jogador do cliente, basta clicar com o botão direito no elemento Entidade do Jogador e ativar **Copiar Jogador do Cliente**. Isso copiará a skin, a capa e o nome do jogador do cliente.

# Outros Jogadores

Se você quiser mostrar outro jogador existente, basta clicar com o botão direito no elemento e definir **Nome do Jogador** para o nome de um jogador existente. Isso mostrará automaticamente a skin, a capa e o nome desse jogador existente, desde que você não tenha uma skin ou capa personalizada definida e **Copiar Jogador do Cliente** esteja **desativado**.

# Entidades de Jogador Personalizadas

Se você não quiser mostrar um jogador real e, em vez disso, quiser personalizar totalmente a skin, a capa e o nome da entidade, você pode clicar com o botão direito no elemento. Há opções para definir uma textura personalizada de skin e capa. Se uma skin e capa personalizadas estiverem ativas, você também pode definir qualquer nome de jogador que quiser sem que a skin do nome do jogador seja copiada, caso o jogador exista.

# Pose da Entidade

O elemento Entidade do Jogador tem suporte completo para personalizar sua pose, ou seja, você pode mover livremente todos os seus membros, partes do corpo etc.

Para fazer isso, clique com o botão direito no elemento e clique em **Pose do Jogador**. Isso abrirá uma tela com controles deslizantes para configurar a rotação X/Y/Z de todas as partes do corpo.

As configurações de pose do jogador têm um modo normal, em que você pode personalizar as rotações com controles deslizantes, e também há um modo avançado que permite inserir texto para todas as rotações com suporte completo a placeholders, o que torna possível até animar a entidade com um elemento Ticker que define variáveis de rotação!

# Alterando o Tamanho da Entidade

No Minecraft 1.20.1+, você pode simplesmente usar os manipuladores normais de redimensionamento do elemento para escalar a entidade.

Para versões mais antigas (1.19.2 e anteriores), os elementos Entidade do Jogador não suportam redimensionamento direto pelos manipuladores de redimensionamento. Em vez disso, você precisa clicar com o botão direito no elemento e clicar em **Escala**. Isso permite definir uma escala para o elemento. O padrão deve ser `30`; então, defini-lo como `60`, por exemplo, faz o jogador ficar duas vezes maior do que o normal, definir como `15` mostra-o com metade do tamanho e assim por diante.

# Dependência: Fancy Entity Renderer (FER)

Para o **Minecraft 1.20.1+**, é necessário um **mod extra** para fazer os elementos Entidade do Jogador funcionarem. O mod se chama **Fancy Entity Renderer** e está disponível no [CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer) e no [Modrinth](https://modrinth.com/mod/fancy-entity-renderer).

Se ainda não houver uma build disponível para a versão do Minecraft que você está usando, é muito provável que ela seja lançada mais tarde.

Lembre-se de que o FER não é desenvolvido por Keksuccino, então ele não tem controle sobre quando as builds são lançadas.
