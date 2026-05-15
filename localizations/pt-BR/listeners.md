---
title: Listeners
description: Como criar e usar listeners no FancyMenu.
---

# Listeners

A partir do FancyMenu v3.8.0, há um novo recurso chamado "listeners".

Listeners executam scripts de ação quando eventos específicos do cliente ou da jogabilidade acontecem.
Eles podem expor variáveis para ações, placeholders e requisitos aninhados no listener.

Diferente da maioria das coisas no FancyMenu, os listeners não ficam presos a uma tela ou overlay. Eles rodam continuamente em segundo plano, aguardando seus eventos. Assim que um listener é disparado, ele executa seu script de ação, mesmo que não haja nenhuma tela aberta naquele momento.

# Usando Listeners

Para criar um novo listener que escuta um evento e executa um script de ação, clique em **barra de menu -> Personalização -> Gerenciar Listeners** enquanto **NÃO** estiver no editor de layout. Lá você encontra uma interface fácil de usar para criar e gerenciar listeners.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Gerenciar listeners" style="max-width:800px;width:100%;height:auto;">

# Variáveis do Listener

Os listeners geralmente expõem um tipo especial de variável para suas ações, requisitos e placeholders aninhados.
Essas variáveis podem ser acessadas como placeholders (na prática, elas são placeholders).

Você usa essas variáveis simplesmente utilizando seus nomes com o prefixo `$$` em campos de texto, de forma parecida com um placeholder normal.

Por exemplo, se você usar o listener **On Keyboard Key Pressed** e quiser imprimir o nome da tecla no log por meio da ação **Print to Log**, você usaria algo como `Key pressed! The key is: $$key_name` como entrada para a mensagem que a ação deve imprimir. Mais tarde, o placeholder da variável será substituído pelo nome real da tecla.

> Embora sejam chamadas de "variáveis", elas não têm nenhuma relação com o sistema normal de [variáveis](/variables) do FancyMenu. Você não pode definir essas variáveis, pois elas são **somente leitura**. Você também não pode usar ações, requisitos e placeholders feitos para o sistema de variáveis do FancyMenu com essas variáveis especiais de listener, então usar **Get Variable Value [FM Variable]**, **Is Variable Value [FM Variable]** ou **Set Variable Value [FM Variable]** não funcionará para variáveis de listener.
{.is-warning}

# Listeners em Detalhe

Esta lista deve incluir a maioria, se não todos, os listeners do FancyMenu. É possível que a lista nem sempre esteja atualizada devido a atualizações do mod.

## On Markdown Text Clicked
- Dispara quando um texto Markdown com um evento `click:` é clicado, por exemplo `[Open](click:open_menu)`.
- Variáveis:
  - `$$text_event_id` – ID do evento do link Markdown

## On Markdown Text Hovered
- Dispara quando um texto Markdown com um evento `hover:` é posicionado com o mouse, por exemplo `[Hint](hover:show_hint)`.
- Variáveis:
  - `$$text_event_id` – ID do evento do link Markdown

## On ZIP Extracted via Action
- Dispara quando a ação **Extract ZIP File In Game Directory** é concluída.
- Variáveis:
  - `$$source_zip_path` – caminho de origem do ZIP resolvido
  - `$$target_folder_path` – caminho de destino da extração resolvido
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – texto do erro quando a extração falhou

## On Element Spawned
- Dispara quando um elemento é gerado por meio de um fluxo de ação/script de geração de elemento.
- Variáveis:
  - `$$element_type` – tipo do elemento gerado
  - `$$element_identifier` – identificador do elemento gerado
  - `$$target_screen` – identificador da tela de destino

## On Animated Texture Started Playing
- Dispara quando uma textura animada começa a tocar.
- Variáveis:
  - `$$texture_source` – origem da textura
  - `$$texture_source_type` – tipo da origem
  - `$$texture_will_restart` – true/false

