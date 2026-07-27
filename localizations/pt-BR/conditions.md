---
title: Condições (Requisitos)
description: Como usar requisitos de carregamento.
---

# Requisitos

Requisitos (chamados **Requisitos de Carregamento** em alguns menus) mostram ou ocultam conteúdo com base em condições como estado de hover, tamanho da janela ou se um mundo está carregado.

Você pode usá-los em [elementos](./elements), em layouts inteiros e em [scripts de ação](./action-scripts).

# Adicionando Requisitos a Elementos

Para adicionar requisitos a um elemento, clique com o botão direito nele e selecione **Requisitos de Carregamento**.

Os requisitos são verificados enquanto o menu está aberto, então os elementos são atualizados quando uma condição muda.

# Requisitos em Todo o Layout

Você também pode alterar a visibilidade de layouts inteiros clicando com o botão direito no **fundo do editor** e depois em **Requisitos de Carregamento [Em Todo o Layout]**.

Quando o resultado em todo o layout muda, o FancyMenu reconstrói a tela atual e aplica os layouts cujos requisitos agora são atendidos.

# Scripts de Ação

Requisitos também podem ser usados em scripts de ação.
Você pode adicioná-los na tela do editor de scripts de ação e usá-los para executar ações específicas somente se a condição do requisito for atendida.

# Combinando Requisitos

- Requisitos fora de grupos usam **AND**, então todos eles precisam ser atendidos.
- Dentro de um grupo, escolha **AND** ou **OR**.
- Use **IF NOT** para inverter um requisito.

Essas regras são as mesmas para elementos, layouts e scripts de ação.

# Valores dos Requisitos

Para requisitos que precisam de um valor, use **Editar Valor do Requisito** e siga a descrição mostrada no editor. Alguns campos suportam conclusão com **TAB**.

Se um requisito importado parar de funcionar após alterar o FancyMenu ou complementos, edite-o na tela de requisitos e verifique `logs/latest.log` em busca de erros.

O editor de requisitos oferece suporte a um menu de contexto com clique com o botão direito, navegação por teclado, busca, desfazer/refazer (`Ctrl/Command + Z` / `Ctrl/Command + Y`) e `Ctrl/Command + S` para salvar.

# Requisitos em Detalhe

Esta seção lista os requisitos integrados do FancyMenu.

## O Elemento Está em Hover (`fancymenu_visibility_requirement_is_element_hovered`)

**Finalidade:** Verifica se um elemento específico está com o cursor do mouse sobre ele.

**Valor:** Obrigatório — [Identificador do elemento](./element-identifiers) de destino (por exemplo, `some_element_ID`).

## O Elemento Está Focado (`is_element_focused`)

**Finalidade:** Verifica se um elemento específico está atualmente com foco do teclado (por exemplo, um campo de texto ou um botão focado).

**Valor:** Obrigatório — ID do elemento de destino (o mesmo ID mostrado no editor)

> [!NOTE]
> Foco e hover são estados diferentes. Um elemento pode manter sua aparência de foco depois que o ponteiro sai dele; clicar ou navegar pelo teclado pode dar foco a ele.

## Algum Elemento Está em Hover (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Finalidade:** Verifica elementos visíveis/renderizáveis na camada de personalização ativa atual, incluindo elementos adicionados por layouts empilhados.

**Valor:** Não é obrigatório

## Algum Botão Está em Hover (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Finalidade:** Verifica se qualquer botão vanilla ou personalizado visível/renderizável na camada de personalização ativa atual está em hover, incluindo botões adicionados por layouts empilhados.

**Valor:** Não é obrigatório

## O Layout Está Ativado (`fancymenu_visibility_requirement_is_layout_enabled`)

**Finalidade:** Verifica se um layout específico está ativado no momento.

**Valor:** Obrigatório — Nome do layout (por exemplo, `my_cool_main_menu_layout`)

## O Agendador Está em Execução (`fancymenu_visibility_requirement_is_scheduler_running`)

**Finalidade:** Verifica se um [agendador](./schedulers) está em execução no momento.

**Valor:** Obrigatório — ID do agendador (por exemplo, `my_scheduler`)

