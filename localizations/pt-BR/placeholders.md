---
title: Placeholders
description: Como usar placeholders.
---
# Placeholders

Placeholders são valores dinâmicos que são substituídos por conteúdo real quando usados. No FancyMenu, os placeholders permitem inserir conteúdo dinâmico em vários elementos, como texto, botões e requisitos de carregamento. Pense neles como variáveis que são avaliadas e substituídas pelos seus valores reais quando seus layouts são exibidos.

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
Um dos recursos mais poderosos do sistema de placeholders do FancyMenu é a possibilidade de aninhar placeholders dentro de outros placeholders. Isso significa que você pode usar a saída de um placeholder como entrada para outro.

Exemplo de placeholders aninhados:
```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```
Este exemplo pega o valor máximo de RAM e divide por 1024 para convertê-lo de MB para GB.

> [!IMPORTANT]
> Diferente do JSON real, placeholders aninhados **não** são **escapados** usando `\\`. Isso é muito importante, porque os placeholders param de funcionar quando escapados (obviamente). Placeholders usam apenas uma sintaxe parecida com JSON. Eles não são JSON de verdade.

# Usando Placeholders

A maioria dos elementos que possuem campos de texto oferece suporte a placeholders. Você pode ver se um campo de texto suporta placeholders ao editá-lo. Se o **editor de texto** em tela cheia abrir ao editar o texto, ele oferece suporte a placeholders.

Para encontrar uma **lista de todos os placeholders**, basta clicar no botão **Placeholders** no **canto superior direito** do **editor de texto**.

Há uma **barra de pesquisa** no topo da lista de placeholders que permite pesquisar por placeholders.

Clicar em um placeholder na lista irá colá-lo no conteúdo de texto.

# Placeholders em Detalhes

Esta lista contém a maioria, senão todos, os placeholders disponíveis no FancyMenu. A lista pode às vezes ficar um pouco desatualizada devido a atualizações do mod.

## Nome do Jogador (playername)
Retorna o nome de usuário do jogador atual.
```
{"placeholder":"playername"}
```
Saída de exemplo: `Steve`

## UUID do Jogador (playeruuid)
Retorna o identificador exclusivo do jogador.
```
{"placeholder":"playeruuid"}
```
Saída de exemplo: `c8cde7fe-7ced-11eb-9439-0242ac130002`

## Versão do Minecraft (mcversion)
Retorna a versão atual do Minecraft.
```
{"placeholder":"mcversion"}
```
Saída de exemplo: `1.19.2`

## Versão do Carregador de Mods (loaderver)
Retorna a versão do carregador de mods (Forge/Fabric).
```
{"placeholder":"loaderver"}
```
Saída de exemplo: `43.2.0`

## Nome do Carregador de Mods (loadername)
Retorna o nome do carregador de mods.
```
{"placeholder":"loadername"}
```
Saída de exemplo: `Forge`

## Versão do Mod (modversion)
Retorna a versão de um mod específico.
```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```
Saída de exemplo: `2.14.9`

## Quantidade Total de Mods (totalmods)
Retorna o número total de mods instalados.
```
{"placeholder":"totalmods"}
```
Saída de exemplo: `45`

## Quantidade de Mods Ativos (loadedmods)
Retorna o número de mods carregados no momento.
```
{"placeholder":"loadedmods"}
```
Saída de exemplo: `43`

## Progresso de Carregamento do Mundo (world_load_progress)
Retorna o progresso atual de carregamento do mundo em porcentagem.
```
{"placeholder":"world_load_progress"}
```
Saída de exemplo: `75`

## Valor de Opção do Minecraft (minecraft_option_value)
Retorna o valor de uma opção do Minecraft.
```
{"placeholder":"minecraft_option_value","values":{"name":"fov"}}
```
Saída de exemplo: `70`

## Último Mundo ou Servidor (last_world_server)
Retorna informações sobre o último mundo ou servidor acessado.
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

## Largura da Tela (guiwidth)
Retorna a largura atual da tela.
```
{"placeholder":"guiwidth"}
```
Saída de exemplo: `1920`

## Altura da Tela (guiheight)
Retorna a altura atual da tela.
```
{"placeholder":"guiheight"}
```
Saída de exemplo: `1080`

## Identificador da Tela Atual (screenid)
Retorna o identificador da tela atual.
```
{"placeholder":"screenid"}
```
Saída de exemplo: `title_screen`

## Largura do Elemento (elementwidth)
Retorna a largura de um elemento específico.
```
{"placeholder":"elementwidth","values":{"id":"my_button"}}
```
Saída de exemplo: `200`

## Altura do Elemento (elementheight)
Retorna a altura de um elemento específico.
```
{"placeholder":"elementheight","values":{"id":"my_button"}}
```
Saída de exemplo: `20`

## Posição X do Elemento (elementposx)
Retorna a posição X de um elemento específico.
```
{"placeholder":"elementposx","values":{"id":"my_button"}}
```
Saída de exemplo: `150`

## Posição Y do Elemento (elementposy)
Retorna a posição Y de um elemento específico.
```
{"placeholder":"elementposy","values":{"id":"my_button"}}
```
Saída de exemplo: `100`

## Posição X do Mouse (mouseposx)
Retorna a posição X atual do mouse.
```
{"placeholder":"mouseposx"}
```
Saída de exemplo: `960`

## Posição Y do Mouse (mouseposy)
Retorna a posição Y atual do mouse.
```
{"placeholder":"mouseposy"}
```
Saída de exemplo: `540`

## Cliques por Segundo (clicks_per_second)
Retorna os cliques por segundo atuais de um botão do mouse.
```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```
Parâmetros:
- `mouse_button`: `left` ou `right`

Saída de exemplo: `8`

## Escala da Interface (guiscale)
Retorna a escala atual da interface.
```
{"placeholder":"guiscale"}
```
Saída de exemplo: `2`

