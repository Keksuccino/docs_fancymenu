---
title: Elementos
description: Tudo o que você precisa saber sobre os tipos de elementos do FancyMenu.
---
# Elementos

Os elementos são os blocos de construção dos seus layouts personalizados no FancyMenu. Você pode adicioná-los a qualquer layout para exibir informações, adicionar interatividade ou criar efeitos visuais impressionantes.

# Adicionando Elementos a um Layout

Você pode adicionar um novo elemento ao seu layout dentro do **Editor de Layout**.

1.  **Clique com o botão direito** no fundo do editor para abrir o menu de contexto.
2.  Passe o mouse sobre **Novo Elemento**.
3.  Uma lista com todos os tipos de elementos disponíveis será exibida. Clique naquele que você quer adicionar.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Depois que um elemento é adicionado, você pode movê-lo, redimensioná-lo e personalizá-lo clicando nele com o **botão direito** para abrir o menu de contexto específico dele. Para saber mais sobre como organizar elementos, veja [Posicionando Elementos](./positioning-elements) e [Identificadores de Elementos](./element-identifiers).

# Elementos em Detalhe

Esta seção lista os elementos nativos do FancyMenu. Use [Camadas e Grupos](./layers-and-groups) para organizar a ordem de renderização.

## Button
Um botão clicável que pode executar uma grande variedade de ações. Este é um dos elementos mais poderosos e versáteis para criar menus interativos.

*   **Casos de uso:**
    *   Criar um botão "Entrar no Discord" ou "Visitar Site".
    *   Adicionar um botão de entrada rápida para um servidor específico.
    *   Construir navegação personalizada entre diferentes menus.
    *   Criar botões que ativam ou desativam outros layouts.
