---
title: Placeholders
description: Como usar placeholders.
---

# Placeholders

Placeholders são valores dinâmicos que são substituídos por conteúdo real quando são usados. No FancyMenu, os placeholders permitem inserir conteúdo dinâmico em vários elementos, como textos, botões e requisitos de carregamento. Pense neles como variáveis que são avaliadas e substituídas pelos seus valores reais quando seus layouts são exibidos.

# Informações gerais

## Sintaxe básica
Placeholders no FancyMenu usam uma sintaxe parecida com JSON:
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

Por exemplo, para exibir o nome do jogador:
```
{"placeholder":"playername"}
```

## Aninhamento de placeholders
Um dos recursos mais poderosos do sistema de placeholders do FancyMenu é a capacidade de aninhar placeholders dentro de outros placeholders. Isso significa que você pode usar a saída de um placeholder como entrada de outro.

Exemplo de placeholders aninhados:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Este exemplo pega o valor máximo de RAM e divide por 1024 para converter de MB para GB.

# Usando placeholders

A maioria dos elementos que possuem campos de texto suporta placeholders. Você pode ver se um campo de texto suporta placeholders ao editá-lo. Se o **editor de texto** em tela cheia abrir ao editar o texto, ele suporta placeholders. 

Para encontrar uma **lista de todos os placeholders**, basta clicar no botão **Placeholders** no **canto superior direito** do **editor de texto**.

Há uma **barra de pesquisa** no topo da lista de placeholders que permite procurar placeholders.

Clicar em um placeholder na lista irá colá-lo no conteúdo do texto.

# Placeholders em detalhes

Esta lista contém a maioria, senão todos, os placeholders disponíveis no FancyMenu. A lista pode ficar um pouco desatualizada devido às atualizações do mod.

## Nome do jogador (playername)
Retorna o nome de usuário do jogador atual.
```
{"placeholder":"playername"}
```
Exemplo de saída: `Steve`

## UUID do jogador (playeruuid)
Retorna o identificador único do jogador.
```
{"placeholder":"playeruuid"}
```
Exemplo de saída: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Versão do Minecraft (mcversion)
Retorna a versão atual do Minecraft.
```
{"placeholder":"mcversion"}
```
Exemplo de saída: `1.19.2`