## Rótulo/Text de Widget Vanilla (vanillabuttonlabel)
Retorna o rótulo/texto de um widget/botão vanilla.
```
{"placeholder":"vanillabuttonlabel","values":{"locator":"some.menu.identifier:505280"}}
```
Saída de exemplo: `Options...`

## Valor de Campo de Texto (text_input_field_value)
Retorna o valor atual de um campo de texto personalizado ou vanilla pelo identificador do elemento.
```
{"placeholder":"text_input_field_value","values":{"element_identifier":"my_input"}}
```
Saída de exemplo: `Hello World`

## Vida Atual do Jogador (current_player_health)
Retorna os pontos de vida atuais do jogador.
```
{"placeholder":"current_player_health"}
```
Saída de exemplo: `20.0`

## Vida Máxima do Jogador (max_player_health)
Retorna os pontos de vida máximos do jogador.
```
{"placeholder":"max_player_health"}
```
Saída de exemplo: `20.0`

## Vida Atual do Jogador (Percentual) (current_player_health_percent)
Retorna a vida do jogador em porcentagem.
```
{"placeholder":"current_player_health_percent"}
```
Saída de exemplo: `100`

## Vida de Absorção Atual do Jogador (current_player_absorption_health)
Retorna os pontos de vida de absorção do jogador (corações dourados).
```
{"placeholder":"current_player_absorption_health"}
```
Saída de exemplo: `4.0`

## Vida Máxima de Absorção do Jogador (max_player_absorption_health)
Retorna a vida máxima de absorção.
```
{"placeholder":"max_player_absorption_health"}
```
Saída de exemplo: `4.0`

## Vida de Absorção Atual do Jogador (Percentual) (current_player_absorption_health_percent)
Retorna a vida de absorção do jogador em porcentagem.
```
{"placeholder":"current_player_absorption_health_percent"}
```
Saída de exemplo: `100`

## Nível de Fome Atual do Jogador (current_player_hunger)
Retorna o nível atual de fome do jogador.
```
{"placeholder":"current_player_hunger"}
```
Saída de exemplo: `20`

## Nível Máximo de Fome do Jogador (max_player_hunger)
Retorna o nível máximo de fome.
```
{"placeholder":"max_player_hunger"}
```
Saída de exemplo: `20`

## Nível de Fome Atual do Jogador (Percentual) (current_player_hunger_percent)
Retorna a fome do jogador em porcentagem.
```
{"placeholder":"current_player_hunger_percent"}
```
Saída de exemplo: `100`

## Saturação de Fome Atual do Jogador (current_player_hunger_saturation)
Retorna o valor atual de saturação de fome do jogador.
```
{"placeholder":"current_player_hunger_saturation"}
```
Saída de exemplo: `5.0`

## Armadura Atual do Jogador (current_player_armor)
Retorna o valor atual de armadura do jogador.
```
{"placeholder":"current_player_armor"}
```
Saída de exemplo: `20`

## Resistência da Armadura do Jogador (player_armor_toughness)
Retorna o valor total de resistência da armadura do jogador.
```
{"placeholder":"player_armor_toughness"}
```
Saída de exemplo: `8.0`

## Armadura Máxima do Jogador (max_player_armor)
Retorna o valor máximo de armadura.
```
{"placeholder":"max_player_armor"}
```
Saída de exemplo: `20`

## Armadura Atual do Jogador (Percentual) (current_player_armor_percent)
Retorna a armadura do jogador em porcentagem.
```
{"placeholder":"current_player_armor_percent"}
```
Saída de exemplo: `100`

## Nível de Oxigênio Atual do Jogador (current_player_oxygen)
Retorna o nível atual de oxigênio do jogador (bolhas de ar).
```
{"placeholder":"current_player_oxygen"}
```
Saída de exemplo: `300`

## Nível Máximo de Oxigênio do Jogador (max_player_oxygen)
Retorna o nível máximo de oxigênio.
```
{"placeholder":"max_player_oxygen"}
```
Saída de exemplo: `300`

## Nível de Oxigênio Atual do Jogador (Percentual) (current_player_oxygen_percent)
Retorna o nível de oxigênio do jogador em porcentagem.
```
{"placeholder":"current_player_oxygen_percent"}
```
Saída de exemplo: `100`

## Nível Atual do Jogador (current_player_level)
Retorna o nível de experiência atual do jogador.
```
{"placeholder":"current_player_level"}
```
Saída de exemplo: `30`

## Experiência Atual do Jogador (current_player_exp)
Retorna a quantidade total de pontos de experiência do jogador.
```
{"placeholder":"current_player_exp"}
```
Saída de exemplo: `1250`

## Progresso de Experiência do Jogador (Percentual) (current_player_exp_progress)
Retorna o progresso da experiência do jogador até o próximo nível em porcentagem.
```
{"placeholder":"current_player_exp_progress"}
```
Saída de exemplo: `75`

## Força de Ataque do Jogador (Percentual) (player_attack_strength)
Retorna o tempo de recarga do ataque do jogador em porcentagem.
```
{"placeholder":"player_attack_strength"}
```
Saída de exemplo: `100`

## Modo de Jogo do Jogador (player_gamemode)
Retorna o modo de jogo atual do jogador.
```
{"placeholder":"player_gamemode"}
```
Saída de exemplo: `survival`

## Direção de Olhar do Jogador (player_view_direction)
Retorna a direção para a qual o jogador está olhando.
```
{"placeholder":"player_view_direction"}
```
Saída de exemplo: `north`

## Coordenada X do Jogador (player_x_coordinate)
Retorna a posição X do jogador no mundo.
```
{"placeholder":"player_x_coordinate"}
```
Saída de exemplo: `125`

## Coordenada Y do Jogador (player_y_coordinate)
Retorna a posição Y do jogador no mundo.
```
{"placeholder":"player_y_coordinate"}
```
Saída de exemplo: `64`

## Coordenada Z do Jogador (player_z_coordinate)
Retorna a posição Z do jogador no mundo.
```
{"placeholder":"player_z_coordinate"}
```
Saída de exemplo: `-250`