## É Escala da GUI (`fancymenu_loading_requirement_is_gui_scale`)

**Finalidade:** Verifica se a escala atual da GUI corresponde a certas condições.

**Valor:** Obrigatório — Use um número para igualdade, `>` para maior que, ou `<` para menor que.

Várias condições separadas por vírgula são combinadas com AND. Por exemplo, `>1,<4` só é atendido quando a escala da GUI é maior que `1` e menor que `4`.

## Botão Está Ativo (`fancymenu_visibility_requirement_is_button_active`)

**Finalidade:** Verifica se um botão específico está ativo (clicável).

**Valor:** Obrigatório — ID do elemento do botão de destino (por exemplo, "some_element_ID")

## É o Título da Tela (`is_menu_title`)

**Finalidade:** Verifica se o título exibido da tela corresponde a um texto específico ou chave de localização. Isso verificará apenas o nome/título exibido da tela, como "Options" ou "Pause". NÃO verificará o identificador do menu/tela (como `title_screen`)!

**Valor:** Obrigatório — O texto exato do título ou a chave de localização da tela

## Tecla Está Pressionada (`is_key_pressed`)

**Finalidade:** Verifica se uma tecla específica do teclado está sendo pressionada no momento.

**Valor:** Obrigatório — O código da tecla de destino. Selecionado por meio de uma interface ao editar o valor do requisito.

## Alguma Tela Está Aberta (`is_any_screen_open`)

**Finalidade:** Verifica se qualquer tela/menu está aberta no momento (retorna falso se nenhuma tela estiver sendo exibida).

**Valor:** Não é obrigatório

## O Overlay de Debug do MC Está Ativado (`is_debug_overlay_enabled`)

**Finalidade:** Verifica se o overlay de debug do F3 está visível no momento.

**Valor:** Não é obrigatório

## Tipo de Cursor Ativo (`is_active_cursor_type`)

**Finalidade:** Verifica se o tipo de cursor atualmente ativo do FancyMenu corresponde a um tipo de cursor padrão específico.

