---
title: Placeholders
description: Como usar placeholders.
---
# Placeholders

Placeholders inserem valores em tempo real em textos, botões, requisitos e outros campos compatíveis.

# Informações Gerais

## Sintaxe Básica
Os placeholders no FancyMenu usam uma sintaxe parecida com JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Por exemplo, para exibir o nome do jogador:
```
{"placeholder":"playername"}
```

## Aninhando Placeholders
Você pode usar um placeholder dentro do valor de outro placeholder.

Exemplo de placeholders aninhados:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Este exemplo pega o valor máximo de RAM e divide por 1024 para convertê-lo de MB para GB.

> [!IMPORTANT]
> Esta é a sintaxe do FancyMenu, não JSON. Placeholders aninhados usam exatamente a forma sem escape mostrada acima, então formatadores JSON irão rejeitá-los ou reescrevê-los. Os nomes dos placeholders diferenciam maiúsculas de minúsculas; placeholders inválidos ou desconhecidos continuam visíveis como texto e são registrados.

# Usando Placeholders

A maioria dos elementos que possuem campos de texto suporta placeholders. Você pode ver se um campo de texto suporta placeholders ao editá-lo. Se o **editor de texto** em tela cheia abrir ao editar o texto, ele suporta placeholders.

Para encontrar uma **lista de todos os placeholders**, basta clicar no botão **Placeholders** no **canto superior direito** do **editor de texto**.

Há uma **barra de pesquisa** no topo da lista de placeholders que permite procurar placeholders.

Clicar em um placeholder na lista irá colá-lo no conteúdo de texto.

# Placeholders em Detalhe

Esta seção lista os placeholders nativos do FancyMenu.

## Resultados Indisponíveis

A saída de um placeholder é sempre texto. Quando os dados não estão disponíveis, o resultado depende do placeholder: os fallbacks comuns são uma string vazia, `0`, `0.0`, `00:00`, `false`, `UNKNOWN` ou `ERROR`. Entradas com um fallback específico o informam diretamente; teste o fallback antes de usar saída dependente do ambiente em um [requisito](./conditions), caminho, comando ou URL.

## Nome do Jogador (`playername`)

**Finalidade:** Retorna o nome de usuário do jogador atual.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"playername"}
```

**Saída:** `Steve`

## UUID do Jogador (`playeruuid`)

**Finalidade:** Retorna o identificador único do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"playeruuid"}
```

**Saída:** `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Versão do Minecraft (`mcversion`)

**Finalidade:** Retorna a versão atual do Minecraft.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"mcversion"}
```

**Saída:** `1.21.1`

## Versão do Loader de Mods (`loaderver`)

**Finalidade:** Retorna a versão do carregador de mods (Fabric/NeoForge).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"loaderver"}
```

**Saída:** `0.16.14`

## Nome do Loader de Mods (`loadername`)

**Finalidade:** Retorna o nome do carregador de mods.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"loadername"}
```

**Saída:** `Fabric`

## Versão do Mod (`modversion`)

**Finalidade:** Retorna a versão de um mod específico.

**Valores:** `modid`

**Exemplo:**

```
{"placeholder":"modversion","values":{"modid":"example_mod"}}
```

**Saída:** `1.2.3`

## Contagem Total de Mods (`totalmods`)

**Finalidade:** Retorna uma contagem aproximada de arquivos de mods com base na pasta `mods` e na contagem de mods carregados. Não conta de forma confiável todos os mods desativados.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"totalmods"}
```

**Saída:** `45`

## Contagem de Mods Ativos (`loadedmods`)

**Finalidade:** Retorna o número de mods atualmente carregados.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"loadedmods"}
```

**Saída:** `43`

## Progresso de Carregamento do Mundo (`world_load_progress`)

**Finalidade:** Retorna o progresso atual de carregamento do mundo em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"world_load_progress"}
```

**Saída:** `75`

## Valor de Opção do Minecraft (`minecraft_option_value`)

**Finalidade:** Retorna o valor de uma opção do Minecraft.

**Valores:** `name`

**Exemplo:**

```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```

**Saída:** `70`

## Último Mundo ou Servidor (`last_world_server`)

**Finalidade:** Retorna informações sobre o último mundo ou servidor acessado.

**Valores:** `type`, `full_world_path`

**Exemplo:**

```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parâmetros:
- `type`: Determina que tipo de informação retornar
  - `"both"`: Retorna o último mundo ou servidor acessado (padrão)
  - `"server"`: Retorna apenas se o último acesso foi a um servidor
  - `"world"`: Retorna apenas se o último acesso foi a um mundo
- `full_world_path`: Controla como os caminhos dos mundos são exibidos
  - `"true"`: Retorna o caminho completo do mundo (padrão)
  - `"false"`: Retorna apenas o nome do mundo sem o caminho (não afeta servidores)

Exemplos:
- Servidor: `mc.hypixel.net`
- Mundo com caminho completo: `saves/New World`
- Mundo sem caminho completo: `New World`

## Largura da Tela (`guiwidth`)

**Finalidade:** Retorna a largura atual da tela em pixels escalados da GUI, não em pixels físicos do monitor.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"guiwidth"}
```

**Saída:** `960`

## Altura da Tela (`guiheight`)

**Finalidade:** Retorna a altura atual da tela em pixels escalados da GUI, não em pixels físicos do monitor.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"guiheight"}
```

**Saída:** `540`

## Identificador da Tela Atual (`screenid`)

**Finalidade:** Retorna o identificador da tela atual.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"screenid"}
```

**Saída:** `title_screen`

## Largura do Elemento (`elementwidth`)

**Finalidade:** Retorna a largura de um elemento específico.

**Valores:** `id`

**Exemplo:**

```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```

**Saída:** `200`

## Altura do Elemento (`elementheight`)

**Finalidade:** Retorna a altura de um elemento específico.

**Valores:** `id`

**Exemplo:**

```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```

**Saída:** `20`

## Posição X do Elemento (`elementposx`)

**Finalidade:** Retorna a posição X de um elemento específico.

**Valores:** `id`

**Exemplo:**

```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```

**Saída:** `150`

## Posição Y do Elemento (`elementposy`)

**Finalidade:** Retorna a posição Y de um elemento específico.

**Valores:** `id`

**Exemplo:**

```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```

**Saída:** `100`

## Posição X do Mouse (`mouseposx`)

**Finalidade:** Retorna a posição X atual do mouse.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"mouseposx"}
```

**Saída:** `960`