## Vida Atual da Montaria (current_mount_health)
Retorna a vida atual da entidade que o jogador está montando.
```
{"placeholder":"current_mount_health"}
```
Saída de exemplo: `30.0`

## Vida Máxima da Montaria (max_mount_health)
Retorna a vida máxima da entidade que o jogador está montando.
```
{"placeholder":"max_mount_health"}
```
Saída de exemplo: `30.0`

## Vida Atual da Montaria (Percentual) (current_mount_health_percent)
Retorna a vida da montaria em porcentagem.
```
{"placeholder":"current_mount_health_percent"}
```
Saída de exemplo: `100`

## Barra de Salto Atual da Montaria (Percentual) (current_mount_jump_meter)
Retorna o valor da barra de potência de salto da montaria.
```
{"placeholder":"current_mount_jump_meter"}
```
Saída de exemplo: `75`

## Vida Atual do Boss (Percentual) (current_boss_health)
Retorna a vida do boss ativo.
```
{"placeholder":"current_boss_health"}
```
Saída de exemplo: `150.0`

## Nome do Boss (boss_name)
Retorna o nome do boss ativo.
```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```
Saída de exemplo: `Ender Dragon`

## Quantidade de Bosses (boss_count)
Retorna o número de bosses ativos.
```
{"placeholder":"boss_count"}
```
Saída de exemplo: `1`

## Quantidade de Efeitos Ativos (effects_count)
Retorna o número de efeitos de poção ativos.
```
{"placeholder":"effects_count"}
```
Saída de exemplo: `3`

## Efeito Ativo (active_effect)
Retorna informações sobre um efeito ativo específico.
```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```
Saída de exemplo: `minecraft:speed`

## Slot Selecionado da Barra de Atalhos (active_hotbar_slot)
Retorna o slot atualmente selecionado da barra de atalhos (0-8).
```
{"placeholder":"active_hotbar_slot"}
```
Saída de exemplo: `4`

## Item do Slot (slot_item)
Retorna informações sobre um item em um slot específico do inventário.
```
{"placeholder":"slot_item","values":{"slot":"0"}}
```
Saída de exemplo: `minecraft:diamond_sword`

## Quantidade de Itens no Slot (slot_item_count)
Retorna o tamanho da pilha do item em um slot específico do inventário do jogador.
```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```
Saída de exemplo: `64`

## Durabilidade do Item no Slot (slot_item_durability)
Retorna informações de durabilidade do item em um slot específico do inventário do jogador.
```
{"placeholder":"slot_item_durability","values":{"slot":"0","format":"percentage"}}
```
Parâmetros:
- `slot`: Número do slot do inventário do jogador.
- `format`: `current`, `remaining`, `max`, `damage`, `percentage` ou `percent`.

Saída de exemplo: `87`

## Nome de Exibição do Item no Slot (slot_item_display_name_fm)
Retorna o nome de exibição do item em um slot específico como um componente de texto JSON. No modo espectador, os slots da barra de atalhos podem resolver nomes de itens do menu espectador, a menos que `ignore_spectator` seja `true`.
```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```
Saída de exemplo: `{"text":"Diamond Sword","color":"aqua"}`

## Quantidade de Itens no Inventário (inventory_item_count)
Retorna a quantidade total de um tipo de item no inventário do jogador. Se `item` estiver vazio, conta todas as pilhas de itens no inventário.
```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```
Saída de exemplo: `12`

## Quantidade de Fome Restaurada pelo Item do Slot do Inventário (inventory_slot_food_point_restore_amount)
Retorna os pontos de fome restaurados pelo item de comida no slot especificado do inventário do jogador.
```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```
Saída de exemplo: `4.0`

## Item do Inventário Sob o Cursor (hovered_inventory_item)
Retorna a chave do item atualmente sob o cursor em uma tela de inventário.
```
{"placeholder":"hovered_inventory_item"}
```
Saída de exemplo: `minecraft:apple`

## Tempo do Jogo no Mundo (game_time)
Retorna o contador atual de ticks do tempo no jogo.
```
{"placeholder":"game_time"}
```
Saída de exemplo: `18000`

## Hora do Dia no Mundo (world_daytime)
Retorna a hora atual do dia no mundo.
```
{"placeholder":"world_daytime"}
```
Saída de exemplo: `13000`

## Hora do Dia no Mundo (world_daytime_hour)
Retorna a parte da hora do tempo do mundo. Por padrão, isso usa o formato de 24 horas; defina `twelve_hour_format` como `"true"` para o formato de 12 horas.
```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```
Saída de exemplo: `12`

## Minuto da Hora do Dia no Mundo (world_daytime_minute)
Retorna a parte dos minutos do tempo do mundo (00-59).
```
{"placeholder":"world_daytime_minute"}
```
Saída de exemplo: `30`

## Dificuldade do Mundo (world_difficulty)
Retorna a dificuldade atual do mundo.
```
{"placeholder":"world_difficulty"}
```
Saída de exemplo: `normal`

## Seed do Mundo Atual (current_world_seed)
Retorna a seed do mundo singleplayer atual. Retorna um valor vazio quando a seed não estiver disponível.
```
{"placeholder":"current_world_seed"}
```
Saída de exemplo: `123456789`

## Bioma Atual (current_biome)
Retorna o bioma em que o jogador está no momento. Defina `as_key` como `"false"` para retornar um nome traduzido/exibido, quando disponível.
```
{"placeholder":"current_biome","values":{"as_key":"true"}}
```
Saída de exemplo: `minecraft:plains`

## Dimensão Atual (current_dimension)
Retorna a dimensão em que o jogador está no momento. Defina `as_key` como `"false"` para retornar um nome traduzido/exibido, quando disponível.
```
{"placeholder":"current_dimension","values":{"as_key":"true"}}
```
Saída de exemplo: `minecraft:overworld`

## Valor de Gamerule (gamerule_value)
Retorna o valor atual de uma gamerule no mundo/servidor carregado. Mundos em servidor exigem o FancyMenu no servidor.
```
{"placeholder":"gamerule_value","values":{"name":"doDaylightCycle"}}
```
Saída de exemplo: `true`