*   **Recursos principais:**
    *   **Ações:** Pode executar uma sequência de [ações](./action-scripts), como abrir uma URL, entrar em um servidor, enviar um comando no chat, imitar a função de outro botão ou controlar variáveis.
    *   **Aparência personalizada:** Texturas totalmente personalizáveis para os estados normal, com hover e inativo. Suporta fundos transparentes, nine-slicing, cores de rótulo personalizadas, cores de rótulo ao passar o mouse, escala do rótulo, alternância de sombra no rótulo e texturas de ícone do botão.
    *   **Sons:** Sons personalizados de clique, hover e saída do hover.
    *   **Modo modelo:** Pode aplicar sua aparência e propriedades a outros botões Vanilla ou modificados no menu. Veja [Modelos de Botão e Slider](./button-slider-templates).
    *   **Cliques automatizados em widgets Vanilla/mod:** Widgets Vanilla e modded existentes têm uma propriedade **Cliques Automatizados** que pode invocar o comportamento original de clique um número escolhido de vezes quando a tela carrega. Veja [Elementos Vanilla](./vanilla-elements#automated-clicks) para detalhes.

## Slider
Um controle deslizante que os usuários podem arrastar para selecionar um valor de uma lista ou de um intervalo. Pode executar ações sempre que seu valor mudar.

*   **Casos de uso:**
    *   Criar um controle de volume personalizado.
    *   Um slider para alternar entre temas diferentes ou imagens de fundo (usando o tipo "Lista").
    *   Ajustar uma opção específica do Minecraft, como brilho ou distância de renderização.
*   **Recursos principais:**
    *   **Tipos:** Pode ser uma `Lista de Valores` (por exemplo, "Fácil", "Normal", "Difícil"), um `Intervalo Inteiro` (por exemplo, 1-100) ou um `Intervalo Decimal` (por exemplo, 0,0-1,0).
    *   **Ações dinâmicas:** Executa ações quando seu valor muda. O valor atual pode ser usado com [Variáveis](./variables).
    *   **Personalização:** O rótulo do slider pode exibir dinamicamente seu valor atual. A alça e as texturas de fundo são totalmente personalizáveis, incluindo fundos transparentes, opções de cor/escala do rótulo, alternância de sombra no texto e sons personalizados de clique/desativação do hover.

## Checkbox
Uma caixa de seleção padrão que pode ser ativada ou desativada. Pode executar ações ao ser alternada.

*   **Casos de uso:**
    *   Uma caixa "Eu concordo com as regras".
    *   Uma configuração para ativar ou desativar um recurso específico no seu menu personalizado.
    *   Ativar ou desativar um layout ou variável.
*   **Recursos principais:**
    *   **Ações ao alternar:** Executa [Scripts de Ação](./action-scripts) quando seu estado muda. O estado atual (`true` ou `false`) fica disponível para suas ações.
    *   **Modo Variável:** Pode ser vinculado diretamente a uma variável do FancyMenu, fazendo com que o estado da caixa seja lido e gravado nessa variável.
    *   **Estado persistente:** Quando o Modo Variável está desativado, a caixa salva automaticamente seu estado pelo identificador do elemento e o restaura após reiniciar o jogo. Esses estados são armazenados em `<game-directory>/checkbox_states.json`. No Modo Variável, a variável do FancyMenu vinculada é a fonte do estado da caixa.
    *   **Aparência personalizada:** Suporta texturas personalizadas para o fundo (nos estados normal, hover e inativo) e para a própria marcação.

## Text Input Field
Um campo onde os usuários podem digitar texto. Seu conteúdo pode ser vinculado a uma variável do FancyMenu, permitindo capturar e usar a entrada do usuário.

*   **Casos de uso:**
    *   Um campo de entrada "IP do Servidor" que funciona com um botão "Entrar no Servidor".
    *   Um campo para inserir o nome de um jogador para uma prévia de skin personalizada.
    *   Criar uma interface básica semelhante a um login.
*   **Recursos principais:**
    *   **Vinculação a variável:** Armazena o texto digitado em uma [variável](./variables) específica.
    *   **Validação de entrada:** Pode ser configurado para aceitar apenas tipos específicos de caracteres, como números, URLs ou texto simples.
    *   **Comprimento máximo:** Você pode definir um limite máximo de caracteres para a entrada.
    *   **Aparência e sons:** Suporta cor de fundo personalizada, cores da borda, arredondamento da borda, cor do texto, texto de dica/placeholder, cor da dica, sons de hover, sons de saída do hover e sons de clique.

## Tooltip
Uma caixa de texto que pode aparecer em uma posição fixa ou seguir o cursor do mouse. Sua visibilidade normalmente é controlada com [Requisitos de Carregamento](./conditions).

*   **Casos de uso:**
    *   Exibir informações detalhadas quando o usuário passa o mouse sobre um botão ou imagem.
    *   Criar dicas de ajuda sensíveis ao contexto que aparecem sob certas condições.
    *   Mostrar informações dinâmicas (como o status de um servidor) ao lado do cursor.
*   **Recursos principais:**
    *   **Seguir o mouse:** Pode ser configurado para seguir o ponteiro do mouse.
    *   **Suporte a Markdown:** O conteúdo do tooltip suporta formatação completa em Markdown.
    *   **Fundo personalizado:** O fundo pode ser uma cor sólida ou uma textura personalizada com nine-slicing para um visual totalmente temático.

## Item
Exibe um único item do Minecraft, seja vanilla ou de um mod.

*   **Casos de uso:**
    *   Usar itens como ícones para botões ou seleções de menu.
    *   Criar uma interface de loja ou seleção de kits.
    *   Exibir o item ou a armadura que um jogador está segurando/equipando.
*   **Recursos principais:**
    *   **Dados personalizados:** Suporta nome personalizado, lore, quantidade, brilho de encantamento e dados NBT. Veja o [Placeholder de Dados NBT](./nbt-data-placeholder).
    *   **Exibição de tooltip:** Pode ser configurado para mostrar o tooltip padrão do item ao passar o mouse.

## Block/Item JSON Model
Renderiza um modelo JSON de bloco ou item dos recursos do Minecraft ou de fontes externas.

*   **Casos de uso:**
    *   Exibir um modelo 3D de resource pack em um menu.
    *   Mostrar prévias de itens/blocos com texturas personalizadas.
    *   Criar elementos decorativos de interface baseados em modelo.
*   **Recursos principais:**
    *   **Fonte do modelo:** Pode carregar JSON do modelo a partir de recursos do Minecraft ou de fontes externas.
    *   **Substituições de textura:** Suporta definir uma textura personalizada.
    *   **Controles de renderização:** Offset do modelo, escala, rotação nos três eixos, renderização translúcida e o transform do GUI do modelo.
    *   **Iluminação:** Duas luzes configuráveis com controles independentes de matiz e rotação.

## Image
Exibe uma imagem estática de um arquivo local, de uma URL da web ou de um local de recurso do Minecraft.

*   **Casos de uso:**
    *   Adicionar o logotipo de um servidor ou a marca de um modpack.
    *   Criar bordas decorativas ou molduras de interface.
    *   Usar imagens como parte de um design de UI mais complexo.
*   **Recursos principais:**
    *   **Nine-slicing:** Redimensiona bordas ou painéis sem distorcer os cantos. Veja [Nine-Slicing & Tiling](./nine-slicing-and-tiling).
    *   **Repetição de textura:** A imagem pode ser repetida em mosaico para preencher a área do elemento.
    *   **Tintura:** Você pode aplicar uma tonalidade de cor à imagem.
    *   **Cantos arredondados:** Imagens que não usam nine-slicing e não são repetidas podem ter cantos arredondados.
    *   **Efeito parallax:** Move-se com o mouse para criar profundidade visual. Veja [Efeito Parallax](./parallax).

## Text
Um elemento altamente versátil para exibir texto. Pode ser usado para qualquer coisa, desde rótulos de uma linha até documentos com várias páginas e roláveis.

*   **Casos de uso:**
    *   Exibir regras do servidor, notas de atualização ou mensagens de boas-vindas.
    *   Criar painéis de informação dinâmicos usando [placeholders](./placeholders), por exemplo `Welcome, {"placeholder":"playername"}!`.
    *   Adicionar rótulos e descrições à sua interface.
*   **Recursos principais:**
    *   **Fontes de conteúdo:** O texto pode ser inserido diretamente, carregado de um arquivo local ou obtido de uma URL da web.
    *   **Suporte a Markdown:** Suporta títulos, listas, blocos de código, tabelas e outras formatações Markdown. Veja [Formatação de Texto](./text-formatting).
    *   **Rolagem:** Torna-se rolável automaticamente se o conteúdo for maior que a área do elemento. As barras de rolagem podem ser personalizadas ou desativadas.
    *   **Estilização:** Controle total sobre cor do texto, escala, alinhamento, sombra e espaçamento entre linhas.

## Video
Reproduz um arquivo de vídeo. É perfeito para intros cinematográficas ou fundos decorativos em loop.

> [!WARNING]
> O elemento nativo de vídeo requer **Watermedia V3** e **Watermedia Binaries V3**. O antigo elemento **Video [MCEF]** está obsoleto.

*   **Casos de uso:**
    *   Um trailer animado de modpack ou servidor.
    *   Um vídeo ambiente em loop para dar vida ao seu menu.
    *   Um vídeo tutorial dentro do jogo.
*   **Recursos principais:**
    *   **Fontes:** Suporta arquivos de vídeo locais e URLs da web. Veja [Vídeos](./video).
    *   **Controle de reprodução:** Pode ser configurado para repetir automaticamente em loop. O volume, o canal de áudio e o comportamento de preservação da proporção são ajustáveis.
    *   **Controle interativo:** A reprodução, o tempo de avanço e o volume do vídeo podem ser controlados via ações de botão.

## GLSL Shader
Renderiza um shader GLSL personalizado dentro de um elemento.

*   **Casos de uso:**
    *   Painéis de shader animados.
    *   Efeitos visuais procedurais.
    *   Efeitos de menu no estilo Shadertoy recortados em um retângulo do elemento.
*   **Recursos principais:**
    *   **Runtime do shader:** Suporta shaders de passe único e multipasse.
    *   **Suporte ao Shadertoy:** Pode usar shaders `mainImage` no estilo Shadertoy.
    *   **Uniforms:** Exibe uniforms do FancyMenu e de entrada. Veja a [API do GLSL Shader](./glsl-shader-api).

## Slideshow
Exibe uma sequência de imagens. Suas imagens e o arquivo de configuração `properties.txt` ficam no próprio subdiretório do slideshow em `<game-directory>/config/fancymenu/slideshows/`.

*   **Casos de uso:**
    *   Uma galeria rotativa de capturas de tela do jogo.
    *   Mostrar os principais recursos de um modpack.
    *   Um fundo dinâmico que alterna entre diferentes cenas.
*   **Recursos principais:**
    *   Carrega [slideshows](./slideshows) pré-configurados.
    *   Pode ser configurado para manter a proporção das imagens.

## Rectangle Shape
Um retângulo simples de cor sólida.

*   **Casos de uso:**
    *   Criar um fundo semitransparente atrás do texto para melhorar a legibilidade.
    *   Projetar painéis e divisórias simples de UI.
    *   Como um placeholder colorido durante o design do layout.
*   **Recursos principais:**
    *   Suporta cores HEX RGBA, cantos arredondados e blur opcional, permitindo que a forma funcione como um painel simples, uma tintura ou um fundo desfocado.

## Circle Shape
Uma forma simples de círculo/elipse de cor sólida.

*   **Casos de uso:**
    *   Criar destaques circulares, indicadores ou áreas suaves de UI.
    *   Construir decorações temáticas de interface sem um arquivo de textura.
*   **Recursos principais:**
    *   Suporta cor, blur e um valor configurável de arredondamento/expoente.

## Splash Text
Uma recriação do icônico splash text amarelo e saltitante do Minecraft na tela de título.

*   **Casos de uso:**
    *   Substituir o splash text vanilla por suas próprias mensagens personalizadas.
    *   Adicionar uma mensagem animada e chamativa a qualquer menu.
*   **Recursos principais:**
    *   **Fontes de conteúdo:** Pode usar os splashes vanilla padrão, uma lista de textos personalizados inseridos diretamente ou texto de um arquivo local.
    *   **Personalização:** Você pode alternar o efeito de salto e personalizar a cor, escala, rotação e sombra do texto.

## Player Entity
Renderiza um modelo de jogador no menu.

*   **Casos de uso:**
    *   Exibir o personagem do jogador atual no menu principal.
    *   Criar uma tela de seleção de equipe ou prévia de classe.
    *   Uma seção de "perfil" mostrando a skin e o nome do jogador.
*   **Recursos principais:**
    *   **Aparência dinâmica:** Pode copiar a skin, capa e nome do jogador atual. Veja [Cabeças de Jogador](./player-heads).
    *   **Poses personalizadas:** Oferece controle refinado sobre a rotação da cabeça, corpo, braços e pernas. A cabeça e o corpo também podem seguir o cursor do mouse.
    *   **Atributos:** Pode ser configurado para ser um bebê, agachado ou usar um modelo slim.

## Browser
Um elemento que renderiza uma página web ao vivo dentro do jogo.

Este elemento requer que o mod **MCEF (Minecraft Chromium Embedded Framework)** esteja instalado e funcionando!

Você pode baixar o MCEF nas páginas oficiais do projeto no [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) e no [Modrinth](https://modrinth.com/mod/mcef).

Para versões mais recentes do Minecraft (1.21.5+), os projetos oficiais do MCEF não fornecem builds, mas existe um fork com builds para as versões mais recentes do Minecraft, que pode ser encontrado [aqui](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) e [aqui](https://modrinth.com/mod/mcef-keksuccino) (Modrinth). Este fork é mantido por Keksuccino, para disponibilizar builds das versões mais recentes do Minecraft o mais rápido possível.

*   **Casos de uso:**
    *   Exibir o Dynmap ao vivo de um servidor.
    *   Incorporar um reprodutor de vídeo do YouTube.
    *   Mostrar uma wiki ou página de documentação diretamente no jogo.
*   **Recursos principais:**
    *   **Interatividade:** Pode ser totalmente interativo, permitindo que os usuários cliquem em links, rolem e digitem.
    *   **Controle de mídia:** Oferece opções para silenciar mídias, repetir vídeos em loop e ocultar controles de vídeo na página carregada.

### Carregando Arquivos HTML Locais
O elemento Browser pode carregar documentos HTML locais de `<game-directory>/config/fancymenu/assets/`.

Para carregar um arquivo HTML local, comece sua URL com `file:///`, seguido do caminho de arquivo CURTO, por exemplo `/config/fancymenu/assets/cool_changelog.html`, o que faz com que ela fique assim: `file:///config/fancymenu/assets/cool_changelog.html`.

No **Linux**, use o [**placeholder de Caminho Absoluto de Arquivo/Pasta**](./placeholders#absolute-filefolder-path-absolute_path) em vez de codificar um caminho absoluto específico da instância: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

O caminho curto no Linux deve começar com `/`, como mostrado no exemplo.

## Element Animator
Uma ferramenta poderosa para criar animações complexas baseadas em keyframes. Ela pode animar a posição, o tamanho e o ponto de ancoragem de um ou vários outros elementos.

*   **Casos de uso:**
    *   Deslizar elementos para dentro ou para fora da tela.
    *   Redimensionar painéis ou notificações.
    *   Animar deslocamentos de posição e transições de âncora.
*   **Recursos principais:**
    *   **Editor de keyframes:** Um editor dedicado para adicionar, editar e sequenciar keyframes em uma linha do tempo.
    *   **Múltiplos alvos:** Um único Animator pode controlar vários elementos "alvo" ao mesmo tempo.
    *   **Controle:** As animações podem ser configuradas para repetir em loop. Você também pode optar por animar apenas posição ou tamanho.
    *   **Deslocamentos de tempo:** Os elementos-alvo podem usar deslocamentos individuais ou aleatórios de tempo de início.
    *   Veja [Element Animator](./element-animator) para configuração e edição de keyframes.

## Ticker
Um elemento invisível que executa uma lista de ações em um intervalo regular (a cada "tick").

> [!NOTE]
> Para automação em segundo plano, considere usar [Agendadores](./schedulers). Os agendadores são globais e podem ser executados de forma independente de uma tela específica.

*   **Casos de uso:**
    *   Verificar periodicamente se um servidor está online e atualizar um elemento de texto.
    *   Criar um cronômetro regressivo que atualiza um rótulo de texto.
    *   Executar um script repetidamente para criar comportamentos personalizados.
*   **Recursos principais:**
    *   **Controle de tempo:** Você pode definir o atraso entre os ticks em milissegundos.
    *   **Modos de tick:** Pode ser configurado para executar continuamente, apenas uma vez por sessão de jogo ou uma vez sempre que o menu for carregado.
    *   **Assíncrono:** Pode executar suas [ações](./action-scripts) separadamente, embora algumas ações não possam ser executadas quando essa opção está ativada.

## Audio
Um elemento invisível que reproduz arquivos de áudio. Ele pode gerenciar uma playlist de faixas e oferece vários controles de reprodução.

*   **Casos de uso:**
    *   Adicionar música de fundo personalizada a um menu.
    *   Criar um player de música com botões para controlar a reprodução (faixa anterior/próxima, volume).
    *   Reproduzir sons ambientes.
*   **Recursos principais:**
    *   **Playlist:** Pode gerenciar várias faixas de áudio.
    *   **Modos de reprodução:** Pode reproduzir faixas em ordem ou em ordem aleatória (com suporte a peso de faixas para tornar algumas mais comuns que outras).
    *   **Controle:** Suporta repetição em loop, ajuste de volume e seleção de canal de som. Veja [Música de Fundo do Menu](./background-music).

## Music Controller
Um elemento invisível usado para controlar a reprodução da música padrão do Minecraft dentro de um menu específico.

*   **Casos de uso:**
    *   Desativar a música padrão do menu em uma tela onde você quer tocar sua própria música personalizada por meio de um [elemento **Audio**](#audio).
    *   Impedir que a música do mundo continue tocando quando um menu é aberto dentro do jogo.
*   **Recursos principais:**
    *   Alternâncias separadas para controlar "Menu Music" e "World Music" vanilla.

## Progress Bar
Uma barra personalizável que representa visualmente um valor numérico.

*   **Casos de uso:**
    *   Uma barra de carregamento que acompanha o progresso de carregamento do mundo usando `{"placeholder":"world_load_progress"}`.
    *   Barras visuais de saúde, fome ou experiência para uma HUD dentro do jogo.
    *   Um indicador de volume controlado por um [elemento **Slider**](#slider).
*   **Recursos principais:**
    *   **Valor dinâmico:** O valor de progresso (0-100 ou 0,0-1,0) é definido por um campo de texto que suporta [placeholders](./placeholders).
    *   **Aparência:** A direção da barra (cima, baixo, esquerda, direita), cores, texturas e nine-slicing para texturas da barra/fundo são todos personalizáveis.
    *   **Animação:** Apresenta uma animação de preenchimento suave para que as mudanças de progresso pareçam menos bruscas.
    *   **Âncora de elemento baseada em progresso:** Quando outro elemento usa a barra de progresso como âncora de **Elemento**, ative **Usar Progresso para Âncora do Elemento** para mover essa âncora até a borda atual da área preenchida. Os elementos ancorados então acompanham o progresso da barra em vez de permanecerem presos aos limites estáticos da barra de progresso.

## Dragger
Um elemento invisível que o usuário pode clicar e arrastar para mover. Outros elementos podem ser ancorados a ele para criar widgets móveis.

*   **Casos de uso:**
    *   Criar um relógio ou painel de informações arrastável.
    *   Permitir que os usuários personalizem a posição dos elementos da UI de acordo com sua preferência.
*   **Recursos principais:**
    *   **Persistência opcional:** Ative **Salvar Deslocamento de Arrasto do Usuário** para manter a posição arrastada pelo usuário entre aberturas de tela e reinicializações do jogo. Desative para redefinir o deslocamento.
    *   **Ponto de ancoragem:** Age como uma âncora móvel para outros elementos, o que é uma parte importante de [Posicionando Elementos](./positioning-elements).

## Cursor
Um elemento invisível que substitui o cursor padrão do sistema por uma imagem personalizada quando um layout está ativo.

*   **Casos de uso:**
    *   Criar uma UI totalmente temática que combine com a estética do seu modpack.
*   **Recursos principais:**
    *   **Textura personalizada:** Use qualquer imagem para o cursor.
    *   **Hotspot:** Define o pixel exato da imagem usado como ponto de clique. Veja [Cursor Personalizado](./custom-cursor).
