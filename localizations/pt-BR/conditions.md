---
title: Condições (Requisitos)
description: Como usar requisitos de carregamento.
---
# Requisitos

Os requisitos (chamados de **Requisitos de Carregamento** em alguns menus) mostram ou ocultam conteúdo com base em condições como o estado de foco do mouse, o tamanho da janela ou se há um mundo carregado.

Você pode usá-los em [elementos](./elements), layouts inteiros e [scripts de ação](./action-scripts).

# Adicionando Requisitos a Elementos

Para adicionar requisitos a um elemento, clique nele com o botão direito e selecione **Requisitos de Carregamento**.

Os requisitos são verificados enquanto o menu está aberto, portanto os elementos são atualizados quando uma condição muda.

# Requisitos para Todo o Layout

Você também pode alterar a visibilidade de layouts inteiros clicando com o botão direito no **plano de fundo do editor** e, em seguida, em **Requisitos de Carregamento [Todo o Layout]**.

Quando o resultado de um requisito para todo o layout muda, o FancyMenu reconstrói a tela atual e aplica os layouts cujos requisitos agora são atendidos.

# Scripts de Ação

Os requisitos também podem ser usados em scripts de ação.
Você pode adicioná-los na tela do editor de scripts de ação e usá-los para executar ações específicas somente se a condição do requisito for atendida.

# Combinando Requisitos

- Requisitos fora de grupos usam **E**, portanto todos devem ser atendidos.
- Dentro de um grupo, escolha **E** ou **OU**.
- Use **SE NÃO** para inverter um requisito.

Essas regras são iguais para elementos, layouts e scripts de ação.

# Valores dos Requisitos

Para requisitos que precisam de um valor, use **Editar Valor do Requisito** e siga a descrição exibida no editor. Alguns campos são compatíveis com a conclusão usando **TAB**.

Se um requisito importado parar de funcionar após a alteração do FancyMenu ou de complementos, edite-o na tela de requisitos e verifique `logs/latest.log` em busca de erros.

O editor de requisitos oferece um menu de contexto acessível com o botão direito, navegação pelo teclado, pesquisa, desfazer/refazer (`Ctrl/Command + Z` / `Ctrl/Command + Y`) e `Ctrl/Command + S` para salvar.

# Requisitos em Detalhes

Esta seção lista os requisitos integrados do FancyMenu.

## Elemento Está Sob o Cursor (`fancymenu_visibility_requirement_is_element_hovered`)

**Finalidade:** Verifica se um elemento específico está sob o cursor do mouse.

**Valor:** Obrigatório — [Identificador do elemento](./element-identifiers) do elemento-alvo (por exemplo, `some_element_ID`).

## Elemento Está Focado (`is_element_focused`)

**Finalidade:** Verifica se um elemento específico está atualmente com o foco do teclado (por exemplo, um campo de texto ou botão focado).

**Valor:** Obrigatório — ID do elemento-alvo (o mesmo ID exibido no editor)

> [!NOTE]
> Foco e estado sob o cursor são diferentes. Um elemento pode manter sua aparência de focado depois que o ponteiro sai dele; clicar ou navegar pelo teclado pode dar foco a ele.

## Algum Elemento Está Sob o Cursor (`fancymenu_visibility_requirement_is_any_element_hovered`)

**Finalidade:** Verifica os elementos visíveis/renderizáveis na camada de personalização ativa atual, incluindo elementos fornecidos por layouts empilhados.

**Valor:** Não obrigatório

## Algum Botão Está Sob o Cursor (`fancymenu_visibility_requirement_is_any_button_hovered`)

**Finalidade:** Verifica se algum botão vanilla ou personalizado visível/renderizável na camada de personalização ativa atual está sob o cursor, incluindo botões fornecidos por layouts empilhados.

**Valor:** Não obrigatório

## Layout Está Ativado (`fancymenu_visibility_requirement_is_layout_enabled`)

**Finalidade:** Verifica se um layout específico está ativado no momento.

**Valor:** Obrigatório — Nome do layout (por exemplo, `my_cool_main_menu_layout`)

## Agendador Está em Execução (`fancymenu_visibility_requirement_is_scheduler_running`)

**Finalidade:** Verifica se um [agendador](./schedulers) está em execução no momento.