## Categoria do Item (item_category)
Retorna a categoria da aba criativa de um item. Defina `as_key` como `"true"` para retornar a chave da categoria em vez do nome exibido.
```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```
Saída de exemplo: `Combat`

## Título/Subtítulo Atual da HUD (current_title)
Retorna o texto do título atualmente exibido.
```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```
Saída de exemplo: `Game Over!`

## Mensagem da Barra de Ação (action_bar_message_fm)
Retorna a mensagem atual da barra de ação vanilla acima da barra de atalhos.
```
{"placeholder":"action_bar_message_fm"}
```
Saída de exemplo: `You may not rest now`

## Tempo da Mensagem da Barra de Ação (action_bar_message_time_fm)
Retorna por quantos ticks a mensagem atual da barra de ação vanilla ainda será exibida.
```
{"placeholder":"action_bar_message_time_fm"}
```
Saída de exemplo: `42`

## Rotação X da Câmera (camera_rotation_x_fm)
Retorna o pitch atual da câmera em graus.
```
{"placeholder":"camera_rotation_x_fm"}
```
Saída de exemplo: `12.5`

## Rotação Y da Câmera (camera_rotation_y_fm)
Retorna o yaw atual da câmera em graus.
```
{"placeholder":"camera_rotation_y_fm"}
```
Saída de exemplo: `-90.0`

## Variação X da Rotação da Câmera (camera_rotation_delta_x_fm)
Retorna a mudança por tick no pitch da câmera.
```
{"placeholder":"camera_rotation_delta_x_fm"}
```
Saída de exemplo: `0.4`

## Variação Y da Rotação da Câmera (camera_rotation_delta_y_fm)
Retorna a mudança por tick no yaw da câmera.
```
{"placeholder":"camera_rotation_delta_y_fm"}
```
Saída de exemplo: `-1.2`

## Tempo do Item Destacado (highlighted_item_time_fm)
Retorna por quantos ticks o nome do item destacado ainda será exibido acima da barra de atalhos.
```
{"placeholder":"highlighted_item_time_fm"}
```
Saída de exemplo: `30`

## Progresso de Uso do Item pelo Jogador (player_item_use_progress_fm)
Retorna o progresso atual de uso do item de `0.0` a `1.0`.
```
{"placeholder":"player_item_use_progress_fm"}
```
Saída de exemplo: `0.65`

## Variação X da Posição do Jogador (player_position_delta_x_fm)
Retorna a mudança por tick na posição do jogador no eixo X.
```
{"placeholder":"player_position_delta_x_fm"}
```
Saída de exemplo: `0.0`

## Variação Y da Posição do Jogador (player_position_delta_y_fm)
Retorna a mudança por tick na posição do jogador no eixo Y.
```
{"placeholder":"player_position_delta_y_fm"}
```
Saída de exemplo: `-0.08`

## Variação Z da Posição do Jogador (player_position_delta_z_fm)
Retorna a mudança por tick na posição do jogador no eixo Z.
```
{"placeholder":"player_position_delta_z_fm"}
```
Saída de exemplo: `0.12`

## IP Atual do Servidor (current_server_ip)
Retorna o IP do servidor conectado.
```
{"placeholder":"current_server_ip"}
```
Saída de exemplo: `mc.hypixel.net`

## Lista de Jogadores do Mundo (world_players_list)
Retorna uma lista de todos os jogadores atualmente no mundo.
```
{"placeholder":"world_players_list","values":{"separator":", "}}
```
Saída de exemplo: `Steve, Alex, Notch`

## MOTD do Servidor (servermotd)
Retorna a Message of the Day de um servidor.
```
{"placeholder":"servermotd","values":{"ip":"mc.hypixel.net","line":"1"}}
```
Saída de exemplo: `Welcome to Hypixel!`

## PING do Servidor (serverping)
Retorna o ping para um servidor em milissegundos.
```
{"placeholder":"serverping","values":{"ip":"mc.hypixel.net"}}
```
Saída de exemplo: `54`

## Quantidade de Jogadores no Servidor (serverplayercount)
Retorna a quantidade de jogadores de um servidor.
```
{"placeholder":"serverplayercount","values":{"ip":"mc.hypixel.net"}}
```
Saída de exemplo: `25000/30000`

## Status do Servidor (serverstatus)
Retorna o status online/offline de um servidor.
```
{"placeholder":"serverstatus","values":{"ip":"mc.hypixel.net"}}
```
Saída de exemplo: `§aOnline` ou `§cOffline`

## Versão do Servidor (serverversion)
Retorna a versão do Minecraft de um servidor.
```
{"placeholder":"serverversion","values":{"ip":"mc.hypixel.net"}}
```
Saída de exemplo: `1.19.2`

## Ano (realtimeyear)
Retorna o ano atual.
```
{"placeholder":"realtimeyear"}
```
Saída de exemplo: `2024`

## Mês (realtimemonth)
Retorna o mês atual (01-12).
```
{"placeholder":"realtimemonth"}
```
Saída de exemplo: `01`

## Dia (realtimeday)
Retorna o dia atual do mês (01-31).
```
{"placeholder":"realtimeday"}
```
Saída de exemplo: `27`

## Hora (realtimehour)
Retorna a hora atual. Por padrão, isso usa o formato de 24 horas; defina `twelve_hour_format` como `"true"` para o formato de 12 horas.
```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"system"}}
```
Saída de exemplo: `14`

## Minuto (realtimeminute)
Retorna o minuto atual (00-59).
```
{"placeholder":"realtimeminute"}
```
Saída de exemplo: `30`

## Segundo (realtimesecond)
Retorna o segundo atual (00-59).
```
{"placeholder":"realtimesecond"}
```
Saída de exemplo: `45`

## Tempo Atual em Milissegundos (Timestamp Unix) (unix_time)
Retorna o timestamp Unix atual em milissegundos.
```
{"placeholder":"unix_time"}
```
Saída de exemplo: `1716552478123`