## On Animated Texture Finished Playing
- Dispara quando uma textura animada termina de tocar.
- Variáveis:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## On Video Playback Status Changed
- Dispara quando um elemento de vídeo ou o plano de fundo de vídeo de um menu muda o status de reprodução.
- Variáveis:
  - `$$video_source` – origem do vídeo
  - `$$video_source_type` – tipo da origem
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` ou `FINISHED`

## On System Message Received in Chat
- Dispara quando o cliente recebe uma mensagem de chat do sistema, como retorno de comando.
- Variáveis:
  - `$$system_message_string` – mensagem em texto simples
  - `$$system_message_component` – componente JSON

## On FM Data Received
- Dispara quando um servidor envia FM Data para este cliente via `/fmdata send`.
- Variáveis:
  - `$$data_identifier` – string identificadora dos dados
  - `$$data` – payload dos dados
  - `$$sent_by` – IP do servidor ou `integrated_server`

## On Remote Server Connected
- Dispara quando o FancyMenu inicializa uma conexão com servidor remoto.
- Variáveis:
  - `$$request_id` – ID da solicitação em cache
  - `$$remote_server_url` – URL do servidor remoto

## On Remote Server Data Received
- Dispara quando dados de texto são recebidos de um servidor remoto conectado.
- Variáveis:
  - `$$request_id` – ID da solicitação
  - `$$remote_server_url` – URL do servidor remoto
  - `$$data` – payload recebido

## On Remote Server Connection Closed
- Dispara quando uma conexão com servidor remoto é fechada.
- Variáveis:
  - `$$request_id` – ID da solicitação
  - `$$remote_server_url` – URL do servidor remoto
  - `$$intentionally_closed` – TRUE se foi fechado por uma ação
  - `$$crashed` – TRUE se a conexão falhou inesperadamente
  - `$$unknown_close_reason` – TRUE se não havia um motivo conhecido para o fechamento

## On Keyboard Key Pressed
- Dispara sempre que uma tecla é pressionada (repete enquanto mantida; funciona em telas e no jogo).
- Variáveis:
  - `$$key_name` – nome exibido da tecla
  - `$$key_keycode` – código da tecla GLFW
  - `$$key_scancode` – código de varredura GLFW
  - `$$key_modifiers` – máscara de bits dos modificadores ativos

## On Keyboard Key Released
- Dispara quando uma tecla é solta (telas e no jogo).
- Variáveis:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## On Keyboard Character Typed in Screen
- Dispara quando um caractere é digitado enquanto uma tela está aberta.
- Variáveis:
  - `$$char` – caractere digitado

## On Mouse Moved in Screen
- Dispara sempre que o mouse se move enquanto uma tela está aberta.
- Variáveis:
  - `$$mouse_pos_x` – X atual
  - `$$mouse_pos_y` – Y atual
  - `$$mouse_move_delta_x` – delta de X desde o último evento
  - `$$mouse_move_delta_y` – delta de Y desde o último evento

## On Mouse Button Clicked
- Dispara quando um botão do mouse é pressionado (telas e no jogo).
- Variáveis:
  - `$$button` – esquerdo/direito/meio
  - `$$mouse_pos_x` – X atual
  - `$$mouse_pos_y` – Y atual

## On Mouse Button Released
- Dispara quando um botão do mouse é solto (telas e no jogo).
- Variáveis:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## On Mouse Scrolled in Screen
- Dispara quando a roda do mouse é rolada enquanto uma tela está aberta.
- Variáveis:
  - `$$scroll_delta_y` – quantidade de rolagem vertical

## On Screen Opened
- Executa logo após qualquer tela se tornar ativa; pode ser usado para substituí-la.
- Variáveis:
  - `$$screen_identifier` – identificador da tela aberta

## On Screen Closed
- Executa imediatamente após uma tela ser fechada.
- Variáveis:
  - `$$screen_identifier` – identificador da tela fechada

## On Quit Minecraft
- Dispara uma vez quando o cliente começa a encerrar.
- Variáveis:
  - `$$timestamp_millis` – epoch em milissegundos no momento de sair
  - `$$timestamp_iso` – timestamp ISO-8601 do momento de saída

## On Death
- Executa quando a tela de morte padrão é aberta para o jogador local.
- Variáveis:
  - `$$days_survived` – dias desde a última morte
  - `$$death_reason_string` – causa em texto simples
  - `$$death_reason_component` – causa como componente JSON
  - `$$death_pos_x` – coordenada X da morte
  - `$$death_pos_y` – coordenada Y da morte
  - `$$death_pos_z` – coordenada Z da morte

## On Variable Updated [FM Variable]
- Dispara sempre que uma variável do FancyMenu é definida/atualizada.
- Variáveis:
  - `$$var_name` – nome da variável
  - `$$old_value` – valor anterior
  - `$$new_value` – novo valor

## On File Downloaded via Action
- Dispara após a ação “Download File to Game Directory” ser concluída.
- Variáveis:
  - `$$download_url` – origem do download
  - `$$target_file_path` – caminho do arquivo salvo
  - `$$download_succeeded` – true/false

## On File Selected
- Dispara após a ação “Select File” ser concluída.
- Variáveis:
  - `$$selected_file_path` – caminho absoluto do arquivo escolhido ou vazio se cancelado
  - `$$target_file_path` – caminho resolvido dentro da instância
  - `$$selection_succeeded` – true se a cópia foi bem-sucedida
  - `$$selection_cancelled` – true se a janela foi fechada
  - `$$failure_reason` – informações do erro em caso de falha

## On Chat Message Received
- Dispara quando uma linha normal de chat de jogador aparece no cliente.
- Variáveis:
  - `$$chat_message_string` – linha em texto simples
  - `$$chat_message_component` – componente JSON completo
  - `$$sender_uuid` – UUID do remetente ou ERROR
  - `$$sender_name` – nome do remetente ou ERROR

## On Chat Message Sent
- Dispara quando o jogador local envia uma mensagem de chat.
- Variáveis:
  - `$$chat_message_string` – linha em texto simples
  - `$$chat_message_component` – componente JSON completo

## On Effect Gained
- Dispara quando o jogador ganha um efeito de status.
- Variáveis:
  - `$$effect_key` – localização de recurso do efeito
  - `$$effect_type` – positivo/negativo/neutro
  - `$$effect_duration` – ticks restantes

## On Effect Lost
- Dispara quando o jogador perde um efeito de status.
- Variáveis:
  - `$$effect_key` – efeito expirado
  - `$$effect_type` – categoria

## On Experience Changed
- Dispara sempre que a experiência total do jogador muda.
- Variáveis:
  - `$$new_experience_amount` – após a mudança
  - `$$old_experience_amount` – antes da mudança
  - `$$is_level_up` – TRUE se o nível aumentou

## On Damage Taken
- Dispara uma vez por golpe quando o jogador recebe dano.
- Variáveis:
  - `$$damage_amount` – saúde removida
  - `$$damage_type` – localização de recurso do tipo de dano
  - `$$is_fatal_damage` – TRUE se for letal
  - `$$damage_source` – localização de recurso do atacante ou NONE

## On Started Freezing
- Dispara quando o jogador começa a congelar.
- Variáveis:
  - `$$freezing_intensity` – 0.0 nenhum, 1.0 totalmente congelado

## On Stopped Freezing
- Dispara quando o jogador para de congelar.
- Variáveis:
  - (nenhuma)

## On Fully Frozen
- Dispara uma vez quando o jogador fica totalmente congelado.
- Variáveis:
  - (nenhuma)

## On Start Looking At Block
- Dispara uma vez quando a mira passa a apontar para um bloco pela primeira vez (distância máxima de 20 blocos).
- Variáveis:
  - `$$block_key` – bloco alvo
  - `$$block_pos_x` – X do bloco
  - `$$block_pos_y` – Y do bloco
  - `$$block_pos_z` – Z do bloco
  - `$$distance_to_player` – dos olhos até a posição de acerto

## On Stop Looking At Block
- Dispara quando a mira deixa de apontar para um bloco (relata o último bloco alvo, máximo de 20 blocos).
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## On Start Looking At Entity
- Dispara uma vez quando a mira passa a apontar para uma entidade pela primeira vez (máximo de 20 blocos).
- Variáveis:
  - `$$entity_key` – tipo da entidade alvo
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Stop Looking At Entity
- Dispara quando a mira deixa de apontar para uma entidade (relata a última entidade alvo, máximo de 20 blocos).
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Spawned
- **Requer o FancyMenu no servidor.** Dispara quando qualquer entidade é gerada em qualquer lugar no mundo/servidor conectado.
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player` – −1 se estiver em outra dimensão
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## On Entity Died
- **Requer o FancyMenu no servidor.** Dispara quando qualquer entidade morre no mundo/servidor conectado.
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player` – −1 se estiver em outra dimensão
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$damage_type`
  - `$$is_same_dimension_as_player`
  - `$$entity_killed_by_name`
  - `$$entity_killed_by_key`
  - `$$entity_killed_by_uuid`

