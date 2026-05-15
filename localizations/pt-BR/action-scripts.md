---
title: Scripts de Ação
description: 'Como usar scripts de ação com botões, sliders, tickers e muito mais.'
---

# Scripts de Ação

O FancyMenu permite adicionar interatividade aos seus menus atribuindo **ações** a elementos. Essas ações são executadas quando um botão é clicado, um ticker está funcionando, um slider é usado ou quando uma tela é aberta ou fechada. Você também pode criar scripts de ação avançados usando instruções simples de controle, como **if**, **else-if**, **else** e **while**, para controlar quais ações são executadas e quando.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Editor de script de ação" style="max-width:800px;width:100%;height:auto;">

# O Que São Ações?

Uma **ação** é uma tarefa ou função que o FancyMenu executa quando é acionada. Por exemplo, uma ação pode abrir uma nova tela, enviar uma mensagem no chat ou ajustar o volume de um elemento de áudio. No editor do FancyMenu, as ações são configuradas com um valor (se necessário) que fornece detalhes extras — como uma URL ou o endereço de um servidor.

# O Que São Instruções?

Para criar comportamentos mais complexos, o FancyMenu oferece suporte a instruções básicas de controle em scripts de ação. Elas incluem:

- **Instrução If:** Executa um bloco de ações somente se uma [condição](/en/conditions) especificada for atendida.
- **Instrução Else-If:** Verifica outra [condição](/en/conditions) se o *if* anterior (ou um *else-if* anterior) não foi atendido.
- **Instrução Else:** Executa se nenhuma das [condições](/en/conditions) anteriores for atendida.
- **Instrução While:** Repete um bloco de ações continuamente enquanto uma [condição](/en/conditions) permanecer verdadeira (com um timeout integrado para evitar loops infinitos).
- **Bloco de Delay:** Aguarda o tempo especificado antes de executar as ações contidas nele. O restante do script continua sendo executado enquanto a contagem regressiva do delay ocorre.
- **Bloco Execute Later:** Coloca em fila as ações contidas para serem executadas na thread principal após um atraso em milissegundos.
- **Comentário:** Adiciona uma observação dentro do script para organização. Comentários não executam nenhuma ação.

Ao combinar essas instruções com ações, você pode criar comportamentos dinâmicos e condicionais, por exemplo, verificar se a vida de um jogador está baixa antes de enviar uma mensagem de aviso ou repetir uma atualização até que uma condição mude.

# Onde Você Pode Usar Scripts de Ação?

Os scripts de ação são versáteis e podem ser usados em todo o seu layout. Você pode atribuí-los, por exemplo, a:

- **Botões:** Executam uma ação quando o botão é clicado.
- **Tickers:** Executam continuamente um script de ação para atualizar informações exibidas na tela dentro de um layout.
- **Sliders:** Disparam um script de ação sempre que o valor do slider muda.
- **Eventos de Tela:** Executam scripts quando uma tela é aberta ou fechada (por exemplo, tocando um som quando um menu aparece).
- **Listeners:** Quando um listener que escuta um evento específico é acionado, ele executará seu script de ação.
- **Schedulers:** Executam ações em intervalos programados, mesmo quando nenhuma tela está aberta.

# Usando Placeholders em Ações

Os valores das ações suportam conteúdo dinâmico por meio de **placeholders**. Na maioria das vezes, esses placeholders usam uma sintaxe parecida com JSON e são substituídos por dados em tempo real quando a ação é executada.

## Placeholders Semelhantes a JSON

Estes são os [placeholders](/en/placeholders) normais que podem ser usados em muitos lugares dentro dos layouts.

Eles seguem esta sintaxe:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Eles podem obter dados do jogo, como o nome do jogador, dimensões da tela ou valores calculados usando o placeholder **Calculator**. Você também pode aninhar placeholders para usos mais avançados.

## Placeholders `$$` (Variáveis)

Os placeholders `$$` são especiais. Alguns recursos do FancyMenu fornecem esses placeholders especiais para suas ações aninhadas, requisitos e placeholders normais, para que possam ser usados internamente e obter mais informações sobre o ambiente (elemento, listener etc.) em que estão.

Por exemplo, se ações forem usadas dentro de um slider, usar `$$value` na ação será substituído pelo valor atual do slider.