> Os placeholders de tempo real (`realtimeyear`, `realtimemonth`, `realtimeday`, `realtimehour`, `realtimeminute`, `realtimesecond` e `unix_time`) suportam um valor `timezone`. Use IDs normais de fuso horário do Java, como `UTC`, `Europe/Berlin` ou `America/New_York`; omita-o ou use `system` para o fuso horário do sistema.
{.is-info}

## Informações da CPU (cpuinfo)
Retorna informações sobre a CPU.
```
{"placeholder":"cpuinfo"}
```
Saída de exemplo: `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`

## Uso da CPU (JVM) (jvmcpu)
Retorna o uso de CPU da JVM em porcentagem.
```
{"placeholder":"jvmcpu"}
```
Saída de exemplo: `25.5`

## Uso da CPU (SO) (oscpu)
Retorna o uso de CPU do sistema operacional em porcentagem.
```
{"placeholder":"oscpu"}
```
Saída de exemplo: `42.8`

## Informações da GPU (gpuinfo)
Retorna informações sobre a GPU.
```
{"placeholder":"gpuinfo"}
```
Saída de exemplo: `NVIDIA GeForce RTX 3080`

## Versão do Java (javaver)
Retorna a versão do Java.
```
{"placeholder":"javaver"}
```
Saída de exemplo: `17.0.2`

## Máquina Virtual Java (jvmname)
Retorna o nome da Java Virtual Machine.
```
{"placeholder":"jvmname"}
```
Saída de exemplo: `OpenJDK 64-Bit Server VM`

## Versão do OpenGL (glver)
Retorna a versão do OpenGL.
```
{"placeholder":"glver"}
```
Saída de exemplo: `4.6.0 NVIDIA 516.94`

## Nome do Sistema Operacional (osname)
Retorna o nome do sistema operacional.
```
{"placeholder":"osname"}
```
Saída de exemplo: `Windows 10`

## FPS (Frames Por Segundo) (fps)
Retorna os quadros por segundo atuais.
```
{"placeholder":"fps"}
```
Saída de exemplo: `120`

## RAM Usada em MB (usedram)
Retorna a quantidade de RAM atualmente em uso (MB).
```
{"placeholder":"usedram"}
```
Saída de exemplo: `4096`

## RAM Máxima em MB (maxram)
Retorna a quantidade máxima de RAM alocada (MB).
```
{"placeholder":"maxram"}
```
Saída de exemplo: `8192`

## RAM Usada em %% (percentram)
Retorna a porcentagem de RAM atualmente em uso.
```
{"placeholder":"percentram"}
```
Saída de exemplo: `50`

## Volume do Elemento de Áudio (audio_element_vol)
Retorna o volume de um elemento de áudio.
```
{"placeholder":"audio_element_vol","values":{"element_identifier":"background_music"}}
```
Saída de exemplo: `0.5`

## Faixa de Áudio Atual (audio_element_current_track)
Retorna o nome da faixa de um elemento de áudio.
```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"background_music","display_name_mappings":"track1.ogg=>Cool Track Name"}}
```
Saída de exemplo: `Cool Track Name`

## Duração do Áudio (audio_duration)
Retorna a duração total de uma faixa de áudio no formato MM:SS.
```
{"placeholder":"audio_duration","values":{"element_identifier":"background_music"}}
```
Saída de exemplo: `03:45`

## Tempo de Reprodução do Áudio (audio_playtime)
Retorna o tempo de reprodução atual de uma faixa de áudio. Defina `show_percentage` como `"true"` para obter um valor de progresso de 0 a 100 em vez de `MM:SS`.
```
{"placeholder":"audio_playtime","values":{"element_identifier":"background_music","show_percentage":"false"}}
```
Saída de exemplo: `01:30` (ou `45` quando `show_percentage` é `"true"`)

## Estado de Reprodução do Áudio (audio_playing_state)
Retorna se um elemento de áudio está reproduzindo (true/false).
```
{"placeholder":"audio_playing_state","values":{"element_identifier":"background_music"}}
```
Saída de exemplo: `true`

## Volume do Elemento de Vídeo (video_element_vol)
Retorna o nível de volume de um elemento de vídeo (0.0 a 1.0).
```
{"placeholder":"video_element_vol","values":{"element_identifier":"my_video_element"}}
```
Saída de exemplo: `0.5`

## Duração do Elemento de Vídeo (video_element_duration)
Retorna a duração total de um elemento de vídeo no formato `MM:SS`. Defina `output_as_timestamp` como `"true"` para retornar um timestamp em milissegundos.
```
{"placeholder":"video_element_duration","values":{"element_identifier":"my_video_element","output_as_timestamp":"false"}}
```
Saída de exemplo: `02:00` (ou `120000` quando `output_as_timestamp` é `"true"`)

## Tempo de Reprodução do Elemento de Vídeo (video_element_playtime)
Retorna o tempo de reprodução atual (progresso) de um elemento de vídeo no formato `MM:SS`. Defina `show_percentage` como `"true"` para um valor de progresso de 0 a 100, ou `output_as_timestamp` como `"true"` para milissegundos.
```
{"placeholder":"video_element_playtime","values":{"element_identifier":"my_video_element","show_percentage":"false","output_as_timestamp":"false"}}
```
Saída de exemplo: `00:45` (ou `38` como porcentagem, ou `45200` como timestamp)

## Estado de Pausa do Elemento de Vídeo (video_element_paused_state)
Retorna se um elemento de vídeo está pausado (true/false).
```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"my_video_element"}}
```
Saída de exemplo: `false`

## Volume do Fundo de Vídeo (video_background_vol)
Retorna o nível de volume de um fundo de menu em vídeo (0.0 a 1.0).
```
{"placeholder":"video_background_vol","values":{"background_identifier":"main_menu_video"}}
```
Saída de exemplo: `0.7`