## On Entity Starts Being In Sight
- Dispara quando uma entidade se torna visível pela primeira vez dentro de 200 blocos.
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Stops Being In Sight
- Dispara quando uma entidade anteriormente visível sai da vista ou fica além de 200 blocos.
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Interacted With Entity
- Dispara quando o jogador interage com sucesso com uma entidade.
- Variáveis:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Mounted
- Dispara quando o jogador começa a montar uma entidade.
- Variáveis:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Entity Unmounted
- Dispara quando o jogador para de montar a entidade atual.
- Variáveis:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## On Block Broke
- Dispara quando o jogador quebra um bloco.
- Variáveis:
  - `$$block_key`
  - `$$broke_with_item_key` – ferramenta usada ou EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Block Placed
- Dispara quando o jogador coloca um bloco.
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Interacted With Block
- Dispara quando o jogador interage com sucesso com um bloco.
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Stepping On Block
- Dispara quando o jogador pisa sobre um bloco.
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## On Enter Biome
- Dispara quando o jogador entra em um novo bioma.
- Variáveis:
  - `$$biome_key` – bioma acessado

## On Leave Biome
- Dispara quando o jogador sai do bioma atual.
- Variáveis:
  - `$$biome_key` – bioma recém-saído

## On Enter Structure
- **Requer o FancyMenu no servidor.** Detecção grosseira de área de estrutura; pode disparar perto/acima/abaixo da estrutura.
- Variáveis:
  - `$$structure_key` – estrutura acessada