Ao usar ações em listeners, cada listener fornecerá seu próprio conjunto exclusivo de variáveis/placeholders para obter mais informações sobre o listener, como botão do mouse pressionado, estrutura inserida etc.

# Como Configurar e Editar Ações

Para adicionar, editar ou remover ações (e blocos de instrução) de um elemento, basta **clicar com o botão direito no elemento** (seja um botão, slider, ticker ou outro item interativo) e então selecionar **Gerenciar Script de Ação**. Isso abre a tela de Gerenciar Ações, onde você pode:

- **Adicionar novas ações ou instruções:** Insira novas entradas de ação ou instruções de controle (if, else-if, else, while) para montar seu script.
- **Editar ações ou instruções existentes:** Modifique o valor da ação ou altere a lógica de controle.
- **Remover ações ou instruções:** Exclua ações indesejadas do script.

Para [listeners](/listeners), há um menu especial para gerenciar e criar listeners, incluindo acesso aos seus scripts de ação, oferecendo a mesma experiência que você teria ao editar o script de ação de um botão ou slider, por exemplo.

> Na tela do Editor de Script de Ação, basta clicar com o botão direito na grande área cinza escuro para abrir um menu de contexto e adicionar ações, instruções e muito mais.
{.is-info}


# Atalhos e Mais do Editor de Script de Ação

O editor de script de ação tem vários recursos de qualidade de vida que tornam a edição de scripts super fácil.

## Atalhos

- `DEL` : Exclui rapidamente a entrada selecionada
- `ENTER` : Inicia a edição em linha da entrada selecionada (ou abre a tela de edição se não houver edição em linha para a entrada selecionada)
- `CTRL + C` : Copia a ação selecionada (por enquanto, só funciona com ações)
- `CTRL + V` : Cola a ação copiada anteriormente
- `CTRL + Z` : Volta um passo (desfazer)
- `CTRL + Y` : Avança um passo (refazer)
- `ARROW UP` : Navega uma entrada para cima a partir da entrada selecionada
- `ARROW DOWN` : Navega uma entrada para baixo a partir da entrada selecionada
- `SHIFT + ARROW UP` : Move a entrada selecionada uma posição para cima
- `SHIFT + ARROW DOWN` : Move a entrada selecionada uma posição para baixo
- `A` : Abre rapidamente a tela Seletor de Ações para adicionar uma nova ação
- `CTRL + S` : Conclui/salva na janela do editor

## Mais Recursos de Qualidade de Vida

- Clicar duas vezes no valor de uma ação permite editar o valor sem abrir a tela completa de edição do valor.
- Cadeias de instruções IF (com instruções ELSE/ELSE-IF anexadas), loops WHILE e pastas podem ser recolhidos (somente visualmente, não afeta a lógica do script).
- O editor sempre adiciona novas ações abaixo da entrada selecionada (ou aninhadas na cadeia/loop/pasta selecionada).
- Clicar com o botão direito no fundo cinza escuro da área do script abre um menu de contexto com opções para adicionar ações, instruções e tudo mais importante.

# Ações em Detalhe

Esta lista contém a maioria, senão todas, as ações disponíveis no FancyMenu. É possível que a lista fique um pouco desatualizada às vezes devido a atualizações do mod.

## Próxima Faixa (`audio_next_track`)
- **Descrição:** Vai para a próxima faixa em um elemento de áudio
- **Valor Necessário:** Sim - `audio_element_identifier` (o ID do elemento de áudio a controlar)

## Faixa Anterior (`audio_previous_track`)
- **Descrição:** Vai para a faixa anterior em um elemento de áudio
- **Valor Necessário:** Sim - `audio_element_identifier` (o ID do elemento de áudio a controlar)

## Definir Volume da Faixa (`set_audio_element_volume`)
- **Descrição:** Define o volume de um elemento de áudio (0.0 a 1.0)
- **Valor Necessário:** Sim - `element_identifier:volume`

## Alternar Reproduzir/Pausar Faixa (`audio_toggle_play`)
- **Descrição:** Alterna entre reproduzir/pausar a faixa atual de um elemento de áudio
- **Valor Necessário:** Sim - `audio_element_identifier`