## Duração do Fundo de Vídeo (video_background_duration)
Retorna a duração total de um fundo de menu em vídeo no formato `MM:SS`. Defina `output_as_timestamp` como `"true"` para retornar um timestamp em milissegundos.
```
{"placeholder":"video_background_duration","values":{"background_identifier":"main_menu_video","output_as_timestamp":"false"}}
```
Saída de exemplo: `03:00` (ou `180000` quando `output_as_timestamp` é `"true"`)

## Tempo de Reprodução do Fundo de Vídeo (video_background_playtime)
Retorna o tempo de reprodução atual (progresso) de um fundo de menu em vídeo no formato `MM:SS`. Defina `show_percentage` como `"true"` para um valor de progresso de 0 a 100, ou `output_as_timestamp` como `"true"` para milissegundos.
```
{"placeholder":"video_background_playtime","values":{"background_identifier":"main_menu_video","show_percentage":"false","output_as_timestamp":"false"}}
```
Saída de exemplo: `01:00` (ou `33` como porcentagem, ou `60500` como timestamp)

## Estado de Pausa do Fundo de Vídeo (video_background_paused_state)
Retorna se um fundo de menu em vídeo está pausado (true/false).
```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"main_menu_video"}}
```
Saída de exemplo: `true`

## Calculadora (calc)
O placeholder de calculadora é uma ferramenta poderosa que permite realizar cálculos matemáticos dentro dos seus layouts. Ele oferece suporte a uma ampla variedade de operações matemáticas e pode funcionar com números decimais e inteiros.

### Sintaxe Básica
```
{"placeholder":"calc","values":{"decimal":"true/false","expression":"sua_expressao"}}
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

## Número Aleatório (random_number)
Gera um número aleatório dentro de um intervalo especificado.
```
{"placeholder":"random_number","values":{"min":"1","max":"100"}}
```
Saída de exemplo: `42`

## Número Máximo (maxnum)
Retorna o maior de dois números.
```
{"placeholder":"maxnum","values":{"first":"10","second":"20"}}
```
Saída de exemplo: `20`

## Número Mínimo (minnum)
Retorna o menor de dois números.
```
{"placeholder":"minnum","values":{"first":"10","second":"20"}}
```
Saída de exemplo: `10`

## Número Absoluto (absnum)
Retorna o valor absoluto de um número.
```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```
Saída de exemplo: `10.5`

## Negar Número (negnum)
Retorna o valor negado de um número.
```
{"placeholder":"negnum","values":{"num":"10.5"}}
```
Saída de exemplo: `-10.5`

## *pi* (Matemática) (math_pi)
Retorna o valor de π.
```
{"placeholder":"math_pi"}
```
Saída de exemplo: `3.141592653589793`

## Seno Trigonométrico (Matemática) (math_sin)
Retorna o seno de um ângulo.
```
{"placeholder":"math_sin","values":{"angle":"45"}}
```
Saída de exemplo: `0.7071067811865476`

## Cosseno Trigonométrico (Matemática) (math_cos)
Retorna o cosseno de um ângulo.
```
{"placeholder":"math_cos","values":{"angle":"45"}}
```
Saída de exemplo: `0.7071067811865476`

## Tangente Trigonométrica (Matemática) (math_tan)
Retorna a tangente de um ângulo.
```
{"placeholder":"math_tan","values":{"angle":"45"}}
```
Saída de exemplo: `1.0`

## Floor (Matemática) (math_floor)
Arredonda um número para baixo até o inteiro mais próximo.
```
{"placeholder":"math_floor","values":{"num":"3.14"}}
```
Saída de exemplo: `3`

## Ceiling (Matemática) (math_ceil)
Arredonda um número para cima até o inteiro mais próximo.
```
{"placeholder":"math_ceil","values":{"num":"3.14"}}
```
Saída de exemplo: `4`

## Round (Matemática) (math_round)
Arredonda um número. Por padrão, arredonda para o inteiro mais próximo; defina `decimals` como um número não negativo para arredondar para essa quantidade de casas decimais.
```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```
Saída de exemplo: `3.14` (com `decimals:-1` ou omitido → `3`)

## Sinal (Matemática) (math_sign)
Retorna o sinal de um número (1 para positivo, -1 para negativo, 0 para zero).
```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```
Saída de exemplo: `-1`

## Seno Hiperbólico (Matemática) (math_sinh)
Retorna o seno hiperbólico de um ângulo.
```
{"placeholder":"math_sinh","values":{"angle":"1"}}
```
Saída de exemplo: `1.1752011936438014`

## Cosseno Hiperbólico (Matemática) (math_cosh)
Retorna o cosseno hiperbólico de um ângulo.
```
{"placeholder":"math_cosh","values":{"angle":"1"}}
```
Saída de exemplo: `1.5430806348152437`

## Tangente Hiperbólica (Matemática) (math_tanh)
Retorna a tangente hiperbólica de um ângulo.
```
{"placeholder":"math_tanh","values":{"angle":"1"}}
```
Saída de exemplo: `0.7615941559557649`

## Dividir Texto (split_text)
Divide o texto usando um delimitador especificado.
```
{"placeholder":"split_text","values":{"input":"hello,world","regex":",","max_parts":"2","split_index":"1"}}
```
Saída de exemplo: `world`

## Aparar Texto (trim_text)
Remove espaços em branco do início e do fim.
```
{"placeholder":"trim_text","values":{"text":"  hello world  "}}
```
Saída de exemplo: `hello world`

## Recortar Texto (crop_text)
Remove caracteres do início e do fim do texto.
```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```
Saída de exemplo: `ello worl`

## Transformar em String (stringify)
Converte um texto em string escapando todos os caracteres de sintaxe.
```
{"placeholder":"stringify","values":{"text":"text with {special} \"characters\""}}
```
Saída de exemplo: `text with \{special\} \"characters\"`

## Localizar Texto (local)
Recupera texto localizado para uma chave.
```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```
Saída de exemplo: `Singleplayer`