**Valor:** Obrigatório — ID do agendador (por exemplo, `my_scheduler`)

## Escala da Interface é (`fancymenu_loading_requirement_is_gui_scale`)

**Finalidade:** Verifica se a escala atual da interface corresponde a determinadas condições.

**Valor:** Obrigatório — Use um número para igualdade, `>` para maior que ou `<` para menor que.

Várias condições separadas por vírgulas são combinadas com E. Por exemplo, `>1,<4` será atendido somente quando a escala da interface for maior que `1` e menor que `4`.

## Botão Está Ativo (`fancymenu_visibility_requirement_is_button_active`)

**Finalidade:** Verifica se um botão específico está ativo (pode ser clicado).

**Valor:** Obrigatório — ID do elemento do botão-alvo (por exemplo, "some_element_ID")

## Título da Tela é (`is_menu_title`)

**Finalidade:** Verifica se o título EXIBIDO da tela corresponde a um texto específico ou a uma chave de localização. Isso verifica somente o nome/título exibido da tela, como "Opções" ou "Pausar". Ele NÃO verifica o identificador do menu/tela (como `title_screen`)!

**Valor:** Obrigatório — Texto exato do título ou chave de localização da tela

## Tecla Está Pressionada (`is_key_pressed`)

**Finalidade:** Verifica se uma tecla específica do teclado está sendo pressionada no momento.

**Valor:** Obrigatório — Código da tecla-alvo. Selecionado por uma interface ao editar o valor do requisito.

## Alguma Tela Está Aberta (`is_any_screen_open`)

**Finalidade:** Verifica se alguma tela/menu está aberto no momento (retorna falso se nenhuma tela estiver sendo exibida).

**Valor:** Não obrigatório

## Sobreposição de Depuração do MC Está Ativada (`is_debug_overlay_enabled`)

**Finalidade:** Verifica se a sobreposição de depuração do F3 está visível no momento.

**Valor:** Não obrigatório

## Tipo de Cursor Ativo é (`is_active_cursor_type`)

**Finalidade:** Verifica se o tipo de cursor atualmente ativo do FancyMenu corresponde a um tipo de cursor padrão específico.

