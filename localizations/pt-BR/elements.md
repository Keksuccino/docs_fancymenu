---
title: Elementos
description: Tudo o que você precisa saber sobre os tipos de elementos do FancyMenu.
---
# Elementos

Os elementos são os blocos de construção dos seus layouts personalizados no FancyMenu. Você pode adicioná-los a qualquer layout para exibir informações, adicionar interatividade ou criar efeitos visuais impressionantes.

# Adicionando Elementos a um Layout

Você pode adicionar um novo elemento ao seu layout dentro do **Editor de Layout**.

1.  **Clique com o botão direito** no plano de fundo do editor para abrir o menu de contexto.
2.  Passe o mouse sobre **Novo Elemento**.
3.  Uma lista com todos os tipos de elementos disponíveis aparecerá. Clique naquele que você deseja adicionar.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Depois que um elemento for adicionado, você pode movê-lo, redimensioná-lo e personalizá-lo **clicando com o botão direito** nele para abrir o menu de contexto específico. Para saber mais sobre como organizar elementos, consulte [Posicionando Elementos](./positioning-elements) e [Identificadores de Elementos](./element-identifiers).

# Elementos em Detalhe

Esta seção lista os elementos integrados do FancyMenu. Use [Camadas e Grupos](./layers-and-groups) para organizar sua ordem de renderização.

## Botão
Um botão clicável que pode executar uma ampla variedade de ações. Este é um dos elementos mais poderosos e versáteis para criar menus interativos.

*   **Casos de uso:**
    *   Criar um botão "Entrar no Discord" ou "Visitar Site".
    *   Adicionar um botão de entrada rápida para um servidor específico.
    *   Construir navegação personalizada entre diferentes menus.
    *   Criar botões que ativam ou desativam outros layouts.