## On Leave Structure
- **Requer o FancyMenu no servidor.** Detecção grosseira; pode disparar perto da área ocupada pela estrutura.
- Variáveis:
  - `$$structure_key` – estrutura recém-saída

## On Enter Structure (High Precision)
- **Requer o FancyMenu no servidor.** Dispara quando o jogador entra nas caixas delimitadoras da estrutura.
- Variáveis:
  - `$$structure_key`

## On Leave Structure (High Precision)
- **Requer o FancyMenu no servidor.** Dispara após o jogador sair das caixas delimitadoras da estrutura.
- Variáveis:
  - `$$structure_key`

## On Dimension Entered
- Dispara quando o jogador entra em uma nova dimensão.
- Variáveis:
  - `$$dimension_key` – dimensão acessada

## On Start Swimming
- Dispara quando o jogador começa a nadar.
- Variáveis:
  - `$$fluid_type` – localização de recurso do fluido

## On Stop Swimming
- Dispara quando o jogador para de nadar.
- Variáveis:
  - `$$fluid_type` – fluido onde a natação parou

## On Start Touching Fluid
- Dispara quando o jogador começa a tocar um fluido.
- Variáveis:
  - `$$fluid_type` – fluido tocado

## On Stop Touching Fluid
- Dispara quando o jogador para de tocar um fluido.
- Variáveis:
  - `$$fluid_type` – fluido que deixou de ser tocado

## On Music Track Started
- Dispara quando uma nova faixa de música começa.
- Variáveis:
  - `$$track_resource_location` – arquivo de áudio
  - `$$track_display_name` – nome legível ou UNKNOWN
  - `$$track_artist` – artista ou UNKNOWN
  - `$$track_duration_ms` – milissegundos (0 se desconhecido)

## On Music Track Stopped
- Dispara quando a faixa de música atual termina ou é substituída.
- Variáveis:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## On World Sound Triggered
- Dispara quando um som posicional do mundo começa perto do jogador.
- Variáveis:
  - `$$sound_resource_location` – arquivo de som
  - `$$sound_display_name` – nome da legenda quando disponível
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – graus 0–360 em relação à direção para a qual o jogador está virado