## Reproduzir Áudio (`play_audio`)
- **Descrição:** Reproduz um recurso de áudio uma vez. A ação rastreia o áudio que iniciou para que ele possa ser interrompido mais tarde por `stop_all_action_audios`.
- **Valor Necessário:** Sim - configuração JSON com `audioSource`, `soundChannel` e `baseVolume`
- **Valor de Exemplo:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

## Parar Todos os Áudios de Ação (`stop_all_action_audios`)
- **Descrição:** Interrompe todas as faixas de áudio iniciadas pela ação **Reproduzir Áudio**. Isso não interrompe elementos de áudio, sons de abrir/fechar menu, sons de botão ou outros sistemas de áudio.
- **Valor Necessário:** Não

## Definir Volume do Elemento de Vídeo (`set_video_element_volume`)
- **Descrição:** Define o volume de um elemento de vídeo (0.0 a 1.0)
- **Valor Necessário:** Sim - `video_element_identifier:volume`

## Definir Tempo de Reprodução do Elemento de Vídeo (`set_video_element_play_time`)
- **Descrição:** Posiciona um elemento de vídeo em um timestamp em milissegundos
- **Valor Necessário:** Sim - `video_element_identifier:timestamp_ms`

## Alternar Estado de Pausa do Elemento de Vídeo (`toggle_video_element_pause_state`)
- **Descrição:** Alterna o estado de pausa de um elemento de vídeo
- **Valor Necessário:** Sim - `video_element_identifier`

## Definir Volume do Fundo de Vídeo (`set_video_menu_background_volume`)
- **Descrição:** Define o volume de um fundo de menu em vídeo (0.0 a 1.0)
- **Valor Necessário:** Sim - `background_identifier:volume`

> Para obter o identificador de um fundo, clique com o botão direito no fundo do editor e clique em 'Copy Background Identifier'.
{.is-info}

## Definir Tempo de Reprodução do Fundo de Vídeo (`set_video_menu_background_play_time`)
- **Descrição:** Posiciona um fundo de menu em vídeo em um timestamp em milissegundos
- **Valor Necessário:** Sim - `background_identifier:timestamp_ms`

> Para obter o identificador de um fundo, clique com o botão direito no fundo do editor e clique em 'Copy Background Identifier'.
{.is-info}

## Alternar Estado de Pausa do Fundo de Vídeo (`toggle_video_menu_background_pause_state`)
- **Descrição:** Alterna o estado de pausa de um fundo de menu em vídeo
- **Valor Necessário:** Sim - `background_identifier`

> Para obter o identificador de um fundo, clique com o botão direito no fundo do editor e clique em 'Copy Background Identifier'.
{.is-info}

## Alternar Layout (`toggle_layout`)
- **Descrição:** Alterna um layout (ativar/desativar) pelo nome
- **Valor Necessário:** Sim - `layout_name`

## Ativar Layout (`enable_layout`)
- **Descrição:** Ativa um layout pelo nome
- **Valor Necessário:** Sim - `layout_name`

## Desativar Layout (`disable_layout`)
- **Descrição:** Desativa um layout pelo nome
- **Valor Necessário:** Sim - `layout_name`

## Abrir Tela ou GUI Personalizada (`opengui`)
- **Descrição:** Abre uma tela pelo seu identificador (vanilla, mod ou GUI personalizada)
- **Valor Necessário:** Sim - `screen_identifier`

> Esta ação **não funcionará em todas as telas**, especialmente telas de mods. Se a ação não conseguir abrir uma tela, ela mostrará um erro. Não há muito o que fazer nesse caso, porque provavelmente se trata de uma tela complexa demais para ser aberta automaticamente pelo FancyMenu.
> 
> A compatibilidade com telas de mods também não será mais adicionada manualmente pelo lado do FancyMenu, porque adicionar compatibilidade para todos os mods por aí levaria uma eternidade, desculpe. Na maioria dos casos, também não é recomendado entrar em contato com o desenvolvedor do outro mod nesse caso, porque se o FancyMenu não consegue abrir a tela, não há uma forma fácil de adicionar suporte para ela. A solução recomendada aqui é tentar usar a ação **"Mimic Vanilla/Mod Button"** para imitar um botão que abre a tela específica. Se não houver botão, infelizmente não há muito o que fazer.
{.is-info}

## Fechar Tela (`closegui`)
- **Descrição:** Fecha a tela ativa
- **Valor Necessário:** Não