## Posição Y do Mouse (`mouseposy`)

**Finalidade:** Retorna a posição Y atual do mouse.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"mouseposy"}
```

**Saída:** `540`

## Cliques Por Segundo (`clicks_per_second`)

**Finalidade:** Retorna os cliques por segundo atuais de um botão do mouse.

**Valores:** `mouse_button`

**Exemplo:**

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parâmetros:
- `mouse_button`: `left` ou `right`

**Saída:** `8`

## Escala da GUI (`guiscale`)

**Finalidade:** Retorna a escala atual da GUI.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"guiscale"}
```

**Saída:** `2`

## Rótulo/Text de Widget/Botão Vanilla (`vanillabuttonlabel`)

**Finalidade:** Retorna o rótulo/texto de um widget/botão vanilla.

**Valores:** `locator`

**Exemplo:**

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```

**Saída:** `Options...`

## Valor do Campo de Texto (`text_input_field_value`)

**Finalidade:** Retorna o valor atual de um campo de texto customizado ou vanilla pelo identificador do elemento.

**Valores:** `element_identifier`

**Exemplo:**

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```

**Saída:** `Hello World`

## Vida Atual do Jogador (`current_player_health`)

**Finalidade:** Retorna os pontos de vida atuais do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_health"}
```

**Saída:** `20.0`

## Vida Máxima do Jogador (`max_player_health`)

**Finalidade:** Retorna os pontos máximos de vida do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"max_player_health"}
```

**Saída:** `20.0`

## Vida Atual do Jogador (Percentual) (`current_player_health_percent`)

**Finalidade:** Retorna a vida do jogador em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_health_percent"}
```

**Saída:** `100`

## Vida de Absorção Atual do Jogador (`current_player_absorption_health`)

**Finalidade:** Retorna os pontos de vida de absorção do jogador (corações dourados).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_absorption_health"}
```

**Saída:** `4.0`

## Vida Máxima de Absorção do Jogador (`max_player_absorption_health`)

**Finalidade:** Retorna a vida máxima de absorção.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"max_player_absorption_health"}
```

**Saída:** `4.0`

## Vida de Absorção Atual do Jogador (Percentual) (`current_player_absorption_health_percent`)

**Finalidade:** Retorna a vida de absorção do jogador em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_absorption_health_percent"}
```

**Saída:** `100`

## Nível de Fome Atual do Jogador (`current_player_hunger`)

**Finalidade:** Retorna o nível atual de fome do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_hunger"}
```

**Saída:** `20`

## Nível Máximo de Fome do Jogador (`max_player_hunger`)

**Finalidade:** Retorna o nível máximo de fome.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"max_player_hunger"}
```

**Saída:** `20`

## Nível Atual de Fome do Jogador (Percentual) (`current_player_hunger_percent`)

**Finalidade:** Retorna a fome do jogador em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_hunger_percent"}
```

**Saída:** `100`

## Saturação de Fome Atual do Jogador (`current_player_hunger_saturation`)

**Finalidade:** Retorna o valor atual de saturação de fome do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_hunger_saturation"}
```

**Saída:** `5.0`

## Armadura Atual do Jogador (`current_player_armor`)

**Finalidade:** Retorna o valor atual da armadura do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_armor"}
```

**Saída:** `20`

## Resistência da Armadura do Jogador (`player_armor_toughness`)

**Finalidade:** Retorna o valor total de resistência da armadura do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_armor_toughness"}
```

**Saída:** `8.0`

## Armadura Máxima do Jogador (`max_player_armor`)

**Finalidade:** Retorna o valor máximo da armadura.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"max_player_armor"}
```

**Saída:** `20`

## Armadura Atual do Jogador (Percentual) (`current_player_armor_percent`)

**Finalidade:** Retorna a armadura do jogador em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_armor_percent"}
```

**Saída:** `100`

## Nível de Oxigênio Atual do Jogador (`current_player_oxygen`)

**Finalidade:** Retorna o nível atual de oxigênio do jogador (bolhas de ar).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_oxygen"}
```

**Saída:** `300`

## Nível Máximo de Oxigênio do Jogador (`max_player_oxygen`)

**Finalidade:** Retorna o nível máximo de oxigênio.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"max_player_oxygen"}
```

**Saída:** `300`

## Nível Atual de Oxigênio do Jogador (Percentual) (`current_player_oxygen_percent`)

**Finalidade:** Retorna o nível de oxigênio do jogador em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_oxygen_percent"}
```

**Saída:** `100`

## Nível Atual do Jogador (`current_player_level`)

**Finalidade:** Retorna o nível de experiência atual do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_level"}
```

**Saída:** `30`

## Experiência Atual do Jogador (`current_player_exp`)

**Finalidade:** Retorna os pontos totais de experiência do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_exp"}
```

**Saída:** `1250`

## Progresso de Experiência do Jogador (Percentual) (`current_player_exp_progress`)

**Finalidade:** Retorna o progresso de experiência do jogador até o próximo nível em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_player_exp_progress"}
```

**Saída:** `75`

## Força de Ataque do Jogador (Percentual) (`player_attack_strength`)

**Finalidade:** Retorna o tempo de recarga do ataque do jogador em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_attack_strength"}
```

**Saída:** `100`

## Modo de Jogo do Jogador (`player_gamemode`)

**Finalidade:** Retorna o modo de jogo atual do jogador.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_gamemode"}
```

**Saída:** `survival`

## Direção de Visão do Jogador (`player_view_direction`)

**Finalidade:** Retorna a direção para a qual o jogador está olhando.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_view_direction"}
```

**Saída:** `north`

## Coordenada X do Jogador (`player_x_coordinate`)

**Finalidade:** Retorna a posição X do jogador no mundo.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_x_coordinate"}
```

**Saída:** `125`

## Coordenada Y do Jogador (`player_y_coordinate`)

**Finalidade:** Retorna a posição Y do jogador no mundo.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_y_coordinate"}
```

**Saída:** `64`

## Coordenada Z do Jogador (`player_z_coordinate`)

**Finalidade:** Retorna a posição Z do jogador no mundo.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_z_coordinate"}
```

**Saída:** `-250`

## Vida Atual da Montaria (`current_mount_health`)

**Finalidade:** Retorna a vida atual da entidade que o jogador está montando.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_mount_health"}
```

**Saída:** `30.0`

## Vida Máxima da Montaria (`max_mount_health`)

**Finalidade:** Retorna a vida máxima da entidade que o jogador está montando.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"max_mount_health"}
```