**Valor:** Obrigatório — Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` ou `not_allowed`

## Barra do Menu de Personalização Está Visível (`is_customization_menu_bar_visible`)

**Finalidade:** Verifica se a barra do menu de personalização do FancyMenu está visível no momento.

**Valor:** Não é obrigatório

## Modo de Modpack Está Ativado (`is_modpack_mode_enabled`)

**Finalidade:** Verifica se o Modo de Modpack do FancyMenu está ativado.

**Valor:** Não é obrigatório

## Botão do Mouse Está Pressionado (`mouse_click`)

**Finalidade:** Retorna verdadeiro enquanto um botão específico do mouse estiver pressionado. Isso não é um evento de clique único; use o [**listener On Mouse Button Clicked**](./listeners#on-mouse-button-clicked-mouse_button_clicked) quando uma ação precisar ser executada uma vez por clique.

**Valor:** Obrigatório — `left` ou `right` para indicar qual botão do mouse verificar

## Está em Tela Cheia (`fancymenu_loading_requirement_is_fullscreen`)

**Finalidade:** Verifica se o jogo está atualmente em modo de tela cheia.

**Valor:** Não é obrigatório

## Largura da Janela é (`fancymenu_loading_requirement_is_window_width`)

**Finalidade:** Verifica se a largura da janela do jogo corresponde a valores específicos.

**Valor:** Obrigatório — Largura da janela em pixels (por exemplo, "1920"). Vários valores podem ser fornecidos separando por vírgulas.

## Altura da Janela é (`fancymenu_loading_requirement_is_window_height`)

**Finalidade:** Verifica se a altura da janela do jogo corresponde a valores específicos.

**Valor:** Obrigatório — Altura da janela em pixels (por exemplo, "1080"). Vários valores podem ser fornecidos separando por vírgulas.

## Largura da Janela é Maior que (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Finalidade:** Verifica se a largura da janela do jogo é maior que um valor específico.

**Valor:** Obrigatório — Largura da janela em pixels (por exemplo, "1920")

## Altura da Janela é Maior que (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Finalidade:** Verifica se a altura da janela do jogo é maior que um valor específico.

**Valor:** Obrigatório — Altura da janela em pixels (por exemplo, "1080")

## Está em Multijogador (`fancymenu_loading_requirement_is_multiplayer`)

**Finalidade:** Verifica se o jogador está atualmente em um mundo multijogador.

**Valor:** Não é obrigatório

## Está em Jogo Solo (`fancymenu_loading_requirement_is_singpleplayer`)

**Finalidade:** Verifica se o jogador está atualmente em um mundo solo.

**Valor:** Não é obrigatório

## O Mundo Está Carregado (`fancymenu_loading_requirement_is_world_loaded`)

**Finalidade:** Verifica se algum mundo está carregado no momento.

**Valor:** Não é obrigatório

## Está em Aventura (`fancymenu_visibility_requirement_is_adventure`)

**Finalidade:** Verifica se o jogador está atualmente no modo aventura.

**Valor:** Não é obrigatório

## Está em Criativo (`fancymenu_visibility_requirement_is_creative`)

**Finalidade:** Verifica se o jogador está atualmente no modo criativo.

**Valor:** Não é obrigatório

## Está em Espectador (`fancymenu_visibility_requirement_is_spectator`)

**Finalidade:** Verifica se o jogador está atualmente no modo espectador.

**Valor:** Não é obrigatório

## Está em Sobrevivência (`fancymenu_visibility_requirement_is_survival`)

**Finalidade:** Verifica se o jogador está atualmente no modo sobrevivência.

**Valor:** Não é obrigatório

## É Modo de Jogo (`is_gamemode`)

**Finalidade:** Verifica se o jogador está em um modo de jogo específico.

**Valor:** Obrigatório — Nome do modo de jogo (por exemplo, "creative", "survival", "adventure", "spectator")

## É Dificuldade (`is_difficulty`)

**Finalidade:** Verifica se a dificuldade atual do jogo corresponde a um valor específico.

**Valor:** Obrigatório — Nome da dificuldade (por exemplo, "peaceful", "easy", "normal", "hard")

## Está em Hardcore (`is_hardcore`)

**Finalidade:** Verifica se o mundo carregado atualmente está no modo hardcore.

**Valor:** Não é obrigatório

## É Perspectiva da Câmera (`is_camera_perspective`)

**Finalidade:** Verifica se a perspectiva atual da câmera corresponde a uma perspectiva específica.

**Valor:** Obrigatório — `first_person`, `third_person_back` ou `third_person_front`

## Está Chovendo (`is_raining`)

**Finalidade:** Verifica se está chovendo atualmente na localização do jogador.

**Valor:** Não é obrigatório

## Está Trovejando (`is_thundering`)

**Finalidade:** Verifica se há uma tempestade com trovões atualmente no mundo do jogador.

**Valor:** Não é obrigatório

## O Clima Está Limpo (`is_clear_weather`)

**Finalidade:** Verifica se o clima está limpo no momento (sem chuva ou trovões).

**Valor:** Não é obrigatório

## Está Nevando (`is_snowing`)

**Finalidade:** Verifica se está nevando atualmente na localização do jogador.

**Valor:** Não é obrigatório

## Jogador Está Correndo (`is_player_running`)

**Finalidade:** Verifica se o jogador está atualmente correndo em sprint.

**Valor:** Não é obrigatório

## Jogador Está Agachado (`is_player_sneaking`)

**Finalidade:** Verifica se o jogador está atualmente agachado/abaixado.

**Valor:** Não é obrigatório

## Jogador Está Usando Item (`is_player_using_item`)

**Finalidade:** Verifica se o jogador está usando um item no momento.

**Valor:** Não é obrigatório

## Jogador Está Nadando (`is_player_swimming`)

**Finalidade:** Verifica se o jogador está nadando no momento.

**Valor:** Não é obrigatório

## Jogador Está Pulando ou Caindo (`is_player_jumping`)

**Finalidade:** Retorna verdadeiro enquanto o jogador estiver no ar em um estado normal de salto ou queda. Natação, fluidos, voo com elytra, dormir, natação visual e rastejar são excluídos.

**Valor:** Não é obrigatório

## Jogador Está Debaixo d'Água (`is_player_under_water`)

**Finalidade:** Verifica se o jogador está completamente debaixo d'água.

**Valor:** Não é obrigatório

## Jogador Está na Água (`is_player_in_water`)

**Finalidade:** Verifica se o jogador está na água (pode estar parcialmente submerso).

**Valor:** Não é obrigatório

## Jogador Está na Lava (`is_player_in_lava`)

**Finalidade:** Verifica se o jogador está na lava.

**Valor:** Não é obrigatório

## Jogador Está em Fluido (`is_player_in_fluid`)

**Finalidade:** Verifica se o jogador está em qualquer fluido (água, lava etc.).

**Valor:** Não é obrigatório

## Jogador Está Montado em Entidade/Veículo (`is_player_riding_entity`)

**Finalidade:** Verifica se o jogador está montado em qualquer entidade.

**Valor:** Não é obrigatório

## Jogador Está Montado em Entidade que Pode Pular (`is_player_riding_jumpable_entity`)

**Finalidade:** Verifica se o jogador está montado em uma entidade que pode pular (como um cavalo).

**Valor:** Não é obrigatório

## Jogador Está Montado em Entidade com Vida (`is_player_riding_entity_with_health`)

**Finalidade:** Verifica se o jogador está montado em uma entidade viva com vida (como animais, não barcos).

**Valor:** Não é obrigatório

## Jogador Está em Neve em Pó (`is_player_in_powder_snow`)

**Finalidade:** Verifica se o jogador está atualmente em neve em pó.

**Valor:** Não é obrigatório

## O Jogador Estava em Neve em Pó (`was_player_in_powder_snow`)

**Finalidade:** Verifica se o jogador estava em neve em pó (usado para efeitos que persistem após sair).

**Valor:** Não é obrigatório

## Jogador Está Usando Abóbora (`is_player_wearing_pumpkin`)

**Finalidade:** Verifica se o jogador está usando uma abóbora entalhada na cabeça.

**Valor:** Não é obrigatório

## Jogador Está Voando com Elytra (`is_player_flying_with_elytra`)

**Finalidade:** Verifica se o jogador está voando com uma elytra no momento.

**Valor:** Não é obrigatório

## Jogador Está Voando no Criativo (`is_player_creative_flying`)

**Finalidade:** Verifica se o jogador está voando no modo criativo.

**Valor:** Não é obrigatório

## Jogador Tem Corações de Absorção (`has_player_absorption_hearts`)

**Finalidade:** Verifica se o jogador tem algum coração de absorção (corações dourados).

**Valor:** Não é obrigatório

## Jogador Está Com o Efeito Wither (`is_player_withered`)

**Finalidade:** Verifica se o jogador está afetado pelo efeito wither.

**Valor:** Não é obrigatório

## Jogador Está Totalmente Congelado (`is_player_fully_frozen`)

**Finalidade:** Verifica se o jogador está totalmente congelado (normalmente por neve em pó).

**Valor:** Não é obrigatório

## Jogador Está Envenenado (`is_player_poisoned`)

**Finalidade:** Verifica se o jogador está afetado pelo efeito de veneno.

**Valor:** Não é obrigatório

## Jogador Está em Bioma (`is_player_in_biome`)

**Finalidade:** Verifica se o jogador está em um bioma específico.

**Valor:** Obrigatório — Identificador do bioma (por exemplo, `minecraft:birch_forest`)

## Jogador Está em Dimensão (`is_player_in_dimension`)

**Finalidade:** Verifica se o jogador está em uma dimensão específica.

**Valor:** Obrigatório — Identificador da dimensão (por exemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## Jogador Está em Estrutura (`is_player_in_structure`)

**Finalidade:** Verifica se o jogador está atualmente dentro de uma estrutura específica. Requer o FancyMenu no servidor para mundos em servidor.

**Valor:** Obrigatório — Identificador da estrutura (por exemplo, `minecraft:village`)

## Entidade Próxima (`is_entity_nearby`)

**Finalidade:** Verifica se um tipo específico de entidade está dentro de um certo raio do jogador.

**Valor:** Obrigatório — Formato: "raio:entity_id" (por exemplo, `10:minecraft:pig` - verifica se há porcos dentro de 10 blocos)

## Efeito Está Ativo (`is_effect_active`)

**Finalidade:** Verifica se um efeito de poção específico está ativo no jogador.

**Valor:** Obrigatório — Identificador do efeito (por exemplo, `minecraft:speed`, `minecraft:strength`)

## Algum Efeito Está Ativo (`is_any_effect_active`)

**Finalidade:** Verifica se o jogador tem algum efeito de poção ativo.

**Valor:** Não é obrigatório

## Jogador é Canhoto (`is_left_handed`)

**Finalidade:** Verifica se o jogador está definido como canhoto nas opções do jogo.

**Valor:** Não é obrigatório

## Slot do Inventário Está Preenchido (`is_inventory_slot_filled`)

**Finalidade:** Verifica se um slot específico do inventário contém um item.

**Valor:** Obrigatório — Número do slot (0-35 para o inventário principal, slots 0-8 são a hotbar)

## Item Está em Hover no Inventário (`is_item_hovered_in_inventory`)

**Finalidade:** Verifica se o cursor está sobre qualquer item em uma tela de inventário.

**Valor:** Não é obrigatório

## Cursor Está Segurando Item do Inventário (`is_cursor_holding_inventory_item`)

**Finalidade:** Verifica se o cursor está atualmente segurando uma pilha de item do inventário.

**Valor:** Não é obrigatório

## Slot da Hotbar Está Selecionado (`is_hotbar_slot_active`)

**Finalidade:** Verifica se um slot específico da hotbar está selecionado no momento.

**Valor:** Obrigatório — Número do slot da hotbar (0-8)

## Jogador Tem Nível de Permissão (`fancymenu_loading_requirement_has_player_permission_level`)

**Finalidade:** Verifica se o jogador tem pelo menos o nível de permissão/OP especificado no mundo ou servidor atual.

**Valor:** Obrigatório — Número do nível de permissão (0-4, onde 4 é operador do servidor)

## Força de Ataque Está Enfraquecida (`is_attack_strength_weakened`)

**Finalidade:** Verifica se a força de ataque do jogador está enfraquecida no momento (não totalmente carregada).

**Valor:** Não é obrigatório

## É Dia em Tempo Real (`fancymenu_visibility_requirement_is_realtime_day`)

**Finalidade:** Verifica se o dia atual do mês no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Número do dia (1-31). Vários valores podem ser fornecidos separando por vírgulas.

## É Hora em Tempo Real (`fancymenu_visibility_requirement_is_realtime_hour`)

**Finalidade:** Verifica se a hora atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Hora no formato 24 horas (0-23). Vários valores podem ser fornecidos separando por vírgulas.

## É Minuto em Tempo Real (`fancymenu_visibility_requirement_is_realtime_minute`)

**Finalidade:** Verifica se o minuto atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Minuto (0-59). Vários valores podem ser fornecidos separando por vírgulas.

## É Mês em Tempo Real (`fancymenu_visibility_requirement_is_realtime_month`)

**Finalidade:** Verifica se o mês atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Número do mês (1-12, onde 1 é janeiro). Vários valores podem ser fornecidos separando por vírgulas.

## É Segundo em Tempo Real (`fancymenu_visibility_requirement_is_realtime_second`)

**Finalidade:** Verifica se o segundo atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Segundo (0-59). Vários valores podem ser fornecidos separando por vírgulas.

## É Dia da Semana em Tempo Real (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Finalidade:** Verifica se o dia atual da semana no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Dia da semana como número (1-7, onde 1 é domingo). Vários valores podem ser fornecidos separando por vírgulas.

## É Ano em Tempo Real (`fancymenu_visibility_requirement_is_realtime_year`)

**Finalidade:** Verifica se o ano atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Ano completo (por exemplo, "2023"). Vários valores podem ser fornecidos separando por vírgulas.

## Arquivo/Pasta Existe (`fancymenu_loading_requirement_file_exists`)

**Finalidade:** Verifica se um arquivo ou diretório existe.

**Valor:** Obrigatório — Um caminho relativo ao diretório ativo do jogo, ou um caminho que comece com `.minecraft/` para o diretório convencional do Minecraft. Arquivos e diretórios contam como existentes.

## O SO é Linux (`fancymenu_loading_requirement_is_os_linux`)

**Finalidade:** Verifica se a plataforma atual não é Windows nem macOS. Normalmente corresponde a ambientes Linux.

**Valor:** Não é obrigatório

## O SO é macOS (`fancymenu_loading_requirement_is_os_macos`)

**Finalidade:** Verifica se o sistema operacional é macOS.

**Valor:** Não é obrigatório

## O SO é Windows (`fancymenu_loading_requirement_is_os_windows`)

**Finalidade:** Verifica se o sistema operacional é Windows.

**Valor:** Não é obrigatório

## Há Conexão com a Internet (`is_internet_connection_available`)

**Finalidade:** Verifica se há uma conexão ativa com a internet disponível.

**Valor:** Não é obrigatório

## É Idioma do Jogo (`fancymenu_loading_requirement_is_language`)

**Finalidade:** Verifica se o idioma atual do jogo corresponde a um valor específico.

**Valor:** Obrigatório — Código do idioma (por exemplo, `en_us` para inglês)

## Mod Está Carregado (`fancymenu_loading_requirement_is_mod_loaded`)

**Finalidade:** Verifica se um mod específico está carregado.

**Valor:** Obrigatório — ID do mod (por exemplo, `fancymenu`, `jei`). Você também pode verificar o OptiFine com `optifine`. Há suporte a vários IDs de mod separados por vírgula; todos os mods listados devem estar carregados.

## MCEF Está Carregado (`is_mcef_loaded`)

**Finalidade:** Verifica se o MCEF (Minecraft Chromium Embedded Framework) está instalado e inicializado. O MCEF é necessário para o [elemento Browser](./elements#browser) e para [tipos de vídeo baseados em MCEF obsoletos](./video#requirements); os [recursos nativos de vídeo](./video) usam Watermedia.

**Valor:** Não é obrigatório

## É Número (`fancymenu_visibility_requirement_is_number`)

**Finalidade:** Oferece comparação numérica avançada com diferentes modos de comparação.

**Valor:** Obrigatório — Formato complexo: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$` em que `comparison_mode` pode ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` ou `smaller-than-or-equals`

## É Texto (`fancymenu_visibility_requirement_is_text`)

**Finalidade:** Oferece comparação de texto avançada com diferentes modos de comparação.

**Valor:** Obrigatório — Formato complexo: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$` em que `comparison_mode` pode ser `equals`, `contains`, `starts-with` ou `ends-with`

