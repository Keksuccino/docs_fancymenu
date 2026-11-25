---
title: Requisitos
description: >-
  Exiba elementos e layouts, deixe botões clicáveis ou execute ações somente
  quando algo for verdadeiro, como o horário, o tamanho da janela ou uma
  variável.
sourceBlobSha: 8d7cc9e0182f8478f3a7ab86391e90cae12c626b
---

# Requisitos

Requisitos são condições, como "o mouse está sobre este botão", "estamos em dezembro" ou "um mundo está carregado". Use-os para:

- exibir um [elemento](/elements) apenas em certas ocasiões,
- carregar um layout inteiro apenas em certas ocasiões,
- deixar botões, controles deslizantes e caixas de seleção clicáveis apenas em certas ocasiões,
- executar partes de um [script de ações](/action-scripts) apenas em certas ocasiões.

O FancyMenu verifica os requisitos o tempo todo enquanto um menu está aberto, então os elementos aparecem, desaparecem ou mudam imediatamente. Esta caixa de informações só aparece quando o mouse está sobre "Multiplayer":

<img width="800" alt="Passar o mouse sobre o botão Multiplayer da tela de título exibe uma caixa de informações com o endereço de um servidor ao lado" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_hover.gif?raw=true">

# Onde encontrá-los

| Onde | O que os requisitos fazem |
|---|---|
| Clique com o botão direito em um elemento -> **Loading Requirements** | O elemento só aparece enquanto os requisitos são atendidos. Também funciona com [elementos Vanilla](/vanilla-elements). |
| Clique com o botão direito no plano de fundo do editor -> **Loading Requirements [Layout-Wide]** | O layout inteiro só é carregado enquanto os requisitos são atendidos. Consulte [Requisitos para todo o layout](#requisitos-para-todo-o-layout). |
| Clique com o botão direito em um botão, controle deslizante ou caixa de seleção -> **Control Active State** | O controle só fica clicável enquanto os requisitos são atendidos. Caso contrário, ele fica esmaecido. Botões Vanilla também têm essa opção. |
| IF, ELSE-IF e WHILE em [scripts de ações](/action-scripts#statements) | As ações dentro deles só são executadas enquanto os requisitos são atendidos. |

No editor de layout, os elementos sempre aparecem para que você ainda possa editá-los. Os requisitos dos elementos funcionam fora do editor.

> [!TIP]
> [Visibilidade de elementos](/element-visibility) mostra outras formas de exibir e ocultar elementos, como usar atrasos, efeitos de desvanecimento e alterná-los com um botão.

# Adicionar um requisito

<img width="800" alt="Copiando o ID do botão Multiplayer e, em seguida, definindo o requisito Is Element Hovered para a caixa de informações, com esse ID em Manage Requirements" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_add.gif?raw=true">

1. Clique com o botão direito no elemento e clique em **Loading Requirements**. A janela **Manage Requirements** será aberta.
2. Clique com o botão direito na lista vazia e clique em **Add Requirement**, ou pressione `A`.
3. Clique em uma categoria em **Available Requirements** ou comece a digitar para pesquisar nomes e descrições. **Requirement Description** explica o requisito selecionado.
4. Clique em **Next Step** para definir o valor. Para requisitos sem valor, a opção exibida será **Done**. Um clique duplo em um requisito faz a mesma coisa.
5. Preencha o valor e clique em **Done**. Por exemplo, **Is Element Hovered** precisa do ID do elemento. Clique com o botão direito em um elemento e clique em **Copy Element ID** para obtê-lo.
6. Clique em **Done** na janela **Manage Requirements**.

## Modo do requisito

O botão **Requirement Mode** no seletor de requisitos alterna entre:

- **Normal**: atendido quando a condição é verdadeira.
- **Opposite**: atendido quando a condição NÃO é verdadeira. Por exemplo, **Is World Loaded** no modo Opposite só é atendido nos menus principais.

A janela **Manage Requirements** mostra o modo e o valor de cada requisito.

## Valores

- Os valores aceitam [espaços reservados](/placeholders) e suas [variáveis](/variables#showing-variables-in-text), como `$$coins`. O FancyMenu os substitui sempre que verifica o requisito.
- Muitos campos de valor sugerem opções enquanto você digita, como biomas, IDs de mods, idiomas ou nomes das suas variáveis. Clique em uma sugestão ou pressione `Tab`.
- Requisitos com um valor simples abrem um editor de texto de uma linha. O título indica o que digitar, como **Target Element ID**.

## Gerenciar requisitos

Clique com o botão direito na lista, em um requisito ou em um grupo na janela **Manage Requirements** para acessar estas opções:

| Opção | Atalho | O que faz |
|---|---|---|
| **Add Requirement** | `A` | Adiciona um requisito. |
| **Add Group** | `G` | Adiciona um grupo (veja abaixo). |
| **Edit Requirement** | `Enter` ou clique duplo | Abre o seletor de requisitos com o tipo, o modo e o valor do requisito. |
| **Remove Requirement** / **Remove Group** | `Delete` | Remove o requisito ou grupo. |
| **Undo** / **Redo** | `Ctrl + Z` / `Ctrl + Y` | Desfaz e refaz alterações nesta janela. |
| **Export Requirements for AI** | | Exporta todos os requisitos da janela para um [chat de IA](/export-for-ai), incluindo as alterações não salvas. |

`Up` e `Down` selecionam o requisito acima ou abaixo. **Done** (`Ctrl + S`) salva, e **Cancel** descarta todas as alterações feitas na janela. No macOS, use `Cmd` no lugar de `Ctrl`.

Quando vários elementos estão selecionados, **Loading Requirements** altera os requisitos de todos eles. Se eles tiverem requisitos diferentes, o FancyMenu pergunta antes, pois todos serão substituídos.

# Combinar requisitos

Todos os requisitos em **Manage Requirements** precisam ser atendidos. Para dizer "isto OU aquilo", use um grupo.

Um grupo funciona como um único requisito:

- Modo **And**: tudo no grupo precisa ser atendido. Os grupos novos começam neste modo.
- Modo **Or**: basta que um requisito do grupo seja atendido.

1. Clique com o botão direito na lista e clique em **Add Group**, ou pressione `G`. O grupo recebe um nome como `group_1`.
2. Clique com o botão direito no grupo e clique em **Group Mode** para alternar entre **And** e **Or**.
3. Clique em **Edit Group Requirements** ou dê um clique duplo no grupo. Uma janela semelhante a **Manage Requirements** será aberta para o grupo.
4. Adicione os requisitos do grupo e clique em **Done**.

Por exemplo, para exibir uma saudação de Natal em dezembro ou sempre que o jogador ativar `xmas_lights`: use um grupo Or com **Is Real Time Month** `12` e **Is Variable Value (FM Variable)** para a variável `xmas_lights`, com o valor `on`.

<img width="800" alt="Adicionando um grupo em Manage Requirements, mudando seu modo para Or e adicionando Is Real Time Month e Is Variable Value (FM Variable) a ele" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/requirements_group.gif?raw=true">

- Os grupos podem conter outros grupos, para expressar condições como "(A e B) ou (C e D)". O título da janela mostra onde você está, como `Edit Group: group_1 › group_2`.
- **Edit Group Identifier** renomeia um grupo. Cada nome só pode ser usado uma vez, inclusive dentro de grupos.
- Um grupo vazio no modo **Or** nunca é atendido.

# Requisitos para todo o layout

Os requisitos para todo o layout determinam se um layout inteiro será carregado. Use-os para criar uma versão noturna da tela de título, um layout para cada idioma ou um layout que só apareça no modo para um jogador.

Clique com o botão direito no plano de fundo do editor e clique em **Loading Requirements [Layout-Wide]**. A opção também está em **menu bar -> Layout -> Layout Properties**.

- Se o resultado mudar enquanto o menu estiver aberto, o FancyMenu monta a tela novamente com os layouts cujos requisitos são atendidos naquele momento.
- Eles também funcionam com [layouts universais](/universal-layouts).
- Para ativar e desativar um layout com um botão, coloque o botão em outro layout. Consulte [Ativar e desativar layouts](/element-visibility#turning-layouts-on-and-off).

# Informações úteis

- Requisitos de mundo e de jogador nunca são atendidos quando nenhum mundo está carregado, como nos menus principais.
- Requisitos relacionados a elementos, ao cursor do mouse, a inventários, ao jogador e ao mundo não funcionam em um [Ticker](/elements#ticker) com **Async** ativado. Nesse caso, o FancyMenu exibe um erro com o nome do requisito.
- Requisitos de complementos que você removeu são ignorados. Salvar o layout no editor os remove permanentemente.
- **menu bar -> Customization -> Settings -> Requirement Caching Duration [MS]** reutiliza os resultados dos requisitos por alguns milissegundos, o que deixa layouts grandes mais rápidos. O valor `0` desativa essa opção e é o padrão. O cache pode fazer com que scripts de ações e alterações rápidas tenham resultados inesperados.

# Todos os requisitos

Os requisitos estão organizados como no seletor de requisitos: primeiro por categoria e depois por nome. Requisitos sem categoria ficam no fim do seletor e na seção [Outros](#outros) desta página.

## Interface

### Is Active Cursor Type

**Identificador:** `is_active_cursor_type`

É atendido quando o cursor do mouse tem um formato específico, como **Pointing Hand** sobre um link ou **Writing Cursor** sobre um campo de texto.

- Valor: clique em **Cursor Type** para escolher **Normal**, **Writing Cursor**, **Crosshair**, **Pointing Hand**, **Resize Horizontal**, **Resize Vertical**, **Resize NWSE**, **Resize NESW**, **Resize All** ou **Not Allowed**.

### Is Any Button Hovered

**Identificador:** `fancymenu_visibility_requirement_is_any_button_hovered`

É atendido quando o mouse está sobre qualquer botão visível, Vanilla ou personalizado.

### Is Any Element Hovered

**Identificador:** `fancymenu_visibility_requirement_is_any_element_hovered`

É atendido quando o mouse está sobre qualquer elemento visível, não apenas botões.

### Is Any Screen Open

**Identificador:** `is_any_screen_open`

É atendido quando qualquer menu está aberto, como o menu de pausa ou o inventário. Não é atendido quando você está jogando sem um menu aberto.

### Is Button Active

**Identificador:** `fancymenu_visibility_requirement_is_button_active`

É atendido quando um botão está clicável.

- Valor: o [ID do elemento](/element-identifiers) do botão. Clique com o botão direito nele no editor e clique em **Copy Element ID**.

### Is Customization Menu Bar Visible

**Identificador:** `is_customization_menu_bar_visible`

É atendido quando a barra de menus do FancyMenu está visível. Não é atendido no Modpack Mode ou quando a barra de menus está desativada.

### Is Element Focused

**Identificador:** `is_element_focused`

É atendido quando um elemento está em foco. Botões e controles deslizantes recebem foco quando você clica neles ou navega até eles com as setas ou `Tab`. Navegar até um elemento com o teclado não conta como passar o mouse sobre ele, então coloque este requisito e **Is Element Hovered** em um [grupo Or](#combinar-requisitos) para jogadores que usam o teclado.

- Valor: o [ID do elemento](/element-identifiers), como `mc_titlescreen_multiplayer_button`.

### Is Element Hovered

**Identificador:** `fancymenu_visibility_requirement_is_element_hovered`

É atendido quando o mouse está sobre um elemento. O elemento precisa estar visível.

- Valor: o [ID do elemento](/element-identifiers), como `mc_titlescreen_multiplayer_button` para o botão Multiplayer da tela de título. Clique com o botão direito em um elemento no editor e clique em **Copy Element ID** para obtê-lo.

### Is Element Scrolled to End

**Identificador:** `is_scroll_area_scrolled_to_end`

É atendido quando uma [área rolável](/scrollable-areas) ou um elemento de texto está totalmente rolado até o fim. Um elemento sem conteúdo para rolar é considerado como estando no fim. Útil para um botão **Accept** que só funciona depois que o jogador rolar pelas regras.

- Valor: o [ID do elemento](/element-identifiers) da área rolável ou do elemento de texto.

### Is GUI Scale

**Identificador:** `fancymenu_loading_requirement_is_gui_scale`

É atendido quando a escala da interface do Minecraft corresponde ao valor definido.

- Valor: um número, como `2` para corresponder exatamente a essa escala, `>2` para uma escala maior que 2 ou `<4` para uma escala menor que 4. Também são aceitos decimais, como `<3.5`.
- Separe várias condições com vírgulas. Para números simples, uma delas precisa corresponder, como `2,3`. Todas as condições `>` e `<` precisam corresponder, como `>1,<4`.

### Is Key Pressed

**Identificador:** `is_key_pressed`

É atendido enquanto uma tecla está pressionada. Para executar ações uma vez a cada pressionamento, use o listener [**On Keyboard Key Pressed**](/listeners#on-keyboard-key-pressed).

- Valor: clique em **Change Key** em **Key Selection** e pressione a tecla.

### Is Layout Enabled

**Identificador:** `fancymenu_visibility_requirement_is_layout_enabled`

É atendido enquanto um layout está ativado.

- Valor: o nome do layout, como `winter_title_screen`.

### Is MC Debug Overlay Enabled

**Identificador:** `is_debug_overlay_enabled`

É atendido quando a tela de depuração F3 está visível. Não é atendido quando a interface está oculta com F1.

### Is Modpack Mode Enabled

**Identificador:** `is_modpack_mode_enabled`

É atendido quando o Modpack Mode do FancyMenu está ativado.

### Is Screen Title

**Identificador:** `is_menu_title`

É atendido quando o título da tela aberta corresponde ao valor, como "Options" ou "Game Menu". Este é o título que os jogadores veem, não o [identificador da tela](/screen-identifiers).

- Valor: o texto do título ou sua chave de localização, como `options.title`. A janela de valores exibe ambos para a tela que você está editando e sugere chaves de localização.
- As chaves de localização funcionam em todos os idiomas. O texto do título precisa corresponder exatamente.

## Tempo real

Estes requisitos verificam o relógio do computador do jogador. Separe vários valores com vírgulas: um deles precisa corresponder.

### Is Real Time Day

**Identificador:** `fancymenu_visibility_requirement_is_realtime_day`

É atendido em determinados dias do mês.

- Valor: de `1` a `31`, como `24,25,26`.

### Is Real Time Hour

**Identificador:** `fancymenu_visibility_requirement_is_realtime_hour`

É atendido em determinados horários.

- Valor: de `0` a `23`, como `20,21,22,23` para o período da noite.

### Is Real Time Minute

**Identificador:** `fancymenu_visibility_requirement_is_realtime_minute`

É atendido em determinados minutos da hora.

- Valor: de `0` a `59`.

### Is Real Time Month

**Identificador:** `fancymenu_visibility_requirement_is_realtime_month`

É atendido em determinados meses.

- Valor: de `1` (janeiro) a `12` (dezembro), como `12` para o Natal.

### Is Real Time Second

**Identificador:** `fancymenu_visibility_requirement_is_realtime_second`

É atendido em determinados segundos do minuto.

- Valor: de `0` a `59`.

### Is Real Time Week Day

**Identificador:** `fancymenu_visibility_requirement_is_realtime_week_day`

É atendido em determinados dias da semana.

- Valor: de `1` (domingo) a `7` (sábado), como `1,7` para os fins de semana.

### Is Real Time Year

**Identificador:** `fancymenu_visibility_requirement_is_realtime_year`

É atendido em determinados anos.

- Valor: o ano completo, como `2027`.

## Sistema

### File/Folder Exists

**Identificador:** `fancymenu_loading_requirement_file_exists`

É atendido quando um arquivo ou uma pasta existe.

- Valor: um caminho na pasta do jogo, como `config/mymodpack/welcome_seen.txt`. Caminhos que começam com `.minecraft/` apontam para a pasta `.minecraft` padrão.

### Is Internet Connection Available

**Identificador:** `is_internet_connection_available`

É atendido quando o computador está conectado à internet. O FancyMenu verifica isso em segundo plano de tempos em tempos.

### Is OS Linux

**Identificador:** `fancymenu_loading_requirement_is_os_linux`

É atendido no Linux. Tecnicamente, em qualquer sistema que não seja Windows nem macOS.

### Is OS macOS

**Identificador:** `fancymenu_loading_requirement_is_os_macos`

É atendido no macOS.

### Is OS Windows

**Identificador:** `fancymenu_loading_requirement_is_os_windows`

É atendido no Windows.

### Scheduler Is Running

**Identificador:** `fancymenu_visibility_requirement_is_scheduler_running`

É atendido enquanto um [agendador](/schedulers) está em execução.

- Valor: o identificador do agendador, como `my_scheduler`.

## Janela

Os tamanhos da janela são medidos em pixels reais da janela do jogo, não em pixels da interface. A descrição do requisito mostra o tamanho atual.

### Is Fullscreen

**Identificador:** `fancymenu_loading_requirement_is_fullscreen`

É atendido enquanto o jogo está em tela cheia.

### Is Window Height

**Identificador:** `fancymenu_loading_requirement_is_window_height`

É atendido quando a janela tem uma determinada altura.

- Valor: a altura, como `1080`. Separe várias alturas com vírgulas: uma delas precisa corresponder.

### Is Window Height Bigger Than

**Identificador:** `fancymenu_loading_requirement_is_window_height_bigger_than`

É atendido enquanto a janela é mais alta que o valor definido.

- Valor: a altura, como `1080`.

### Is Window Width

**Identificador:** `fancymenu_loading_requirement_is_window_width`

É atendido quando a janela tem uma determinada largura.

- Valor: a largura, como `1920`. Separe várias larguras com vírgulas: uma delas precisa corresponder.

### Is Window Width Bigger Than

**Identificador:** `fancymenu_loading_requirement_is_window_width_bigger_than`

É atendido enquanto a janela é mais larga que o valor definido.

- Valor: a largura, como `1920`.

## Mundo

Estes requisitos nunca são atendidos quando nenhum mundo está carregado. **Is Player In Structure** e **Is In Active Raid Area** precisam do FancyMenu no servidor. No modo para um jogador, eles sempre funcionam.

### Has Player Absorption Hearts

**Identificador:** `has_player_absorption_hearts`

É atendido enquanto o jogador tem corações dourados de absorção.

### Has Player Permission Level

**Identificador:** `fancymenu_loading_requirement_has_player_permission_level`

É atendido enquanto o jogador tem, no mundo ou no servidor, pelo menos um determinado nível de permissão, como o de operador.

- Valor: de `0` a `4`. O nível `0` é sempre atendido, `2` é suficiente para comandos como `/gamemode`, e `4` é o nível concedido pelo comando `/op`.

### Is Adventure

**Identificador:** `fancymenu_visibility_requirement_is_adventure`

É atendido enquanto o jogador está no modo Aventura.

### Is Any Effect Active

**Identificador:** `is_any_effect_active`

É atendido enquanto o jogador tem qualquer efeito, como Velocidade ou Veneno.

### Is Attack Strength Weakened

**Identificador:** `is_attack_strength_weakened`

É atendido enquanto o ataque do jogador não está totalmente carregado. Isso acontece quando o indicador de ataque é exibido.

### Is Block/Item In Tag

**Identificador:** `is_in_tag`

É atendido quando um bloco ou item pertence a uma tag, como `minecraft:logs` ou `c:tools`. As tags só existem enquanto um mundo está carregado.

- Valor: clique em **Tag Type** para escolher **Block** ou **Item** e, em seguida, informe a **Block/Item Key** e a **Tag**. Ambos os campos sugerem valores. O `#` antes da tag é opcional.
- A chave funciona muito bem com variáveis de listener, como `$$block_key`. Por exemplo, uma instrução IF no script do listener [**On Block Broke**](/listeners#on-block-broke) pode exibir uma notificação somente para troncos.

### Is Camera Perspective

**Identificador:** `is_camera_perspective`

É atendido enquanto a câmera está em uma determinada perspectiva (F5).

- Valor: clique no botão para escolher **First Person**, **Third Person** ou **Front View**.

### Is Clear Weather

**Identificador:** `is_clear_weather`

É atendido quando não está chovendo nem trovejando.

### Is Creative

**Identificador:** `fancymenu_visibility_requirement_is_creative`

É atendido enquanto o jogador está no modo Criativo.

### Is Cursor Holding Inventory Item

**Identificador:** `is_cursor_holding_inventory_item`

É atendido enquanto o cursor do mouse está carregando um item em uma tela de inventário.

### Is Difficulty

**Identificador:** `is_difficulty`

É atendido quando o mundo está em uma determinada dificuldade.

- Valor: `peaceful`, `easy`, `normal` ou `hard`.

### Is Effect Active

**Identificador:** `is_effect_active`

É atendido enquanto o jogador tem um determinado efeito.

- Valor: a chave do efeito, como `minecraft:speed`. O campo sugere efeitos enquanto você está em um mundo.

### Is Entity Nearby

**Identificador:** `is_entity_nearby`

É atendido enquanto há uma entidade de um determinado tipo perto do jogador.

- Valor: a **Entity Registry Key**, como `minecraft:creeper`, e o **Check Radius In Blocks**, como `10`. O campo da chave sugere entidades enquanto você está em um mundo.

### Is Game Mode

**Identificador:** `is_gamemode`

É atendido enquanto o jogador está em um determinado modo de jogo.

- Valor: `survival`, `creative`, `adventure` ou `spectator`.

### Is Hardcore

**Identificador:** `is_hardcore`

É atendido em mundos Hardcore.

### Is Hotbar Slot Selected

**Identificador:** `is_hotbar_slot_active`

É atendido enquanto um determinado espaço da barra de atalhos está selecionado.

- Valor: de `0` (o espaço à esquerda) a `8`.

### Is In Active Raid Area

**Identificador:** `is_in_active_raid_area`

É atendido enquanto o jogador está na área de uma invasão, onde a barra da invasão é exibida. Precisa do FancyMenu no servidor.

### Is Inventory Slot Filled

**Identificador:** `is_inventory_slot_filled`

É atendido enquanto um espaço do inventário do jogador contém um item.

- Valor: o número do espaço. De `0` a `8` correspondem à barra de atalhos; de `9` a `35`, ao restante do inventário.

### Is Item Hovered In Inventory

**Identificador:** `is_item_hovered_in_inventory`

É atendido enquanto o mouse está sobre um item em uma tela de inventário, como o inventário do jogador ou um baú.

### Is Multiplayer

**Identificador:** `fancymenu_loading_requirement_is_multiplayer`

É atendido enquanto o jogador está em um servidor.

### Is Player Creative Flying

**Identificador:** `is_player_creative_flying`

É atendido enquanto o jogador voa no modo Criativo.

### Is Player Flying With Elytra

**Identificador:** `is_player_flying_with_elytra`

É atendido enquanto o jogador plana com uma elytra.

### Is Player Fully Frozen

**Identificador:** `is_player_fully_frozen`

É atendido enquanto o jogador está completamente congelado pela neve fofa, com corações congelados na barra de vida.

### Is Player In Biome

**Identificador:** `is_player_in_biome`

É atendido enquanto o jogador está em um determinado bioma.

- Valor: a chave do bioma, como `minecraft:birch_forest`. O campo sugere biomas enquanto você está em um mundo.

### Is Player In Dimension

**Identificador:** `is_player_in_dimension`

É atendido enquanto o jogador está em uma determinada dimensão.

- Valor: a chave da dimensão: `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end` ou uma dimensão de um mod. O campo sugere dimensões enquanto você está em um mundo.

### Is Player In Fluid

**Identificador:** `is_player_in_fluid`

É atendido enquanto o jogador está em qualquer fluido, como água ou lava.

### Is Player In Lava

**Identificador:** `is_player_in_lava`

É atendido enquanto o jogador está na lava.

### Is Player In Powder Snow

**Identificador:** `is_player_in_powder_snow`

É atendido enquanto o jogador está na neve fofa.

### Is Player In Structure

**Identificador:** `is_player_in_structure`

É atendido enquanto o jogador está dentro de uma determinada estrutura. Precisa do FancyMenu no servidor.

- Valor: a chave da estrutura, como `minecraft:village_plains`. O campo sugere estruturas enquanto você está em um mundo.

### Is Player In Water

**Identificador:** `is_player_in_water`

É atendido enquanto o jogador está na água, mesmo que parcialmente.

### Is Player Jumping or Falling

**Identificador:** `is_player_jumping`

É atendido enquanto o jogador está no ar. Nadar, estar em fluidos, voar com elytra, dormir e rastejar não contam.

### Is Player Left-Handed

**Identificador:** `is_left_handed`

É atendido quando a opção "Main Hand" em Personalização da Skin do Minecraft está definida como "Left".

### Is Player Poisoned

**Identificador:** `is_player_poisoned`

É atendido enquanto o jogador está sob o efeito de Veneno, com corações envenenados na barra de vida.

### Is Player Riding Entity With Health

**Identificador:** `is_player_riding_entity_with_health`

É atendido enquanto o jogador monta uma entidade viva, como um cavalo ou porco. Barcos e carrinhos de mina não contam.

### Is Player Riding Entity/Vehicle

**Identificador:** `is_player_riding_entity`

É atendido enquanto o jogador está montado em qualquer coisa, como um cavalo, barco ou carrinho de mina.

### Is Player Riding Jumpable Entity

**Identificador:** `is_player_riding_jumpable_entity`

É atendido enquanto o jogador monta uma entidade que pode pular, como um cavalo.

### Is Player Running

**Identificador:** `is_player_running`

É atendido enquanto o jogador corre.

### Is Player Sneaking

**Identificador:** `is_player_sneaking`

É atendido enquanto o jogador se esgueira.

### Is Player Swimming

**Identificador:** `is_player_swimming`

É atendido enquanto o jogador nada.

### Is Player Under Water

**Identificador:** `is_player_under_water`

É atendido enquanto a cabeça do jogador está submersa.

### Is Player Using Item

**Identificador:** `is_player_using_item`

É atendido enquanto o jogador usa um item, como ao comer, beber uma poção ou puxar um arco.

### Is Player Wearing Pumpkin

**Identificador:** `is_player_wearing_pumpkin`

É atendido enquanto o jogador usa uma abóbora esculpida na cabeça.

### Is Player Withered

**Identificador:** `is_player_withered`

É atendido enquanto o jogador está sob o efeito de Murchamento, com corações murchos na barra de vida.

### Is Raining

**Identificador:** `is_raining`

É atendido enquanto está chovendo onde o jogador está.

### Is Singleplayer

**Identificador:** `fancymenu_loading_requirement_is_singpleplayer`

É atendido enquanto o jogador está em um mundo para um jogador.

### Is Snowing

**Identificador:** `is_snowing`

É atendido enquanto está nevando onde o jogador está.

### Is Spectator

**Identificador:** `fancymenu_visibility_requirement_is_spectator`

É atendido enquanto o jogador está no modo Espectador.

### Is Survival

**Identificador:** `fancymenu_visibility_requirement_is_survival`

É atendido enquanto o jogador está no modo Sobrevivência.

### Is Thundering

**Identificador:** `is_thundering`

É atendido durante uma tempestade com trovões.

### Is World Loaded

**Identificador:** `fancymenu_loading_requirement_is_world_loaded`

É atendido enquanto o jogador está em um mundo, no modo para um jogador ou multijogador.

### Was Player In Powder Snow

**Identificador:** `was_player_in_powder_snow`

É atendido enquanto o jogador esteve na neve fofa há pouco.

## Outros

### Is Game Language

**Identificador:** `fancymenu_loading_requirement_is_language`

É atendido quando o Minecraft usa um determinado idioma.

- Valor: o código do idioma, como `en_us` ou `de_de`. O campo sugere todos os idiomas.

### Is Mod Loaded

**Identificador:** `fancymenu_loading_requirement_is_mod_loaded`

É atendido quando determinados mods estão instalados.

- Valor: o ID do mod, como `jei`. O campo sugere os IDs dos seus mods. Separe vários IDs com vírgulas: todos precisam estar instalados. `optifine` verifica se o OptiFine está instalado.

### Is Number

**Identificador:** `fancymenu_visibility_requirement_is_number`

Compara dois números. Insira espaços reservados ou variáveis nos campos, como `$$coins`.

- **Compare Mode**: **Equals**, **Bigger Than**, **Smaller Than**, **Bigger Than Or Equals** ou **Smaller Than Or Equals**.
- **Number**: o número a verificar, como `$$coins`.
- **Compare to Number**: o número com o qual comparar, como `100`.

São aceitos números decimais, como `2.5`. Se um campo não contiver um número, o requisito nunca será atendido.

### Is Resource Pack Enabled

**Identificador:** `is_resource_pack_enabled`

É atendido enquanto um pacote de recursos está ativado.

- Valor: o nome do pacote como aparece na tela de Pacotes de Recursos, como `Programmer Art`, ou seu ID. Não diferencia maiúsculas de minúsculas.

### Is Rinku Loaded

**Identificador:** `is_rinku_loaded`

É atendido quando o mod [Rinku](https://modrinth.com/mod/rinku) está instalado. O [elemento Navegador](/elements#browser) e os antigos [tipos de vídeo baseados no Rinku](/video#requirements) precisam dele.

### Is Server IP

**Identificador:** `fancymenu_visibility_requirement_is_server_ip`

É atendido enquanto o jogador está em um servidor específico.

- Valor: o endereço do servidor, como `play.example.net`. Se houver uma porta, como em `play.example.net:25566`, ela também precisa corresponder.

### Is Server Online

**Identificador:** `fancymenu_loading_requirement_is_server_online`

É atendido enquanto um servidor está online. O FancyMenu envia pings em segundo plano a cada 30 segundos, aproximadamente, então pode levar um momento após o jogo iniciar.

- Valor: o endereço do servidor, como `play.example.net`.

### Is Text

**Identificador:** `fancymenu_visibility_requirement_is_text`

Compara dois textos. Insira espaços reservados ou variáveis nos campos, como `$$key_name`.

- **Compare Mode**: **Equals**, **Contains**, **Starts With** ou **Ends With**.
- **Text**: o texto a verificar.
- **Compare to Text**: o texto com o qual comparar.

Maiúsculas e minúsculas fazem diferença.

### Is Variable Value (FM Variable)

**Identificador:** `fancymenu_visibility_requirement_is_variable_value`

É atendido quando uma das suas [variáveis](/variables) tem determinado valor.

- **Variable Name**: o nome da variável, sem `$$`. O campo sugere suas variáveis.
- **Variable Value to Check For**: o valor, como `on`. Ele precisa corresponder ao valor inteiro, incluindo maiúsculas e minúsculas.

Nunca é atendido se a variável não existir. Para uma variável de lista, o requisito compara a matriz JSON de todas as entradas, como `["apple","banana"]`. Para verificar uma única entrada, use **List Contains Entry (FM Variable)**.

### List Contains Entry (FM Variable)

**Identificador:** `list_contains_entry`

É atendido quando uma [variável de lista](/variables#text-and-list-variables) contém determinada entrada.

- **List Variable Name**: o nome da lista, sem `$$`. O campo sugere suas variáveis de lista e avisa quando você digita o nome de uma variável de texto.
- **Entry to Look For**: a entrada. Ela precisa corresponder a uma entrada inteira, não apenas a parte dela.
- **Ignore Case**: quando ativado, `Apple` também corresponde a `apple`.

Nunca é atendido se a lista não existir.

### Mouse Button Is Pressed

**Identificador:** `mouse_click`

É atendido enquanto um botão do mouse está pressionado. Para executar ações uma vez a cada clique, use o listener [**On Mouse Button Clicked**](/listeners#on-mouse-button-clicked).

- Valor: `left` ou `right`.

### Only Once Per Session

**Identificador:** `once_per_session`

É atendido na primeira vez que é verificado e nunca mais até o jogo ser reiniciado. Cada cópia desse requisito funciona de forma independente.

Para elementos que devem aparecer apenas uma vez por sessão de jogo, é mais fácil usar a opção [**Load Once Per Session**](/element-visibility#load-once-per-session) dos elementos: eles permanecem até uma nova tela ser aberta.