**Saída:** `30.0`

## Vida Atual da Montaria (Percentual) (`current_mount_health_percent`)

**Finalidade:** Retorna a vida da montaria em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_mount_health_percent"}
```

**Saída:** `100`

## Medidor de Salto da Montaria Atual (Percentual) (`current_mount_jump_meter`)

**Finalidade:** Retorna o valor do medidor de força de salto da montaria.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_mount_jump_meter"}
```

**Saída:** `75`

## Vida Atual do Boss (Percentual) (`current_boss_health`)

**Finalidade:** Retorna a vida de um boss ativo selecionado como uma porcentagem inteira de `0` a `100`. `boss_index` começa em zero; `0` seleciona a primeira barra de boss.

**Valores:** `boss_index`

**Exemplo:**

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

**Saída:** `75`

## Nome do Boss (`boss_name`)

**Finalidade:** Retorna o nome do boss ativo.

**Valores:** `boss_index`, `as_json`

**Exemplo:**

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

**Saída:** `Ender Dragon`

## Quantidade de Bosses (`boss_count`)

**Finalidade:** Retorna o número de bosses ativos.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"boss_count"}
```

**Saída:** `1`

## Quantidade de Efeitos Ativos (`effects_count`)

**Finalidade:** Retorna o número de efeitos de poção ativos.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"effects_count"}
```

**Saída:** `3`

## Efeito Ativo (`active_effect`)

**Finalidade:** Retorna informações sobre um efeito ativo específico.

**Valores:** `effect_index`

**Exemplo:**

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

**Saída:** `minecraft:speed`

## Slot da Hotbar Selecionado (`active_hotbar_slot`)

**Finalidade:** Retorna o slot da hotbar atualmente selecionado (0-8).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"active_hotbar_slot"}
```

**Saída:** `4`

## Item do Slot (`slot_item`)

**Finalidade:** Retorna informações sobre um item em um slot específico do inventário.

**Valores:** `slot`

**Exemplo:**

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

**Saída:** `minecraft:diamond_sword`

## Quantidade de Itens no Slot (`slot_item_count`)

**Finalidade:** Retorna o tamanho da pilha do item em um slot específico do inventário do jogador.

**Valores:** `slot`

**Exemplo:**

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

**Saída:** `64`

## Durabilidade do Item no Slot (`slot_item_durability`)

**Finalidade:** Retorna informações de durabilidade do item em um slot específico do inventário do jogador.

**Valores:** `slot`, `format`

**Exemplo:**

```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parâmetros:
- `slot`: Número do slot do inventário do jogador.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` ou `percent`.

**Saída:** `87`

## Nome de Exibição do Item no Slot (`slot_item_display_name_fm`)

**Finalidade:** Retorna o nome de exibição do item em um slot específico como um componente de texto JSON. No modo espectador, slots da hotbar podem resolver nomes de itens do menu de espectador, a menos que `ignore_spectator` seja `true`.

**Valores:** `slot`, `ignore_spectator`

**Exemplo:**

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

**Saída:** `{"text":"Diamond Sword","color":"aqua"}`

## Quantidade de Itens no Inventário (`inventory_item_count`)

**Finalidade:** Retorna o número total de itens correspondentes em todo o inventário do jogador. Quando `item` está vazio, soma as quantidades de todas as slots ocupadas do inventário.

**Valores:** `item`

**Exemplo:**

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

**Saída:** `12`

## Quantidade de Recuperação de Fome do Item no Slot do Inventário (`inventory_slot_food_point_restore_amount`)

**Finalidade:** Retorna os pontos de fome restaurados pelo item de comida no slot indicado do inventário do jogador.

**Valores:** `slot`

**Exemplo:**

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

**Saída:** `4.0`

## Item do Inventário em Destaque (`hovered_inventory_item`)

**Finalidade:** Retorna a chave do item que está atualmente sob o cursor em uma tela de inventário.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"hovered_inventory_item"}
```

**Saída:** `minecraft:apple`

## Tempo do Jogo no Mundo (`game_time`)

**Finalidade:** Retorna o contador atual de ticks do tempo no jogo.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"game_time"}
```

**Saída:** `18000`

## Horário do Mundo (`world_daytime`)

**Finalidade:** Retorna o horário atual do mundo.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"world_daytime"}
```

**Saída:** `13000`

## Hora do Horário do Mundo (`world_daytime_hour`)

**Finalidade:** Retorna o componente de hora do tempo do mundo. Por padrão, isso usa o formato de 24 horas; defina `twelve_hour_format` como `"true"` para o formato de 12 horas.

**Valores:** `twelve_hour_format`

**Exemplo:**

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

**Saída:** `12`

## Minuto do Horário do Mundo (`world_daytime_minute`)

**Finalidade:** Retorna o componente de minuto do tempo do mundo (00-59).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"world_daytime_minute"}
```

**Saída:** `30`

## Dificuldade do Mundo (`world_difficulty`)

**Finalidade:** Retorna a dificuldade atual do mundo.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"world_difficulty"}
```

**Saída:** `normal`

## Seed do Mundo Atual (`current_world_seed`)

**Finalidade:** Retorna a seed do mundo singleplayer atual. Retorna um valor vazio quando a seed não está disponível.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_world_seed"}
```

**Saída:** `123456789`

## Bioma Atual (`current_biome`)

**Finalidade:** Retorna o bioma em que o jogador está atualmente. Defina `as_key` como `"false"` para retornar um nome traduzido/de exibição quando disponível.

**Valores:** `as_key`

**Exemplo:**

```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```

**Saída:** `minecraft:plains`

## Dimensão Atual (`current_dimension`)

**Finalidade:** Retorna a dimensão em que o jogador está atualmente. Defina `as_key` como `"false"` para retornar um nome traduzido/de exibição quando disponível.

**Valores:** `as_key`

**Exemplo:**

```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```

**Saída:** `minecraft:overworld`

## Valor de Gamerule (`gamerule_value`)

**Finalidade:** Retorna o valor atual de uma gamerule no mundo/servidor carregado. Mundos em servidor exigem o FancyMenu no servidor.

**Valores:** `name`

**Exemplo:**

```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```

**Saída:** `true`

## Categoria do Item (`item_category`)

**Finalidade:** Retorna a categoria da aba criativa de um item. Defina `as_key` como `"true"` para retornar a chave da categoria em vez do nome de exibição.

**Valores:** `item`, `as_key`

**Exemplo:**

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

**Saída:** `Combat`

## Título/Subtítulo Atual do HUD (`current_title`)

**Finalidade:** Retorna o texto do título exibido no momento.

**Valores:** `is_subtitle`, `as_json`

**Exemplo:**

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

**Saída:** `Game Over!`

## Mensagem da Barra de Ações (`action_bar_message_fm`)

**Finalidade:** Retorna a mensagem atual da barra de ações vanilla como um componente de texto serializado do Minecraft.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"action_bar_message_fm"}
```

