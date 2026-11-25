---
title: Locais de armazenamento de dados
description: >-
  Onde o FancyMenu salva layouts, recursos, configurações e tudo mais, e quais
  arquivos pertencem aos perfis.
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# Locais de armazenamento de dados

O FancyMenu salva tudo em duas pastas do diretório do seu jogo. Esse é o diretório da instância do seu launcher, que pode ser diferente de `.minecraft`.

- `config/fancymenu/` contém sua configuração: layouts, recursos, variáveis, configurações e muito mais. É o [perfil](/profiles) carregado; por isso, modpacks incluem essa pasta.
- `fancymenu_data/` contém dados desta instância do jogo, como posições do Dragger e downloads. Ela permanece igual em todos os perfis.

**barra de menus -> Ferramentas -> Abrir diretório do FancyMenu** abre `config/fancymenu/`.

A maioria dos arquivos e pastas só aparece depois que você usa o recurso correspondente. Feche o jogo antes de alterar ou excluir arquivos dessas pastas.

> [!TIP]
> Para compartilhar essas pastas entre instâncias, você pode movê-las para outro local e deixar um link simbólico (uma junção no Windows) no lugar delas.

# Sua configuração

Tudo fica em `<game-directory>/config/fancymenu/`. Todo o conteúdo pertence ao [perfil](/profiles) carregado.

| O quê | Onde |
| --- | --- |
| Layouts, em arquivos `.txt`, também em subpastas | `customization/` |
| [Recursos locais](/resources#local-resources), como imagens e sons | `assets/` |
| Configurações do FancyMenu | `options.txt` |
| Telas com **Personalização da tela atual** ativada | `customizablemenus.txt` |
| [GUIs personalizadas](/custom-guis) e as telas que elas substituem | `custom_gui_screens.txt` |
| [Variáveis](/variables) | `user_variables.db` |
| [Ouvintes](/listeners) | `listener_instances.txt` |
| [Agendadores](/schedulers) | `scheduler_instances.txt` |
| [Panoramas](/panoramas) | `panoramas/` |
| [Apresentações de slides](/slideshows) | `slideshows/` |
| [Localizações personalizadas](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Temas da própria interface do FancyMenu (**barra de menus -> Personalização -> Configurações -> Interface do FancyMenu -> Tema da interface**) | `ui_themes/` |
| Estados dos [elementos de caixa de seleção](/elements#checkbox) que não usam uma variável | `checkbox_states.json` |
| Estados de volume e pausa definidos por ações para [elementos de vídeo](/video) | `video_element_controller_metas.json` |
| Volume definido por ações para [elementos de áudio](/elements#audio) | `audio_element_controller_metas.json` |
| Estados ligado e desligado definidos por ações para [animadores de elementos](/element-animator) | `animation_controller_states.json` |
| Telas com **Expor conteúdo da área de rolagem da tela atual** ativado (consulte [Personalizar telas com rolagem](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| Ouvintes do servidor [FM Data](/fm-data) | `fmdata_server_listeners.json` |
| Dados de boas-vindas do [FM Data](/fm-data) | `fmdata_welcome_data.json` |
| Posição, tamanho e visibilidade dos widgets do editor de layout | `layout_editor/widgets/` |
| Nome, ícone e detalhes do perfil carregado | `profile.json` e `profile_icon.png` |
| Todos os outros [perfis](/profiles#where-profiles-are-stored) | `profiles/` |
| Quais atualizações de arquivos antigos o FancyMenu já realizou | `legacy_checklist.txt` |

`customizablemenus.txt` lista as telas pelo nome da classe Java. Identificadores de tela curtos, como `title_screen`, são ignorados nesse arquivo. Consulte [Identificadores de tela](/screen-identifiers).

Em um servidor dedicado, o FancyMenu usa apenas os dois arquivos de [FM Data](/fm-data), na pasta `config/fancymenu/` do servidor.

# Dados da instância

Tudo fica em `<game-directory>/fancymenu_data/`. Essa pasta não faz parte dos perfis, então permanece ao trocar de perfil.

| O quê | Onde |
| --- | --- |
| Posições dos [elementos Dragger](/dragger) | `dragger_metas.json` |
| O último mundo ou servidor, usado pela ação **Entrar no último mundo/servidor** e pelo espaço reservado **Último mundo ou servidor** | `last_world.fmdata` |
| Capturas de tela do [Carregamento contínuo do mundo](/seamless-world-loading) | `seamless_world_loading/` |
| Salvamentos do [Buddy](/decoration-overlays#buddy), dois arquivos por sobreposição do Buddy | `buddy/` |
| Arquivos de [Exportação para IA](/export-for-ai) | `ai_exports/` |
| Suas ações favoritas no seletor de ações | `action_favorites.json` |
| O volume das prévias de áudio e vídeo nos seletores de arquivos | `browser_audio_settings.json` e `browser_video_settings.json` |
| O quadro exibido por um [plano de fundo de vídeo](/video) quando está pausado | `video_thumbnails/` |
| FFmpeg, que o FancyMenu baixa para o [Criador de AFMA](/animations#fma-and-afma) | `ffmpeg_cache/` |
| Uma indicação de que o FancyMenu já definiu a [**Escala padrão da interface**](/global-customizations) | `default_scale_set.fm` |
| Arquivos temporários, excluídos a cada inicialização do jogo | `fancymenu_temp/` |

- O FancyMenu define a **Escala padrão da interface** apenas uma vez. Exclua `default_scale_set.fm` para que a escala seja definida novamente na próxima inicialização.
- As capturas de tela do Carregamento contínuo do mundo mostram tudo o que estava na tela dentro do mundo. Exclua-as com o jogo fechado se não quiser mantê-las.

# Arquivos de versões antigas

Versões antigas do FancyMenu salvavam alguns arquivos em outros locais. O FancyMenu os transfere para os novos locais na próxima inicialização do jogo:

- `checkbox_states.json` e `normalized_scroll_screens.json`, do próprio diretório do jogo para `config/fancymenu/`.
- `dragger_metas.json`, de `config/fancymenu/` para `fancymenu_data/`.
