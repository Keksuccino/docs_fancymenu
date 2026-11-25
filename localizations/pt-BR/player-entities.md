---
title: Entidades de jogador
description: >-
  Exiba jogadores nos seus menus com o elemento Entidade de jogador, incluindo
  skin, nome, pose, armadura e muito mais.
sourceBlobSha: b8f8d4340ca3a87e1c55c86f95f36786ab840644
---

# Entidades de jogador

O elemento Entidade de jogador exibe um jogador em 3D, como o personagem do próprio jogador ao lado dos botões da tela inicial. Ele pode copiar quem está jogando, exibir qualquer outro jogador ou representar um personagem próprio, com skin, capa e nome próprios.

<img width="800" alt="Cinco entidades de jogador: um jogador real com skin e capa, um com armadura de diamante encantada, espada e escudo, um agachado, um acenando e um bebê" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> No Minecraft 1.20.1 e versões mais recentes, as Entidades de jogador precisam do mod Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Sem ele, elas aparecem como um quadrado vermelho. Se ainda não houver uma versão do mod para a sua versão do Minecraft, não será possível exibir Entidades de jogador nela.

# Adicionar uma Entidade de jogador

Clique com o botão direito no fundo do editor e selecione **Novo elemento -> Entidade de jogador**. Arraste as alças para alterar o tamanho. O tamanho do jogador acompanha a altura do elemento.

Todas as configurações abaixo ficam no menu aberto ao clicar com o botão direito no elemento.

# Quem ela exibe

- **Copiar jogador do cliente** exibe quem está jogando, com o nome, a skin e a capa dessa pessoa. Enquanto essa opção estiver ativada, as configurações de nome, skin e capa ficarão bloqueadas.
- **Nome do jogador** pode ser qualquer nome; não precisa pertencer a um jogador real. Aceita [placeholders](/placeholders).
- **Exibir nome do jogador** mostra a etiqueta de nome acima da cabeça. Com **Rotação da etiqueta de nome** desativada, a etiqueta não gira junto com o jogador.

## Skin e capa

- **Skin automática** e **Capa automática** carregam a skin e a capa do jogador indicado em **Nome do jogador**. É necessária uma conexão com a internet.
- **Textura da skin** e **Textura da capa** usam seus próprios arquivos de skin e capa, como uma skin dos seus [recursos](/resources). As skins são os arquivos de skin normais do Minecraft.
- **Skin slim** é para skins com braços finos, como a da Alex. **Skin automática** e **Copiar jogador do cliente** detectam isso automaticamente.

# Pose e movimento

<img width="800" alt="Duas Entidades de jogador acompanham o ponteiro do mouse enquanto ele se move: a da esquerda vira apenas a cabeça; a da direita vira a cabeça e o corpo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **Cabeça acompanha o mouse** e **Corpo acompanha o mouse** fazem o jogador olhar para o ponteiro do mouse. As duas opções vêm ativadas nas novas Entidades de jogador.
- **Pose** define a pose do corpo: **Em pé**, **Agachado**, **Dormindo**, **Nadando**, **Morrendo** ou **Ataque giratório**.
- **Movimento do corpo** anima a pose.

## Pose da entidade

**Pose da entidade** abre uma janela com as rotações X, Y e Z da **Cabeça**, do **Corpo**, do **Braço esquerdo**, do **Braço direito**, da **Perna esquerda** e da **Perna direita**, de `-180` a `180`.

<img width="800" alt="A janela Pose da entidade, com controles deslizantes de rotação para a cabeça e o corpo do jogador" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

**Modo avançado**, ao lado de um controle deslizante, transforma o valor em um campo de texto que aceita [placeholders](/placeholders). Se o campo contiver uma [variável](/variables), como `$$arm_angle`, um [Scheduler](/schedulers) poderá animar o jogador alterando essa variável.

# Armadura, itens e mais

- **Armadura e ferramentas** equipa itens no jogador: **Armadura da cabeça**, **Armadura do peito**, **Armadura das pernas**, **Armadura dos pés**, **Item da mão esquerda** e **Item da mão direita**. Defina cada opção com um ID de item, como `minecraft:diamond_sword`. Os IDs de item aceitam placeholders. **Encantar armadura da cabeça** e as outras opções de encantamento adicionam o brilho de encantamento.
- **É bebê** deixa o jogador pequeno, como um bebê.
- **Papagaio** coloca um papagaio no ombro direito ou, com **Papagaio no ombro esquerdo**, no ombro esquerdo.

# É bom saber

- Não é possível girar, inclinar, esmaecer nem deixar as Entidades de jogador transparentes.
- Para exibir apenas a cabeça de um jogador, consulte [Cabeças de jogador](/player-heads).
- No Minecraft 1.19.2, as Entidades de jogador não precisam do Fancy Entity Renderer, mas têm menos configurações: **Agachado** no lugar de **Pose**, e não há **Rotação da etiqueta de nome**, **Movimento do corpo** nem **Armadura e ferramentas**. O tamanho é definido por **Escala da entidade** (padrão `30`; portanto, `60` é o dobro do tamanho), em vez de acompanhar o tamanho do elemento.