**Saída:** `{"text":"You may not rest now","color":"red"}`

## Tempo da Mensagem da Barra de Ações (`action_bar_message_time_fm`)

**Finalidade:** Retorna quantos ticks ainda a mensagem atual da barra de ações vanilla será exibida.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"action_bar_message_time_fm"}
```

**Saída:** `42`

## Rotação X da Câmera (`camera_rotation_x_fm`)

**Finalidade:** Retorna o pitch atual da câmera em graus.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"camera_rotation_x_fm"}
```

**Saída:** `12.5`

## Rotação Y da Câmera (`camera_rotation_y_fm`)

**Finalidade:** Retorna o yaw atual da câmera em graus.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"camera_rotation_y_fm"}
```

**Saída:** `-90.0`

## Delta X da Rotação da Câmera (`camera_rotation_delta_x_fm`)

**Finalidade:** Retorna a variação por tick do pitch da câmera.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

**Saída:** `0.4`

## Delta Y da Rotação da Câmera (`camera_rotation_delta_y_fm`)

**Finalidade:** Retorna a variação por tick do yaw da câmera.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

**Saída:** `-1.2`

## Tempo do Item Destacado (`highlighted_item_time_fm`)

**Finalidade:** Retorna quantos ticks o nome do item destacado ainda será exibido acima da hotbar.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"highlighted_item_time_fm"}
```

**Saída:** `30`

## Progresso de Uso do Item pelo Jogador (`player_item_use_progress_fm`)

**Finalidade:** Retorna o progresso atual de uso do item de `0.0` a `1.0`.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_item_use_progress_fm"}
```

**Saída:** `0.65`

## Delta X da Posição do Jogador (`player_position_delta_x_fm`)

**Finalidade:** Retorna a variação por tick da posição do jogador no eixo X.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_position_delta_x_fm"}
```

**Saída:** `0.0`

## Delta Y da Posição do Jogador (`player_position_delta_y_fm`)

**Finalidade:** Retorna a variação por tick da posição do jogador no eixo Y.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_position_delta_y_fm"}
```

**Saída:** `-0.08`

## Delta Z da Posição do Jogador (`player_position_delta_z_fm`)

**Finalidade:** Retorna a variação por tick da posição do jogador no eixo Z.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"player_position_delta_z_fm"}
```

**Saída:** `0.12`

## IP Atual do Servidor (`current_server_ip`)

**Finalidade:** Retorna o IP do servidor conectado.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"current_server_ip"}
```

**Saída:** `mc.hypixel.net`

## Lista de Jogadores do Mundo (`world_players_list`)

**Finalidade:** Retorna uma lista de todos os jogadores atualmente no mundo.

**Valores:** `separator`

**Exemplo:**

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

**Saída:** `Steve, Alex, Notch`

## MOTD do Servidor (`servermotd`)

**Finalidade:** Retorna a Message of the Day de um servidor.

**Valores:** `ip`, `line`

**Exemplo:**

```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```

**Saída:** `Welcome to Hypixel!`

## PING do Servidor (`serverping`)

**Finalidade:** Retorna o ping para um servidor em milissegundos.

**Valores:** `ip`

**Exemplo:**

```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```

**Saída:** `54`

## Contagem de Jogadores do Servidor (`serverplayercount`)

**Finalidade:** Retorna a quantidade de jogadores de um servidor.

**Valores:** `ip`

**Exemplo:**

```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```

**Saída:** `25000/30000`

## Status do Servidor (`serverstatus`)

**Finalidade:** Retorna o status online/offline de um servidor.

**Valores:** `ip`

**Exemplo:**

```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```

**Saída:** `§aOnline` ou `§cOffline`

## Versão do Servidor (`serverversion`)

**Finalidade:** Retorna a versão do Minecraft de um servidor.

**Valores:** `ip`

**Exemplo:**

```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```

**Saída:** `1.21.1`

> [!NOTE]
> Os placeholders de tempo em tempo real abaixo aceitam um valor `timezone`. Use um ID de fuso horário Java, como `UTC`, `Europe/Berlin` ou `America/New_York`; omita-o ou use `system` para usar o fuso horário do sistema. `unix_time` sempre retorna o timestamp Unix e não possui valor `timezone`.

## Ano (`realtimeyear`)

**Finalidade:** Retorna o ano atual.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"realtimeyear"}
```

**Saída:** `2024`

## Mês (`realtimemonth`)

**Finalidade:** Retorna o mês atual (01-12).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"realtimemonth"}
```

**Saída:** `01`

## Dia (`realtimeday`)

**Finalidade:** Retorna o dia atual do mês (01-31).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"realtimeday"}
```

**Saída:** `27`

## Hora (`realtimehour`)

**Finalidade:** Retorna a hora atual. Por padrão, isso usa o formato de 24 horas; defina `twelve_hour_format` como `"true"` para o formato de 12 horas.

**Valores:** `twelve_hour_format`, `timezone`

**Exemplo:**

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```

**Saída:** `14`

## Minuto (`realtimeminute`)

**Finalidade:** Retorna o minuto atual (00-59).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"realtimeminute"}
```

**Saída:** `30`

## Segundo (`realtimesecond`)

**Finalidade:** Retorna o segundo atual (00-59).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"realtimesecond"}
```

**Saída:** `45`

## Tempo Atual em Milissegundos (Timestamp Unix) (`unix_time`)

**Finalidade:** Retorna o timestamp Unix atual em milissegundos.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"unix_time"}
```

**Saída:** `1716552478123`

## Informações da CPU (`cpuinfo`)

**Finalidade:** Retorna informações sobre a CPU.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"cpuinfo"}
```

**Saída:** `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Uso da CPU (JVM) (`jvmcpu`)

**Finalidade:** Retorna o uso de CPU da JVM em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"jvmcpu"}
```

**Saída:** `25.5`

## Uso da CPU (SO) (`oscpu`)

**Finalidade:** Retorna o uso de CPU do sistema operacional em porcentagem.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"oscpu"}
```

**Saída:** `42.8`

## Informações da GPU (`gpuinfo`)

