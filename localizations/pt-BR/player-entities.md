---
title: Entidades de Jogador
description: >-
  Como o elemento "Player Entity" do FancyMenu funciona e como usá-lo
  corretamente.
---

# Entidades de Jogador

O FancyMenu permite adicionar entidades de jogador às telas, para que você possa exibir o jogador do cliente ou outros jogadores, incluindo entidades personalizadas que não representam um jogador real, com skin, nome, capa e muito mais personalizados.

# Jogador do Cliente

Para mostrar um "espelho" do jogador do cliente, basta clicar com o botão direito no elemento Player Entity e ativar **Copy Client Player**. Isso copiará a skin, a capa e o nome do jogador do cliente.

# Outros Jogadores

Se você quiser mostrar outro jogador existente, basta clicar com o botão direito no elemento e definir **Player Name** para o nome de um jogador existente. Isso exibirá automaticamente a skin, a capa e o nome desse jogador existente, desde que você não tenha uma skin ou capa personalizada definida e **Copy Client Player** esteja **desativado**.

# Entidades de Jogador Personalizadas

Se você não quiser mostrar um jogador real e, em vez disso, quiser personalizar totalmente a skin, a capa e o nome da entidade, você pode clicar com o botão direito no elemento. Há opções para definir uma skin e uma textura de capa personalizadas. Se uma skin e capa personalizadas estiverem ativas, você também pode definir qualquer nome de jogador que quiser sem que a skin do nome do jogador seja copiada, caso o jogador exista.

# Pose da Entidade

O elemento Player Entity tem suporte total para personalizar sua pose; em outras palavras, você pode mover livremente todos os seus membros, partes do corpo etc.

Para fazer isso, clique com o botão direito no elemento e clique em **Player Pose**. Isso abrirá uma tela com controles deslizantes para configurar a rotação X/Y/Z de todas as partes do corpo.

As configurações de pose do jogador têm um modo normal, no qual você pode personalizar as rotações com controles deslizantes, e também há um modo avançado que permite inserir texto para todas as rotações com suporte total a placeholders, o que até torna possível animar a entidade com um elemento Ticker que define variáveis de rotação!

# Alterando o Tamanho da Entidade

No Minecraft 1.21.1+, você pode simplesmente usar os manipuladores normais de redimensionamento do elemento para escalar a entidade.

Em versões mais antigas (1.21.0 e anteriores), os elementos Player Entity não oferecem suporte a redimensionamento direto pelos manipuladores de redimensionamento. Em vez disso, você precisa clicar com o botão direito no elemento e clicar em **Scale**. Isso permite definir uma escala para o elemento. O valor padrão deve ser `30`, então defini-lo como `60`, por exemplo, faz o jogador ficar duas vezes maior que o normal; defini-lo como `15` o mostra com metade do tamanho e assim por diante.

# Dependência: Fancy Entity Renderer (FER)

No Minecraft 1.21.1+, é necessário um mod extra para fazer os elementos Player Entity funcionarem. O mod se chama "Fancy Entity Renderer" e está disponível no CurseForge e no Modrinth.

Se ainda não houver uma versão disponível para a versão do Minecraft que você está usando, muito provavelmente ela será lançada mais tarde.

Lembre-se de que o FER não é desenvolvido por Keksuccino, então ele não tem controle sobre quando as versões são lançadas.
