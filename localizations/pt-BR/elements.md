---
title: Elementos
description: Tudo o que você precisa saber sobre os tipos de elementos do FancyMenu.
---

# Elementos

Os elementos são os blocos de construção dos seus layouts personalizados no FancyMenu. Você pode adicioná-los a qualquer layout para exibir informações, adicionar interatividade ou criar efeitos visuais impressionantes.

# Adicionando Elementos a um Layout

Você pode adicionar um novo elemento ao seu layout dentro do **Editor de Layout**.

1.  **Clique com o botão direito** no fundo do editor para abrir o menu de contexto.
2.  Passe o mouse sobre **New Element**.
3.  Uma lista de todos os tipos de elementos disponíveis aparecerá. Clique naquele que você quer adicionar.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Depois que um elemento for adicionado, você pode movê-lo, redimensioná-lo e personalizá-lo clicando com o **botão direito** sobre ele para abrir seu menu de contexto específico. Para saber mais sobre como organizar elementos, consulte as páginas [Posicionamento de Elementos](https://docs.fancymenu.net/en/positioning-elements) e [Identificadores de Elementos](https://docs.fancymenu.net/en/element-identifiers).

# Elementos em Detalhe

A lista a seguir contém a maioria, senão todos, os elementos disponíveis no FancyMenu. A lista pode, às vezes, ficar um pouco desatualizada devido a atualizações do FancyMenu.

## Botão
Um botão clicável que pode executar uma grande variedade de ações. Este é um dos elementos mais poderosos e versáteis para criar menus interativos.

*   **Casos de uso:**
    *   Criar um botão de "Entrar no Discord" ou "Visitar site".
    *   Adicionar um botão de acesso rápido para um servidor específico.
    *   Construir navegação personalizada entre diferentes menus.
    *   Criar botões que ativam ou desativam outros layouts.
*   **Recursos principais:**
    *   **Ações:** Pode executar uma sequência de ações, como abrir uma URL, entrar em um servidor, enviar um comando de chat, imitar a função de outro botão, controlar variáveis e muito mais. Saiba mais na documentação de [Scripts de Ação](https://docs.fancymenu.net/en/action-scripts).
    *   **Aparência Personalizada:** Texturas totalmente personalizáveis para os estados normal, com o mouse em cima e inativo. Suporta fundos transparentes, nine-slicing, cores personalizadas do rótulo, cores do rótulo ao passar o mouse, escala do rótulo, alternância de sombra no texto e texturas de ícone do botão.
    *   **Sons:** Sons personalizados de clique, passar o mouse e sair do botão.
    *   **Modo Modelo:** Pode atuar como um modelo para aplicar sua aparência e propriedades a todos os outros botões Vanilla ou modificados no menu, garantindo uma aparência consistente. Leia mais na página [Modelos de Botão e Slider](https://docs.fancymenu.net/en/button-slider-templates).

## Slider
Um controle deslizante que os usuários podem arrastar para selecionar um valor de uma lista ou de um intervalo. Pode executar ações sempre que seu valor muda.

*   **Casos de uso:**
    *   Criar um controle de volume personalizado.
    *   Um slider para alternar entre diferentes temas ou imagens de fundo (usando o tipo "List").
    *   Ajustar uma opção específica do Minecraft, como brilho ou distância de renderização.
*   **Recursos principais:**
    *   **Tipos:** Pode ser uma `Value List` (por exemplo, "Fácil", "Normal", "Difícil"), um `Integer Range` (por exemplo, 1-100) ou um `Decimal Range` (por exemplo, 0.0-1.0).
    *   **Ações Dinâmicas:** Executa ações quando o valor muda. O valor atual do slider pode ser usado dentro de suas ações para realizar tarefas dinâmicas, que podem ser usadas com [Variáveis](https://docs.fancymenu.net/en/variables).
    *   **Personalização:** O rótulo do slider pode exibir dinamicamente seu valor atual. As texturas do controle e do fundo são totalmente personalizáveis, incluindo fundos transparentes, opções de cor/escala do rótulo, alternância de sombra do texto e sons personalizados de clique/saída do mouse.

## Checkbox
Uma caixa de seleção padrão que pode ser marcada ou desmarcada. Pode executar ações ao ser alternada.

*   **Casos de uso:**
    *   Uma caixa "Eu concordo com as regras".
    *   Uma configuração para ativar ou desativar um recurso específico no seu menu personalizado.
    *   Ativar ou desativar um layout ou variável.
*   **Recursos principais:**
    *   **Ações ao Alternar:** Executa [Scripts de Ação](https://docs.fancymenu.net/en/action-scripts) quando seu estado muda. O estado atual (`true` ou `false`) pode ser acessado dentro de suas ações.
    *   **Modo de Variável:** Pode ser vinculado diretamente a uma variável do FancyMenu, fazendo com que o estado da caixa de seleção leia e escreva nessa variável.
    *   **Aparência Personalizada:** Suporta texturas personalizadas para o fundo (nos estados normal, com hover e inativo) e para o próprio marcação.

## Campo de Entrada de Texto
Um campo onde os usuários podem digitar texto. Seu conteúdo pode ser vinculado a uma variável do FancyMenu, permitindo capturar e usar a entrada do usuário.

*   **Casos de uso:**
    *   Um campo de entrada de "IP do servidor" que funciona com um botão "Entrar no Servidor".
    *   Um campo para inserir o nome de um jogador para uma pré-visualização de skin personalizada.
    *   Criar uma interface básica parecida com login.
*   **Recursos principais:**
    *   **Vinculação de Variável:** O texto digitado pelo usuário é armazenado em uma [variável](https://docs.fancymenu.net/en/variables) especificada.
    *   **Validação de Entrada:** Pode ser configurado para aceitar apenas tipos específicos de caracteres, como números, URLs ou texto simples.
    *   **Comprimento Máximo:** Você pode definir um limite máximo de caracteres para a entrada.
    *   **Aparência e Sons:** Suporta cor de fundo personalizada, cores da borda, arredondamento da borda, cor do texto, texto de dica/placeholder, cor da dica, sons ao passar o mouse, sons ao sair e sons ao clicar.

## Dica de Ferramenta
Uma caixa de texto que pode ser configurada para aparecer em um local específico ou seguir o cursor do mouse. Sua visibilidade normalmente é controlada por [Condições (Requisitos de Carregamento)](https://docs.fancymenu.net/en/conditions).

*   **Casos de uso:**
    *   Exibir informações detalhadas quando o usuário passa o mouse sobre um botão ou imagem.
    *   Criar dicas de ajuda contextuais que aparecem sob certas condições.
    *   Mostrar informações dinâmicas (como o status do servidor) ao lado do cursor.
*   **Recursos principais:**
    *   **Seguir o Mouse:** Pode ser configurada para seguir o ponteiro do mouse.
    *   **Suporte a Markdown:** O conteúdo da dica de ferramenta suporta formatação completa em Markdown.
    *   **Fundo Personalizado:** O fundo pode ser uma cor sólida ou uma textura personalizada com nine-slicing para um visual totalmente temático.

## Item
Exibe um único item do Minecraft, seja do vanilla ou de um mod.

*   **Casos de uso:**
    *   Usar itens como ícones para botões ou seleções de menu.
    *   Criar uma interface de loja ou seleção de kits.
    *   Exibir o item ou a armadura que um jogador está segurando/usando.
*   **Recursos principais:**
    *   **Dados Personalizados:** Você pode definir o nome, lore, quantidade, brilho de encantamento e até dados NBT personalizados do item. Saiba mais sobre o uso de NBT na documentação de [Marcador de Posição de Dados NBT](https://docs.fancymenu.net/en/nbt-data-placeholder).
    *   **Exibição de Tooltip:** Pode ser configurado para mostrar a tooltip padrão do item ao passar o mouse.

## Modelo JSON de Bloco/Item
Renderiza um modelo JSON de bloco ou item a partir de recursos do Minecraft ou de fontes externas.

*   **Casos de uso:**
    *   Exibir um modelo 3D de resource pack em um menu.
    *   Mostrar prévias de item/bloco com texturas personalizadas.
    *   Criar elementos decorativos de UI baseados em modelos.
*   **Recursos principais:**
    *   **Fonte do Modelo:** Pode carregar JSON de modelo dos recursos do Minecraft ou de fontes externas.
    *   **Substituições de Textura:** Suporta definir uma textura personalizada.
    *   **Controles de Renderização:** Inclui controles de rotação e iluminação.

## Imagem
Exibe uma imagem estática de um arquivo local, de uma URL da web ou de uma localização de recurso do Minecraft.

*   **Casos de uso:**
    *   Adicionar um logo de servidor ou a marca de um modpack.
    *   Criar bordas decorativas ou molduras de UI.
    *   Usar imagens como parte de um design de UI mais complexo.
*   **Recursos principais:**
    *   **Nine-Slicing:** Permite usar a imagem como uma borda ou painel escalável sem distorcer os cantos. Saiba mais na página [Nine-Slicing e Tile](https://docs.fancymenu.net/en/nine-slicing-and-tiling).
    *   **Repetição de Textura:** A imagem pode ser repetida em mosaico para preencher a área do elemento.
    *   **Tintura:** Você pode aplicar uma tonalidade de cor à imagem.
    *   **Cantos Arredondados:** Imagens que não usam nine-slicing nem repetição podem ter cantos arredondados.
    *   **Efeito Parallax:** Pode ser configurada para se mover levemente com o mouse para um efeito 3D. Veja a página [Efeito Parallax](https://docs.fancymenu.net/en/parallax) para mais informações.

## Texto
Um elemento extremamente versátil para exibir texto. Pode ser usado para qualquer coisa, desde rótulos de uma linha até documentos multipágina com rolagem.

*   **Casos de uso:**
    *   Exibir regras do servidor, notas de atualização ou mensagens de boas-vindas.
    *   Criar painéis de informação dinâmicos usando [placeholders](https://docs.fancymenu.net/en/placeholders), por exemplo, "Bem-vindo, `{"placeholder":"playername"}`!".
    *   Adicionar rótulos e descrições à sua interface.
*   **Recursos principais:**
    *   **Fontes de Conteúdo:** O texto pode ser inserido diretamente, carregado de um arquivo local ou obtido de uma URL da web.
    *   **Suporte a Markdown:** Suporta uma ampla variedade de Markdown para formatação rica de texto, incluindo títulos, listas, blocos de código e tabelas. A aparência dos elementos Markdown é totalmente personalizável. Veja a página [Formatação de Texto](https://docs.fancymenu.net/en/text-formatting) para mais informações.
    *   **Rolagem:** Torna-se automaticamente rolável se o conteúdo for maior que a área do elemento. As barras de rolagem podem ser personalizadas ou desativadas.
    *   **Estilo:** Controle total sobre cor do texto, escala, alinhamento, sombra e espaçamento entre linhas.

## Vídeo
Reproduz um arquivo de vídeo. Isso é perfeito para introduções cinematográficas ou fundos decorativos em loop.

> O novo elemento nativo de Vídeo no FancyMenu 3.9.0 requer **Watermedia V3** e **Watermedia Binaries V3**. O antigo elemento **Video [MCEF]** foi descontinuado.
{.is-warning}

*   **Casos de uso:**
    *   Um trailer animado do modpack ou servidor.
    *   Um vídeo ambiente em loop para dar vida ao seu menu.
    *   Um vídeo tutorial dentro do jogo.
*   **Recursos principais:**
    *   **Fontes:** Suporta arquivos de vídeo locais e URLs da web. Veja a página [Vídeos (MP4)](https://docs.fancymenu.net/en/video) para detalhes.
    *   **Controle de Reprodução:** Pode ser configurado para entrar em loop automaticamente. O volume, o canal de som e o comportamento de preservação da proporção são ajustáveis.
    *   **Controle Interativo:** A reprodução, o tempo de busca e o volume do vídeo podem ser controlados por ações de botão.

## Shader GLSL
Renderiza um shader GLSL personalizado dentro de um elemento.

*   **Casos de uso:**
    *   Painéis animados com shader.
    *   Efeitos visuais procedurais.
    *   Efeitos de menu no estilo Shadertoy recortados em um retângulo do elemento.
*   **Recursos principais:**
    *   **Tempo de Execução do Shader:** Suporta shaders de passagem única e de múltiplas passagens.
    *   **Suporte a Shadertoy:** Pode usar shaders `mainImage` no estilo Shadertoy.
    *   **Uniforms:** Expõe uniforms do FancyMenu e de entrada. Veja a página [API do Shader GLSL](https://docs.fancymenu.net/en/glsl-shader-api) para detalhes.

## Apresentação de Slides
Exibe uma sequência de imagens. A configuração da apresentação (imagens, tempo, transições) é feita em um arquivo `.properties` separado localizado no diretório `/config/fancymenu/assets/slideshows/`.

*   **Casos de uso:**
    *   Uma galeria rotativa de capturas de tela do jogo.
    *   Mostrar recursos principais de um modpack.
    *   Um fundo dinâmico que alterna entre diferentes cenas.
*   **Recursos principais:**
    *   Carrega apresentações pré-configuradas. Veja a documentação de [Apresentações de Slides](https://docs.fancymenu.net/en/slideshows) para instruções de configuração.
    *   Pode ser configurado para manter a proporção das imagens.

## Forma de Retângulo
Um retângulo simples de cor sólida.

*   **Casos de uso:**
    *   Criar um fundo semitransparente atrás do texto para melhorar a legibilidade.
    *   Projetar painéis e divisórias simples de UI.
    *   Como um espaço reservado colorido durante o design do layout.
*   **Recursos principais:**
    *   Suporta cores HEX RGBA, cantos arredondados e blur opcional, permitindo que a forma funcione como um painel simples, uma tonalidade ou um fundo desfocado.

## Forma de Círculo
Uma forma simples de círculo/elipse de cor sólida.

*   **Casos de uso:**
    *   Criar destaques, indicadores ou áreas suaves de UI circulares.
    *   Construir decorações de UI temáticas sem um arquivo de textura.
*   **Recursos principais:**
    *   Funciona de forma semelhante ao elemento Forma de Retângulo e suporta personalização visual de cor/blur.

## Texto de Destaque
Uma recriação do icônico texto amarelo e saltitante de destaque do Minecraft da tela de título.

*   **Casos de uso:**
    *   Substituir o texto de destaque vanilla por suas próprias mensagens personalizadas.
    *   Adicionar uma mensagem animada e chamativa a qualquer menu.
*   **Recursos principais:**
    *   **Fontes de Conteúdo:** Pode usar os destaques padrão do vanilla, uma lista de texto personalizado inserido diretamente ou texto de um arquivo local.
    *   **Personalização:** Você pode ativar/desativar o efeito de salto e personalizar a cor, a escala, a rotação e a sombra do texto.

## Entidade do Jogador
Renderiza um modelo de jogador no menu.

*   **Casos de uso:**
    *   Exibir o personagem do jogador atual no menu principal.
    *   Criar uma tela de seleção de equipe ou prévia de classe.
    *   Uma seção de "perfil" mostrando a skin e o nome do jogador.
*   **Recursos principais:**
    *   **Aparência Dinâmica:** Pode ser configurado para copiar automaticamente a skin, a capa e o nome do jogador atual. Para saber mais, confira o guia [Cabeças de Jogador](https://docs.fancymenu.net/en/player-heads).
    *   **Poses Personalizadas:** Oferece controle detalhado sobre a rotação da cabeça, corpo, braços e pernas. A cabeça e o corpo também podem ser configurados para seguir o cursor do mouse.
    *   **Atributos:** Pode ser configurado para ser um bebê, agachar ou usar um modelo esguio.

## Navegador
Um elemento que renderiza uma página da web ao vivo dentro do jogo.

Este elemento requer que o mod **MCEF (Minecraft Chromium Embedded Framework)** esteja instalado e funcionando!

Você pode baixar o MCEF nas páginas oficiais do projeto no [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) e no [Modrinth](https://modrinth.com/mod/mcef).

Para versões mais novas do Minecraft (1.21.5+), os projetos oficiais do MCEF não fornecem builds, mas existe um fork com builds para as versões mais recentes do Minecraft, que pode ser encontrado [aqui](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) e [aqui](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Este fork é mantido por Keksuccino, para disponibilizar builds para as versões mais recentes do Minecraft o mais rápido possível.

*   **Casos de uso:**
    *   Exibir o Dynmap ao vivo de um servidor.
    *   Incorporar um player de vídeo do YouTube.
    *   Mostrar um wiki ou página de documentação diretamente no jogo.
*   **Recursos principais:**
    *   **Interatividade:** Pode ser totalmente interativo, permitindo que os usuários cliquem em links, rolem a página e digitem.
    *   **Controle de Mídia:** Oferece opções para silenciar a mídia, colocar vídeos em loop e ocultar os controles de vídeo na página carregada.

### Carregando Arquivos HTML Locais
O elemento Navegador permite carregar documentos HTML locais em `/config/fancymenu/assets/`! Isso significa que você pode exibir conteúdo local renderizado pelo navegador para changelogs com visual sofisticado e muito mais.

Para carregar um arquivo HTML local, comece sua URL com `file:///`, seguido do caminho CURTO do arquivo, por exemplo `/config/fancymenu/assets/cool_changelog.html`, o que faz com que fique assim: `file:///config/fancymenu/assets/cool_changelog.html`.

No **Linux**, você precisa fornecer o caminho absoluto do arquivo, mas como codificar um caminho absoluto diretamente quebraria o layout, você precisa permitir que um placeholder converta o caminho curto para um absoluto dinamicamente: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

É SUPER IMPORTANTE que você comece o caminho curto com `/` no Linux, como no exemplo acima. Sem isso, não funcionará.

## Animador de Elementos
Uma ferramenta poderosa para criar animações complexas baseadas em keyframes. Ela pode animar a posição, o tamanho e o ponto de ancoragem de um ou vários outros elementos.

*   **Casos de uso:**
    *   Criar uma animação de introdução sofisticada na qual elementos do menu deslizam ou desaparecem gradualmente na tela.
    *   Fazer elementos decorativos pulsarem, girarem ou se moverem ao longo de um caminho.
    *   Animar uma notificação para aparecer e depois desaparecer.
*   **Recursos principais:**
    *   **Editor de Keyframes:** Um editor dedicado para adicionar, editar e sequenciar keyframes em uma linha do tempo.
    *   **Múltiplos Alvos:** Um único Animador pode controlar vários elementos "alvo" ao mesmo tempo.
    *   **Controle:** As animações podem ser configuradas para entrar em loop. Você também pode escolher animar apenas posição ou tamanho.
    *   **Deslocamentos de Tempo:** Os elementos-alvo podem usar deslocamentos de tempo de início individuais ou aleatórios.
    *   **[Saiba mais sobre o Animador de Elementos.](https://docs.fancymenu.net/en/element-animator)**

## Ticker
Um elemento invisível que executa uma lista de ações em um intervalo regular (a cada "tick").

> Para novas automações de fundo no FancyMenu 3.9.0+, considere usar [Agendadores](https://docs.fancymenu.net/en/schedulers). Os Agendadores são globais, mais fáceis de organizar e podem continuar executando independentemente de uma tela específica.
{.is-info}

*   **Casos de uso:**
    *   Verificar periodicamente o status online de um servidor e atualizar um elemento de texto.
    *   Criar um temporizador regressivo que atualiza um rótulo de texto.
    *   Executar um script repetidamente para criar comportamentos personalizados.
*   **Recursos principais:**
    *   **Controle de Tempo:** Você pode definir o atraso entre ticks em milissegundos.
    *   **Modos de Tick:** Pode ser configurado para executar continuamente, apenas uma vez por sessão de jogo ou uma vez toda vez que o menu é carregado.
    *   **Assíncrono:** Pode executar suas [ações](https://docs.fancymenu.net/en/action-scripts) em uma thread separada para evitar impacto no desempenho do jogo, embora algumas ações não possam ser executadas dessa forma.

## Áudio
Um elemento invisível que reproduz arquivos de áudio. Ele pode gerenciar uma playlist de faixas e oferece vários controles de reprodução.

*   **Casos de uso:**
    *   Adicionar música de fundo personalizada a um menu.
    *   Criar um player de música com botões para controlar a reprodução (faixa anterior/próxima, volume).
    *   Reproduzir paisagens sonoras ambientes.
*   **Recursos principais:**
    *   **Playlist:** Pode gerenciar várias faixas de áudio.
    *   **Modos de Reprodução:** Pode reproduzir faixas em ordem ou em ordem aleatória (com suporte a peso de faixa para tornar algumas mais comuns que outras).
    *   **Controle:** Suporta loop, ajuste de volume e pode ser atribuído a um canal de som específico (por exemplo, Master, Music). Para mais informações, consulte a página [Música de Fundo do Menu](https://docs.fancymenu.net/en/background-music).

## Controlador de Música
Um elemento invisível usado para controlar a reprodução da música padrão do Minecraft dentro de um menu específico.

*   **Casos de uso:**
    *   Desativar a música padrão do menu em uma tela onde você quer tocar sua própria música personalizada por meio de um elemento **Áudio**.
    *   Impedir que a música do mundo continue tocando quando um menu é aberto no jogo.
*   **Recursos principais:**
    *   Alternâncias separadas para controlar a "Menu Music" vanilla e a "World Music".

## Barra de Progresso
Uma barra personalizável que representa visualmente um valor numérico.

*   **Casos de uso:**
    *   Uma barra de carregamento que acompanha o progresso de carregamento do mundo usando `{"placeholder":"world_load_progress"}`.
    *   Barras visuais de vida, fome ou experiência para um HUD no jogo.
    *   Um indicador de volume controlado por um elemento **Slider**.
*   **Recursos principais:**
    *   **Valor Dinâmico:** O valor de progresso (0-100 ou 0.0-1.0) é definido por meio de um campo de texto que suporta [placeholders](https://docs.fancymenu.net/en/placeholders).
    *   **Aparência:** A direção da barra (cima, baixo, esquerda, direita), as cores, as texturas e o nine-slicing para texturas de barra/fundo são todos personalizáveis.
    *   **Animação:** Conta com uma animação suave de preenchimento para tornar as mudanças de progresso menos bruscas.

## Arrastador
Um elemento invisível no qual o usuário pode clicar e arrastar para mover. Outros elementos podem ser ancorados a ele para criar widgets móveis.

*   **Casos de uso:**
    *   Criar um relógio ou painel de informações arrastável.
    *   Permitir que os usuários personalizem a posição dos elementos da interface conforme sua preferência.
*   **Recursos principais:**
    *   **Posição Persistente:** O deslocamento arrastado é salvo, então o elemento permanece onde o usuário o deixou, mesmo após reiniciar o jogo.
    *   **Ponto de Ancoragem:** Age como uma âncora móvel para outros elementos, o que é uma parte fundamental do [Posicionamento de Elementos](https://docs.fancymenu.net/en/positioning-elements).

## Cursor
Um elemento invisível que substitui o cursor padrão do sistema por uma imagem personalizada quando um layout está ativo.

*   **Casos de uso:**
    *   Criar uma interface totalmente temática que combine com a estética do seu modpack.
*   **Recursos principais:**
    *   **Textura Personalizada:** Use qualquer imagem como cursor.
    *   **Hotspot:** Você pode definir o pixel exato na imagem que serve como o "ponto de clique". Veja o guia [Cursor Personalizado](https://docs.fancymenu.net/en/custom-cursor) para mais informações.