**Valor:** Obrigatório — Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` ou `not_allowed`

## Barra de Menu de Personalização Está Visível (`is_customization_menu_bar_visible`)

**Finalidade:** Verifica se a barra de menu de personalização do FancyMenu está visível no momento.

**Valor:** Não obrigatório

## Modo de Modpack Está Ativado (`is_modpack_mode_enabled`)

**Finalidade:** Verifica se o Modo de Modpack do FancyMenu está ativado.

**Valor:** Não obrigatório

## Botão do Mouse Está Pressionado (`mouse_click`)

**Finalidade:** Retorna verdadeiro enquanto um botão específico do mouse estiver pressionado. Este não é um evento de clique único; use o [listener **Ao Clicar em um Botão do Mouse**](./listeners#on-mouse-button-clicked-mouse_button_clicked) quando uma ação precisar ser executada uma vez por clique.

**Valor:** Obrigatório — `left` ou `right` para indicar qual botão do mouse verificar

## Está em Tela Cheia (`fancymenu_loading_requirement_is_fullscreen`)

**Finalidade:** Verifica se o jogo está no modo de tela cheia.

**Valor:** Não obrigatório

## Largura da Janela é (`fancymenu_loading_requirement_is_window_width`)

**Finalidade:** Verifica se a largura da janela do jogo corresponde a valores específicos.

**Valor:** Obrigatório — Largura da janela em pixels (por exemplo, "1920"). Vários valores podem ser fornecidos separando-os por vírgulas.

## Altura da Janela é (`fancymenu_loading_requirement_is_window_height`)

**Finalidade:** Verifica se a altura da janela do jogo corresponde a valores específicos.

**Valor:** Obrigatório — Altura da janela em pixels (por exemplo, "1080"). Vários valores podem ser fornecidos separando-os por vírgulas.

## Largura da Janela é Maior que (`fancymenu_loading_requirement_is_window_width_bigger_than`)

**Finalidade:** Verifica se a largura da janela do jogo é maior que um valor específico.

**Valor:** Obrigatório — Largura da janela em pixels (por exemplo, "1920")

## Altura da Janela é Maior que (`fancymenu_loading_requirement_is_window_height_bigger_than`)

**Finalidade:** Verifica se a altura da janela do jogo é maior que um valor específico.

**Valor:** Obrigatório — Altura da janela em pixels (por exemplo, "1080")

## É Multijogador (`fancymenu_loading_requirement_is_multiplayer`)

**Finalidade:** Verifica se o jogador está em um mundo multijogador no momento.

**Valor:** Não obrigatório

## É Um Jogador (`fancymenu_loading_requirement_is_singpleplayer`)

**Finalidade:** Verifica se o jogador está em um mundo para um jogador no momento.

**Valor:** Não obrigatório

## Mundo Está Carregado (`fancymenu_loading_requirement_is_world_loaded`)

**Finalidade:** Verifica se há algum mundo carregado no momento.

**Valor:** Não obrigatório

## Está no Modo Aventura (`fancymenu_visibility_requirement_is_adventure`)

**Finalidade:** Verifica se o jogador está no modo de jogo aventura.

**Valor:** Não obrigatório

## Está no Modo Criativo (`fancymenu_visibility_requirement_is_creative`)

**Finalidade:** Verifica se o jogador está no modo de jogo criativo.

**Valor:** Não obrigatório

## Está no Modo Espectador (`fancymenu_visibility_requirement_is_spectator`)

**Finalidade:** Verifica se o jogador está no modo de jogo espectador.

**Valor:** Não obrigatório

## Está no Modo Sobrevivência (`fancymenu_visibility_requirement_is_survival`)

**Finalidade:** Verifica se o jogador está no modo de jogo sobrevivência.

**Valor:** Não obrigatório

## É um Modo de Jogo (`is_gamemode`)

**Finalidade:** Verifica se o jogador está em um modo de jogo específico.

**Valor:** Obrigatório — Nome do modo de jogo (por exemplo, "creative", "survival", "adventure", "spectator")

## É uma Dificuldade (`is_difficulty`)

**Finalidade:** Verifica se a dificuldade atual do jogo corresponde a um valor específico.

**Valor:** Obrigatório — Nome da dificuldade (por exemplo, "peaceful", "easy", "normal", "hard")

## É Hardcore (`is_hardcore`)

**Finalidade:** Verifica se o mundo carregado está no modo hardcore.

**Valor:** Não obrigatório

## Perspectiva da Câmera é (`is_camera_perspective`)

**Finalidade:** Verifica se a perspectiva atual da câmera corresponde a uma perspectiva específica.

**Valor:** Obrigatório — `first_person`, `third_person_back` ou `third_person_front`

## Está Chovendo (`is_raining`)

**Finalidade:** Verifica se está chovendo no local do jogador.

**Valor:** Não obrigatório

## Está Trovejando (`is_thundering`)

**Finalidade:** Verifica se há uma tempestade no mundo do jogador.

**Valor:** Não obrigatório

## O Clima Está Limpo (`is_clear_weather`)

**Finalidade:** Verifica se o clima está limpo (sem chuva ou trovoadas).

**Valor:** Não obrigatório

## Está Nevando (`is_snowing`)

**Finalidade:** Verifica se está nevando no local do jogador.

**Valor:** Não obrigatório

## O Jogador Está Correndo (`is_player_running`)

**Finalidade:** Verifica se o jogador está correndo no momento.

**Valor:** Não obrigatório

## O Jogador Está Agachado (`is_player_sneaking`)

**Finalidade:** Verifica se o jogador está se esgueirando/agachado no momento.

**Valor:** Não obrigatório

## O Jogador Está Usando um Item (`is_player_using_item`)

**Finalidade:** Verifica se o jogador está usando um item no momento.

**Valor:** Não obrigatório

## O Jogador Está Nadando (`is_player_swimming`)

**Finalidade:** Verifica se o jogador está nadando no momento.

**Valor:** Não obrigatório

## O Jogador Está Pulando ou Caindo (`is_player_jumping`)

**Finalidade:** Retorna verdadeiro enquanto o jogador estiver no ar em um estado normal de salto ou queda. Natação, fluidos, voo com élitros, sono, natação visual e rastejamento são excluídos.

**Valor:** Não obrigatório

## O Jogador Está Debaixo d'Água (`is_player_under_water`)

**Finalidade:** Verifica se o jogador está completamente debaixo d'água.

**Valor:** Não obrigatório

## O Jogador Está na Água (`is_player_in_water`)

**Finalidade:** Verifica se o jogador está na água (ele pode estar parcialmente submerso).

**Valor:** Não obrigatório

## O Jogador Está na Lava (`is_player_in_lava`)

**Finalidade:** Verifica se o jogador está na lava.

**Valor:** Não obrigatório

## O Jogador Está em um Fluido (`is_player_in_fluid`)

**Finalidade:** Verifica se o jogador está em qualquer fluido (água, lava etc.).

**Valor:** Não obrigatório

## O Jogador Está Montado em uma Entidade/Veículo (`is_player_riding_entity`)

**Finalidade:** Verifica se o jogador está montado em alguma entidade.

**Valor:** Não obrigatório

## O Jogador Está Montado em uma Entidade que Pode Pular (`is_player_riding_jumpable_entity`)

**Finalidade:** Verifica se o jogador está montado em uma entidade que pode pular (como um cavalo).

**Valor:** Não obrigatório

## O Jogador Está Montado em uma Entidade com Vida (`is_player_riding_entity_with_health`)

**Finalidade:** Verifica se o jogador está montado em uma entidade viva com vida (como animais, mas não barcos).

**Valor:** Não obrigatório

## O Jogador Está na Neve Fofa (`is_player_in_powder_snow`)

**Finalidade:** Verifica se o jogador está na neve fofa no momento.

**Valor:** Não obrigatório

## O Jogador Estava na Neve Fofa (`was_player_in_powder_snow`)

**Finalidade:** Verifica se o jogador estava na neve fofa (usado para efeitos que persistem depois que ele sai dela).

**Valor:** Não obrigatório

## O Jogador Está Usando uma Abóbora (`is_player_wearing_pumpkin`)

**Finalidade:** Verifica se o jogador está usando uma abóbora esculpida na cabeça.

**Valor:** Não obrigatório

## O Jogador Está Voando com um Élitra (`is_player_flying_with_elytra`)

**Finalidade:** Verifica se o jogador está voando com um élitra.

**Valor:** Não obrigatório

## O Jogador Está Voando no Modo Criativo (`is_player_creative_flying`)

**Finalidade:** Verifica se o jogador está voando no modo criativo.

**Valor:** Não obrigatório

## O Jogador Tem Corações de Absorção (`has_player_absorption_hearts`)

**Finalidade:** Verifica se o jogador tem corações de absorção (corações dourados).

**Valor:** Não obrigatório

## O Jogador Está Sob o Efeito Wither (`is_player_withered`)

**Finalidade:** Verifica se o jogador está afetado pelo efeito Wither.

**Valor:** Não obrigatório

## O Jogador Está Completamente Congelado (`is_player_fully_frozen`)

**Finalidade:** Verifica se o jogador está completamente congelado (geralmente devido à neve fofa).

**Valor:** Não obrigatório

## O Jogador Está Envenenado (`is_player_poisoned`)

**Finalidade:** Verifica se o jogador está afetado pelo efeito de veneno.

**Valor:** Não obrigatório

## O Jogador Está em um Bioma (`is_player_in_biome`)

**Finalidade:** Verifica se o jogador está em um bioma específico.

**Valor:** Obrigatório — Identificador do bioma (por exemplo, `minecraft:birch_forest`)

## O Jogador Está em uma Dimensão (`is_player_in_dimension`)

**Finalidade:** Verifica se o jogador está em uma dimensão específica.

**Valor:** Obrigatório — Identificador da dimensão (por exemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## O Jogador Está em uma Estrutura (`is_player_in_structure`)

**Finalidade:** Verifica se o jogador está dentro de uma estrutura específica. Requer o FancyMenu no servidor para mundos de servidor.

**Valor:** Obrigatório — Identificador da estrutura (por exemplo, `minecraft:village`)

## Há uma Entidade Próxima (`is_entity_nearby`)

**Finalidade:** Verifica se um tipo específico de entidade está dentro de determinado raio do jogador.

**Valor:** Obrigatório — Formato: "raio:identificador_da_entidade" (por exemplo, `10:minecraft:pig` — verifica se há porcos em até 10 blocos)

## Efeito Está Ativo (`is_effect_active`)

**Finalidade:** Verifica se um efeito de poção específico está ativo no jogador.

**Valor:** Obrigatório — Identificador do efeito (por exemplo, `minecraft:speed`, `minecraft:strength`)

## Algum Efeito Está Ativo (`is_any_effect_active`)

**Finalidade:** Verifica se o jogador tem algum efeito de poção ativo.

**Valor:** Não obrigatório

## O Jogador é Canhoto (`is_left_handed`)

**Finalidade:** Verifica se o jogador está configurado para o modo canhoto nas opções do jogo.

**Valor:** Não obrigatório

## Slot do Inventário Está Preenchido (`is_inventory_slot_filled`)

**Finalidade:** Verifica se um slot específico do inventário contém um item.

**Valor:** Obrigatório — Número do slot (0–35 para o inventário principal; os slots 0–8 são a barra rápida)

## Há um Item sob o Cursor no Inventário (`is_item_hovered_in_inventory`)

**Finalidade:** Verifica se o cursor está sobre algum item em uma tela de inventário.

**Valor:** Não obrigatório

## O Cursor Está Segurando um Item do Inventário (`is_cursor_holding_inventory_item`)

**Finalidade:** Verifica se o cursor está segurando uma pilha de itens do inventário.

**Valor:** Não obrigatório

## Slot da Barra Rápida Está Selecionado (`is_hotbar_slot_active`)

**Finalidade:** Verifica se um slot específico da barra rápida está selecionado no momento.

**Valor:** Obrigatório — Número do slot da barra rápida (0–8)

## O Jogador Tem Nível de Permissão (`fancymenu_loading_requirement_has_player_permission_level`)

**Finalidade:** Verifica se o jogador tem pelo menos o nível de permissão/OP especificado no mundo ou servidor atual.

**Valor:** Obrigatório — Número do nível de permissão (0–4, sendo 4 o nível de operador do servidor)

## Força do Ataque Está Enfraquecida (`is_attack_strength_weakened`)

**Finalidade:** Verifica se a força de ataque do jogador está enfraquecida no momento (não está totalmente carregada).

**Valor:** Não obrigatório

## É Dia no Horário Real (`fancymenu_visibility_requirement_is_realtime_day`)

**Finalidade:** Verifica se o dia atual do mês no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Número do dia (1–31). Vários valores podem ser fornecidos separando-os por vírgulas.

## É uma Hora no Horário Real (`fancymenu_visibility_requirement_is_realtime_hour`)

**Finalidade:** Verifica se a hora atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Hora no formato de 24 horas (0–23). Vários valores podem ser fornecidos separando-os por vírgulas.

## É um Minuto no Horário Real (`fancymenu_visibility_requirement_is_realtime_minute`)

**Finalidade:** Verifica se o minuto atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Minuto (0–59). Vários valores podem ser fornecidos separando-os por vírgulas.

## É um Mês no Horário Real (`fancymenu_visibility_requirement_is_realtime_month`)

**Finalidade:** Verifica se o mês atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Número do mês (1–12, sendo 1 janeiro). Vários valores podem ser fornecidos separando-os por vírgulas.

## É um Segundo no Horário Real (`fancymenu_visibility_requirement_is_realtime_second`)

**Finalidade:** Verifica se o segundo atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Segundo (0–59). Vários valores podem ser fornecidos separando-os por vírgulas.

## É um Dia da Semana no Horário Real (`fancymenu_visibility_requirement_is_realtime_week_day`)

**Finalidade:** Verifica se o dia atual da semana no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Dia da semana como número (1–7, sendo 1 domingo). Vários valores podem ser fornecidos separando-os por vírgulas.

## É um Ano no Horário Real (`fancymenu_visibility_requirement_is_realtime_year`)

**Finalidade:** Verifica se o ano atual no mundo real corresponde a um valor específico.

**Valor:** Obrigatório — Ano completo (por exemplo, "2023"). Vários valores podem ser fornecidos separando-os por vírgulas.

## Arquivo/Pasta Existe (`fancymenu_loading_requirement_file_exists`)

**Finalidade:** Verifica se um arquivo ou diretório existe.

**Valor:** Obrigatório — Um caminho relativo ao diretório ativo do jogo ou um caminho que comece com `.minecraft/`, referente ao diretório convencional do Minecraft. Arquivos e diretórios são considerados existentes.

## O Sistema Operacional é Linux (`fancymenu_loading_requirement_is_os_linux`)

**Finalidade:** Verifica se a plataforma atual não é Windows nem macOS. Normalmente, isso corresponde a ambientes Linux.

**Valor:** Não obrigatório

## O Sistema Operacional é macOS (`fancymenu_loading_requirement_is_os_macos`)

**Finalidade:** Verifica se o sistema operacional é macOS.

**Valor:** Não obrigatório

## O Sistema Operacional é Windows (`fancymenu_loading_requirement_is_os_windows`)

**Finalidade:** Verifica se o sistema operacional é Windows.

**Valor:** Não obrigatório

## Há uma Conexão com a Internet (`is_internet_connection_available`)

**Finalidade:** Verifica se há uma conexão ativa com a internet.

**Valor:** Não obrigatório

## O Idioma do Jogo é (`fancymenu_loading_requirement_is_language`)

**Finalidade:** Verifica se o idioma atual do jogo corresponde a um valor específico.

**Valor:** Obrigatório — Código do idioma (por exemplo, `en_us` para inglês)

## Mod Está Carregado (`fancymenu_loading_requirement_is_mod_loaded`)

**Finalidade:** Verifica se um mod específico está carregado.

**Valor:** Obrigatório — ID do mod (por exemplo, `fancymenu`, `jei`). Você também pode verificar o OptiFine com `optifine`. Vários IDs de mods separados por vírgulas são compatíveis; todos os mods listados devem estar carregados.

## Rinku Está Carregado (`is_rinku_loaded`)

**Finalidade:** Verifica se o [Rinku](https://modrinth.com/mod/rinku) está instalado e inicializado. O [Rinku](https://modrinth.com/mod/rinku) é necessário para o [elemento Navegador](./elements#browser) e para os [tipos de vídeo baseados no Rinku e obsoletos](./video#requirements); os recursos de [vídeo nativos](./video) usam o Watermedia.

**Valor:** Não obrigatório

## É um Número (`fancymenu_visibility_requirement_is_number`)

**Finalidade:** Oferece uma comparação avançada de números com diferentes modos de comparação.

**Valor:** Obrigatório — Formato complexo: `["mode":"comparison_mode","number":"value1","compare_with":"value2"]$`, em que `comparison_mode` pode ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` ou `smaller-than-or-equals`