## Atualizar Tela (`update_screen`)
- **Descrição:** Reinicializa a tela atual
- **Valor Necessário:** Não

## Voltar para a Última Tela (`back_to_last_screen`)
- **Descrição:** Volta para a tela anterior (a que estava antes da atual)
- **Valor Necessário:** Não

## Entrar em Servidor (`joinserver`)
- **Descrição:** Conecta o jogador a um servidor Minecraft
- **Valor Necessário:** Sim - `server_ip:port`

## Entrar no Mundo (`loadworld`)
- **Descrição:** Entra em um mundo Minecraft
- **Valor Necessário:** Sim - `world_folder_name`

## Entrar/Conectar ao Último Mundo/Servidor (`join_last_world`)
- **Descrição:** Entra/conecta ao último mundo ou servidor em que o jogador estava
- **Valor Necessário:** Não

## Sair do Mundo ou Servidor (`disconnect_server_or_world`)
- **Descrição:** Sai de um mundo ou servidor e abre uma tela especificada
- **Valor Necessário:** Sim - `screen_identifier`

## Fechar o Minecraft (`quitgame`)
- **Descrição:** Fecha completamente o Minecraft
- **Valor Necessário:** Não

## Enviar Mensagem/Comando no Chat (`sendmessage`)
- **Descrição:** Envia uma mensagem no chat ou executa um comando no chat
- **Valor Necessário:** Sim - `message_text` ou `/command_text`

## Executar Comando como Servidor Integrado (`execute_command_as_integrated_server`)
- **Descrição:** Executa forçadamente um comando no modo singleplayer como o servidor integrado, ignorando permissões e a configuração de cheats.
- **Valor Necessário:** Sim - texto do comando, por exemplo `/give @p minecraft:diamond 1`

> Esta ação só funciona no modo singleplayer enquanto o mundo não estiver aberto para LAN. Ela intencionalmente não faz nada em servidores multiplayer.
{.is-warning}

## Colar no Chat (`paste_to_chat`)
- **Descrição:** Cola texto no campo de entrada do chat (anexar ou substituir)
- **Valor Necessário:** Sim - `true:Texto` ou `false:Texto`

## Exibir no Chat [Client-Side] (`display_in_chat_client_side`)
- **Descrição:** Exibe texto diretamente no chat local (sem servidor)
- **Valor Necessário:** Sim - `text_or_json`

## Enviar Dados do FM para o Servidor (`send_fm_data_to_server`)
- **Descrição:** Envia dados de texto personalizados para o servidor atual do FancyMenu através do canal de pacotes FM Data.
- **Valor Necessário:** Sim - `data_identifier||data`

## Conectar ao Servidor Remoto (`connect_to_remote_server`)
- **Descrição:** Abre ou reutiliza uma conexão WebSocket iniciada pelo cliente com um servidor remoto externo.
- **Valor Necessário:** Sim - URL do servidor remoto, por exemplo `wss://example.com/ws`

## Enviar Dados ao Servidor Remoto (`send_data_to_remote_server`)
- **Descrição:** Abre ou reutiliza uma conexão com um servidor remoto e envia dados de texto para ele.
- **Valor Necessário:** Sim - `remote_server_url||data`

## Fechar Conexão com Servidor Remoto (`close_remote_server_connection`)
- **Descrição:** Fecha uma conexão específica com um servidor remoto por ID de solicitação.
- **Valor Necessário:** Sim - ID da solicitação, geralmente de uma variável de listener de Servidor Remoto, como `$$request_id`

## Fechar Todas as Conexões com Servidores Remotos (`close_all_remote_server_connections`)
- **Descrição:** Fecha todas as conexões ativas com servidores remotos abertas pelo FancyMenu.
- **Valor Necessário:** Não

## Abrir URL no Navegador (`openlink`)
- **Descrição:** Abre um link no seu navegador padrão
- **Valor Necessário:** Sim - `https://example.com`

## Copiar Texto para a Área de Transferência (`copytoclipboard`)
- **Descrição:** Copia texto para a área de transferência
- **Valor Necessário:** Sim - `text_to_copy`

## Imprimir no Log do Jogo (`print_to_log`)
- **Descrição:** Escreve uma linha no log do jogo
- **Valor Necessário:** Sim - `text_to_log`