## Texto da Web (webtext)
Recupera o conteúdo de texto de uma URL da web.
```
{"placeholder":"webtext","values":{"link":"http://somewebsite.com/textfile.txt"}}
```
Saída de exemplo: Conteúdo de texto da URL

## Texto Aleatório (randomtext)
Retorna uma linha aleatória de um arquivo de texto, URL ou texto simples direto. O texto muda em intervalos especificados.
```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/<file_name.txt>","interval":"10"}}
```
Parâmetros:
- `source`: A origem das linhas de texto (substitui o antigo parâmetro `path`)
  - Caminho do arquivo: `/config/fancymenu/assets/quotes.txt`
  - URL: `https://example.com/quotes.txt`
  - Texto simples: `Linha 1\nLinha 2\nLinha 3`
- `interval`: Tempo em segundos entre as mudanças de texto

O placeholder agora oferece suporte a três tipos de origem:
1. **Arquivos locais**: Arquivos de texto do diretório do jogo
   ```
   {"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/quotes.txt","interval":"10"}}
   ```
2. **URLs**: Arquivos de texto remotos da internet
   ```
   {"placeholder":"randomtext","values":{"source":"https://example.com/quotes.txt","interval":"10"}}
   ```
3. **Texto simples**: Entrada de texto direta com linhas separadas por `\n`
   ```
   {"placeholder":"randomtext","values":{"source":"Primeira linha\nSegunda linha\nTerceira linha","interval":"5"}}
   ```

Observação: placeholders antigos usando `path` em vez de `source` continuarão funcionando.

## Analisador JSON (json)
Analisa dados JSON de um arquivo, URL ou conteúdo JSON direto e extrai valores usando expressões de caminho JSON.
```
{"placeholder":"json","values":{"source":"path_or_link_or_json_content","json_path":"$.some.json.path"}}
```
Parâmetros:
- `source`: A origem dos dados JSON
  - Caminho do arquivo: `/config/fancymenu/assets/data.json`
  - URL: `https://api.example.com/data.json`
  - JSON direto: `{"name":"Steve","level":42}`
- `json_path`: A expressão de caminho JSON para extrair os dados

O placeholder agora oferece suporte a três tipos de origem:
1. **Arquivos locais**: Arquivos JSON do diretório do jogo
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
- `$.items[0].id` - Obtém o "id" do primeiro item em uma matriz
- `$.scores.*` - Obtém todos os valores do objeto "scores"

## Caminho Absoluto de Arquivo/Pasta (absolute_path)
Retorna o caminho absoluto de um arquivo.
```
{"placeholder":"absolute_path","values":{"short_path":"relative/path/to/file.txt"}}
```
Saída de exemplo: `C:/Users/Username/AppData/Roaming/.minecraft/relative/path/to/file.txt`

## Contagem de Caracteres do Texto (text_character_count)
Retorna o número de caracteres no texto fornecido.
```
{"placeholder":"text_character_count","values":{"text":"Hello World!"}}
```
Saída de exemplo: `12`

## Largura do Texto (text_width)
Retorna a largura em pixels do texto fornecido quando renderizado.
```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```
Saída de exemplo: `66`

## Texto em Maiúsculas (uppercase_text)
Converte o texto de entrada para letras maiúsculas.
```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```
Saída de exemplo: `HELLO WORLD`

## Texto em Minúsculas (lowercase_text)
Converte o texto de entrada para letras minúsculas.
```
{"placeholder":"lowercase_text","values":{"text":"Hello World"}}
```
Saída de exemplo: `hello world`

## Texto em Title Case (title_case_text)
Converte o texto de entrada para title case.
```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```
Saída de exemplo: `Hello World`

## Texto em Sentence Case (sentence_case_text)
Converte o texto de entrada para sentence case.
```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```
Saída de exemplo: `Hello world. This is fancymenu!`

## Texto em Snake Case (snake_case_text)
Converte o texto de entrada para `snake_case`.
```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```
Saída de exemplo: `hello_world`

## Texto em Kebab Case (kebab_case_text)
Converte o texto de entrada para `kebab-case`.
```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```
Saída de exemplo: `hello-world`

## Texto em Case Alternado (alternating_case_text)
Converte o texto de entrada para case alternado.
```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```
Saída de exemplo: `aLtErNaTiNg CaSe`

## Alternar Caso do Texto (toggle_case_text)
Alterna o caso de cada letra no texto de entrada.
```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```
Saída de exemplo: `tOGGLE cASE`

## Codificar para Base64 (base64_encode)
Codifica o texto fornecido como Base64.
```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```
Saída de exemplo: `SGVsbG8gV29ybGQ=`

## Decodificar de Base64 (base64_decode)
Decodifica uma string Base64 de volta para texto simples.
```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```
Saída de exemplo: `Hello World`

## Texto do Arquivo (file_text)
Retorna linhas de texto de um arquivo ou URL. Pode retornar todas as linhas ou apenas as últimas X linhas.
```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/some_file.txt","mode":"all","separator":"\n","last_lines":"1"}}
```
Parâmetros:
- `path_or_url`: Caminho do arquivo ou URL de onde ler
- `mode`: Pode ser `"all"` (retorna todas as linhas) ou `"last"` (retorna apenas as últimas X linhas)
- `separator`: Texto usado para juntar as linhas (padrão: `"\n"`)
- `last_lines`: Número de linhas a retornar quando o modo é `"last"` (padrão: `"1"`)

Saída de exemplo: Depende do conteúdo do arquivo

## Conteúdo da Área de Transferência (clipboard_content)
Retorna o conteúdo de texto atualmente armazenado na área de transferência do sistema.
```
{"placeholder":"clipboard_content"}
```
Saída de exemplo: Qualquer texto que esteja atualmente na área de transferência

## Substituir Texto (replace_text)
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

Saída de exemplo: `Hello FancyMenu! This is a test.`

## Switch Case (switch_case)
Executa uma operação switch-case com base em um valor.
```
{"placeholder":"switch_case","values":{"value":"1","cases":"1:first case,2:second case,3:third case","default":"default case"}}
```
Saída de exemplo: `first case` (se o valor for 1)