## É um Texto (`fancymenu_visibility_requirement_is_text`)

**Finalidade:** Oferece uma comparação avançada de textos com diferentes modos de comparação.

**Valor:** Obrigatório — Formato complexo: `["mode":"comparison_mode","text":"text1","compare_with":"text2"]$`, em que `comparison_mode` pode ser `equals`, `contains`, `starts-with` ou `ends-with`

## IP do Servidor é (`fancymenu_visibility_requirement_is_server_ip`)

**Finalidade:** Verifica se o IP do servidor atual corresponde a um valor específico.

**Valor:** Obrigatório — Endereço IP do servidor (com ou sem porta)

## Servidor Está Online (`fancymenu_loading_requirement_is_server_online`)

**Finalidade:** Verifica se um servidor específico está online e acessível.

**Valor:** Obrigatório — Endereço IP do servidor (com ou sem porta)

## Pacote de Recursos Está Ativado (`is_resource_pack_enabled`)

**Finalidade:** Verifica se um pacote de recursos específico está selecionado/ativo no momento.

**Valor:** Obrigatório — Título do pacote de recursos ou ID do pacote (por exemplo, `Programmer Art` ou o ID do pacote)

## Valor da Variável (Variável do FM) (`fancymenu_visibility_requirement_is_variable_value`)

**Finalidade:** Verifica se uma variável do FancyMenu tem um valor específico.

**Valor:** Obrigatório — Formato: "nome_da_variável:valor_esperado"

## Apenas Uma Vez por Sessão (`once_per_session`)

**Finalidade:** Cada instância configurada retorna verdadeiro uma vez por sessão de jogo. Instâncias diferentes são acompanhadas de forma independente.

**Valor:** Não obrigatório