## On Weather Changed
- Dispara quando o clima muda globalmente ou localmente (mudança de bioma ou entrar em local coberto pode disparar novamente).
- Variáveis:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE se a neve é renderizada
  - `$$weather_can_rain` – TRUE se a chuva é renderizada

## On Started Burning
- Dispara quando o jogador começa a queimar.
- Variáveis:
  - (nenhuma)

## On Stopped Burning
- Dispara quando o jogador para de queimar.
- Variáveis:
  - (nenhuma)

## On Started Drowning
- Dispara quando o jogador começa a sofrer dano por afogamento.
- Variáveis:
  - (nenhuma)

## On Position Changed
- Dispara sempre que a posição em blocos do jogador muda.
- Variáveis:
  - `$$old_pos_x` – X anterior em blocos
  - `$$old_pos_y` – Y anterior em blocos
  - `$$old_pos_z` – Z anterior em blocos
  - `$$new_pos_x` – novo X em blocos
  - `$$new_pos_y` – novo Y em blocos
  - `$$new_pos_z` – novo Z em blocos

## On Started Running
- Dispara quando o jogador começa a correr.
- Variáveis:
  - (nenhuma)

## On Stopped Running
- Dispara quando o jogador para de correr.
- Variáveis:
  - (nenhuma)

## On Jump
- Dispara sempre que o jogador pula.
- Variáveis:
  - (nenhuma)

## On Server Joined
- Dispara após entrar com sucesso em um servidor multiplayer.
- Variáveis:
  - `$$server_ip` – endereço do servidor acessado

## On Server Left
- Dispara após desconectar de um servidor multiplayer.
- Variáveis:
  - `$$server_ip` – endereço do servidor deixado

## Singleplayer World Entered
- Dispara após um mundo singleplayer terminar de carregar e o controle ser devolvido.
- Variáveis:
  - `$$world_name` – nome exibido
  - `$$world_save_path` – pasta de salvamento absoluta
  - `$$world_difficulty` – chave de dificuldade
  - `$$world_cheats_allowed` – TRUE se cheats estiverem habilitados
  - `$$world_icon_path` – caminho absoluto do ícone
  - `$$world_is_first_join` – TRUE na primeira visita

## Singleplayer World Left
- Dispara após um mundo singleplayer ser fechado e terminar de salvar.
- Variáveis:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## On Other Player Joined World/Server
- Dispara quando outro jogador entra no mundo/servidor atual.
- Variáveis:
  - `$$player_name` – nome do jogador que entrou
  - `$$player_uuid` – UUID

## On Other Player Left World/Server
- Dispara quando outro jogador sai do mundo/servidor atual.
- Variáveis:
  - `$$player_name`
  - `$$player_uuid`

## On Other Player Died
- Dispara quando outro jogador no mundo atual morre.
- Variáveis:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## On Item Picked Up
- Dispara quando o jogador coleta uma entidade de item.
- Variáveis:
  - `$$item_key` – localização de recurso do item coletado

## On Item Dropped
- Dispara quando o jogador descarta um item do inventário.
- Variáveis:
  - `$$item_key` – localização de recurso do item descartado

## On Item Consumed
- Dispara quando o jogador termina de consumir um item.
- Variáveis:
  - `$$item_key` – item consumido

## On Item Hovered in Inventory
- Dispara quando o usuário passa o mouse sobre um item em qualquer tela de inventário.
- Variáveis:
  - `$$item_key` – localização de recurso do item sob o mouse
  - `$$item_display_name_string` – nome exibido do item em texto simples
  - `$$item_display_name_json` – nome exibido do item como componente JSON

## On Item Used
- Dispara quando o jogador usa um item.
- Variáveis:
  - `$$item_key` – item usado
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – tipo da entidade alvo ou vazio
  - `$$used_on_block_key` – bloco alvo ou vazio
  - `$$target_pos_x` – X alvo ou -1
  - `$$target_pos_y` – Y alvo ou -1
  - `$$target_pos_z` – Z alvo ou -1

## On Item Broke
- Dispara quando um item no inventário do jogador quebra.
- Variáveis:
  - `$$item_key` – item quebrado
  - `$$item_type` – ferramenta/armadura/outro
