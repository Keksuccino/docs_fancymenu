---
title: Locais de Armazenamento de Dados
description: >-
  Onde o FancyMenu armazena layouts, recursos, configuração e estado persistente
  em tempo de execução.
---

# Locais de Armazenamento de Dados

`<game-directory>` significa a pasta da instância ativa do Minecraft, que pode ser diferente de `.minecraft`.

Diretórios e arquivos normalmente só são criados depois que o recurso relacionado é inicializado ou usado. Feche o Minecraft antes de editar manualmente arquivos de estado gerados e mantenha um backup ao migrar ou redefinir dados.

# Layouts, Recursos e Configuração

Algumas entradas são configuração ou ativos criados manualmente; outras são estado que o FancyMenu atualiza em tempo de execução.

| Sistema / Recurso | Arquivo ou Diretório |
| --- | --- |
| Telas personalizáveis | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [GUIs personalizadas](./custom-guis) e regras de substituição de tela | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| Layouts | `<game-directory>/config/fancymenu/customization/` |
| [Recursos locais](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [Arquivos de localização personalizados](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [Panoramas](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [Slideshows](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [Variáveis do FancyMenu](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| Metadados do controlador do elemento [vídeo](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| Metadados do controlador do elemento [áudio](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| Servidores ouvintes do [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| Dados de boas-vindas do [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| Instâncias de [Listener](./listeners) e scripts de ação | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Schedulers](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` é gerenciado pela alternância **Personalização da Tela Atual** e armazena identificadores concretos de classes de tela. Não adicione identificadores de [Universal Layout](./universal-layouts); o FancyMenu os ignora ao carregar o arquivo.

Em um servidor dedicado, os dois arquivos do FM Data ficam relativos à raiz do jogo desse servidor. Outros recursos e configurações de propriedade do cliente pertencem à instância de cada jogador.

# Estado Persistente em Tempo de Execução

O FancyMenu mantém estado adicional gerado, por instância, fora de `config/fancymenu/`. Inclua esses caminhos em um backup apenas quando quiser preservar o estado relacionado do usuário/tempo de execução; eles não são definições de layout nem ativos-fonte.

| Sistema / Recurso | Arquivo ou Diretório |
| --- | --- |
| Estados não variáveis de [Checkbox](./elements#checkbox) | `<game-directory>/checkbox_states.json` |
| Posições/metadados do elemento [Dragger](./dragger) | `<game-directory>/fancymenu_data/dragger_metas.json` |
| Último estado do mundo | `<game-directory>/fancymenu_data/last_world.fmdata` |
| Estado do [Seamless World Loading](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Salvamentos do pet Buddy e de nível | `<game-directory>/fancymenu_data/buddy/` |
| Posições e visibilidade dos widgets do editor de layout | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| Marcador de inicialização da escala padrão da GUI | `<game-directory>/fancymenu_data/default_scale_set.fm` |

O Buddy mantém o estado do pet e o estado de nível/conquistas em arquivos JSON separados dentro do seu diretório. Cada instância de sobreposição do Buddy usa seu próprio par de arquivos.

Os arquivos dos widgets do editor de layout armazenam a posição, o tamanho, a visibilidade, o estado expandido e o lado de encaixe de cada widget. Excluir `default_scale_set.fm` faz com que o FancyMenu trate a escala padrão de GUI configurada como ainda não aplicada na próxima inicialização.