**Finalidade:** Retorna o nome informado para o dispositivo de renderização ativo do Minecraft. Isso não garante a identificação de uma GPU física específica.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"gpuinfo"}
```

**Saída:** `NVIDIA GeForce RTX 3080`

## Versão do Java (`javaver`)

**Finalidade:** Retorna a versão do Java.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"javaver"}
```

**Saída:** `17.0.2`

## Máquina Virtual Java (`jvmname`)

**Finalidade:** Retorna o nome da Java Virtual Machine.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"jvmname"}
```

**Saída:** `OpenJDK 64-Bit Server VM`

## Versão do OpenGL (`glver`)

**Finalidade:** Retorna informações do driver do dispositivo de renderização ativo do Minecraft. Apesar do nome legada `glver`, o valor não é garantido ser apenas uma string de versão do OpenGL.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"glver"}
```

**Saída:** `4.6.0 NVIDIA 516.94`

## Nome do Sistema Operacional (`osname`)

**Finalidade:** Retorna o nome do sistema operacional.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"osname"}
```

**Saída:** `Windows 10`

## FPS (Quadros Por Segundo) (`fps`)

**Finalidade:** Retorna o número atual de quadros por segundo.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"fps"}
```

**Saída:** `120`

## RAM Usada em MB (`usedram`)

**Finalidade:** Retorna a quantidade de RAM atualmente em uso (MB).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"usedram"}
```

**Saída:** `4096`

## RAM Máxima em MB (`maxram`)

**Finalidade:** Retorna a RAM máxima alocada (MB).

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"maxram"}
```

**Saída:** `8192`

## RAM Usada em %% (`percentram`)

**Finalidade:** Retorna a porcentagem de RAM atualmente em uso.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"percentram"}
```

**Saída:** `50`

## Volume do Elemento de Áudio (`audio_element_vol`)

**Finalidade:** Retorna o volume de um elemento de áudio.

**Valores:** `element_identifier`

**Exemplo:**

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```

**Saída:** `0.5`

## Faixa de Áudio Atual (`audio_element_current_track`)

**Finalidade:** Retorna o nome da faixa de um elemento de áudio.

**Valores:** `element_identifier`, `display_name_mappings`

**Exemplo:**

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Menu Theme%:%track2.ogg=>Credits Theme"}}
```

Em `display_name_mappings`, `=>` separa o nome do arquivo do seu nome de exibição e `%:%` separa os mapeamentos.

**Saída:** `Menu Theme`

## Duração do Áudio (`audio_duration`)

**Finalidade:** Retorna a duração da faixa carregada atual do [elemento de áudio](./elements#audio) no formato `MM:SS`. A faixa pode estar tocando, pausada ou parada.

**Valores:** `element_identifier`

**Exemplo:**

```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```

**Saída:** `03:45`

## Tempo de Reprodução do Áudio (`audio_playtime`)

**Finalidade:** Retorna o tempo de reprodução atual de uma faixa de áudio. Defina `show_percentage` como `"true"` para obter um valor de progresso de 0 a 100 em vez de `MM:SS`.

**Valores:** `element_identifier`, `show_percentage`

**Exemplo:**

```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```

**Saída:** `01:30` (ou `45` quando `show_percentage` é `"true"`)

**Resultado indisponível:** `00:00`, ou `0` no modo de porcentagem. O valor atual fica disponível enquanto a faixa está tocando ou pausada; faixas paradas, ausentes ou não prontas usam o resultado indisponível.

## Estado de Reprodução do Áudio (`audio_playing_state`)

**Finalidade:** Retorna se um elemento de áudio está tocando (true/false).

**Valores:** `element_identifier`

**Exemplo:**

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```

**Saída:** `true`

## Volume do Elemento de Vídeo (`video_element_vol`)

**Finalidade:** Retorna o nível de volume de um elemento de vídeo (0.0 a 1.0).

**Valores:** `element_identifier`

**Exemplo:**

```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```

**Saída:** `0.5`

## Duração do Elemento de Vídeo (`video_element_duration`)

**Finalidade:** Retorna a duração total de um elemento de vídeo no formato `MM:SS`. Defina `output_as_timestamp` como `"true"` para retornar um timestamp em milissegundos.

**Valores:** `element_identifier`, `output_as_timestamp`

**Exemplo:**

```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```

**Saída:** `02:00` (ou `120000` quando `output_as_timestamp` é `"true"`)

## Tempo de Reprodução do Elemento de Vídeo (`video_element_playtime`)

**Finalidade:** Retorna o tempo atual de reprodução (progresso) de um elemento de vídeo no formato `MM:SS`. Defina `show_percentage` como `"true"` para um valor de progresso de 0 a 100, ou `output_as_timestamp` como `"true"` para milissegundos.

**Valores:** `element_identifier`, `show_percentage`, `output_as_timestamp`

**Exemplo:**

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```

**Saída:** `00:45` (ou `38` em porcentagem, ou `45200` como timestamp)

## Estado Pausado do Elemento de Vídeo (`video_element_paused_state`)

**Finalidade:** Retorna se um elemento de vídeo está pausado (true/false).

**Valores:** `element_identifier`

**Exemplo:**

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```

**Saída:** `false`

## Volume do Fundo de Vídeo (`video_background_vol`)

**Finalidade:** Retorna o nível de volume de um fundo de vídeo do menu (0.0 a 1.0).

**Valores:** `background_identifier`

**Exemplo:**

```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```

**Saída:** `0.7`

## Duração do Fundo de Vídeo (`video_background_duration`)

**Finalidade:** Retorna a duração total de um fundo de vídeo do menu no formato `MM:SS`. Defina `output_as_timestamp` como `"true"` para retornar um timestamp em milissegundos.

**Valores:** `background_identifier`, `output_as_timestamp`

**Exemplo:**

```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```

**Saída:** `03:00` (ou `180000` quando `output_as_timestamp` é `"true"`)

## Tempo de Reprodução do Fundo de Vídeo (`video_background_playtime`)

**Finalidade:** Retorna o tempo atual de reprodução (progresso) de um fundo de vídeo do menu no formato `MM:SS`. Defina `show_percentage` como `"true"` para um valor de progresso de 0 a 100, ou `output_as_timestamp` como `"true"` para milissegundos.

**Valores:** `background_identifier`, `show_percentage`, `output_as_timestamp`