## É IP do Servidor (`fancymenu_visibility_requirement_is_server_ip`)

**Finalidade:** Verifica se o IP do servidor atual corresponde a um valor específico.

**Valor:** Obrigatório — Endereço IP do servidor (com ou sem porta)

## O Servidor Está Online (`fancymenu_loading_requirement_is_server_online`)

**Finalidade:** Verifica se um servidor específico está online e acessível.

**Valor:** Obrigatório — Endereço IP do servidor (com ou sem porta)

## Pacote de Recursos Está Ativado (`is_resource_pack_enabled`)

**Finalidade:** Verifica se um pacote de recursos específico está selecionado/ativo no momento.

**Valor:** Obrigatório — Título do pacote de recursos ou ID do pacote (por exemplo, `Programmer Art` ou o ID do pacote)

## É Valor de Variável (Variável FM) (`fancymenu_visibility_requirement_is_variable_value`)

**Finalidade:** Verifica se uma variável do FancyMenu tem um valor específico.

**Valor:** Obrigatório — Formato: "nome_da_variável:valor_esperado"

## Apenas Uma Vez por Sessão (`once_per_session`)

**Finalidade:** Cada instância configurada retorna verdadeiro uma vez por sessão de jogo. Instâncias diferentes são rastreadas de forma independente.

**Valor:** Não é obrigatório
