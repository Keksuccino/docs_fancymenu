---
title: Scripts de Ação
description: 'Como usar scripts de ação com botões, sliders, tickers e muito mais.'
---
# Scripts de Ação

Scripts de ação executam tarefas configuradas quando um [Botão](./elements#button) é clicado, um [Ticker](./elements#ticker) é atualizado, um [Slider](./elements#slider) muda, uma tela é aberta ou fechada, ou outro evento compatível ocorre. Declarações como **if**, **else-if**, **else** e **while** adicionam controle condicional.

> [!CAUTION]
> Scripts de ação importados podem modificar arquivos, contatar servidores, abrir links ou executar comandos. Use apenas fontes em que você confia.

<img src="https://github.com/Keksuccino/FancyMenu/blob/master/assets/docs/action_script_editor.png?raw=true" alt="Editor de scripts de ação" style="max-width:800px;width:100%;height:auto;">

# O Que São Ações?

Uma **ação** é uma tarefa ou operação que o FancyMenu executa quando acionada. Por exemplo, uma ação pode abrir uma nova tela, enviar uma mensagem no chat ou ajustar o volume de um [elemento de Áudio](./elements#audio). No editor do FancyMenu, as ações são configuradas com um valor (se necessário) que fornece detalhes extras — como uma URL ou endereço de servidor.

# Declarações

Para criar comportamentos mais complexos, o FancyMenu oferece suporte a declarações de controle em scripts de ação:

| Declaração | Comportamento |
|---|---|
| **If** | Executa suas ações somente quando seus [requisitos](./conditions) forem atendidos. |
| **Else-If** | Verifica outro conjunto de [requisitos](./conditions) quando o **If** ou **Else-If** anterior não foi executado. |
| **Else** | Executa quando nenhum dos requisitos anteriores de **If** ou **Else-If** é atendido. |
| **While** | Repete suas ações enquanto seus [requisitos](./conditions) permanecerem verdadeiros. Ele para após três segundos para evitar loops infinitos; não o use como temporizador. |

# Blocos

Blocos podem ser adicionados aos scripts e oferecem recursos úteis para ter mais controle sobre o fluxo/tempo de execução do script, além de alguns recursos úteis de qualidade de vida:

| Bloco | Comportamento |
|---|---|
| **Delay** | Inicia uma contagem regressiva sem interromper o restante do script. As ações aninhadas tornam-se elegíveis após o atraso; a reinicialização da tela reseta a contagem regressiva. |
| **Execute Later** | Agenda uma nova execução de suas ações aninhadas após o atraso, toda vez que o bloco é alcançado. |
| **Comment** | Adiciona uma nota dentro do script para organização e não executa uma ação. |

# Execução do Script

As ações são executadas de cima para baixo. Uma ação com falha é registrada, e então o script continua.

Downloads, extração de ZIP e solicitações HTTP terminam mais tarde; a próxima ação não espera. Use [**On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action), [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) ou uma variável de resposta HTTP quando o trabalho posterior depender do resultado.

# Onde Você Pode Usar Scripts de Ação?

Scripts de ação são versáteis e podem ser usados em todo o seu layout. Você pode atribuí-los, por exemplo, a:

- [**Botões**](./elements#button): Executa uma ação quando o botão é clicado.
- [**Tickers**](./elements#ticker): Executa continuamente um script de ação para atualizar informações na tela dentro de um layout.
- [**Sliders**](./elements#slider): Aciona um script de ação sempre que o valor do slider muda.
- **Eventos da Tela:** Executa scripts quando uma tela é aberta ou fechada (por exemplo, reproduzir um som quando um menu aparece).
- [**Listeners**](./listeners): Quando um listener recebe seu evento configurado, ele executa seu script de ação.
- [**Schedulers**](./schedulers): Executa ações em intervalos programados, mesmo quando nenhuma tela está aberta.

# Usando Placeholders em Ações

Os valores das ações suportam conteúdo dinâmico por meio de **placeholders**. Na maioria das vezes, esses placeholders usam uma sintaxe semelhante a JSON e são substituídos por dados em tempo real quando a ação é executada.

## Placeholders no Estilo JSON

Estes são os [placeholders](./placeholders) normais que podem ser usados em muitos lugares ao longo dos layouts.

Eles seguem esta sintaxe:

```json
{"placeholder": "placeholder_id", "values": {"key1": "value1", "key2": "value2"}}
```

Eles podem buscar dados do jogo, como o nome do jogador, dimensões da tela ou valores calculados usando o placeholder [**Calculator**](./placeholders#calculator-calc). Você também pode aninhar placeholders para usos mais avançados.

## Placeholders `$$` (Variáveis)

Valores `$$` são valores somente leitura fornecidos a um script de ação específico pelo recurso que o está executando.

Por exemplo, um [Slider](./elements#slider) fornece seu valor atual como `$$value`.

Cada [listener](./listeners) documenta os valores `$$` que fornece, como um botão do mouse pressionado ou uma estrutura inserida.

Os nomes `$$` diferenciam maiúsculas de minúsculas e só funcionam no script que os fornece. Veja [Listeners](./listeners#listener-variables).

## Delimitadores de Valor da Ação

Use o delimitador exato mostrado para cada ação: `:`, `||` ou `|||`. Não há sintaxe de escape para delimitadores dentro de um campo.

Os placeholders são substituídos antes de o valor ser dividido. Para `set_variable`, apenas os dois-pontos iniciais separam o nome do valor, então os dois-pontos posteriores continuam fazendo parte do valor.

## Valores de Texto

Os [códigos de formatação do FancyMenu](./text-formatting#minecraft-text-formatting) usam `&` no lugar do caractere `§` do Minecraft sempre que uma ação aceita texto formatado.

- [**Send Chat Message/Command**](#send-chat-messagecommand-sendmessage) e [**Paste to Chat**](#paste-to-chat-paste_to_chat) aceitam esses códigos de formatação.
- [**Display In Chat [Client-Side]**](#display-in-chat-client-side-display_in_chat_client_side) aceita texto simples ou JSON serializado de componente de texto do Minecraft.
- [**Open URL in Browser**](#open-url-in-browser-openlink) aplica a mesma conversão de códigos de formatação antes de passar a URL para o sistema operacional.

# Como Configurar e Editar Ações

Para editar as ações e blocos de declarações de um elemento, **clique com o botão direito no elemento** e selecione **Manage Action Script**. No editor, você pode:

- **Adicionar novas ações ou declarações:** Insira novas entradas de ação ou declarações de controle (if, else-if, else, while) para montar seu script.
- **Editar ações ou declarações existentes:** Modifique o valor da ação ou altere a lógica de controle.
- **Remover ações ou declarações:** Exclua do script as ações indesejadas.

Crie e edite scripts de listeners por meio de [**Customization -> Manage Listeners**](./listeners#using-listeners).

# Atalhos do Editor de Scripts de Ação

## Atalhos

- `DEL` : Exclui rapidamente a entrada selecionada
- `ENTER` : Inicia a edição em linha da entrada selecionada (ou abre a tela de edição se não houver edição em linha para a entrada selecionada)
- `Ctrl/Command + C` : Copia a ação selecionada (por enquanto, só funciona com ações)
- `Ctrl/Command + V` : Cola a ação copiada anteriormente
- `Ctrl/Command + Z` : Volta um passo (desfazer)
- `Ctrl/Command + Y` : Avança um passo (refazer)
- `ARROW UP` : Navega uma entrada para cima a partir da selecionada atualmente
- `ARROW DOWN` : Navega uma entrada para baixo a partir da selecionada atualmente
- `SHIFT + ARROW UP` : Move a entrada selecionada uma posição para cima
- `SHIFT + ARROW DOWN` : Move a entrada selecionada uma posição para baixo
- `A` : Abre rapidamente a tela de seleção de ações para adicionar uma nova ação
- `Ctrl/Command + S` : Conclui/salva a partir da janela do editor

## Edição

- Dar duplo clique no valor de uma ação permite editar o valor sem abrir a tela completa de edição de valor.
- Cadeias de declarações IF (com declarações ELSE/ELSE-IF anexadas), loops WHILE e pastas podem ser recolhidos (apenas visualmente, não afeta a lógica do script).
- O editor sempre adiciona novas ações abaixo da entrada selecionada (ou aninhadas na cadeia/loop/pasta selecionada).
- Clicar com o botão direito no fundo cinza-escuro da área do script abre um menu de contexto com opções para adicionar ações, declarações e tudo mais importante.

# Ações em Detalhe

Esta seção lista as ações integradas do FancyMenu.

## Next Track (`audio_next_track`)

**Finalidade:** Vai para a próxima faixa em um [elemento de Áudio](./elements#audio)

**Valor:** Obrigatório — `audio_element_identifier` (o ID do elemento de áudio a controlar)

## Previous Track (`audio_previous_track`)

**Finalidade:** Vai para a faixa anterior em um [elemento de Áudio](./elements#audio)

**Valor:** Obrigatório — `audio_element_identifier` (o ID do elemento de áudio a controlar)

## Set Track Volume (`set_audio_element_volume`)

**Finalidade:** Define o volume de um [elemento de Áudio](./elements#audio) (`0.0` a `1.0`)

**Valor:** Obrigatório — `element_identifier:volume`

## Toggle Play/Pause Track (`audio_toggle_play`)

**Finalidade:** Alterna a faixa atual de um [elemento de Áudio](./elements#audio) entre reproduzindo e pausado

**Valor:** Obrigatório — `audio_element_identifier`

## Play Audio (`play_audio`)

**Finalidade:** Reproduz um recurso de áudio uma vez. O áudio iniciado por esta ação pode ser interrompido posteriormente com [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

**Valor:** Obrigatório — configuração JSON com `audioSource`, `soundChannel` e `baseVolume`

**Exemplo:** `{"audioSource":"[source:local]/config/fancymenu/assets/example.ogg","soundChannel":"master","baseVolume":1.0}`

**Comportamento:**

- `baseVolume` é limitado a `0.0`–`1.0`.
- Um canal de som desconhecido usa o canal Master.
- A ação não pode ser executada a partir de um [Ticker](./elements#ticker) assíncrono; o FancyMenu mostra um erro em vez disso.
- O FancyMenu espera até dez segundos para o recurso de áudio ficar pronto.
- Faixas iniciadas com sucesso podem ser interrompidas com [**Stop All Action Audios**](#stop-all-action-audios-stop_all_action_audios).

## Stop All Action Audios (`stop_all_action_audios`)

**Finalidade:** Interrompe todas as faixas de áudio iniciadas pela [ação **Play Audio**](#play-audio-play_audio). Isso não interrompe [elementos de Áudio](./elements#audio), sons de abrir/fechar menu, sons de botão ou outros sistemas de áudio.

**Valor:** Não obrigatório

## Set Video Element Volume (`set_video_element_volume`)

**Finalidade:** Define o volume de um [elemento de Vídeo](./video) (`0.0` a `1.0`)

**Valor:** Obrigatório — `video_element_identifier:volume`

## Set Video Element Play Time (`set_video_element_play_time`)

**Finalidade:** Avança um [elemento de Vídeo](./video) para um timestamp em milissegundos

**Valor:** Obrigatório — `video_element_identifier:timestamp_ms`

## Toggle Video Element Paused State (`toggle_video_element_pause_state`)

**Finalidade:** Alterna o estado de pausa de um [elemento de Vídeo](./video)

**Valor:** Obrigatório — `video_element_identifier`

## Set Video Background Volume (`set_video_menu_background_volume`)

**Finalidade:** Define o volume de um [fundo de menu em vídeo](./video) (`0.0` a `1.0`)

**Valor:** Obrigatório — `background_identifier:volume`

> [!NOTE]
> Para obter o identificador de um fundo, clique com o botão direito no fundo do editor e clique em 'Copy Background Identifier'.

## Set Video Background Play Time (`set_video_menu_background_play_time`)

**Finalidade:** Avança um [fundo de menu em vídeo](./video) para um timestamp em milissegundos

**Valor:** Obrigatório — `background_identifier:timestamp_ms`

> [!NOTE]
> Para obter o identificador de um fundo, clique com o botão direito no fundo do editor e clique em 'Copy Background Identifier'.

## Toggle Video Background Paused State (`toggle_video_menu_background_pause_state`)

**Finalidade:** Alterna o estado de pausa de um [fundo de menu em vídeo](./video)

**Valor:** Obrigatório — `background_identifier`

> [!NOTE]
> Para obter o identificador de um fundo, clique com o botão direito no fundo do editor e clique em 'Copy Background Identifier'.

## Toggle Layout (`toggle_layout`)

**Finalidade:** Alterna um layout (ativar/desativar) pelo nome do arquivo sem `.txt`

**Valor:** Obrigatório — `layout_name`

## Enable Layout (`enable_layout`)

**Finalidade:** Ativa e salva um layout pelo nome do arquivo sem `.txt`

**Valor:** Obrigatório — `layout_name`

## Disable Layout (`disable_layout`)

**Finalidade:** Desativa e salva um layout pelo nome do arquivo sem `.txt`

**Valor:** Obrigatório — `layout_name`

As três ações de layout salvam o estado no arquivo do layout e atualizam a tela atual imediatamente. Use o nome do arquivo com distinção entre maiúsculas e minúsculas, sem `.txt`.

## Open Screen or Custom GUI (`opengui`)

**Finalidade:** Abre uma tela pelo seu identificador (vanilla, mod ou GUI personalizada)

**Valor:** Obrigatório — `screen_identifier`

Copie o identificador exato, com distinção entre maiúsculas e minúsculas, da sobreposição de depuração [Screen Identifiers](./screen-identifiers).

Algumas telas de mods não podem ser criadas diretamente. Se a abertura falhar, use [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button-mimicbutton) em um widget que normalmente abriria essa tela.

## Close Screen (`closegui`)

**Finalidade:** Fecha a tela ativa

**Valor:** Não obrigatório

## Update Screen (`update_screen`)

**Finalidade:** Reinicializa a tela atual

**Valor:** Não obrigatório

## Back to Last Screen (`back_to_last_screen`)

**Finalidade:** Retorna ao pai de uma [GUI personalizada](./custom-guis) ou à instância de tela fechada mais recentemente

**Valor:** Não obrigatório

## Join Server (`joinserver`)

**Finalidade:** Conecta o jogador a um servidor Minecraft

**Valor:** Obrigatório — `server_ip` ou `server_ip:port`

Esta ação não pode ser executada enquanto um mundo ou servidor já estiver carregado. A porta `25565` é usada quando omitida. Se o endereço não estiver na lista de servidores salvos do Minecraft, o FancyMenu o adiciona e salva.

## Enter World (`loadworld`)

**Finalidade:** Entra em um mundo Minecraft

**Valor:** Obrigatório — `world_folder_name`

O valor é o nome da pasta de salvamento. A ação não faz nada se esse salvamento não existir ou se outro mundo/servidor já estiver carregado.

## Enter/Join Last World/Server (`join_last_world`)

**Finalidade:** Entra/conecta ao último mundo ou servidor em que o jogador esteve

**Valor:** Não obrigatório

Esta ação não pode ser executada enquanto outro mundo/servidor estiver carregado. Um servidor lembrado que não está na lista de servidores salvos do Minecraft é adicionado e salvo antes da conexão.

## Leave World or Server (`disconnect_server_or_world`)

**Finalidade:** Sai de um mundo ou servidor e abre uma tela especificada

**Valor:** Obrigatório — `screen_identifier`

Esta ação só é executada enquanto um mundo e um jogador estiverem carregados. O destino pode ser um identificador de [GUI personalizada](./custom-guis) ou um [identificador de tela](./screen-identifiers) que o FancyMenu consiga construir. Se o destino não puder ser aberto, o FancyMenu retorna para a tela de Título.

## Quit Minecraft (`quitgame`)

**Finalidade:** Encerra o Minecraft completamente

**Valor:** Não obrigatório

## Send Chat Message/Command (`sendmessage`)

**Finalidade:** Envia uma mensagem de chat ou executa um comando de chat. O texto da mensagem aceita [códigos de formatação do FancyMenu](./text-formatting#minecraft-text-formatting).

**Valor:** Obrigatório — `message_text` ou `/command_text`

## Execute Command As Integrated Server (`execute_command_as_integrated_server`)

**Finalidade:** Executa forçadamente um comando no singleplayer como o servidor integrado, ignorando permissões e a configuração de cheats.

**Valor:** Obrigatório — texto do comando, por exemplo `/give @p minecraft:diamond 1`

> [!WARNING]
> Esta ação só funciona no singleplayer enquanto o mundo **não estiver aberto para LAN**. Ela intencionalmente não faz nada quando não existe servidor integrado ou quando o servidor integrado está publicado para LAN.

## Paste to Chat (`paste_to_chat`)

**Finalidade:** Cola texto formatado no campo de entrada do chat enquanto um jogador/mundo está carregado

**Valor:** Obrigatório — `true:Text` ou `false:Text`

Quando o chat ainda não está aberto, o FancyMenu o abre e define o texto de entrada. Quando o chat já está aberto, `true` acrescenta ao texto existente e `false` o substitui.

## Display In Chat [Client-Side] (`display_in_chat_client_side`)

**Finalidade:** Exibe uma mensagem de chat do lado do cliente enquanto um mundo ou servidor está carregado. Nada é enviado ao servidor.

**Valor:** Obrigatório — `text_or_json`

O valor pode ser texto simples ou um componente de texto serializado do Minecraft. A ação não faz nada quando nenhum mundo está carregado.

## Send FM Data To Server (`send_fm_data_to_server`)

**Finalidade:** Envia [FM Data](./fm-data) para o servidor atual do FancyMenu.

**Valor:** Obrigatório — `data_identifier||data`

## Connect To Remote Server (`connect_to_remote_server`)

**Finalidade:** Abre ou reutiliza uma conexão WebSocket iniciada pelo cliente com um servidor remoto externo.

**Valor:** Obrigatório — URL do servidor remoto, por exemplo `wss://example.com/ws`

Veja [Remote Server Communication](./remote-server-communication#url-modes) para os formatos de URL aceitos.

## Send Data To Remote Server (`send_data_to_remote_server`)

**Finalidade:** Abre ou reutiliza uma conexão com servidor remoto e envia dados de texto para ela.

**Valor:** Obrigatório — `remote_server_url||data`

## Close Remote Server Connection (`close_remote_server_connection`)

**Finalidade:** Fecha uma conexão específica com servidor remoto por ID da solicitação.

**Valor:** Obrigatório — ID da solicitação, geralmente `$$request_id` de [**On Remote Server Connected**](./listeners#on-remote-server-connected-remote_server_connected)

## Close All Remote Server Connections (`close_all_remote_server_connections`)

**Finalidade:** Fecha todas as conexões ativas com servidor remoto abertas pelo FancyMenu.

**Valor:** Não obrigatório

## Open URL in Browser (`openlink`)

**Finalidade:** Envia uma URL ao manipulador padrão do sistema operacional sem um prompt de confirmação do FancyMenu

**Valor:** Obrigatório — `https://example.com`

Use links `https://` confiáveis. O FancyMenu não mostra um prompt de confirmação antes de passar a URL para o sistema operacional.

## Copy Text to Clipboard (`copytoclipboard`)

**Finalidade:** Copia texto para a área de transferência

**Valor:** Obrigatório — `text_to_copy`

## Print to Game Log (`print_to_log`)

**Finalidade:** Escreve uma linha no log do jogo

**Valor:** Obrigatório — `text_to_log`

## Set Variable Value (FM Variable) (`set_variable`)

**Finalidade:** Armazena conteúdo de texto em uma [variável do FancyMenu](./variables)

**Valor:** Obrigatório — `variable_name:variable_value`

Os dois-pontos iniciais separam o nome do valor. Dois-pontos posteriores continuam fazendo parte do valor. As alterações são salvas imediatamente.

## Clear All Variables (FM Variable) (`clear_variables`)

**Finalidade:** Limpa todos os valores armazenados de [variáveis do FancyMenu](./variables)

**Valor:** Não obrigatório

## Send HTTP Request (`send_http_request`)

**Finalidade:** Inicia uma solicitação HTTP/HTTPS em segundo plano; pode registrar e/ou armazenar a resposta em uma variável

**Valor:** Obrigatório — configuração da solicitação HTTP

| Configuração | Comportamento |
|---|---|
| URL | Endpoint HTTP ou HTTPS |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` ou `OPTIONS` |
| Body | Enviado para métodos diferentes de `GET` e `HEAD` |
| Content type | Valor `Content-Type` da solicitação |
| Timeout | Segundos usados tanto para conexão quanto para leitura da resposta |
| Log response | Lê e grava a resposta no log |
| Response variable | Lê a resposta e a armazena após a conclusão da solicitação |
| Single-line response | Remove quebras de linha da resposta antes de armazená-la |
| Authentication | None, Basic, Bearer ou API key |
| Headers | Cabeçalhos personalizados opcionais da solicitação |

As solicitações são executadas de forma assíncrona, então a próxima ação não espera. Os corpos das respostas só são lidos quando o registro está ativado ou uma variável de resposta está configurada; corpos sem sucesso são lidos a partir da resposta de erro. Não armazene senhas ou tokens de acesso na configuração da ação.

## Manage Resource Pack (`manage_resource_pack`)

**Finalidade:** Ativa, desativa ou alterna um pacote de recursos, com recarregamento opcional

**Valor:** Obrigatório — `pack_name_or_id|||MODE|||reload_bool`

Nomes exibidos e IDs internos de pacotes são correspondidos sem diferenciar maiúsculas de minúsculas. Pacotes marcados como obrigatórios não podem ser desativados.

## Reload Resource Packs (`reload_resource_packs`)

**Finalidade:** Recarrega os pacotes de recursos do Minecraft. Um cooldown interno de cinco segundos ignora gatilhos repetidos durante esse período para evitar spam de recarregamento.

**Valor:** Não obrigatório

## Reload FancyMenu (`reloadmenu`)

**Finalidade:** Recarrega layouts, [GUIs personalizadas](./custom-guis), [panoramas](./panoramas), [slideshows](./slideshows), configurações e recursos gerenciados pelo FancyMenu

**Valor:** Não obrigatório

Isso não recarrega os pacotes de recursos do Minecraft. Use [**Reload Resource Packs**](#reload-resource-packs-reload_resource_packs) para isso.

> [!WARNING]
> Recarregar é caro em termos de desempenho. Acione isso por meio de uma ação deliberada de botão, e não por um [Ticker](./elements#ticker) ou por um [listener](./listeners) acionado com frequência.

## Toggle Element Animator (`toggle_element_animator`)

**Finalidade:** Alterna o estado salvo de reprodução e reseta a linha do tempo ativa correspondente do Animator

**Valor:** Obrigatório — `animator_identifier`

Veja [Element Animator](./element-animator) para configuração e detalhes do identificador.

## Enable Element Animator (`enable_element_animator`)

**Finalidade:** Ativa a reprodução; uma linha do tempo ativa do Animator só é redefinida quando o estado muda de desativado para ativado

**Valor:** Obrigatório — `animator_identifier`

## Disable Element Animator (`disable_element_animator`)

**Finalidade:** Desativa a reprodução e reseta a linha do tempo ativa correspondente do Animator

**Valor:** Obrigatório — `animator_identifier`

## Reset Element Animator (`reset_element_animator`)

**Finalidade:** Reseta a linha do tempo ativa correspondente do Animator sem alterar se a reprodução está ativada

**Valor:** Obrigatório — `animator_identifier`

## Mimic Vanilla/Mod Button (`mimicbutton`)

**Finalidade:** Imita a ação de clique de um botão vanilla ou de mod

**Valor:** Obrigatório — o [localizador de widget](./widget-locators) completo, por exemplo `example.menu.identifier:505280`

## Mimic Keybind (`mimic_keybind`)

**Finalidade:** Executa um atalho de teclado ou mouse do Minecraft, opcionalmente mantendo-o pressionado

**Valor:** Obrigatório — `keybind_id|||keep_pressed_bool|||duration_ms`

| Campo | Significado |
|---|---|
| `keybind_id` | Identificador do atalho do Minecraft, como `key.jump` |
| `keep_pressed_bool` | `true` para manter a tecla pressionada; `false` para um pressionamento normal |
| `duration_ms` | Duração de pressão quando `keep_pressed_bool` é `true`; padrão `1000` |

## Set Text Input Field Value (`set_text_input_field_value`)

**Finalidade:** Define o valor de um [campo de entrada de texto](./elements#text-input-field) personalizado ou Vanilla por identificador do elemento.

**Valor:** Obrigatório — `element_identifier|||new_value|||force_set_when_inactive`

Os três campos devem ser separados com o delimitador triple-pipe `|||`. Defina `force_set_when_inactive` como `true` para atualizar também um campo de entrada desativado; quando for `false`, campos inativos permanecem inalterados.

## Create File in Game Directory (`create_file_in_game_dir`)

**Finalidade:** Cria um arquivo vazio relativo ao diretório de jogo ativo. Aceita o prefixo `.minecraft/` para usar o diretório convencional do Minecraft (que pode ser diferente da instância atual).

**Valor:** Obrigatório — `file_path`

Exemplo: `config/some_mod_folder/new_file.txt`. Diretórios pai ausentes são criados; um arquivo existente permanece inalterado.

## Delete File/Folder in Game Directory (`delete_file_in_game_dir`)

**Finalidade:** Exclui um arquivo ou exclui recursivamente uma pasta relativa ao diretório de jogo ativo. Aceita `.minecraft/` para usar o diretório convencional do Minecraft. Adicione `*` para excluir **todos os arquivos diretamente dentro** de uma pasta (ignora subdiretórios e mantém a pasta).

**Valor:** Obrigatório — `target_path`

Por exemplo, `config/downloads/*` exclui os arquivos diretamente dentro de `config/downloads/`, mas não percorre nem exclui seus subdiretórios.

## Copy File/Folder in Game Directory (`copy_file_in_game_dir`)

**Finalidade:** Copia dentro do diretório de jogo ativo; `.minecraft/` usa o diretório convencional do Minecraft. Um diretório nomeado é copiado recursivamente. Adicione `*` ao caminho de **origem** para copiar apenas cada arquivo filho direto; o destino deve ser um diretório e não pode usar `*`.

**Valor:** Obrigatório — `source||destination`

Por exemplo, `config/source/*||config/destination/` copia apenas os arquivos diretamente dentro de `config/source/`. Com uma origem curinga, o FancyMenu cria o diretório de destino quando necessário, mas não copia nenhum subdiretório da origem. A cópia recusa qualquer destino existente/arquivo em conflito em vez de sobrescrevê-lo.

## Move File/Folder in Game Directory (`move_file_in_game_dir`)

**Finalidade:** Move dentro do diretório de jogo ativo; `.minecraft/` usa o diretório convencional do Minecraft. Adicione `*` ao caminho de **origem** para mover apenas cada arquivo filho direto; o destino deve ser um diretório e não pode usar `*`.

**Valor:** Obrigatório — `source||destination`

Por exemplo, `config/source/*||config/destination/` move apenas os arquivos diretamente dentro de `config/source/`. Com uma origem curinga, o FancyMenu cria o diretório de destino quando necessário, mas deixa os subdiretórios de origem no lugar. A movimentação recusa um destino existente/arquivo em conflito em vez de sobrescrevê-lo.

## Rename File/Folder in Game Directory (`rename_file_in_game_dir`)

**Finalidade:** Renomeia um arquivo ou pasta dentro de sua pasta pai atual; `.minecraft/` usa o diretório convencional do Minecraft. Mantém o conteúdo intacto e recusa um nome de destino já existente.

**Valor:** Obrigatório — `path||new_name`

## Download File to Game Directory (`download_file_to_game_dir`)

**Finalidade:** Faz o download de um arquivo em segundo plano para um diretório relativo ao diretório de jogo ativo; `.minecraft/` usa o diretório convencional do Minecraft.

**Valor:** Obrigatório — `url||target_folder`

O segundo campo é um **diretório de destino**, não um caminho completo de arquivo de destino. O FancyMenu cria o diretório quando necessário e determina o nome do arquivo a partir do cabeçalho `Content-Disposition` da resposta, depois recorre ao caminho da URL. O nome resolvido é decodificado e sanitizado antes do uso; se nenhuma das fontes fornecer um nome utilizável, o FancyMenu gera um. Um arquivo existente com o mesmo nome é sobrescrito.

O [**listener On File Downloaded via Action**](./listeners#on-file-downloaded-via-action-file_downloaded_via_action) é acionado após tentativas de download bem-sucedidas e malsucedidas e expõe a URL, o caminho de destino resolvido e o estado de sucesso.

Em caso de sucesso, `$$target_file_path` é o caminho do arquivo salvo. Em caso de falha, ele pode conter apenas o diretório de destino porque nenhum nome final de arquivo foi resolvido.

## Extract ZIP File In Game Directory (`extract_zip_file_in_game_dir`)

**Finalidade:** Extrai um ZIP para uma pasta de destino dentro do diretório de jogo ativo ou do diretório convencional `.minecraft`. Aciona [**On ZIP Extracted via Action**](./listeners#on-zip-extracted-via-action-zip_extracted_via_action) quando terminar.

**Valor:** Obrigatório — `source_zip_path||target_folder_path`

Arquivos existentes com nomes correspondentes são substituídos. Extraia apenas arquivos ZIP confiáveis.

## Open File/Folder In Game Directory (`open_file_folder_in_game_dir`)

**Finalidade:** Abre um arquivo ou pasta com o aplicativo padrão do sistema operacional. O destino deve permanecer dentro do diretório de jogo ou do diretório padrão `.minecraft` por motivos de segurança.

**Valor:** Obrigatório — `target_path`

## Write File in Game Directory (`write_file_in_game_dir`)

**Finalidade:** Escreve ou acrescenta texto relativo ao diretório de jogo ativo; `.minecraft/` usa o diretório convencional do Minecraft. Cria o arquivo e os diretórios pai, se estiverem ausentes. `\n` insere quebras de linha; `append_bool=false` substitui um arquivo existente.

**Valor:** Obrigatório — `path|||content|||append_bool`

## Select File from System (`select_file_to_game_dir`)

**Finalidade:** Abre um seletor nativo de arquivos e copia o arquivo selecionado para dentro do diretório de jogo ativo, ou do `.minecraft/` convencional quando prefixado. Suporta filtros de extensão, um rótulo de filtro personalizado e um alternador de sobrescrita.

**Valor:** Obrigatório — `target_path|||filter_description|||extensions|||overwrite_bool`

`target_path` é o caminho completo do arquivo de destino. Separe várias extensões com `;` ou `,`, por exemplo `png;jpg`; uma lista vazia de extensões permite todos os arquivos. Se `overwrite_bool` for `false`, a ação falha em vez de substituir um arquivo de destino existente.

O [**listener On File Selected**](./listeners#on-file-selected-file_selected_via_action) é acionado quando o arquivo é copiado, o seletor é cancelado ou a seleção falha. Ele expõe o caminho selecionado, o caminho de destino resolvido, os estados de sucesso/cancelado e um motivo da falha.

## Show Toast (`show_toast`)

**Finalidade:** Exibe uma notificação toast configurável

**Valor:** Obrigatório — configuração JSON do toast

O editor armazena esta ação como JSON. Prefira a janela de configuração em vez de editar o valor manualmente.

| Campo | Significado |
|---|---|
| `width` | Limitado a `120`–`320` pixels |
| `durationMs` | Limitado a `1000`–`600000` milissegundos |
| `title` | Texto simples, um componente de texto serializado do Minecraft ou vazio |
| `message` | Texto simples, um componente de texto serializado ou vazio |
| `iconSource` | [Fonte de imagem](./resources) opcional |
| `backgroundSource` | [Fonte de imagem](./resources) opcional |

## Start Scheduler (`start_scheduler`)

**Finalidade:** Inicia um scheduler pelo seu ID.

**Valor:** Obrigatório — `scheduler_id`

Veja [Schedulers](./schedulers) para criar e gerenciar IDs de scheduler.

## Stop Scheduler (`stop_scheduler`)

**Finalidade:** Interrompe um scheduler pelo seu ID.

**Valor:** Obrigatório — `scheduler_id`

## Set Minecraft Option (`edit_minecraft_option`)

**Finalidade:** Edita uma opção de configuração do Minecraft

**Valor:** Obrigatório — `option_name:set_to_value`