**Exemplo:**

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```

**Saída:** `01:00` (ou `33` em porcentagem, ou `60500` como timestamp)

## Estado Pausado do Fundo de Vídeo (`video_background_paused_state`)

**Finalidade:** Retorna se um fundo de vídeo do menu está pausado (true/false).

**Valores:** `background_identifier`

**Exemplo:**

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```

**Saída:** `true`

## Calculadora (`calc`)

**Finalidade:** O placeholder de calculadora é uma ferramenta poderosa que permite fazer cálculos matemáticos dentro dos seus layouts. Ele suporta uma ampla variedade de operações matemáticas e pode funcionar tanto com números decimais quanto inteiros.

**Valores:** `decimal`, `expression`

### Sintaxe Básica

**Exemplo:**

```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"your_expression"}}
```

A calculadora tem dois parâmetros principais:
- `decimal`: Determina se o resultado deve incluir casas decimais (`true`) ou ser arredondado para inteiros (`false`)
- `expression`: A expressão matemática a ser avaliada

### Operações Suportadas
A calculadora suporta estas operações matemáticas:
- Aritmética básica: `+` (adição), `-` (subtração), `*` (multiplicação), `/` (divisão)
- Parênteses: `( )` para agrupar operações
- Potência: `^` para expoentes
- Raiz quadrada: `sqrt()`
- Funções trigonométricas: `sin()`, `cos()`, `tan()`
- Constantes matemáticas: `pi`, `e`
- Valor absoluto: `abs()`
- Logaritmos: `log()`, `ln()`

## Número Aleatório (`random_number`)

**Finalidade:** Gera um número aleatório dentro de um intervalo especificado.

**Valores:** `min`, `max`

**Exemplo:**

```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```

**Saída:** `42`

## Número Máximo (`maxnum`)

**Finalidade:** Retorna o maior de dois números.

**Valores:** `first`, `second`

**Exemplo:**

```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```

**Saída:** `20`

## Número Mínimo (`minnum`)

**Finalidade:** Retorna o menor de dois números.

**Valores:** `first`, `second`

**Exemplo:**

```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```

**Saída:** `10`

## Número Absoluto (`absnum`)

**Finalidade:** Retorna o valor absoluto de um número.

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

**Saída:** `10.5`

## Tornar Número Negativo (`negnum`)

**Finalidade:** Converte um número positivo em negativo. Zero e valores já negativos são retornados sem alteração.

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

**Saída:** `-10.5`

## *pi* (Matemática) (`math_pi`)

**Finalidade:** Retorna o valor de π.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"math_pi"}
```

**Saída:** `3.141592653589793`

## Seno Trigonométrico (Matemática) (`math_sin`)

**Finalidade:** Retorna o seno de um ângulo em radianos. Converta valores em graus para radianos primeiro.

**Valores:** `angle`

**Exemplo:**

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

**Saída:** `1.0`

## Cosseno Trigonométrico (Matemática) (`math_cos`)

**Finalidade:** Retorna o cosseno de um ângulo em radianos. Converta valores em graus para radianos primeiro.

**Valores:** `angle`

**Exemplo:**

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

**Saída:** `1.0`

## Tangente Trigonométrica (Matemática) (`math_tan`)

**Finalidade:** Retorna a tangente de um ângulo em radianos. Converta valores em graus para radianos primeiro.

**Valores:** `angle`

**Exemplo:**

```
{"placeholder":"math_tan","values":{"angle":"0"}}
```

**Saída:** `0.0`

## Piso (Matemática) (`math_floor`)

**Finalidade:** Retorna o piso matemático de um número, formatado com sufixo decimal `.0`.

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```

**Saída:** `3.0`

## Teto (Matemática) (`math_ceil`)

**Finalidade:** Retorna o teto matemático de um número, formatado com sufixo decimal `.0`.

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```

**Saída:** `4.0`

Use [**Round**](#round-math-math_round) ou [**Calculator**](#calculator-calc) com saída decimal desativada quando precisar de texto inteiro sem `.0`.

## Arredondar (Matemática) (`math_round`)

**Finalidade:** Arredonda um número. Por padrão, ele arredonda para o inteiro mais próximo; defina `decimals` como um número não negativo para arredondar para essa quantidade de casas decimais.

**Valores:** `num`, `decimals`

**Exemplo:**

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

**Saída:** `3.14` (com `decimals:-1` ou omitido → `3`)

## Sinal (Matemática) (`math_sign`)

**Finalidade:** Retorna o sinal de um número (1 para positivo, -1 para negativo, 0 para zero).

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

**Saída:** `-1`

## Seno Hiperbólico (Matemática) (`math_sinh`)

**Finalidade:** Retorna o seno hiperbólico de um número.

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

**Saída:** `1.1752011936438014`

## Cosseno Hiperbólico (Matemática) (`math_cosh`)

**Finalidade:** Retorna o cosseno hiperbólico de um número.

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

**Saída:** `1.5430806348152437`

## Tangente Hiperbólica (Matemática) (`math_tanh`)

**Finalidade:** Retorna a tangente hiperbólica de um número.

**Valores:** `num`

**Exemplo:**

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

**Saída:** `0.7615941559557649`

## Dividir Texto (`split_text`)

**Finalidade:** Divide um texto usando um delimitador especificado.

**Valores:** `input`, `regex`, `max_parts`, `split_index`

**Exemplo:**

```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```

**Saída:** `world`

## Aparar Texto (`trim_text`)

**Finalidade:** Remove espaços em branco no início e no fim.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```

**Saída:** `hello world`

## Cortar Texto (`crop_text`)

**Finalidade:** Remove caracteres do início e do fim do texto.

**Valores:** `text`, `remove_from_start`, `remove_from_end`

**Exemplo:**

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

**Saída:** `ello worl`

## Stringify (`stringify`)

**Finalidade:** Converte um texto em string escapando todos os caracteres de sintaxe.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```

**Saída:** `text with \{special\} \"characters\"`

## Localizar Texto (`local`)

**Finalidade:** Recupera texto localizado para uma chave.

**Valores:** `key`

**Exemplo:**

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

**Saída:** `Singleplayer`

## Texto da Web (`webtext`)

**Finalidade:** Recupera o conteúdo textual de uma URL.

**Valores:** `link`

**Exemplo:**

```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```

**Saída:** `Welcome to the server!`

## Texto Aleatório (`randomtext`)

**Finalidade:** Retorna uma linha aleatória de um arquivo de texto, URL ou texto simples direto. O texto muda em intervalos especificados. O conteúdo de arquivos e URLs é atualizado aproximadamente a cada 30 segundos; conteúdo de texto simples direto permanece em cache porque não precisa ser recarregado.

