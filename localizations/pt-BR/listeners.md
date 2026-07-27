---
title: Listeners
description: Como criar e usar listeners no FancyMenu.
---

# Listeners

Listeners executam [scripts de ação](./action-scripts) quando eventos específicos acontecem. Eles não estão vinculados a uma tela aberta, então também podem ser executados enquanto você joga ou durante o carregamento.

Listeners podem fornecer valores `$$`, como uma tecla pressionada ou um botão do mouse clicado, para suas ações e requisitos.

> [!CAUTION]
> Um listener pode executar ações de arquivo, rede, comando, área de transferência, resource pack ou link sem que uma tela esteja aberta. Importe listeners apenas de fontes confiáveis.

# Usando Listeners

Fora do Editor de Layout, abra **menu bar -> Customization -> Manage Listeners** para criar ou editar listeners.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/manage_listeners.png?raw=true" alt="Gerenciar listeners" style="max-width:800px;width:100%;height:auto;">

# Variáveis de Listener

Listeners podem fornecer valores somente leitura para suas ações e requisitos. Use os nomes `$$` deles em campos de texto compatíveis.

Por exemplo, use [**On Keyboard Key Pressed**](#on-keyboard-key-pressed-keyboard_key_pressed) com a [ação **Print to Game Log**](./action-scripts#print-to-game-log-print_to_log). O valor `Key pressed! The key is: $$key_name` insere o nome da tecla pressionada.

> [!WARNING]
> Variáveis de listener são separadas das [variáveis armazenadas](./variables) do FancyMenu. Ações, requisitos e placeholders de variáveis armazenadas não funcionam com valores `$$`.

Os nomes das variáveis de listener diferenciam maiúsculas de minúsculas e só funcionam dentro do script daquele listener.

Trate valores vindos do chat, de servidores remotos, de arquivos e de entrada do usuário como não confiáveis. Não os insira diretamente em caminhos, URLs ou comandos.

As variáveis de listener são strings. Quando uma informação não estiver disponível, um listener pode retornar um valor sentinela documentado, como `ERROR`, `UNKNOWN`, `NONE`, `EMPTY`, `0`, `-1` ou uma string vazia. Teste esses valores antes de inserir dados do listener em caminhos, comandos ou URLs.

# Listeners em Detalhe

Esta seção lista os listeners integrados do FancyMenu.

## Ao Clicar em Texto Markdown (`text_clicked`)
- Dispara quando [texto Markdown com um evento `click:`](./text-formatting#click-and-hover-events) é clicado, por exemplo `[Open](click:open_menu)`.
- Variáveis:
  - `$$text_event_id` – ID do evento do link Markdown

## Ao Passar o Mouse Sobre Texto Markdown (`text_hovered`)
- Dispara quando [texto Markdown com um evento `hover:`](./text-formatting#click-and-hover-events) recebe hover, por exemplo `[Hint](hover:show_hint)`.
- Variáveis:
  - `$$text_event_id` – ID do evento do link Markdown

## Ao Extrair ZIP via Ação (`zip_extracted_via_action`)
- Dispara quando a [ação **Extract ZIP File In Game Directory**](./action-scripts#extract-zip-file-in-game-directory-extract_zip_file_in_game_dir) termina.
- Variáveis:
  - `$$source_zip_path` – caminho de origem normalizado para o usuário; caminhos do diretório do jogo podem ser retornados como `/...`, enquanto caminhos convencionais do diretório do Minecraft podem usar `.minecraft/...`
  - `$$target_folder_path` – caminho de destino normalizado para o usuário usando os mesmos formatos de caminho
  - `$$extract_succeeded` – true/false
  - `$$failure_reason` – texto do erro quando a extração falha

## Ao Gerar Elemento (`element_spawned_via_action`)
- Dispara quando um recurso suportado do FancyMenu ou um add-on gera dinamicamente uma instância de elemento.
- Variáveis:
  - `$$element_type` – tipo do elemento gerado
  - `$$element_identifier` – identificador do elemento gerado
  - `$$target_screen` – identificador da tela de destino

## Ao Começar a Reproduzir Textura Animada (`animated_texture_started_playing`)
- Dispara quando uma [textura animada](./fma) começa a ser reproduzida.
- Variáveis:
  - `$$texture_source` – origem da textura
  - `$$texture_source_type` – tipo da origem
  - `$$texture_will_restart` – true/false

## Ao Terminar de Reproduzir Textura Animada (`animated_texture_finished_playing`)
- Dispara quando uma textura animada termina de ser reproduzida.
- Variáveis:
  - `$$texture_source`
  - `$$texture_source_type`
  - `$$texture_will_restart`

## Ao Mudar o Status da Reprodução de Vídeo (`video_playback_status_changed`)
- Dispara quando um [elemento de vídeo ou plano de fundo do menu](./video) muda o status de reprodução.
- Variáveis:
  - `$$video_source` – origem do vídeo
  - `$$video_source_type` – tipo da origem
  - `$$is_looping` – true/false
  - `$$new_status` – `PLAYING`, `STOPPED`, `PAUSED` ou `FINISHED`

## Ao Receber Mensagem de Sistema no Chat (`system_message_received_in_chat`)
- Dispara quando o cliente recebe uma mensagem de chat de sistema, como feedback de comando.
- Variáveis:
  - `$$system_message_string` – mensagem em texto simples
  - `$$system_message_component` – componente JSON

## Ao Receber FM Data (`fm_data_received`)
- Dispara quando um servidor envia [FM Data](./fm-data) para este cliente via `/fmdata send`.
- Variáveis:
  - `$$data_identifier` – string identificadora dos dados
  - `$$data` – payload dos dados
  - `$$sent_by` – IP do servidor ou `integrated_server`

## Ao Conectar a Servidor Remoto (`remote_server_connected`)
- Dispara depois que uma [conexão com servidor remoto](./remote-server-communication) é aberta com sucesso.
- Variáveis:
  - `$$request_id` – ID da solicitação em cache
  - `$$remote_server_url` – URL do servidor remoto

## Ao Receber Dados de Servidor Remoto (`remote_server_data_received`)
- Dispara quando dados de texto são recebidos de um servidor remoto conectado.
- Variáveis:
  - `$$request_id` – ID da solicitação
  - `$$remote_server_url` – URL do servidor remoto
  - `$$data` – payload recebido

## Ao Fechar Conexão com Servidor Remoto (`remote_server_connection_closed`)
- Dispara quando a conexão com um servidor remoto é encerrada.
- Variáveis:
  - `$$request_id` – ID da solicitação
  - `$$remote_server_url` – URL do servidor remoto
  - `$$intentionally_closed` – TRUE se foi fechada por uma ação
  - `$$crashed` – TRUE se a conexão caiu inesperadamente
  - `$$unknown_close_reason` – TRUE se nenhuma causa conhecida de encerramento estava disponível

## Ao Pressionar Tecla do Teclado (`keyboard_key_pressed`)
- Dispara sempre que uma tecla é pressionada (repete enquanto mantida; funciona em telas e no jogo).
- Variáveis:
  - `$$key_name` – nome exibido da tecla
  - `$$key_keycode` – código de tecla GLFW
  - `$$key_scancode` – código de varredura GLFW
  - `$$key_modifiers` – máscara de bits dos modificadores ativos

## Ao Soltar Tecla do Teclado (`keyboard_key_released`)
- Dispara quando uma tecla é solta (telas e no jogo).
- Variáveis:
  - `$$key_name`
  - `$$key_keycode`
  - `$$key_scancode`
  - `$$key_modifiers`

## Ao Digitar Caractere do Teclado em uma Tela (`keyboard_char_typed`)
- Dispara quando um caractere é digitado enquanto uma tela está aberta.
- Variáveis:
  - `$$char` – caractere digitado

## Ao Mover o Mouse em uma Tela (`mouse_moved`)
- Dispara sempre que o mouse se move enquanto uma tela está aberta.
- Variáveis:
  - `$$mouse_pos_x` – X atual
  - `$$mouse_pos_y` – Y atual
  - `$$mouse_move_delta_x` – delta de X desde o último evento
  - `$$mouse_move_delta_y` – delta de Y desde o último evento

## Ao Clicar em Botão do Mouse (`mouse_button_clicked`)
- Dispara quando um botão do mouse é pressionado (telas e no jogo).
- Variáveis:
  - `$$button` – esquerda/direita/meio
  - `$$mouse_pos_x` – X atual
  - `$$mouse_pos_y` – Y atual

## Ao Soltar Botão do Mouse (`mouse_button_released`)
- Dispara quando um botão do mouse é solto (telas e no jogo).
- Variáveis:
  - `$$button`
  - `$$mouse_pos_x`
  - `$$mouse_pos_y`

## Ao Rolar o Mouse em uma Tela (`mouse_scrolled`)
- Dispara quando a roda do mouse é rolada enquanto uma tela está aberta.
- Variáveis:
  - `$$scroll_delta_y` – quantidade de rolagem vertical

## Ao Abrir Tela (`screen_open`)
- Executa logo depois que qualquer tela se torna ativa; pode ser usado para substituí-la.
- Variáveis:
  - `$$screen_identifier` – identificador da tela aberta

## Ao Fechar Tela (`screen_close`)
- Executa imediatamente depois que uma tela é fechada.
- Variáveis:
  - `$$screen_identifier` – identificador da tela fechada

## Ao Sair do Minecraft (`quit_minecraft`)
- Dispara uma vez quando o cliente começa a encerrar.
- Variáveis:
  - `$$timestamp_millis` – epoch em milissegundos no momento de sair
  - `$$timestamp_iso` – timestamp ISO-8601 do momento de sair

## Ao Morrer (`player_death`)
- Executa quando a tela de morte padrão é aberta para o jogador local.
- Variáveis:
  - `$$days_survived` – dias desde a última morte
  - `$$death_reason_string` – causa em texto simples
  - `$$death_reason_component` – causa em componente JSON
  - `$$death_pos_x` – coordenada X da morte
  - `$$death_pos_y` – coordenada Y da morte
  - `$$death_pos_z` – coordenada Z da morte

## Ao Atualizar Variável [FM Variable] (`fm_variable_updated`)
- Dispara sempre que uma [variável do FancyMenu](./variables) é definida ou atualizada.
- Variáveis:
  - `$$var_name` – nome da variável
  - `$$old_value` – valor anterior
  - `$$new_value` – novo valor

## Ao Baixar Arquivo via Ação (`file_downloaded_via_action`)
- Dispara após a [ação **Download File to Game Directory**](./action-scripts#download-file-to-game-directory-download_file_to_game_dir) terminar.
- Variáveis:
  - `$$download_url` – origem do download
  - `$$target_file_path` – caminho do arquivo salvo com sucesso; em caso de falha, isso pode conter apenas o diretório de destino porque nenhum nome final de arquivo foi resolvido
  - `$$download_succeeded` – true/false

## Ao Selecionar Arquivo (`file_selected_via_action`)
- Dispara após a conclusão da [ação **Select File from System**](./action-scripts#select-file-from-system-select_file_to_game_dir).
- Variáveis:
  - `$$selected_file_path` – caminho absoluto do arquivo escolhido ou vazio se cancelado
  - `$$target_file_path` – caminho resolvido dentro da instância
  - `$$selection_succeeded` – true se a cópia foi bem-sucedida
  - `$$selection_cancelled` – true se a caixa de diálogo foi fechada
  - `$$failure_reason` – informações do erro em caso de falha

## Ao Receber Mensagem de Chat (`chat_message_received`)
- Dispara quando uma linha normal de chat de jogador aparece no cliente.
- Variáveis:
  - `$$chat_message_string` – linha em texto simples
  - `$$chat_message_component` – componente JSON completo
  - `$$sender_uuid` – UUID do remetente ou ERROR
  - `$$sender_name` – nome do remetente ou ERROR

## Ao Enviar Mensagem de Chat (`chat_message_sent`)
- Dispara quando o jogador local envia uma mensagem de chat.
- Variáveis:
  - `$$chat_message_string` – linha em texto simples
  - `$$chat_message_component` – componente JSON completo

## Ao Ganhar Efeito (`effect_gained`)
- Dispara quando o jogador ganha um efeito de status.
- Variáveis:
  - `$$effect_key` – localização de recurso do efeito
  - `$$effect_type` – positive/negative/neutral
  - `$$effect_duration` – ticks restantes

## Ao Perder Efeito (`effect_lost`)
- Dispara quando o jogador perde um efeito de status.
- Variáveis:
  - `$$effect_key` – efeito expirado
  - `$$effect_type` – categoria

## Ao Mudar Experiência (`experience_changed`)
- Dispara sempre que a experiência total do jogador muda.
- Variáveis:
  - `$$new_experience_amount` – após a mudança
  - `$$old_experience_amount` – antes da mudança
  - `$$is_level_up` – TRUE se o nível aumentou

## Ao Sofrer Dano (`damage_taken`)
- Dispara uma vez por golpe quando o jogador sofre dano.
- Variáveis:
  - `$$damage_amount` – vida removida
  - `$$damage_type` – localização de recurso do tipo de dano
  - `$$is_fatal_damage` – TRUE se for letal
  - `$$damage_source` – localização de recurso do agressor ou NONE

## Ao Começar a Congelar (`started_freezing`)
- Dispara quando o jogador começa a congelar.
- Variáveis:
  - `$$freezing_intensity` – 0.0 nenhuma, 1.0 totalmente congelado

## Ao Parar de Congelar (`stopped_freezing`)
- Dispara quando o jogador para de congelar.
- Variáveis:
  - (nenhuma)

## Ao Ficar Totalmente Congelado (`fully_frozen`)
- Dispara uma vez quando o jogador fica totalmente congelado.
- Variáveis:
  - (nenhuma)

## Ao Começar a Olhar para um Bloco (`start_looking_at_block`)
- Dispara uma vez quando a mira aponta pela primeira vez para um bloco (distância máxima de 20 blocos).
- Variáveis:
  - `$$block_key` – bloco alvo
  - `$$block_pos_x` – X do bloco
  - `$$block_pos_y` – Y do bloco
  - `$$block_pos_z` – Z do bloco
  - `$$distance_to_player` – dos olhos até o ponto de acerto

## Ao Parar de Olhar para um Bloco (`stop_looking_at_block`)
- Dispara quando a mira para de apontar para um bloco (reporta o último bloco alvo, máximo de 20 blocos).
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`
  - `$$distance_to_player`

## Ao Começar a Olhar para uma Entidade (`start_looking_at_entity`)
- Dispara uma vez quando a mira aponta pela primeira vez para uma entidade (máximo de 20 blocos).
- Variáveis:
  - `$$entity_key` – tipo da entidade alvo
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Ao Parar de Olhar para uma Entidade (`stop_looking_at_entity`)
- Dispara quando a mira para de apontar para uma entidade (reporta a última entidade alvo, máximo de 20 blocos).
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Ao Gerar Entidade (`entity_spawned`)
- **Requer FancyMenu no servidor.** Dispara quando qualquer entidade aparece em qualquer lugar no mundo/servidor conectado.
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player` – −1 se estiver em outra dimensão
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`
  - `$$dimension_key`
  - `$$is_same_dimension_as_player`

## Ao Morrer Entidade (`entity_died`)
- **Requer FancyMenu no servidor.** Dispara quando qualquer entidade morre no mundo/servidor conectado.
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

## Ao Começar a Ver uma Entidade (`entity_starts_being_in_sight`)
- Dispara quando uma entidade fica visível pela primeira vez dentro de 200 blocos.
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Ao Parar de Ver uma Entidade (`entity_stops_being_in_sight`)
- Dispara quando uma entidade antes visível sai da vista ou se afasta para além de 200 blocos.
- Variáveis:
  - `$$entity_key`
  - `$$distance_to_player`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Ao Interagir com Entidade (`entity_interacted`)
- Dispara quando o jogador interage com sucesso com uma entidade.
- Variáveis:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Ao Montar em Entidade (`entity_mounted`)
- Dispara quando o jogador começa a montar em uma entidade.
- Variáveis:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Ao Desmontar de Entidade (`entity_unmounted`)
- Dispara quando o jogador para de montar na entidade atual.
- Variáveis:
  - `$$entity_key`
  - `$$entity_pos_x`
  - `$$entity_pos_y`
  - `$$entity_pos_z`
  - `$$entity_uuid`

## Ao Quebrar Bloco (`block_broke`)
- Dispara quando o jogador quebra um bloco.
- Variáveis:
  - `$$block_key`
  - `$$broke_with_item_key` – ferramenta usada ou EMPTY
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Ao Colocar Bloco (`block_placed`)
- Dispara quando o jogador coloca um bloco.
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Ao Interagir com Bloco (`interacted_with_block`)
- Dispara quando o jogador interage com sucesso com um bloco.
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Ao Pisando em Bloco (`stepping_on_block`)
- Dispara quando o jogador pisa sobre um bloco.
- Variáveis:
  - `$$block_key`
  - `$$block_pos_x`
  - `$$block_pos_y`
  - `$$block_pos_z`

## Ao Entrar no Bioma (`enter_biome`)
- Dispara quando o jogador entra em um novo bioma.
- Variáveis:
  - `$$biome_key` – bioma em que entrou

## Ao Sair do Bioma (`leave_biome`)
- Dispara quando o jogador sai do bioma atual.
- Variáveis:
  - `$$biome_key` – bioma acabado de sair

## Ao Entrar em Estrutura (`enter_structure`)
- **Requer FancyMenu no servidor.** Detecção grosseira de área de estrutura; pode disparar perto, acima ou abaixo da estrutura.
- Variáveis:
  - `$$structure_key` – estrutura em que entrou

## Ao Sair de Estrutura (`leave_structure`)
- **Requer FancyMenu no servidor.** Detecção grosseira; pode disparar perto da área ocupada pela estrutura.
- Variáveis:
  - `$$structure_key` – estrutura da qual acabou de sair

## Ao Entrar em Estrutura (Alta Precisão) (`enter_structure_high_precision`)
- **Requer FancyMenu no servidor.** Dispara quando o jogador entra nas caixas delimitadoras de uma estrutura.
- Variáveis:
  - `$$structure_key`

## Ao Sair de Estrutura (Alta Precisão) (`leave_structure_high_precision`)
- **Requer FancyMenu no servidor.** Dispara depois que o jogador sai das caixas delimitadoras de uma estrutura.
- Variáveis:
  - `$$structure_key`

## Ao Entrar na Dimensão (`enter_dimension`)
- Dispara quando o jogador entra em uma nova dimensão.
- Variáveis:
  - `$$dimension_key` – dimensão em que entrou

## Ao Começar a Nadar (`start_swimming`)
- Dispara quando o jogador começa a nadar.
- Variáveis:
  - `$$fluid_type` – localização de recurso do fluido

## Ao Parar de Nadar (`stop_swimming`)
- Dispara quando o jogador para de nadar.
- Variáveis:
  - `$$fluid_type` – fluido em que a natação parou

## Ao Começar a Tocar em Fluido (`start_touching_fluid`)
- Dispara quando o jogador começa a tocar um fluido.
- Variáveis:
  - `$$fluid_type` – fluido tocado

## Ao Parar de Tocar em Fluido (`stop_touching_fluid`)
- Dispara quando o jogador para de tocar um fluido.
- Variáveis:
  - `$$fluid_type` – fluido que não está mais sendo tocado

## Ao Iniciar Faixa de Música (`music_track_started`)
- Dispara quando uma nova faixa de música começa.
- Variáveis:
  - `$$track_resource_location` – arquivo de áudio
  - `$$track_display_name` – nome legível ou UNKNOWN
  - `$$track_artist` – artista ou UNKNOWN
  - `$$track_duration_ms` – milissegundos (0 se desconhecido)

## Ao Parar Faixa de Música (`music_track_stopped`)
- Dispara quando a faixa de música atual termina ou é substituída.
- Variáveis:
  - `$$track_resource_location`
  - `$$track_display_name`
  - `$$track_artist`
  - `$$track_duration_ms`

## Ao Acionar Som do Mundo (`world_sound_triggered`)
- Dispara quando um som posicional do mundo começa perto do jogador.
- Variáveis:
  - `$$sound_resource_location` – arquivo de som
  - `$$sound_display_name` – nome da legenda quando disponível
  - `$$sound_origin_pos_x`
  - `$$sound_origin_pos_y`
  - `$$sound_origin_pos_z`
  - `$$sound_origin_distance_to_player`
  - `$$sound_origin_direction_from_player` – graus de 0 a 360 em relação à direção para a qual o jogador está virado

## Ao Mudar o Clima (`weather_changed`)
- Dispara quando o clima muda globalmente ou localmente (mudanças de bioma ou entrar em ambientes fechados podem disparar novamente).
- Variáveis:
  - `$$weather_type` – clear/rain/thunder
  - `$$weather_can_snow` – TRUE se a neve é renderizada
  - `$$weather_can_rain` – TRUE se a chuva é renderizada

## Ao Começar a Queimar (`started_burning`)
- Dispara quando o jogador começa a queimar.
- Variáveis:
  - (nenhuma)

## Ao Parar de Queimar (`stopped_burning`)
- Dispara quando o jogador para de queimar.
- Variáveis:
  - (nenhuma)

## Ao Começar a Se Afogar (`started_drowning`)
- Dispara quando o jogador começa a sofrer dano por afogamento.
- Variáveis:
  - (nenhuma)

## Ao Mudar de Posição (`position_changed`)
- Dispara sempre que a posição em blocos do jogador muda.
- Variáveis:
  - `$$old_pos_x` – bloco X anterior
  - `$$old_pos_y` – bloco Y anterior
  - `$$old_pos_z` – bloco Z anterior
  - `$$new_pos_x` – novo bloco X
  - `$$new_pos_y` – novo bloco Y
  - `$$new_pos_z` – novo bloco Z

## Ao Começar a Correr (`started_running`)
- Dispara quando o jogador começa a correr em sprint.
- Variáveis:
  - (nenhuma)

## Ao Parar de Correr (`stopped_running`)
- Dispara quando o jogador para de correr em sprint.
- Variáveis:
  - (nenhuma)

## Ao Pular (`jump`)
- Dispara sempre que o jogador pula.
- Variáveis:
  - (nenhuma)

## Ao Entrar no Servidor (`server_joined`)
- Dispara depois de entrar com sucesso em um servidor multiplayer.
- Variáveis:
  - `$$server_ip` – endereço do servidor em que entrou

## Ao Sair do Servidor (`server_left`)
- Dispara depois de desconectar de um servidor multiplayer.
- Variáveis:
  - `$$server_ip` – endereço do servidor do qual saiu

## Mundo Singleplayer Entrado (`world_entered`)
- Dispara depois que um mundo singleplayer termina de carregar e o controle retorna.
- Variáveis:
  - `$$world_name` – nome exibido
  - `$$world_save_path` – pasta de salvamento absoluta
  - `$$world_difficulty` – chave da dificuldade
  - `$$world_cheats_allowed` – TRUE se cheats estiverem ativados
  - `$$world_icon_path` – caminho absoluto do ícone
  - `$$world_is_first_join` – TRUE na primeira visita

## Mundo Singleplayer Saído (`world_left`)
- Dispara depois que um mundo singleplayer fecha e termina de salvar.
- Variáveis:
  - `$$world_name`
  - `$$world_save_path`
  - `$$world_difficulty`
  - `$$world_cheats_allowed`
  - `$$world_icon_path`

## Ao Outro Jogador Entrar no Mundo/Servidor (`other_player_joined_world`)
- Dispara quando outro jogador entra no mundo/servidor atual.
- Variáveis:
  - `$$player_name` – nome do jogador que entrou
  - `$$player_uuid` – UUID

## Ao Outro Jogador Sair do Mundo/Servidor (`other_player_left_world`)
- Dispara quando outro jogador sai do mundo/servidor atual.
- Variáveis:
  - `$$player_name`
  - `$$player_uuid`

## Ao Outro Jogador Morrer (`other_player_died`)
- Dispara quando outro jogador no mundo atual morre.
- Variáveis:
  - `$$player_name`
  - `$$player_uuid`
  - `$$death_pos_x`
  - `$$death_pos_y`
  - `$$death_pos_z`

## Ao Pegar Item (`item_picked_up`)
- Dispara quando o jogador pega uma entidade item.
- Variáveis:
  - `$$item_key` – localização de recurso do item coletado

## Ao Largar Item (`item_dropped`)
- Dispara quando o jogador joga um item fora do inventário.
- Variáveis:
  - `$$item_key` – localização de recurso do item descartado

## Ao Consumir Item (`item_consumed`)
- Dispara quando o jogador termina de consumir um item.
- Variáveis:
  - `$$item_key` – item consumido

## Ao Passar o Mouse Sobre Item no Inventário (`item_hovered_in_inventory`)
- Dispara quando o usuário passa o mouse sobre um item em qualquer tela de inventário.
- Variáveis:
  - `$$item_key` – localização de recurso do item sob o mouse
  - `$$item_display_name_string` – nome exibido do item em texto simples
  - `$$item_display_name_json` – nome exibido do item em componente JSON

## Ao Usar Item (`item_used`)
- Dispara quando o jogador usa um item.
- Variáveis:
  - `$$item_key` – item usado
  - `$$used_on_type` – block/entity/self/none
  - `$$used_on_entity_key` – tipo da entidade alvo ou vazio
  - `$$used_on_block_key` – bloco alvo ou vazio
  - `$$target_pos_x` – X do alvo ou -1
  - `$$target_pos_y` – Y do alvo ou -1
  - `$$target_pos_z` – Z do alvo ou -1

## Ao Quebrar Item (`item_broke`)
- Dispara quando um item no inventário do jogador quebra.
- Variáveis:
  - `$$item_key` – item quebrado
  - `$$item_type` – tool/armor/other