## Versão do carregador de mods (loaderver)
Retorna a versão do carregador de mods (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Exemplo de saída: `43.2.0`

## Nome do carregador de mods (loadername)
Retorna o nome do carregador de mods.
```
{"placeholder":"loadername"}
```
Exemplo de saída: `Forge`

## Versão do mod (modversion)
Retorna a versão de um mod específico.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Exemplo de saída: `2.14.9`

## Total de mods (totalmods)
Retorna o número total de mods instalados.
```
{"placeholder":"totalmods"}
```
Exemplo de saída: `45`

## Quantidade de mods ativos (loadedmods)
Retorna o número de mods carregados no momento.
```
{"placeholder":"loadedmods"}
```
Exemplo de saída: `43`

## Progresso de carregamento do mundo (world_load_progress)
Retorna o progresso atual de carregamento do mundo em porcentagem.
```
{"placeholder":"world_load_progress"}
```
Exemplo de saída: `75`

## Valor de opção do Minecraft (minecraft_option_value)
Retorna o valor de uma opção do Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Exemplo de saída: `70`

## Último mundo ou servidor (last_world_server)
Retorna informações sobre o último mundo ou servidor acessado.
```
{"placeholder":"last_world_server","values":{"type":"both","full_world_path":"true"}}
```
Parâmetros:
- `type`: Determina que tipo de informação retornar
  - `"both"`: Retorna o último mundo ou servidor acessado (padrão)
  - `"server"`: Retorna apenas se o último acesso foi a um servidor
  - `"world"`: Retorna apenas se o último acesso foi a um mundo
- `full_world_path`: Controla como os caminhos do mundo são exibidos
  - `"true"`: Retorna o caminho completo do mundo (padrão)
  - `"false"`: Retorna apenas o nome do mundo, sem o caminho (não afeta servidores)

Exemplos:
- Servidor: `mc.hypixel.net`
- Mundo com caminho completo: `saves/New World`
- Mundo sem caminho completo: `New World`

## Largura da tela (guiwidth)
Retorna a largura atual da tela.
```
{"placeholder":"guiwidth"}
```
Exemplo de saída: `1920`

## Altura da tela (guiheight)
Retorna a altura atual da tela.
```
{"placeholder":"guiheight"}
```
Exemplo de saída: `1080`

## Identificador da tela atual (screenid)
Retorna o identificador da tela atual.
```
{"placeholder":"screenid"}
```
Exemplo de saída: `title_screen`

## Largura do elemento (elementwidth)
Retorna a largura de um elemento específico.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Exemplo de saída: `200`

## Altura do elemento (elementheight)
Retorna a altura de um elemento específico.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Exemplo de saída: `20`

## Posição X do elemento (elementposx)
Retorna a posição X de um elemento específico.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Exemplo de saída: `150`

## Posição Y do elemento (elementposy)
Retorna a posição Y de um elemento específico.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Exemplo de saída: `100`

## Posição X do mouse (mouseposx)
Retorna a posição X atual do mouse.
```
{"placeholder":"mouseposx"}
```
Exemplo de saída: `960`

## Posição Y do mouse (mouseposy)
Retorna a posição Y atual do mouse.
```
{"placeholder":"mouseposy"}
```
Exemplo de saída: `540`

## Cliques por segundo (clicks_per_second)
Retorna os cliques por segundo atuais de um botão do mouse.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parâmetros:
- `mouse_button`: `left` ou `right`

Exemplo de saída: `8`

## Escala da GUI (guiscale)
Retorna a escala atual da GUI.
```
{"placeholder":"guiscale"}
```
Exemplo de saída: `2`

## Rótulo/texto de widget vanilla (vanillabuttonlabel)
Retorna o rótulo/texto de um widget/botão vanilla.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Exemplo de saída: `Options...`

## Valor de campo de entrada de texto (text_input_field_value)
Retorna o valor atual de um campo de entrada de texto customizado ou vanilla pelo identificador do elemento.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Exemplo de saída: `Hello World`

## Vida atual do jogador (current_player_health)
Retorna os pontos de vida atuais do jogador.
```
{"placeholder":"current_player_health"}
```
Exemplo de saída: `20.0`

## Vida máxima do jogador (max_player_health)
Retorna os pontos máximos de vida do jogador.
```
{"placeholder":"max_player_health"}
```
Exemplo de saída: `20.0`

## Vida atual do jogador (Percentual) (current_player_health_percent)
Retorna a vida do jogador em porcentagem.
```
{"placeholder":"current_player_health_percent"}
```
Exemplo de saída: `100`

## Absorção atual do jogador (current_player_absorption_health)
Retorna os pontos de absorção do jogador (corações dourados).
```
{"placeholder":"current_player_absorption_health"}
```
Exemplo de saída: `4.0`

## Absorção máxima do jogador (max_player_absorption_health)
Retorna a absorção máxima de vida.
```
{"placeholder":"max_player_absorption_health"}
```
Exemplo de saída: `4.0`

## Absorção atual do jogador (Percentual) (current_player_absorption_health_percent)
Retorna a absorção de vida do jogador em porcentagem.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Exemplo de saída: `100`

## Fome atual do jogador (current_player_hunger)
Retorna o nível atual de fome do jogador.
```
{"placeholder":"current_player_hunger"}
```
Exemplo de saída: `20`

## Fome máxima do jogador (max_player_hunger)
Retorna o nível máximo de fome.
```
{"placeholder":"max_player_hunger"}
```
Exemplo de saída: `20`

## Fome atual do jogador (Percentual) (current_player_hunger_percent)
Retorna a fome do jogador em porcentagem.
```
{"placeholder":"current_player_hunger_percent"}
```
Exemplo de saída: `100`

## Saturação de fome atual do jogador (current_player_hunger_saturation)
Retorna o valor atual de saturação de fome do jogador.
```
{"placeholder":"current_player_hunger_saturation"}
```
Exemplo de saída: `5.0`

## Armadura atual do jogador (current_player_armor)
Retorna o valor atual de armadura do jogador.
```
{"placeholder":"current_player_armor"}
```
Exemplo de saída: `20`

## Resistência da armadura do jogador (player_armor_toughness)
Retorna o valor total de resistência da armadura do jogador.
```
{"placeholder":"player_armor_toughness"}
```
Exemplo de saída: `8.0`

## Armadura máxima do jogador (max_player_armor)
Retorna o valor máximo de armadura.
```
{"placeholder":"max_player_armor"}
```
Exemplo de saída: `20`

## Armadura atual do jogador (Percentual) (current_player_armor_percent)
Retorna a armadura do jogador em porcentagem.
```
{"placeholder":"current_player_armor_percent"}
```
Exemplo de saída: `100`

## Nível de oxigênio atual do jogador (current_player_oxygen)
Retorna o nível atual de oxigênio do jogador (bolhas de ar).
```
{"placeholder":"current_player_oxygen"}
```
Exemplo de saída: `300`

## Nível máximo de oxigênio do jogador (max_player_oxygen)
Retorna o nível máximo de oxigênio.
```
{"placeholder":"max_player_oxygen"}
```
Exemplo de saída: `300`

## Nível de oxigênio atual do jogador (Percentual) (current_player_oxygen_percent)
Retorna o nível de oxigênio do jogador em porcentagem.
```
{"placeholder":"current_player_oxygen_percent"}
```
Exemplo de saída: `100`

## Nível atual do jogador (current_player_level)
Retorna o nível de experiência atual do jogador.
```
{"placeholder":"current_player_level"}
```
Exemplo de saída: `30`

## Experiência atual do jogador (current_player_exp)
Retorna o total de pontos de experiência do jogador.
```
{"placeholder":"current_player_exp"}
```
Exemplo de saída: `1250`

## Progresso de experiência do jogador (Percentual) (current_player_exp_progress)
Retorna o progresso de experiência do jogador para o próximo nível em porcentagem.
```
{"placeholder":"current_player_exp_progress"}
```
Exemplo de saída: `75`

## Força de ataque do jogador (Percentual) (player_attack_strength)
Retorna o tempo de recarga do ataque do jogador em porcentagem.
```
{"placeholder":"player_attack_strength"}
```
Exemplo de saída: `100`

## Modo de jogo do jogador (player_gamemode)
Retorna o modo de jogo atual do jogador.
```
{"placeholder":"player_gamemode"}
```
Exemplo de saída: `survival`

## Direção de visão do jogador (player_view_direction)
Retorna a direção para a qual o jogador está olhando.
```
{"placeholder":"player_view_direction"}
```
Exemplo de saída: `north`

## Coordenada X do jogador (player_x_coordinate)
Retorna a posição X do jogador no mundo.
```
{"placeholder":"player_x_coordinate"}
```
Exemplo de saída: `125`

## Coordenada Y do jogador (player_y_coordinate)
Retorna a posição Y do jogador no mundo.
```
{"placeholder":"player_y_coordinate"}
```
Exemplo de saída: `64`

## Coordenada Z do jogador (player_z_coordinate)
Retorna a posição Z do jogador no mundo.
```
{"placeholder":"player_z_coordinate"}
```
Exemplo de saída: `-250`

## Vida atual da montaria (current_mount_health)
Retorna a vida atual da entidade que o jogador está montando.
```
{"placeholder":"current_mount_health"}
```
Exemplo de saída: `30.0`

## Vida máxima da montaria (max_mount_health)
Retorna a vida máxima da entidade que o jogador está montando.
```
{"placeholder":"max_mount_health"}
```
Exemplo de saída: `30.0`

## Vida atual da montaria (Percentual) (current_mount_health_percent)
Retorna a vida da montaria em porcentagem.
```
{"placeholder":"current_mount_health_percent"}
```
Exemplo de saída: `100`

## Medidor atual de salto da montaria (Percentual) (current_mount_jump_meter)
Retorna o valor do medidor de força do salto da montaria.
```
{"placeholder":"current_mount_jump_meter"}
```
Exemplo de saída: `75`

## Vida atual do chefe (Percentual) (current_boss_health)
Retorna a vida do chefe ativo.
```
{"placeholder":"current_boss_health"}
```
Exemplo de saída: `150.0`

## Nome do chefe (boss_name)
Retorna o nome do chefe ativo.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Exemplo de saída: `Ender Dragon`

## Quantidade de chefes (boss_count)
Retorna o número de chefes ativos.
```
{"placeholder":"boss_count"}
```
Exemplo de saída: `1`

## Quantidade de efeitos ativos (effects_count)
Retorna o número de efeitos de poção ativos.
```
{"placeholder":"effects_count"}
```
Exemplo de saída: `3`

## Efeito ativo (active_effect)
Retorna informações sobre um efeito ativo específico.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Exemplo de saída: `minecraft:speed`

## Slot selecionado da hotbar (active_hotbar_slot)
Retorna o slot atualmente selecionado da hotbar (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Exemplo de saída: `4`

## Item do slot (slot_item)
Retorna informações sobre um item em um slot específico do inventário.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Exemplo de saída: `minecraft:diamond_sword`

## Quantidade de itens do slot (slot_item_count)
Retorna o tamanho da pilha do item em um slot específico do inventário do jogador.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Exemplo de saída: `64`

## Durabilidade do item do slot (slot_item_durability)
Retorna informações de durabilidade do item em um slot específico do inventário do jogador.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parâmetros:
- `slot`: Número do slot do inventário do jogador.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` ou `percent`.

Exemplo de saída: `87`

## Nome exibido do item do slot (slot_item_display_name_fm)
Retorna o nome exibido do item em um slot específico como um componente de texto JSON. No modo espectador, os slots da hotbar podem resolver nomes de itens do menu espectador, a menos que `ignore_spectator` seja `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Exemplo de saída: `{"text":"Diamond Sword","color":"aqua"}`

## Quantidade de item no inventário (inventory_item_count)
Retorna a contagem total de um tipo de item no inventário do jogador. Se `item` estiver vazio, conta todas as pilhas de itens no inventário.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Exemplo de saída: `12`

## Quantidade de restauração de fome do item no slot do inventário (inventory_slot_food_point_restore_amount)
Retorna os pontos de fome restaurados pelo item de comida no slot informado do inventário do jogador.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Exemplo de saída: `4.0`

## Item do inventário sob o cursor (hovered_inventory_item)
Retorna a chave do item que está sob o cursor no momento em uma tela de inventário.
```
{"placeholder":"hovered_inventory_item"}
```
Exemplo de saída: `minecraft:apple`

## Tempo de jogo do mundo (game_time)
Retorna o contador atual de ticks do tempo do jogo.
```
{"placeholder":"game_time"}
```
Exemplo de saída: `18000`

## Horário do dia do mundo (world_daytime)
Retorna o horário atual do dia no mundo.
```
{"placeholder":"world_daytime"}
```
Exemplo de saída: `13000`

## Hora do horário do dia do mundo (world_daytime_hour)
Retorna o componente de hora do tempo do mundo. Por padrão, isso usa o formato de 24 horas; defina `twelve_hour_format` como `"true"` para usar o formato de 12 horas.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Exemplo de saída: `12`

## Minuto do horário do dia do mundo (world_daytime_minute)
Retorna o componente de minuto do tempo do mundo (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Exemplo de saída: `30`

## Dificuldade do mundo (world_difficulty)
Retorna a dificuldade atual do mundo.
```
{"placeholder":"world_difficulty"}
```
Exemplo de saída: `normal`

## Seed do mundo atual (current_world_seed)
Retorna a seed do mundo singleplayer atual. Retorna um valor vazio quando a seed não estiver disponível.
```
{"placeholder":"current_world_seed"}
```
Exemplo de saída: `123456789`

## Bioma atual (current_biome)
Retorna o bioma em que o jogador está no momento. Defina `as_key` como `"false"` para retornar um nome traduzido/exibido quando उपलब्धo.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Exemplo de saída: `minecraft:plains`

## Dimensão atual (current_dimension)
Retorna a dimensão em que o jogador está no momento. Defina `as_key` como `"false"` para retornar um nome traduzido/exibido quando disponível.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Exemplo de saída: `minecraft:overworld`

## Valor da gamerule (gamerule_value)
Retorna o valor atual de uma gamerule no mundo/servidor carregado. Mundos em servidor exigem o FancyMenu no servidor.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Exemplo de saída: `true`

## Categoria do item (item_category)
Retorna a categoria da aba Criativo de um item. Defina `as_key` como `"true"` para retornar a chave da categoria em vez do nome exibido.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Exemplo de saída: `Combat`

## Título/subtítulo atual da HUD (current_title)
Retorna o texto do título exibido no momento.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Exemplo de saída: `Game Over!`

## Mensagem da barra de ação (action_bar_message_fm)
Retorna a mensagem atual padrão da barra de ação acima da hotbar.
```
{"placeholder":"action_bar_message_fm"}
```
Exemplo de saída: `You may not rest now`

## Tempo da mensagem da barra de ação (action_bar_message_time_fm)
Retorna por quantos ticks a mensagem atual da barra de ação ainda será exibida.
```
{"placeholder":"action_bar_message_time_fm"}
```
Exemplo de saída: `42`

## Rotação X da câmera (camera_rotation_x_fm)
Retorna o pitch atual da câmera em graus.
```
{"placeholder":"camera_rotation_x_fm"}
```
Exemplo de saída: `12.5`

## Rotação Y da câmera (camera_rotation_y_fm)
Retorna o yaw atual da câmera em graus.
```
{"placeholder":"camera_rotation_y_fm"}
```
Exemplo de saída: `-90.0`

## Variação X da rotação da câmera (camera_rotation_delta_x_fm)
Retorna a mudança por tick no pitch da câmera.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Exemplo de saída: `0.4`

## Variação Y da rotação da câmera (camera_rotation_delta_y_fm)
Retorna a mudança por tick no yaw da câmera.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Exemplo de saída: `-1.2`

## Tempo do item destacado (highlighted_item_time_fm)
Retorna por quantos ticks o nome do item destacado ainda será exibido acima da hotbar.
```
{"placeholder":"highlighted_item_time_fm"}
```
Exemplo de saída: `30`

## Progresso de uso do item pelo jogador (player_item_use_progress_fm)
Retorna o progresso atual de uso do item de `0.0` a `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Exemplo de saída: `0.65`

## Variação X da posição do jogador (player_position_delta_x_fm)
Retorna a mudança por tick na posição do jogador no eixo X.
```
{"placeholder":"player_position_delta_x_fm"}
```
Exemplo de saída: `0.0`

## Variação Y da posição do jogador (player_position_delta_y_fm)
Retorna a mudança por tick na posição do jogador no eixo Y.
```
{"placeholder":"player_position_delta_y_fm"}
```
Exemplo de saída: `-0.08`

## Variação Z da posição do jogador (player_position_delta_z_fm)
Retorna a mudança por tick na posição do jogador no eixo Z.
```
{"placeholder":"player_position_delta_z_fm"}
```
Exemplo de saída: `0.12`

## IP do servidor atual (current_server_ip)
Retorna o IP do servidor conectado.
```
{"placeholder":"current_server_ip"}
```
Exemplo de saída: `mc.hypixel.net`

## Lista de jogadores do mundo (world_players_list)
Retorna uma lista de todos os jogadores atualmente no mundo.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Exemplo de saída: `Steve, Alex, Notch`

## MOTD do servidor (servermotd)
Retorna a Message of the Day de um servidor.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Exemplo de saída: `Welcome to Hypixel!`

## PING do servidor (serverping)
Retorna o ping de um servidor em milissegundos.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Exemplo de saída: `54`

## Quantidade de jogadores no servidor (serverplayercount)
Retorna a quantidade de jogadores de um servidor.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Exemplo de saída: `25000/30000`

## Status do servidor (serverstatus)
Retorna o status online/offline de um servidor.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Exemplo de saída: `§aOnline` ou `§cOffline`

## Versão do servidor (serverversion)
Retorna a versão do Minecraft de um servidor.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Exemplo de saída: `1.19.2`

## Ano (realtimeyear)
Retorna o ano atual.
```
{"placeholder":"realtimeyear"}
```
Exemplo de saída: `2024`

## Mês (realtimemonth)
Retorna o mês atual (01-12).
```
{"placeholder":"realtimemonth"}
```
Exemplo de saída: `01`

## Dia (realtimeday)
Retorna o dia atual do mês (01-31).
```
{"placeholder":"realtimeday"}
```
Exemplo de saída: `27`

## Hora (realtimehour)
Retorna a hora atual. Por padrão, isso usa o formato de 24 horas; defina `twelve_hour_format` como `"true"` para usar o formato de 12 horas.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Exemplo de saída: `14`

## Minuto (realtimeminute)
Retorna o minuto atual (00-59).
```
{"placeholder":"realtimeminute"}
```
Exemplo de saída: `30`

## Segundo (realtimesecond)
Retorna o segundo atual (00-59).
```
{"placeholder":"realtimesecond"}
```
Exemplo de saída: `45`

## Hora atual em milissegundos (Unix Timestamp) (unix_time)
Retorna o timestamp Unix atual em milissegundos.
```
{"placeholder":"unix_time"}
```
Exemplo de saída: `1716552478123`

> Os placeholders de tempo real (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` e `unix_time`) suportam um valor `timezone`. Use IDs normais de fuso horário do Java, como `UTC`, `Europe/Berlin` ou `America/New_York`; omita-o ou use `system` para o fuso horário do sistema.
{.is-info}

## Informações da CPU (cpuinfo)
Retorna informações sobre a CPU.
```
{"placeholder":"cpuinfo"}
```
Exemplo de saída: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Uso da CPU (JVM) (jvmcpu)
Retorna o uso de CPU da JVM em porcentagem.
```
{"placeholder":"jvmcpu"}
```
Exemplo de saída: `25.5`

## Uso da CPU (SO) (oscpu)
Retorna o uso de CPU do sistema operacional em porcentagem.
```
{"placeholder":"oscpu"}
```
Exemplo de saída: `42.8`

## Informações da GPU (gpuinfo)
Retorna informações sobre a GPU.
```
{"placeholder":"gpuinfo"}
```
Exemplo de saída: `NVIDIA GeForce RTX 3080`

## Versão do Java (javaver)
Retorna a versão do Java.
```
{"placeholder":"javaver"}
```
Exemplo de saída: `17.0.2`

## Máquina virtual Java (jvmname)
Retorna o nome da Java Virtual Machine.
```
{"placeholder":"jvmname"}
```
Exemplo de saída: `OpenJDK 64-Bit Server VM`

## Versão do OpenGL (glver)
Retorna a versão do OpenGL.
```
{"placeholder":"glver"}
```
Exemplo de saída: `4.6.0 NVIDIA 516.94`

## Nome do sistema operacional (osname)
Retorna o nome do sistema operacional.
```
{"placeholder":"osname"}
```
Exemplo de saída: `Windows 10`

## FPS (quadros por segundo) (fps)
Retorna os quadros por segundo atuais.
```
{"placeholder":"fps"}
```
Exemplo de saída: `120`

## RAM usada em MB (usedram)
Retorna a quantidade de RAM atualmente em uso (MB).
```
{"placeholder":"usedram"}
```
Exemplo de saída: `4096`

## RAM máxima em MB (maxram)
Retorna a quantidade máxima de RAM alocada (MB).
```
{"placeholder":"maxram"}
```
Exemplo de saída: `8192`

## RAM usada em %% (percentram)
Retorna a porcentagem de RAM atualmente em uso.
```
{"placeholder":"percentram"}
```
Exemplo de saída: `50`

## Volume do elemento de áudio (audio_element_vol)
Retorna o volume de um elemento de áudio.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Exemplo de saída: `0.5`

## Faixa de áudio atual (audio_element_current_track)
Retorna o nome da faixa de um elemento de áudio.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Exemplo de saída: `Cool Track Name`

## Duração do áudio (audio_duration)
Retorna a duração total de uma faixa de áudio no formato MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Exemplo de saída: `03:45`

## Tempo de reprodução do áudio (audio_playtime)
Retorna o tempo atual de reprodução de uma faixa de áudio. Defina `show_percentage` como `"true"` para obter um valor de progresso de 0 a 100 em vez de `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Exemplo de saída: `01:30` (ou `45` quando `show_percentage` é `"true"`)

## Estado de reprodução do áudio (audio_playing_state)
Retorna se um elemento de áudio está tocando (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Exemplo de saída: `true`

## Volume do elemento de vídeo (video_element_vol)
Retorna o nível de volume de um elemento de vídeo (0.0 a 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Exemplo de saída: `0.5`

## Duração do elemento de vídeo (video_element_duration)
Retorna a duração total de um elemento de vídeo no formato `MM:SS`. Defina `output_as_timestamp` como `"true"` para retornar um timestamp em milissegundos.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Exemplo de saída: `02:00` (ou `120000` quando `output_as_timestamp` é `"true"`)

## Tempo de reprodução do elemento de vídeo (video_element_playtime)
Retorna o tempo atual de reprodução (progresso) de um elemento de vídeo no formato `MM:SS`. Defina `show_percentage` como `"true"` para um valor de progresso de 0 a 100, ou `output_as_timestamp` como `"true"` para milissegundos.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Exemplo de saída: `00:45` (ou `38` como porcentagem, ou `45200` como timestamp)

## Estado pausado do elemento de vídeo (video_element_paused_state)
Retorna se um elemento de vídeo está pausado (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Exemplo de saída: `false`

## Volume do plano de fundo em vídeo (video_background_vol)
Retorna o nível de volume de um plano de fundo em vídeo do menu (0.0 a 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Exemplo de saída: `0.7`

## Duração do plano de fundo em vídeo (video_background_duration)
Retorna a duração total de um plano de fundo em vídeo do menu no formato `MM:SS`. Defina `output_as_timestamp` como `"true"` para retornar um timestamp em milissegundos.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Exemplo de saída: `03:00` (ou `180000` quando `output_as_timestamp` é `"true"`)

## Tempo de reprodução do plano de fundo em vídeo (video_background_playtime)
Retorna o tempo atual de reprodução (progresso) de um plano de fundo em vídeo do menu no formato `MM:SS`. Defina `show_percentage` como `"true"` para um valor de progresso de 0 a 100, ou `output_as_timestamp` como `"true"` para milissegundos.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Exemplo de saída: `01:00` (ou `33` como porcentagem, ou `60500` como timestamp)

## Estado pausado do plano de fundo em vídeo (video_background_paused_state)
Retorna se um plano de fundo em vídeo do menu está pausado (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Exemplo de saída: `true`

## Calculadora (calc)
O placeholder de calculadora é uma ferramenta poderosa que permite realizar cálculos matemáticos dentro dos seus layouts. Ele suporta uma ampla variedade de operações matemáticas e pode funcionar com números decimais e inteiros.

### Sintaxe básica
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"sua_expressao"}}
```

A calculadora tem dois parâmetros principais:
- `decimal`: Determina se o resultado deve incluir casas decimais (`true`) ou ser arredondado para inteiros (`false`)
- `expression`: A expressão matemática a ser avaliada

### Operações suportadas
A calculadora suporta estas operações matemáticas:
- Aritmética básica: `+` (adição), `-` (subtração), `*` (multiplicação), `/` (divisão)
- Parênteses: `( )` para agrupar operações
- Potência: `^` para expoentes
- Raiz quadrada: `sqrt()`
- Funções trigonométricas: `sin()`, `cos()`, `tan()`
- Constantes matemáticas: `pi`, `e`
- Valor absoluto: `abs()`
- Logaritmos: `log()`, `ln()`

## Número aleatório (random_number)
Gera um número aleatório dentro de um intervalo especificado.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Exemplo de saída: `42`

## Número máximo (maxnum)
Retorna o maior de dois números.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Exemplo de saída: `20`

## Número mínimo (minnum)
Retorna o menor de dois números.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Exemplo de saída: `10`

## Número absoluto (absnum)
Retorna o valor absoluto de um número.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Exemplo de saída: `10.5`

## Negar número (negnum)
Retorna o valor negado de um número.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Exemplo de saída: `-10.5`

## *pi* (Matemática) (math_pi)
Retorna o valor de π.
```
{"placeholder":"math_pi"}
```
Exemplo de saída: `3.141592653589793`

## Seno trigonométrico (Matemática) (math_sin)
Retorna o seno de um ângulo.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Exemplo de saída: `0.7071067811865476`

## Cosseno trigonométrico (Matemática) (math_cos)
Retorna o cosseno de um ângulo.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Exemplo de saída: `0.7071067811865476`

## Tangente trigonométrica (Matemática) (math_tan)
Retorna a tangente de um ângulo.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Exemplo de saída: `1.0`

## Piso (Matemática) (math_floor)
Arredonda um número para baixo até o inteiro mais próximo.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Exemplo de saída: `3`

## Teto (Matemática) (math_ceil)
Arredonda um número para cima até o inteiro mais próximo.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Exemplo de saída: `4`

## Arredondar (Matemática) (math_round)
Arredonda um número. Por padrão, arredonda para o inteiro mais próximo; defina `decimals` como um número não negativo para arredondar para essa quantidade de casas decimais.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Exemplo de saída: `3.14` (com `decimals:-1` ou omitido → `3`)

## Sinal (Matemática) (math_sign)
Retorna o sinal de um número (1 para positivo, -1 para negativo, 0 para zero).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Exemplo de saída: `-1`

## Seno hiperbólico (Matemática) (math_sinh)
Retorna o seno hiperbólico de um ângulo.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Exemplo de saída: `1.1752011936438014`

## Cosseno hiperbólico (Matemática) (math_cosh)
Retorna o cosseno hiperbólico de um ângulo.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Exemplo de saída: `1.5430806348152437`

## Tangente hiperbólica (Matemática) (math_tanh)
Retorna a tangente hiperbólica de um ângulo.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Exemplo de saída: `0.7615941559557649`

## Dividir texto (split_text)
Divide o texto usando um delimitador especificado.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Exemplo de saída: `world`

## Limpar espaços do texto (trim_text)
Remove espaços em branco do início e do fim.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Exemplo de saída: `hello world`

## Recortar texto (crop_text)
Remove caracteres do início e do fim do texto.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Exemplo de saída: `ello worl`

## Stringify (stringify)
Converte o texto em string escapando todos os caracteres de sintaxe.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Exemplo de saída: `text with \{special\} \"characters\"`

## Localizar texto (local)
Obtém o texto localizado de uma chave.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Exemplo de saída: `Singleplayer`

## Texto da web (webtext)
Obtém o conteúdo de texto de uma URL da web.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Exemplo de saída: conteúdo de texto da URL

## Texto aleatório (randomtext)
Retorna uma linha aleatória de um arquivo de texto, URL ou texto simples direto. O texto muda em intervalos especificados.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parâmetros:
- `source`: A origem das linhas de texto (substitui o antigo parâmetro `path`)
  - Caminho de arquivo: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Texto simples: `Linha 1\nLinha 2\nLinha 3`
- `interval`: Tempo em segundos entre as mudanças de texto

O placeholder agora suporta três tipos de origem:
1. **Arquivos locais**: arquivos de texto da pasta do seu jogo
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: arquivos de texto remotos da internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texto simples**: entrada de texto direta com linhas separadas por `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"Primeira linha\nSegunda linha\nTerceira linha","interval":"5"}}
   ```

Observação: placeholders antigos que usam `path` em vez de `source` continuarão funcionando.

## Analisador JSON (json)
Analisa dados JSON de um arquivo, URL ou conteúdo JSON direto e extrai valores usando expressões JSON path.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parâmetros:
- `source`: A origem dos dados JSON
  - Caminho de arquivo: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - JSON direto: `{"name":"Steve","level":42}`
- `json_path`: A expressão JSON path para extrair dados

O placeholder agora suporta três tipos de origem:
1. **Arquivos locais**: arquivos JSON da pasta do seu jogo
   ```
   {"placeholder":"json","values":{"source":"/config/fancymenu/assets/playerdata.json","json_path":"$.player.name"}}
   ```
2. **URLs**: dados JSON remotos de APIs ou serviços web
   ```
   {"placeholder":"json","values":{"source":"https://api.minecraft.com/server/status","json_path":"$.online"}}
   ```
3. **JSON direto**: conteúdo JSON embutido
   ```
   {"placeholder":"json","values":{"source":"{"name":"Steve","score":42,"rank":"Diamond"}","json_path":"$.rank"}}
   ```

Exemplos de JSON path:
- `$.name` - Obtém o campo "name" na raiz
- `$.player.level` - Obtém o campo aninhado "level" dentro de "player"
- `$.items[0].id` - Obtém o "id" do primeiro item em um array
- `$.scores.*` - Obtém todos os valores do objeto "scores"

## Caminho absoluto de arquivo/pasta (absolute_path)
Retorna o caminho absoluto de um arquivo.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Exemplo de saída: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Contagem de caracteres do texto (text_character_count)
Retorna o número de caracteres no texto fornecido.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Exemplo de saída: `12`

## Largura do texto (text_width)
Retorna a largura em pixels do texto fornecido quando renderizado.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Exemplo de saída: `66`

## Texto em maiúsculas (uppercase_text)
Converte o texto de entrada para letras maiúsculas.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Exemplo de saída: `HELLO WORLD`

## Texto em minúsculas (lowercase_text)
Converte o texto de entrada para letras minúsculas.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Exemplo de saída: `hello world`

## Texto em Title Case (title_case_text)
Converte o texto de entrada para Title Case.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Exemplo de saída: `Hello World`

## Texto em Sentence Case (sentence_case_text)
Converte o texto de entrada para Sentence Case.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Exemplo de saída: `Hello world. This is fancymenu!`

## Texto em snake_case (snake_case_text)
Converte o texto de entrada para `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Exemplo de saída: `hello_world`

## Texto em kebab-case (kebab_case_text)
Converte o texto de entrada para `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Exemplo de saída: `hello-world`

## Texto em case alternado (alternating_case_text)
Converte o texto de entrada para case alternado.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Exemplo de saída: `aLtErNaTiNg CaSe`

## Alternar caixa do texto (toggle_case_text)
Alterna a caixa de todas as letras do texto de entrada.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Exemplo de saída: `tOGGLE cASE`

## Codificar em Base64 (base64_encode)
Codifica o texto fornecido em Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Exemplo de saída: `SGVsbG8gV29ybGQ=`

## Decodificar de Base64 (base64_decode)
Decodifica uma string Base64 de volta para texto simples.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Exemplo de saída: `Hello World`

## Texto de arquivo (file_text)
Retorna linhas de texto de um arquivo ou URL. Pode retornar todas as linhas ou apenas as últimas X linhas.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parâmetros:
- `path_or_url`: Caminho do arquivo ou URL de onde ler
- `mode`: `"all"` (retorna todas as linhas) ou `"last"` (retorna apenas as últimas X linhas)
- `separator`: Texto usado para unir as linhas (padrão: `"\n"`)
- `last_lines`: Número de linhas a retornar quando o modo for `"last"` (padrão: `"1"`)

Exemplo de saída: Depende do conteúdo do arquivo

## Conteúdo da área de transferência (clipboard_content)
Retorna o conteúdo de texto atualmente armazenado na área de transferência do sistema.
```
{"placeholder":"clipboard_content"}
```
Exemplo de saída: Qualquer texto que estiver atualmente na área de transferência

## Substituir texto (replace_text)
Substitui texto em uma string usando texto literal ou expressões regulares.
```
{"placeholder":"replace_text","values":{"text":"Hello World! This is a test.","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```
Parâmetros:
- `text`: O texto de entrada a ser processado
- `search`: O texto ou padrão regex a ser procurado
- `replacement`: O texto de substituição
- `use_regex`: Se deve usar regex (`"true"`) ou correspondência literal (`"false"`)
- `replace_all`: Substituir todas as ocorrências (`"true"`) ou apenas a primeira (`"false"`)

Exemplo de saída: `Hello FancyMenu! This is a test.`

## Estrutura switch-case (switch_case)
Executa uma operação switch-case com base em um valor.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Exemplo de saída: `first case` (se o valor for 1)

## Obter valor de variável (Variável FM) (getvariable)
Recupera o valor de uma variável armazenada anteriormente.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Exemplo de saída: Depende do valor armazenado

## Obter dados NBT (nbt_data_get)
Recupera dados NBT no cliente (semelhante ao comando `/data get`). Use a variante do servidor `nbt_data_get_server` quando estiver conectado a um servidor e precisar de valores autoritativos do lado do servidor.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parâmetros:
- `source_type`: `"entity"` ou `"block"`
- `entity_selector`: Seletor de entidade como `@s`, `@p`, `@e` ou UUID/nome (para entidades)
- `block_pos`: Posição do bloco no formato `"x y z"` (para blocos)
- `nbt_path`: O caminho NBT a ser recuperado
- `scale`: Fator de escala opcional para valores numéricos (padrão: `"1.0"`)
- `return_type`: Como retornar os dados:
  - `"value"`: Padrão, retorna o valor (com escala opcional para números)
  - `"string"`: Retorna os dados NBT reais como string
  - `"snbt"`: Retorna como SNBT (NBT formatado)
  - `"json"`: Retorna como componente formatado em JSON (para tags compostas)

Exemplo de saída: `20` (para nível de fome)

## Obter dados NBT (lado do servidor) (nbt_data_get_server)
Consulta dados NBT no lado do servidor (usando um pacote) e armazena o resultado em cache por um curto período. Os valores espelham o placeholder do lado do cliente.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Exemplo de saída: `minecraft:diamond_sword`

## Última mensagem de morte (lastdeathmessage)
Retorna a última mensagem de morte registrada do jogador cliente. Defina `as_json_component` como `"true"` para obter o componente de texto JSON bruto.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Exemplo de saída: `Steve was slain by Zombie`

## Duração da execução (uptime_duration)
Retorna há quanto tempo o FancyMenu está carregado. Por padrão, o valor está em segundos; defina `output_as_millis` como `"true"` para receber milissegundos.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Exemplo de saída: `742` (segundos desde o carregamento)

## Nomes de salvamentos do mundo (level_save_names)
Lista todos os nomes de salvamentos locais do mundo unidos pelo separador escolhido. Executa na thread do cliente.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Exemplo de saída: `Creative Test, Survival World, Hardcore`

## Dados do salvamento do mundo (level_save_data)
Retorna os dados serializados do nível para o nome do mundo fornecido (deve corresponder ao nome exibido na lista de salvamentos).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Exemplo de saída: `{"name":"Survival World","gameMode":"survival",...}`

## Conversor de base numérica (number_base_convert)
Converte um número (inteiro ou fracionário) de uma base para outra (2–36). Usa decimal por padrão se as bases não forem fornecidas.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Exemplo de saída: `43.8`

## Tamanho do arquivo (file_size)
Retorna o tamanho de um arquivo local em bytes. Apenas caminhos locais são permitidos.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Exemplo de saída: `1284`

## MD5 do arquivo (file_md5)
Retorna o hash MD5 de um arquivo local como uma string hexadecimal em letras minúsculas.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Exemplo de saída: `d41d8cd98f00b204e9800998ecf8427e`

# Exemplos práticos

## Criando uma exibição dinâmica de memória
```
RAM usada: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Criando um relógio em tempo real
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
```

## Criando uma exibição de informações do sistema
```
SO: {"placeholder":"osname"}
CPU: {"placeholder":"cpuinfo"}
GPU: {"placeholder":"gpuinfo"}
Java: {"placeholder":"javaver"}
```

## HUD de status do jogador
```
Vida: {"placeholder":"current_player_health"} / {"placeholder":"max_player_health"} ({"placeholder":"current_player_health_percent"}%)
Armadura: {"placeholder":"current_player_armor"} / {"placeholder":"max_player_armor"}
Nível de XP: {"placeholder":"current_player_level"}
```

## Cálculo complexo com placeholders aninhados
```
{"placeholder":"calc","values":{"decimal":"true","expression":"({"placeholder":"usedram"} / {"placeholder":"maxram"}) * 100"}}
```

## Exibição de coordenadas com arredondamento
```
X: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_x_coordinate"}"}}
Y: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_y_coordinate"}"}}
Z: {"placeholder":"math_round","values":{"num":"{"placeholder":"player_z_coordinate"}"}}
```

# Boas práticas

1. **Cache operações caras**: Alguns placeholders (como os que leem informações do sistema) podem exigir muitos recursos. Considere usar variáveis para armazenar seus valores se precisar usá-los várias vezes.

2. **Use configurações decimais apropriadas**: Ao trabalhar com cálculos, use o parâmetro `decimal` de forma adequada. Defina como `false` quando precisar de inteiros e como `true` quando precisar de valores decimais precisos.

3. **Trate valores ausentes**: Sempre considere o que deve acontecer se um placeholder não retornar valor. Talvez seja interessante fornecer valores padrão nesses casos.

4. **Teste o desempenho**: Ao usar muitos placeholders ou estruturas aninhadas complexas, teste o impacto no desempenho, especialmente em sistemas mais modestos.

5. **Use dimensionamento/posicionamento avançados**: Para elementos de UI dinâmicos, combine placeholders com dimensionamento e posicionamento avançados para criar layouts responsivos.

6. **Combine com variáveis**: Use placeholders junto com variáveis para conteúdos ainda mais dinâmicos que podem ser atualizados por meio de ações.

# Problemas comuns e soluções

## Placeholder não atualiza
Se o valor de um placeholder não estiver atualizando como esperado, verifique:
- Se o placeholder está formatado corretamente
- Se você está usando a capitalização correta para os IDs dos placeholders
- Se o placeholder exige condições específicas para atualizar

## Placeholders aninhados não funcionam
Ao aninhar placeholders:
- Garanta o escape correto de aspas
- Verifique se cada placeholder aninhado é válido por si só

## Problemas de desempenho
Se você notar problemas de desempenho:
- Reduza o número de placeholders usados
- Evite aninhamento desnecessário
- Considere usar variáveis para valores acessados com frequência
- Use o placeholder apropriado para a sua necessidade (por exemplo, não use placeholders em tempo real quando valores estáticos forem suficientes)