## Definir Valor de Variável (Variável FM) (`set_variable`)
- **Descrição:** Armazena conteúdo de texto em uma variável do FancyMenu
- **Valor Necessário:** Sim - `variable_name:variable_value`

## Limpar Todas as Variáveis (Variável FM) (`clear_variables`)
- **Descrição:** Limpa TODAS as variáveis armazenadas do FancyMenu
- **Valor Necessário:** Não

## Enviar Requisição HTTP (`send_http_request`)
- **Descrição:** Envia uma requisição HTTP; pode armazenar a resposta em uma variável
- **Valor Necessário:** Sim - configuração da requisição HTTP

> Esta ação permite enviar dados para APIs REST, webhooks ou qualquer endpoint HTTP.
> Suporta vários métodos de autenticação, cabeçalhos personalizados e diferentes tipos de requisição.
> 
> Esta ação também permite armazenar a resposta da requisição em uma variável do FancyMenu para uso posterior!
{.is-info}

## Gerenciar Pacote de Recursos (`manage_resource_pack`)
- **Descrição:** Ativa/desativa/alternar um pacote de recursos pelo nome exibido (recarregamento opcional)
- **Valor Necessário:** Sim - `pack_name|||MODE|||reload_bool`

## Recarregar Pacotes de Recursos (`reload_resource_packs`)
- **Descrição:** Recarrega os pacotes de recursos (cooldown de 5s)
- **Valor Necessário:** Não

## Recarregar o FancyMenu (`reloadmenu`)
- **Descrição:** Recarrega o FancyMenu, incluindo panoramas, slideshows e todos os recursos (pesado)
- **Valor Necessário:** Não

> Esta ação tem um **grande impacto no desempenho** e pode causar travamentos se usada em Tickers. Não é recomendado usar esta ação em nada além de um botão.
{.is-warning}

## Alternar Animator de Elemento (`toggle_element_animator`)
- **Descrição:** Alterna o estado de reprodução de um animator de elemento
- **Valor Necessário:** Sim - `animator_identifier`

## Ativar Animator de Elemento (`enable_element_animator`)
- **Descrição:** Ativa um animator de elemento
- **Valor Necessário:** Sim - `animator_identifier`

## Desativar Animator de Elemento (`disable_element_animator`)
- **Descrição:** Desativa um animator de elemento
- **Valor Necessário:** Sim - `animator_identifier`

## Redefinir Animator de Elemento (`reset_element_animator`)
- **Descrição:** Redefine a linha do tempo/estado de um animator de elemento
- **Valor Necessário:** Sim - `animator_identifier`

## Imitar Botão Vanilla/Mod (`mimicbutton`)
- **Descrição:** Imita a ação de clique de um botão vanilla ou de mod
- **Valor Necessário:** Sim - `screen_identifier:widget_locator`

## Imitar Tecla de Atalho (`mimic_keybind`)
- **Descrição:** Executa uma tecla de atalho do Minecraft (segurar opcionalmente)
- **Valor Necessário:** Sim - `keybind_id|||keep_pressed_bool|||duration_ms`

## Definir Valor de Campo de Entrada de Texto (`set_text_input_field_value`)
- **Descrição:** Define o valor de um campo de entrada personalizado ou vanilla pelo identificador do elemento.
- **Valor Necessário:** Sim - `element_identifier|||new_value|||force_set_when_inactive`

## Criar Arquivo no Diretório do Jogo (`create_file_in_game_dir`)
- **Descrição:** Cria um arquivo vazio no diretório do jogo (raiz da instância). Aceita o prefixo `.minecraft/` para apontar para o diretório padrão do perfil do launcher (pode ser diferente do diretório da instância atual).
- **Valor Necessário:** Sim - `file_path`

## Excluir Arquivo/Pasta no Diretório do Jogo (`delete_file_in_game_dir`)
- **Descrição:** Exclui um arquivo ou pasta no diretório do jogo (raiz da instância). Aceita o prefixo `.minecraft/` para atingir o perfil padrão do launcher (pode ser diferente da instância em execução). Adicione `*` para excluir **todos os arquivos diretamente dentro** de uma pasta (ignora subpastas; mantém a pasta).
- **Valor Necessário:** Sim - `target_path`