## Obter Valor de Variável (Variável FM) (getvariable)
Recupera o valor de uma variável armazenada anteriormente.
```
{"placeholder":"getvariable","values":{"name":"some_variable"}}
```
Saída de exemplo: Depende do valor armazenado

## Obter Dados NBT (nbt_data_get)
Recupera dados NBT no cliente (semelhante ao comando `/data get`). Use a variante do servidor `nbt_data_get_server` ao se conectar a um servidor e precisar de valores autoritativos do lado do servidor.
```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```
Parâmetros:
- `source_type`: `"entity"` ou `"block"`
- `entity_selector`: Seletor de entidade como `@s`, `@p`, `@e`, ou UUID/nome (para entidades)
- `block_pos`: Posição do bloco no formato `"x y z"` (para blocos)
- `nbt_path`: O caminho NBT a ser recuperado
- `scale`: Fator de escala opcional para valores numéricos (padrão: `"1.0"`)
- `return_type`: Como retornar os dados:
  - `"value"`: Padrão, retorna o valor (com escala opcional para números)
  - `"string"`: Retorna os dados NBT reais como string
  - `"snbt"`: Retorna como SNBT (NBT formatado)
  - `"json"`: Retorna como componente formatado em JSON (para tags compostas)

Saída de exemplo: `20` (para nível de fome)

## Obter Dados NBT (Lado do Servidor) (nbt_data_get_server)
Consulta dados NBT do lado do servidor (usando um pacote) e armazena os resultados em cache por um curto período. Os valores espelham o placeholder do lado do cliente.
```
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","block_pos":"","storage_id":"minecraft:storage_key","nbt_path":"SelectedItem.id","scale":"1.0","return_type":"value"}}
```
Saída de exemplo: `minecraft:diamond_sword`

## Última Mensagem de Morte (lastdeathmessage)
Retorna a última mensagem de morte registrada do jogador cliente. Defina `as_json_component` como `"true"` para obter o componente de texto JSON bruto.
```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```
Saída de exemplo: `Steve was slain by Zombie`

## Duração de Uptime (uptime_duration)
Retorna há quanto tempo o FancyMenu foi carregado. Por padrão, o valor está em segundos; defina `output_as_millis` como `"true"` para receber milissegundos.
```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```
Saída de exemplo: `742` (segundos desde o carregamento)

## Nomes de Saves de Mundos (level_save_names)
Lista todos os nomes de saves de mundos locais unidos pelo separador escolhido. Executa na thread do cliente.
```
{"placeholder":"level_save_names","values":{"separator":", "}}
```
Saída de exemplo: `Creative Test, Survival World, Hardcore`

## Dados de Save do Mundo (level_save_data)
Retorna os dados serializados do nível para o nome do mundo fornecido (deve corresponder ao nome exibido na lista de saves).
```
{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}
```
Saída de exemplo: `{"name":"Survival World","gameMode":"survival",...}`

## Conversor de Base Numérica (number_base_convert)
Converte um número (inteiro ou fracionário) de uma base para outra (2–36). Usa decimal por padrão se as bases não forem fornecidas.
```
{"placeholder":"number_base_convert","values":{"input":"67.5","from_base":"10","to_base":"16"}}
```
Saída de exemplo: `43.8`

## Tamanho do Arquivo (file_size)
Retorna o tamanho de um arquivo local em bytes. Apenas caminhos locais são permitidos.
```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Saída de exemplo: `1284`

## MD5 do Arquivo (file_md5)
Retorna o hash MD5 de um arquivo local como uma string hexadecimal em minúsculas.
```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/notes.txt"}}
```
Saída de exemplo: `d41d8cd98f00b204e9800998ecf8427e`

# Exemplos Práticos

## Criando uma Exibição Dinâmica de Memória
```
RAM usada: {"placeholder":"usedram"}MB / {"placeholder":"maxram"}MB ({"placeholder":"percentram"}%)
```

## Criando um Relógio em Tempo Real
```
{"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}:{"placeholder":"realtimesecond"}
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

1. **Faça Cache de Operações Caras**: Alguns placeholders (como os que leem informações do sistema) podem consumir muitos recursos. Considere usar variáveis para armazenar seus valores se precisar usá-los várias vezes.

2. **Use Configurações Apropriadas de Decimais**: Ao trabalhar com cálculos, use o parâmetro `decimal` de forma adequada. Defina como `false` quando precisar de inteiros e como `true` quando precisar de valores decimais precisos.

3. **Trate Valores Ausentes**: Sempre considere o que deve acontecer se um placeholder não retornar valor. Talvez seja interessante fornecer valores padrão nesses casos.

4. **Teste o Desempenho**: Ao usar muitos placeholders ou estruturas aninhadas complexas, teste o impacto no desempenho, especialmente em sistemas mais fracos.

5. **Use Dimensionamento/Posicionamento Avançado**: Para elementos de UI dinâmicos, combine placeholders com dimensionamento e posicionamento avançados para criar layouts responsivos.

6. **Combine com Variáveis**: Use placeholders junto com variáveis para conteúdo ainda mais dinâmico, que pode ser atualizado por meio de ações.

# Problemas Comuns e Soluções

## Placeholder Não Atualiza
Se o valor de um placeholder não estiver atualizando como esperado, verifique:
- Se o placeholder está formatado corretamente
- Se você está usando a capitalização correta para os IDs dos placeholders
- Se o placeholder exige condições específicas para atualizar

## Placeholders Aninhados Não Funcionam
Ao aninhar placeholders:
- Garanta o escape correto das aspas
- Verifique se cada placeholder aninhado é válido por si só

## Problemas de Desempenho
Se você notar problemas de desempenho:
- Reduza a quantidade de placeholders usados
- Evite aninhamento desnecessário
- Considere usar variáveis para valores acessados com frequência
- Use o placeholder adequado para suas necessidades (por exemplo, não use placeholders em tempo real quando valores estáticos forem suficientes)