**Valores:** `source`, `interval`

Nos valores dos placeholders, `/config/...` significa `<game-directory>/config/...`; não é um caminho na raiz do sistema de arquivos. Veja [Resources](./resources#local-resources).

**Exemplo:**

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parâmetros:
- `source`: A origem das linhas de texto (substitui o antigo parâmetro `path`)
  - Caminho de arquivo: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Texto simples: `Line 1\nLine 2\nLine 3`
- `interval`: Tempo em segundos entre as mudanças de texto

O placeholder agora suporta três tipos de origem:
1. **Arquivos locais**: Arquivos de texto da pasta do seu jogo
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: Arquivos de texto remotos da internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texto simples**: Entrada de texto direta com linhas separadas por `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"First line\nSecond line\nThird line","interval":"5"}}
   ```

Observação: Placeholders antigos que usam `path` em vez de `source` continuarão funcionando.

## Parser de JSON (`json`)

**Finalidade:** Analisa dados JSON de um arquivo, URL ou conteúdo JSON direto e extrai valores usando expressões de caminho JSON.

**Valores:** `source`, `json_path`

**Exemplo:**

```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parâmetros:
- `source`: A origem dos dados JSON
  - Caminho de arquivo: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - JSON direto: `{"name":"Steve","level":42}`
- `json_path`: A expressão de caminho JSON para extrair dados

O placeholder agora suporta três tipos de origem:
1. **Arquivos locais**: Arquivos JSON da pasta do seu jogo
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: Dados JSON remotos de APIs ou serviços web
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON direto**: Conteúdo JSON embutido
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Exemplos de caminhos JSON:
- `$.name` - Obtém o campo "name" da raiz
- `$.player.level` - Obtém o campo aninhado "level" dentro de "player"
- `$.items[0].id` - Obtém o "id" do primeiro item em um array
- `$.scores.*` - Obtém todos os valores do objeto "scores"

## Caminho Absoluto de Arquivo/Pasta (`absolute_path`)

**Finalidade:** Retorna o caminho absoluto de um arquivo.

**Valores:** `short_path`

**Exemplo:**

```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```

**Saída:** `C:/Games/PrismLauncher/instances/My Pack/relative/path/to/file.txt`

## Contagem de Caracteres do Texto (`text_character_count`)

**Finalidade:** Retorna o número de caracteres no texto fornecido.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```

**Saída:** `12`

## Largura do Texto (`text_width`)

**Finalidade:** Retorna a largura em pixels do texto fornecido quando renderizado.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

**Saída:** `66`

## Texto em Maiúsculas (`uppercase_text`)

**Finalidade:** Converte o texto de entrada para letras maiúsculas.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

**Saída:** `HELLO WORLD`

## Texto em Minúsculas (`lowercase_text`)

**Finalidade:** Converte o texto de entrada para letras minúsculas.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```

**Saída:** `hello world`

## Texto em Title Case (`title_case_text`)

**Finalidade:** Converte o texto de entrada para title case.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

**Saída:** `Hello World`

## Texto em Case de Frase (`sentence_case_text`)

**Finalidade:** Converte o texto de entrada para case de frase.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

**Saída:** `Hello world. This is fancymenu!`

## Texto em Snake Case (`snake_case_text`)

**Finalidade:** Converte o texto de entrada para `snake_case`.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

**Saída:** `hello_world`

## Texto em Kebab Case (`kebab_case_text`)

**Finalidade:** Converte o texto de entrada para `kebab-case`.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

**Saída:** `hello-world`

## Texto em Case Alternado (`alternating_case_text`)

**Finalidade:** Converte o texto de entrada para case alternado.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

**Saída:** `aLtErNaTiNg CaSe`

## Alternar Case do Texto (`toggle_case_text`)

**Finalidade:** Alterna o case de cada letra no texto de entrada.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

**Saída:** `tOGGLE cASE`

## Codificar para Base64 (`base64_encode`)

**Finalidade:** Codifica o texto fornecido em Base64.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

**Saída:** `SGVsbG8gV29ybGQ=`

## Decodificar de Base64 (`base64_decode`)

**Finalidade:** Decodifica uma string Base64 de volta para texto simples.

**Valores:** `text`

**Exemplo:**

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

**Saída:** `Hello World`

## Texto do Arquivo (`file_text`)

**Finalidade:** Retorna linhas de texto de um arquivo ou URL. Pode retornar todas as linhas ou apenas as últimas X linhas.

**Valores:** `path_or_url`, `mode`, `separator`, `last_lines`

**Exemplo:**

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parâmetros:
- `path_or_url`: Caminho do arquivo ou URL de onde ler
- `mode`: Pode ser `"all"` (retorna todas as linhas) ou `"last"` (retorna apenas as últimas X linhas)
- `separator`: Texto usado entre as linhas (padrão: `"\n"`)
- `last_lines`: Número de linhas a retornar quando o modo é `"last"` (padrão: `"1"`)

**Saída:**

```text
First line
Second line
```

## Conteúdo da Área de Transferência (`clipboard_content`)

**Finalidade:** Retorna o conteúdo de texto atualmente armazenado na área de transferência do sistema.

**Valores:** Nenhum

**Exemplo:**

```
{"placeholder":"clipboard_content"}
```

**Saída:** `Hello from the clipboard`

## Substituir Texto (`replace_text`)

**Finalidade:** Substitui texto em uma string usando texto literal ou expressões regulares.

**Valores:** `text`, `search`, `replacement`, `use_regex`, `replace_all`

**Exemplo:**

```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parâmetros:
- `text`: O texto de entrada a ser processado
- `search`: O texto ou padrão regex a ser procurado
- `replacement`: O texto de substituição
- `use_regex`: Se deve usar regex (`"true"`) ou correspondência literal (`"false"`)
- `replace_all`: Substituir todas as ocorrências (`"true"`) ou apenas a primeira (`"false"`)

**Saída:** `Hello FancyMenu! This is a test.`

## Estrutura de Escolha (`switch_case`)

**Finalidade:** Executa uma operação switch-case com base em um valor.

**Valores:** `value`, `cases`, `default`

**Exemplo:**

```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```

**Saída:** `first case` (se o valor for 1)

## Obter Valor de Variável (Variável FM) (`getvariable`)

**Finalidade:** Recupera o valor de uma variável armazenada anteriormente.

**Valores:** `name`

**Exemplo:**

```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```

**Saída:** `42`

## Obter Dados NBT (`nbt_data_get`)

**Finalidade:** Recupera dados NBT no cliente (semelhante ao comando `/data get`). Use a variante do servidor `nbt_data_get_server` quando estiver conectado a um servidor e precisar de valores autoritativos do lado do servidor.

**Valores:** `source_type`, `entity_selector`, `nbt_path`, `scale`, `return_type`

**Exemplo:**

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parâmetros:
- `source_type`: Pode ser `"entity"` ou `"block"`
- `entity_selector`: Seletor de entidade como `@s`, `@p`, `@e` ou UUID/nome (para entidades)
- `block_pos`: Posição do bloco no formato `"x y z"` (para blocos)
- `nbt_path`: O caminho NBT a ser recuperado
- `scale`: Fator de escala opcional para valores numéricos (padrão: `"1.0"`)
- `return_type`: Como retornar os dados:
  - `"value"`: Padrão, retorna o valor (com escala opcional para números)
  - `"string"`: Retorna os dados NBT reais como string
  - `"snbt"`: Retorna como SNBT (NBT formatado)
  - `"json"`: Retorna como componente formatado em JSON (para tags compostas)

**Saída:** `20` (para nível de fome)

## Obter Dados NBT (Lado do Servidor) (`nbt_data_get_server`)

**Finalidade:** Consulta dados NBT no lado do servidor (usando um pacote) e armazena os resultados em cache por um curto período. Os valores são equivalentes ao placeholder do lado do cliente.

**Valores:** `source_type`, `entity_selector`, `block_pos`, `storage_id`, `nbt_path`, `scale`, `return_type`

**Exemplo:**

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```

**Saída:** `minecraft:diamond_sword`

## Última Mensagem de Morte (`lastdeathmessage`)

**Finalidade:** Retorna a última mensagem de morte registrada do jogador cliente. Defina `as_json_component` como `"true"` para obter o componente de texto JSON bruto.

**Valores:** `as_json_component`

**Exemplo:**

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

**Saída:** `Steve was slain by Zombie`

## Duração de Uptime (`uptime_duration`)

**Finalidade:** Retorna há quanto tempo o FancyMenu foi carregado. Por padrão, o valor está em segundos; defina `output_as_millis` como `"true"` para receber milissegundos.

**Valores:** `output_as_millis`

**Exemplo:**

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

**Saída:** `742` (segundos desde o carregamento)

## Nomes de Salvamentos do Mundo (`level_save_names`)

**Finalidade:** Lista todos os nomes de salvamentos de mundos locais unidos pelo separador escolhido. Executa na thread do cliente.

**Valores:** `separator`

**Exemplo:**

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

**Saída:** `Creative Test, Survival World, Hardcore`

## Dados de Salvamento do Mundo (`level_save_data`)

**Finalidade:** Retorna dados serializados do nível para o nome do mundo fornecido (deve corresponder ao nome exibido na lista de mundos salvos).

**Valores:** `level_name`

**Exemplo:**

```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```

**Saída:** `{"name":"Survival World","gameMode":"survival",...}`

## Conversor de Base Numérica (`number_base_convert`)

**Finalidade:** Converte um número (inteiro ou fracionário) de uma base para outra (2–36). Usa decimal por padrão se as bases não forem informadas.

**Valores:** `input`, `from_base`, `to_base`

**Exemplo:**

```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```

**Saída:** `43.8`

## Tamanho do Arquivo (`file_size`)

**Finalidade:** Retorna o tamanho de um arquivo local em bytes. Apenas caminhos locais são permitidos.

**Valores:** `path`

**Exemplo:**

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Saída:** `1284`

## MD5 do Arquivo (`file_md5`)

**Finalidade:** Retorna o hash MD5 de um arquivo local como uma string hexadecimal em letras minúsculas.

**Valores:** `path`

**Exemplo:**

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```

**Saída:** `d41d8cd98f00b204e9800998ecf8427e`

# Exemplos Práticos

## Criando uma Exibição Dinâmica de Memória
```
RAM usada: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Criando um Relógio em Tempo Real
```
{"placeholder":"realtimehour","values":{"timezone":"system"}}:{"placeholder":"realtimeminute","values":{"timezone":"system"}}:{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

## Criando uma Exibição de Informações do Sistema
```
SO: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD de Status do Jogador
```
Vida: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armadura: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Nível de XP: {"placeholder":"current_player_level"}
```

## Cálculo Complexo com Placeholders Aninhados
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Exibição de Coordenadas com Arredondamento
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Boas Práticas

1. **Faça Cache de Operações Caras**: Alguns placeholders (como os que leem informações do sistema) podem exigir bastante recursos. Considere usar variáveis para armazenar seus valores se precisar usá-los várias vezes.

2. **Use Configurações de Decimal Adequadas**: Ao trabalhar com cálculos, use o parâmetro `decimal` de forma apropriada. Defina como `false` quando precisar de inteiros e como `true` quando precisar de valores decimais precisos.

3. **Trate Valores Ausentes**: Sempre considere o que deve acontecer se um placeholder não retornar valor. Talvez seja útil fornecer valores padrão nesses casos.

4. **Teste o Desempenho**: Ao usar muitos placeholders ou estruturas aninhadas complexas, teste o impacto no desempenho, especialmente em sistemas mais simples.

5. **Use Dimensionamento/Posicionamento Avançado**: Para elementos de interface dinâmicos, combine placeholders com dimensionamento e posicionamento avançados para criar layouts responsivos.

6. **Combine com Variáveis**: Use placeholders junto com variáveis para conteúdo ainda mais dinâmico que possa ser atualizado por meio de ações.

# Problemas Comuns e Soluções

## Placeholder Não Está Atualizando
Se o valor de um placeholder não estiver sendo atualizado como esperado, verifique:
- Se o placeholder está formatado corretamente
- Se você está usando a capitalização correta para os IDs dos placeholders
- Se o placeholder requer condições específicas para atualizar

## Placeholders Aninhados Não Funcionam
Ao aninhar placeholders:
- Certifique-se de que as aspas estejam escapadas corretamente
- Verifique se cada placeholder aninhado é válido por conta própria

## Problemas de Desempenho
Se você notar problemas de desempenho:
- Reduza a quantidade de placeholders usados
- Evite aninhamento desnecessário
- Considere usar variáveis para valores acessados com frequência
- Use o placeholder apropriado para sua necessidade (por exemplo, não use placeholders em tempo real quando valores estáticos forem suficientes)