## Copiar Arquivo/Pasta no Diretório do Jogo (`copy_file_in_game_dir`)
- **Descrição:** Copia dentro do diretório do jogo (raiz da instância); o prefixo `.minecraft/` aponta para o perfil padrão do launcher (nem sempre a instância atual). Adicione `*` ao caminho de **origem** para copiar todos os arquivos diretamente dentro dessa pasta (ignora subpastas); o destino deve ser um diretório e não pode usar `*`.
- **Valor Necessário:** Sim - `source||destination`

## Mover Arquivo/Pasta no Diretório do Jogo (`move_file_in_game_dir`)
- **Descrição:** Move dentro do diretório do jogo (raiz da instância); o prefixo `.minecraft/` aponta para o perfil padrão do launcher (pode ser diferente da instância atual). Adicione `*` ao caminho de **origem** para mover todos os arquivos diretamente dentro dessa pasta (ignora subpastas); o destino deve ser um diretório e não pode usar `*`.
- **Valor Necessário:** Sim - `source||destination`

## Renomear Arquivo/Pasta no Diretório do Jogo (`rename_file_in_game_dir`)
- **Descrição:** Renomeia um arquivo ou pasta dentro do diretório do jogo (raiz da instância); o prefixo `.minecraft/` aponta para o perfil padrão do launcher (pode ser diferente da instância atual). Mantém o conteúdo intacto, apenas o nome muda.
- **Valor Necessário:** Sim - `path||new_name`

## Baixar Arquivo para o Diretório do Jogo (`download_file_to_game_dir`)
- **Descrição:** Baixa um arquivo de forma assíncrona para o diretório do jogo (raiz da instância); o prefixo `.minecraft/` aponta para o perfil padrão do launcher (não necessariamente a instância em execução). Informe a **pasta de destino**; o nome do arquivo é derivado automaticamente dos cabeçalhos/URL.
- **Valor Necessário:** Sim - `url||target_folder`

## Extrair Arquivo ZIP no Diretório do Jogo (`extract_zip_file_in_game_dir`)
- **Descrição:** Extrai um arquivo ZIP para uma pasta de destino dentro do diretório do jogo ou do diretório padrão `.minecraft`. Aciona o listener **On ZIP Extracted via Action** quando terminar.
- **Valor Necessário:** Sim - `source_zip_path||target_folder_path`

## Abrir Arquivo/Pasta no Diretório do Jogo (`open_file_folder_in_game_dir`)
- **Descrição:** Abre um arquivo ou pasta com o aplicativo padrão do sistema operacional. O destino deve permanecer dentro do diretório do jogo ou do diretório padrão `.minecraft` por segurança.
- **Valor Necessário:** Sim - `target_path`

## Escrever Arquivo no Diretório do Jogo (`write_file_in_game_dir`)
- **Descrição:** Escreve ou adiciona texto dentro do diretório do jogo (raiz da instância); o prefixo `.minecraft/` aponta para o perfil padrão do launcher (pode ser diferente desta instância). Cria o arquivo se ele não existir. Suporta `\n` no valor para inserir quebras de linha; o modo de anexar é controlado pelo último booleano.
- **Valor Necessário:** Sim - `path|||content|||append_bool`

## Selecionar Arquivo do Sistema (`select_file_to_game_dir`)
- **Descrição:** Abre um seletor de arquivos nativo (qualquer local) e copia o arquivo selecionado para o diretório do jogo (raiz da instância) ou para `.minecraft/` padrão quando houver prefixo (esse padrão pode ser diferente desta instância). Suporta filtros de extensão, rótulo de filtro personalizado e alternância opcional de sobrescrita.
- **Valor Necessário:** Sim - configuração de seleção

## Mostrar Toast (`show_toast`)
- **Descrição:** Exibe uma notificação toast configurável
- **Valor Necessário:** Sim - configuração do toast

## Iniciar Scheduler (`start_scheduler`)
- **Descrição:** Inicia um scheduler pelo seu ID.
- **Valor Necessário:** Sim - `scheduler_id`

## Parar Scheduler (`stop_scheduler`)
- **Descrição:** Para um scheduler pelo seu ID.
- **Valor Necessário:** Sim - `scheduler_id`

## Definir Opção do Minecraft (`edit_minecraft_option`)
- **Descrição:** Edita uma opção de configuração do Minecraft
- **Valor Necessário:** Sim - `option_name:set_to_value`