*   **Principais recursos:**
    *   **Ações:** Pode executar uma sequência de [ações](./action-scripts), como abrir uma URL, entrar em um servidor, enviar um comando de chat, imitar a função de outro botão ou controlar variáveis.
    *   **Aparência personalizada:** Texturas totalmente personalizáveis para os estados normal, com hover e inativo. Suporta fundos transparentes, nine-slicing, cores personalizadas do rótulo, cores do rótulo no hover, escala do rótulo, alternância de sombra do rótulo e texturas de ícone do botão.
    *   **Sons:** Sons personalizados de clique, hover e sair do hover.
    *   **Modo de modelo:** Pode aplicar sua aparência e propriedades a outros botões vanilla ou modificados no menu. Veja [Modelos de Botão e Slider](./button-slider-templates).
    *   **Cliques automatizados em widgets vanilla/mod:** Widgets vanilla e modded existentes têm uma propriedade **Cliques Automatizados** que pode acionar o comportamento original de clique um número escolhido de vezes quando a tela carrega. Veja [Elementos Vanilla](./vanilla-elements#automated-clicks) para mais detalhes.

## Slider
Um slider que os usuários podem arrastar para selecionar um valor de uma lista ou de um intervalo. Ele pode executar ações sempre que seu valor muda.

*   **Casos de uso:**
    *   Criar um controle de volume personalizado.
    *   Um slider para alternar entre temas ou imagens de fundo diferentes (usando o tipo "Lista").
    *   Ajustar uma opção específica do Minecraft, como brilho ou distância de renderização.
*   **Principais recursos:**
    *   **Tipos:** Pode ser uma `Lista de Valores` (por exemplo, "Fácil", "Normal", "Difícil"), um `Intervalo Inteiro` (por exemplo, 1-100) ou um `Intervalo Decimal` (por exemplo, 0.0-1.0).
    *   **Ações dinâmicas:** Executa ações quando seu valor muda. O valor atual pode ser usado com [Variáveis](./variables).
    *   **Personalização:** O rótulo do slider pode exibir dinamicamente seu valor atual. A alça e as texturas de fundo são totalmente personalizáveis, incluindo fundos transparentes, opções de cor/escala do rótulo, alternância de sombra do texto e sons personalizados de clique/sair do hover.

## Caixa de Seleção
Uma caixa de seleção padrão que pode ser ativada ou desativada. Ela pode executar ações quando é alternada.

*   **Casos de uso:**
    *   Uma caixa de seleção "Eu concordo com as regras".
    *   Uma configuração para ativar ou desativar um recurso específico no seu menu personalizado.
    *   Alternar um layout ou variável entre ligado e desligado.
*   **Principais recursos:**
    *   **Ações ao alternar:** Executa [Scripts de Ação](./action-scripts) quando seu estado muda. O estado atual (`true` ou `false`) fica disponível para suas ações.
    *   **Modo de variável:** Pode ser vinculado diretamente a uma variável do FancyMenu, fazendo com que o estado da caixa de seleção leia e escreva nessa variável.
    *   **Estado persistente:** Quando o Modo de Variável está desativado, a caixa de seleção salva automaticamente seu estado pelo identificador do elemento e o restaura após reiniciar o jogo. Esses estados são armazenados em `<game-directory>/checkbox_states.json`. No Modo de Variável, a variável do FancyMenu vinculada passa a ser a fonte do estado da caixa de seleção.
    *   **Aparência personalizada:** Suporta texturas personalizadas para o fundo (nos estados normal, com hover e inativo) e para a própria marcação.

## Campo de Texto
Um campo onde os usuários podem digitar texto. Seu conteúdo pode ser vinculado a uma variável do FancyMenu, permitindo capturar e usar a entrada do usuário.

*   **Casos de uso:**
    *   Um campo de entrada de "IP do Servidor" que funciona com um botão "Entrar no Servidor".
    *   Um campo para inserir o nome de um jogador para uma prévia de skin personalizada.
    *   Criar uma interface básica semelhante a um login.
*   **Principais recursos:**
    *   **Vinculação de variável:** Armazena o texto digitado em uma [variável](./variables) especificada.
    *   **Validação de entrada:** Pode ser configurado para aceitar apenas tipos específicos de caracteres, como números, URLs ou texto puro.
    *   **Comprimento máximo:** Você pode definir um limite máximo de caracteres para a entrada.
    *   **Aparência e sons:** Suporta cor de fundo personalizada, cores da borda, arredondamento da borda, cor do texto, texto de dica/placeholder, cor da dica, sons de hover, sons de sair do hover e sons de clique.

## Tooltip
Uma caixa de texto que pode aparecer em uma posição fixa ou seguir o cursor do mouse. Sua visibilidade normalmente é controlada com [Requisitos de Carregamento](./conditions).

*   **Casos de uso:**
    *   Exibir informações detalhadas quando um usuário passa o mouse sobre um botão ou imagem.
    *   Criar dicas de ajuda sensíveis ao contexto que aparecem sob certas condições.
    *   Mostrar informações dinâmicas (como o status do servidor) ao lado do cursor.
*   **Principais recursos:**
    *   **Seguir o mouse:** Pode ser configurado para seguir o ponteiro do mouse.
    *   **Suporte a Markdown:** O conteúdo do tooltip suporta formatação completa em Markdown.
    *   **Fundo personalizado:** O fundo pode ser uma cor sólida ou uma textura personalizada com nine-slicing para uma aparência totalmente temática.

## Item
Exibe um único item do Minecraft, seja vanilla ou de um mod.

*   **Casos de uso:**
    *   Usar itens como ícones para botões ou seleções de menu.
    *   Criar uma interface de loja ou seleção de kits.
    *   Exibir o item ou a armadura que um jogador está segurando.
*   **Principais recursos:**
    *   **Dados personalizados:** Suporta nome personalizado, lore, quantidade, efeito brilhante de encantamento e dados NBT. Veja o [Placeholder de Dados NBT](./nbt-data-placeholder).
    *   **Exibição de tooltip:** Pode ser configurado para mostrar o tooltip padrão do item ao passar o mouse.

## Modelo JSON de Bloco/Item
Renderiza um modelo JSON de bloco ou item dos recursos do Minecraft ou de fontes externas.

*   **Casos de uso:**
    *   Exibir um modelo 3D de resource pack em um menu.
    *   Mostrar prévias de item/bloco com texturas personalizadas.
    *   Construir elementos decorativos de UI baseados em modelo.
*   **Principais recursos:**
    *   **Fonte do modelo:** Pode carregar JSON de modelo dos recursos do Minecraft ou de fontes externas.
    *   **Substituição de textura:** Suporta definir uma textura personalizada.
    *   **Controles de renderização:** Deslocamento do modelo, escala, rotação em três eixos, renderização translúcida e o transform do GUI do modelo.
    *   **Iluminação:** Duas luzes configuráveis com controles independentes de matiz e rotação.

## Imagem
Exibe uma imagem estática de um arquivo local, de uma URL da web ou de um local de recurso do Minecraft.

*   **Casos de uso:**
    *   Adicionar um logotipo de servidor ou marca de modpack.
    *   Criar bordas decorativas ou molduras de UI.
    *   Usar imagens como parte de um design de UI mais complexo.
*   **Principais recursos:**
    *   **Nine-Slicing:** Dimensiona bordas ou painéis sem distorcer os cantos. Veja [Nine-Slicing e Tiling](./nine-slicing-and-tiling).
    *   **Repetição de textura:** A imagem pode ser repetida em mosaico para preencher a área do elemento.
    *   **Tintura:** Você pode aplicar uma tonalidade de cor à imagem.
    *   **Cantos arredondados:** Imagens que não usam nine-slicing nem repetição podem ter cantos arredondados.
    *   **Efeito paralaxe:** Move-se com o mouse para criar profundidade visual. Veja [Efeito Paralaxe](./parallax).

## Texto
Um elemento altamente versátil para exibir texto. Ele pode ser usado para tudo, desde rótulos de uma linha até documentos paginados e roláveis.

*   **Casos de uso:**
    *   Exibir regras do servidor, notas de atualização ou mensagens de boas-vindas.
    *   Criar painéis de informações dinâmicos usando [placeholders](./placeholders), por exemplo `Welcome, {"placeholder":"playername"}!`.
    *   Adicionar rótulos e descrições à sua interface.
*   **Principais recursos:**
    *   **Fontes de conteúdo:** O texto pode ser inserido diretamente, carregado de um arquivo local ou obtido de uma URL da web.
    *   **Suporte a Markdown:** Suporta títulos, listas, blocos de código, tabelas e outras formatações Markdown. Veja [Formatação de Texto](./text-formatting).
    *   **Rolagem:** Torna-se rolável automaticamente se o conteúdo for maior que a área do elemento. As barras de rolagem podem ser personalizadas ou desativadas.
    *   **Estilo:** Controle total sobre cor do texto, escala, alinhamento, sombra e espaçamento entre linhas.

## Vídeo
Reproduz um arquivo de vídeo. Isso é perfeito para intros cinematográficas ou fundos decorativos em loop.

> [!WARNING]
> O elemento nativo de Vídeo requer **Watermedia V3** e **Watermedia Binaries V3**. O antigo elemento **Video [Rinku]** está obsoleto.

*   **Casos de uso:**
    *   Um trailer animado de modpack ou servidor.
    *   Um vídeo ambiente em loop para dar vida ao seu menu.
    *   Um vídeo tutorial dentro do jogo.
*   **Principais recursos:**
    *   **Fontes:** Suporta arquivos de vídeo locais e URLs da web. Veja [Vídeos](./video).
    *   **Controle de reprodução:** Pode ser configurado para repetir automaticamente. Seu volume, canal de som e comportamento de preservação da proporção são ajustáveis.
    *   **Controle interativo:** A reprodução, o tempo de avanço e o volume do vídeo podem ser controlados por ações de botão.

## Shader GLSL
Renderiza um shader GLSL personalizado dentro de um elemento.

*   **Casos de uso:**
    *   Painéis de shader animados.
    *   Efeitos visuais procedurais.
    *   Efeitos de menu no estilo Shadertoy recortados ao retângulo de um elemento.
*   **Principais recursos:**
    *   **Tempo de execução do shader:** Suporta shaders de passagem única e multipassagem.
    *   **Suporte a Shadertoy:** Pode usar shaders `mainImage` no estilo Shadertoy.
    *   **Uniforms:** Expõe uniforms do FancyMenu e de entrada. Veja a [API de Shader GLSL](./glsl-shader-api).

## Apresentação de Slides
Exibe uma sequência de imagens. Suas imagens e o arquivo de configuração `properties.txt` ficam no próprio subdiretório da apresentação em `<game-directory>/config/fancymenu/slideshows/`.

*   **Casos de uso:**
    *   Uma galeria rotativa de capturas de tela do jogo.
    *   Mostrar os principais recursos de um modpack.
    *   Um fundo dinâmico que alterna entre diferentes cenas.
*   **Principais recursos:**
    *   Carrega [apresentações de slides](./slideshows) pré-configuradas.
    *   Pode ser configurado para manter a proporção das imagens.

## Forma Retângulo
Um retângulo simples, de cor sólida.

*   **Casos de uso:**
    *   Criar um fundo semitransparente atrás do texto para melhorar a legibilidade.
    *   Projetar painéis e divisórias de UI simples.
    *   Servir como um espaço reservado colorido durante o design do layout.
*   **Principais recursos:**
    *   Suporta cores HEX RGBA, cantos arredondados e desfoque opcional, permitindo que a forma funcione como um painel simples, uma tintura ou um fundo desfocado.

## Forma Círculo
Uma forma simples de círculo/elipse de cor sólida.

*   **Casos de uso:**
    *   Criar destaques circulares, indicadores ou áreas suaves de UI.
    *   Construir decorações de UI temáticas sem um arquivo de textura.
*   **Principais recursos:**
    *   Suporta cor, desfoque e um valor configurável de arredondamento/expoente.

## Texto de Splash
Uma recriação do icônico texto de splash amarelo e saltitante do título de Minecraft.

*   **Casos de uso:**
    *   Substituir o texto de splash vanilla por suas próprias mensagens personalizadas.
    *   Adicionar uma mensagem animada e chamativa a qualquer menu.
*   **Principais recursos:**
    *   **Fontes de conteúdo:** Pode usar os splashes padrão do vanilla, uma lista de textos personalizados inseridos diretamente ou texto de um arquivo local.
    *   **Personalização:** Você pode ativar ou desativar o efeito de salto e personalizar a cor, escala, rotação e sombra do texto.

## Entidade do Jogador
Renderiza um modelo de jogador no menu.

*   **Casos de uso:**
    *   Exibir o personagem do jogador atual no menu principal.
    *   Criar uma tela de seleção de equipe ou prévia de classe.
    *   Uma seção de "perfil" mostrando a skin e o nome do jogador.
*   **Principais recursos:**
    *   **Aparência dinâmica:** Pode copiar a skin, capa e nome do jogador atual. Veja [Cabeças de Jogador](./player-heads).
    *   **Poses personalizadas:** Oferece controle detalhado da rotação da cabeça, corpo, braços e pernas. A cabeça e o corpo também podem seguir o cursor do mouse.
    *   **Atributos:** Pode ser configurado para ser um bebê, agachado ou usar um modelo fino.

## Navegador
Um elemento que renderiza uma página da web ao vivo dentro do jogo.

Este elemento requer que o mod **[Rinku](https://modrinth.com/mod/rinku)** esteja instalado e funcionando!

Você pode baixar o Rinku nas páginas oficiais do projeto no [CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku) e no [Modrinth](https://modrinth.com/mod/rinku).

*   **Casos de uso:**
    *   Exibir um Dynmap ao vivo de um servidor.
    *   Incorporar um player de vídeo do YouTube.
    *   Mostrar uma wiki ou página de documentação diretamente no jogo.
*   **Principais recursos:**
    *   **Interatividade:** Pode ser totalmente interativo, permitindo que os usuários cliquem em links, rolem e digitem.
    *   **Controle de mídia:** Oferece opções para silenciar mídias, repetir vídeos e ocultar os controles de vídeo na página carregada.

### Carregando Arquivos HTML Locais
O elemento Navegador pode carregar documentos HTML locais de `<game-directory>/config/fancymenu/assets/`.

Para carregar um arquivo HTML local, comece sua URL com `file:///`, seguido do caminho CURTO do arquivo, por exemplo `/config/fancymenu/assets/cool_changelog.html`, o que faz com que ela fique assim: `file:///config/fancymenu/assets/cool_changelog.html`.

No **Linux**, use o [**Placeholder de Caminho Absoluto de Arquivo/Pasta**](./placeholders#absolute-filefolder-path-absolute_path) em vez de codificar um caminho absoluto específico da instância: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

O caminho curto no Linux deve começar com `/`, como mostrado no exemplo.

## Animação de Elemento
Uma ferramenta poderosa para criar animações complexas baseadas em keyframes. Ela pode animar a posição, o tamanho e o ponto de ancoragem de um ou vários outros elementos.

*   **Casos de uso:**
    *   Fazer elementos deslizarem para dentro ou para fora da tela.
    *   Redimensionar painéis ou notificações.
    *   Animar deslocamentos de posição e transições de ancoragem.
*   **Principais recursos:**
    *   **Editor de Keyframes:** Um editor dedicado para adicionar, editar e organizar keyframes em uma linha do tempo.
    *   **Multi-alvo:** Um único Animator pode controlar vários elementos "alvo" ao mesmo tempo.
    *   **Controle:** As animações podem ser configuradas para repetir. Você também pode escolher animar apenas posição ou tamanho.
    *   **Deslocamentos de tempo:** Elementos-alvo podem usar deslocamentos de tempo de início individuais ou aleatórios.
    *   Veja [Animação de Elemento](./element-animator) para configuração e edição de keyframes.

## Ticker
Um elemento invisível que executa uma lista de ações em intervalos regulares (a cada "tick").

> [!NOTE]
> Para automação em segundo plano, considere usar [Agendadores](./schedulers). Os agendadores são globais e podem ser executados independentemente de uma tela específica.

*   **Casos de uso:**
    *   Verificar periodicamente se um servidor está online e atualizar um elemento de texto.
    *   Criar um temporizador regressivo que atualiza um rótulo de texto.
    *   Executar um script repetidamente para criar comportamentos personalizados.
*   **Principais recursos:**
    *   **Controle de tempo:** Você pode definir o atraso entre ticks em milissegundos.
    *   **Modos de tick:** Pode ser configurado para executar continuamente, apenas uma vez por sessão de jogo ou uma vez toda vez que o menu é carregado.
    *   **Assíncrono:** Pode executar suas [ações](./action-scripts) separadamente, embora algumas ações não possam ser executadas enquanto essa opção estiver ativada.

## Áudio
Um elemento invisível que reproduz arquivos de áudio. Ele pode gerenciar uma lista de reprodução de faixas e oferece vários controles de reprodução.

*   **Casos de uso:**
    *   Adicionar música de fundo personalizada a um menu.
    *   Criar um player de música com botões para controlar a reprodução (faixa seguinte/anterior, volume).
    *   Reproduzir paisagens sonoras ambiente.
*   **Principais recursos:**
    *   **Lista de reprodução:** Pode gerenciar várias faixas de áudio.
    *   **Modos de reprodução:** Pode reproduzir faixas em ordem ou embaralhá-las (com suporte a ponderação de faixas para tornar algumas mais comuns que outras).
    *   **Controle:** Suporta repetição, ajuste de volume e seleção de canal de som. Veja [Música de Fundo do Menu](./background-music).

## Controlador de Música
Um elemento invisível usado para controlar a reprodução padrão de música do Minecraft dentro de um menu específico.

*   **Casos de uso:**
    *   Desativar a música padrão do menu em uma tela onde você deseja tocar sua própria música personalizada por meio de um elemento [**Áudio**](#audio).
    *   Impedir que a música do mundo continue tocando quando um menu é aberto durante o jogo.
*   **Principais recursos:**
    *   Alternâncias separadas para controlar "Menu Music" e "World Music" do vanilla.

## Barra de Progresso
Uma barra personalizável que representa visualmente um valor numérico.

*   **Casos de uso:**
    *   Uma barra de carregamento que acompanha o progresso do carregamento do mundo usando `{"placeholder":"world_load_progress"}`.
    *   Barras visuais de saúde, fome ou experiência para um HUD no jogo.
    *   Um indicador de volume controlado por um elemento [**Slider**](#slider).
*   **Principais recursos:**
    *   **Valor dinâmico:** O valor de progresso (0-100 ou 0.0-1.0) é definido por um campo de texto que suporta [placeholders](./placeholders).
    *   **Aparência:** A direção da barra (para cima, para baixo, para a esquerda, para a direita), cores, texturas e nine-slicing para texturas da barra/fundo são totalmente personalizáveis.
    *   **Animação:** Apresenta uma animação suave de preenchimento para tornar as mudanças de progresso menos bruscas.
    *   **Âncora de elemento baseada em progresso:** Quando outro elemento usa a barra de progresso como sua âncora de **Elemento**, ative **Usar Progresso para Âncora de Elemento** para mover essa âncora até a borda atual da área preenchida. Os elementos ancorados então acompanham o progresso da barra em vez de permanecer presos aos limites estáticos da barra de progresso.

## Arrastador
Um elemento invisível que o usuário pode clicar e arrastar para mover. Outros elementos podem ser ancorados a ele para criar widgets móveis.

*   **Casos de uso:**
    *   Criar um relógio ou painel de informações arrastável.
    *   Permitir que os usuários personalizem a posição dos elementos de UI de acordo com sua preferência.
*   **Principais recursos:**
    *   **Persistência opcional:** Ative **Salvar Deslocamento de Arraste do Usuário** para manter a posição arrastada pelo usuário entre aberturas de tela e reinícios do jogo. Desative isso para redefinir o deslocamento.
    *   **Ponto de ancoragem:** Atua como uma âncora móvel para outros elementos, o que é uma parte essencial de [Posicionando Elementos](./positioning-elements).

## Cursor
Um elemento invisível que substitui o cursor padrão do sistema por uma imagem personalizada quando um layout está ativo.

*   **Casos de uso:**
    *   Criar uma interface totalmente temática que combine com a estética do seu modpack.
*   **Principais recursos:**
    *   **Textura personalizada:** Use qualquer imagem para o cursor.
    *   **Hotspot:** Define o pixel exato da imagem usado como ponto de clique. Veja [Cursor Personalizado](./custom-cursor).
