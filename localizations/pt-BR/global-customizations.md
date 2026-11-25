---
title: Personalizações Globais
description: >-
  Altere os botões, controles deslizantes, fundos dos menus, músicas e janela de
  todas as telas de uma só vez, sem layouts.
sourceBlobSha: cafc7ed87ce931e406fb14b7a605085b565ce1a7
---

# Personalizações Globais

As Personalizações Globais alteram todas as telas de uma só vez: botões, controles deslizantes, fundos dos menus, músicas, a janela do jogo e muito mais. Elas não precisam de layout e também funcionam em telas cuja personalização está desativada.

Abra-as em **barra de menus -> Personalização -> Personalizações Globais**, em qualquer tela fora do editor de layouts. As alterações são aplicadas na hora e salvas automaticamente.

<img width="800" alt="As telas Título, Opções e Música e sons sem nenhum layout, todas com os mesmos botões de madeira, alças de controle deslizante de latão, rótulos que ficam dourados ao passar o mouse e um fundo noturno" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/global_customizations_tour.gif?raw=true">

> [!TIP]
> Para alterar apenas algumas telas, use [layouts](/layout-editor). Para dar uma aparência própria aos botões de certos layouts, use [Modelos de botões e controles deslizantes](/button-slider-templates).

# Botões e controles deslizantes

Estas configurações alteram todos os botões e controles deslizantes de todas as telas, inclusive os de outros mods.

- Botões e controles deslizantes que receberam texturas ou configurações de rótulo próprias de um [layout](/layout-editor) ou [modelo](/button-slider-templates) mantêm essas configurações.
- Botões que são apenas imagens, como o botão do livro de receitas, mantêm a aparência original.

## Texturas dos botões

**Texturas de botão personalizadas** oferece uma textura para cada estado de um botão:

- **Normal**
- **Ao passar o mouse**: enquanto o cursor estiver sobre o botão ou ele estiver selecionado pelo teclado.
- **Inativo**: enquanto não for possível clicar no botão.

Defina as três texturas. Se um estado não tiver textura, será exibido o botão padrão do Minecraft.

Outras configurações no mesmo menu:

- **Fundo transparente** oculta o fundo de todos os botões, mostrando apenas os rótulos. Essa opção prevalece sobre as texturas.
- **Fundos de botão com nove fatias** mantém as bordas das texturas nítidas em botões de qualquer tamanho, usando os quatro tamanhos de borda abaixo dessa opção. Consulte [Nove fatias e ladrilhamento](/nine-slicing-and-tiling).

> [!TIP]
> Sem o recurso de nove fatias, as texturas são esticadas para se ajustarem ao tamanho de cada botão. Os botões do Minecraft têm 20 pixels de altura e, na maioria dos casos, 200 ou 150 pixels de largura. Com o recurso de nove fatias, uma única textura pequena serve para todos eles.

## Texturas dos controles deslizantes

**Texturas personalizadas de controle deslizante** tem duas partes:

- **Textura do fundo do controle deslizante**: a barra do controle. Defina-a com **Definir textura**. **Fundo transparente** e **Fundo do controle deslizante com nove fatias** funcionam como as opções correspondentes dos botões.
- **Texturas da alça do controle deslizante**: a parte que você arrasta, com texturas **Normal**, **Ao passar o mouse** e **Inativo**, além da opção **Alça do controle deslizante com nove fatias**.

A alça dos controles deslizantes do Minecraft tem 8 pixels de largura e a mesma altura do controle, geralmente 20 pixels. Sem o recurso de nove fatias, as texturas da alça são esticadas para esse tamanho.

## Rótulos

**Rótulos dos botões** e **Rótulos dos controles deslizantes** têm as mesmas configurações:

| Configuração | O que faz |
|---|---|
| **Sublinhar rótulo ao passar o mouse** | Sublinha o rótulo enquanto o cursor estiver sobre ele. |
| **Cor base do rótulo** | A cor do rótulo. Defina-a com o seletor de cores ou como um código HEX, como `#FFF1D6`. |
| **Cor do rótulo ao passar o mouse** | A cor do rótulo quando o cursor estiver sobre ele. |
| **Escala do rótulo** | O tamanho do rótulo. `1` é o tamanho normal. |
| **Alinhamento do rótulo** | **À esquerda**, **Centralizado** ou **À direita**. |
| **Sombra do rótulo** | A sombra escura atrás do rótulo. Se estiver desativada, nenhum rótulo terá sombra, nem mesmo os de layouts. |

Os rótulos com configurações próprias de um layout ou modelo mantêm essas configurações. Para **Escala do rótulo** e **Alinhamento do rótulo**, a configuração global só é aplicada a rótulos com tamanho normal e alinhamento **Centralizado**.

## Som de clique

- **Som de clique de botão personalizado** substitui o som de clique dos botões e controles deslizantes do Minecraft. Botões com som de clique próprio definido em um layout mantêm esse som.
- **Volume do som de clique de botão personalizado** varia de 0% a 100%. O controle de volume do canal desse som nas configurações de som do Minecraft também se aplica.
- **Canal do som de clique de botão personalizado** é o canal de som em que ele é reproduzido, como Música. Por padrão, é Volume principal, o canal de todos os sons.

# Fundos dos menus

**Textura personalizada de fundo do menu** é uma imagem exibida atrás de todos os menus, exceto a tela Título:

- Ela também aparece atrás do menu de pausa e das Opções durante o jogo, ocultando o mundo nesses casos. Inventários, placas e livros continuam transparentes.
- **Manter proporção da textura de fundo** preserva as proporções da imagem. Ela ainda preenche a tela inteira, mas as partes que não couberem serão cortadas. Se estiver desativada, a imagem será esticada para preencher a tela.

**Panorama personalizado de fundo do menu** substitui o panorama do Minecraft na tela Título e em todos os menus exibidos antes de você entrar em um mundo:

- **Escolher panorama** seleciona um dos seus [panoramas](/panoramas).
- **Limpar panorama** restaura o panorama do Minecraft.
- **Panorama atual** mostra qual está selecionado.

Se os dois estiverem definidos, a textura cobrirá o panorama, que só ficará visível na tela Título.

Telas cujo layout tenha um [fundo de menu](/menu-backgrounds) próprio exibem esse fundo.

# Música dos menus

- **Reproduzir música padrão dos menus** ativa ou desativa a música do Minecraft nos menus.
- **Faixas personalizadas de música dos menus** abre **Gerenciar faixas de música dos menus**. **Adicionar faixa** adiciona uma música, **Remover faixa** remove a faixa selecionada, **Limpar faixas** remove todas e **Concluído** salva a lista.

As faixas são reproduzidas em ordem aleatória nos menus antes de você entrar em um mundo, substituindo a música dos menus do Minecraft. Saiba mais sobre elas e sobre a música em telas individuais: [Música de fundo dos menus](/background-music).

# Telas e pop-ups

| Configuração | O que faz |
|---|---|
| [**Intro do jogo**](/game-intro) | Reproduz uma animação ou um vídeo antes de a tela Título aparecer. |
| **Ícones de mundos na tela do modo Singleplayer** | Os ícones dos mundos na lista de mundos. Se estiver desativada, eles ficam ocultos. |
| **Ícones de servidores na tela do modo Multiplayer** | Os ícones dos servidores na lista de servidores. Se estiver desativada, eles ficam ocultos. |
| [**Carregamento contínuo do mundo**](/seamless-world-loading) | Faz uma captura de tela quando você sai de um mundo ou servidor e a exibe como fundo de carregamento quando você entra nele novamente. |
| **Notificações de conquistas** | Os pop-ups no canto superior direito exibidos quando você desbloqueia uma conquista, além dos sons correspondentes. Se estiver desativada, as notificações ficam ocultas. As mensagens de conquista no chat continuam aparecendo, e o ouvinte [Ao desbloquear conquista](/listeners#on-achievement-unlocked) continua funcionando. |

# Janela e inicialização do jogo

| Configuração | O que faz |
|---|---|
| [**Ícone personalizado da janela**](/window-customization#custom-icon) | O ícone da janela do jogo. São necessários ícones PNG de 16x16 e 32x32, além de um ícone para macOS. |
| [**Título personalizado da janela**](/window-customization#custom-title) | Substitui o título da janela do Minecraft. [Placeholders](/placeholders) funcionam, e o título é atualizado quando eles mudam. |
| **Escala padrão da interface** | Define a escala da interface do Minecraft uma vez, na primeira inicialização da instância do jogo, por exemplo, `2` ou `3`. `-1` desativa essa opção. Criada para modpacks. |
| **Forçar tela cheia ao iniciar** | Inicia o jogo em tela cheia sempre que ele é aberto. |

O FancyMenu registra que definiu a **Escala padrão da interface** no arquivo `fancymenu_data/default_scale_set.fm`. Exclua esse arquivo para que a escala seja definida novamente na próxima inicialização (consulte [Locais de armazenamento de dados](/data-storage-locations#instance-data)).

# Bom saber

- As Personalizações Globais são salvas no arquivo `options.txt` do FancyMenu. Portanto, elas pertencem ao [perfil](/profiles) carregado e são incluídas em modpacks que contenham `config/fancymenu/`.
- Texturas e sons podem ser arquivos da sua instância, links da web ou arquivos de pacotes de recursos. Consulte [Recursos](/resources).
- **barra de menus -> Ajuda -> Exportar para IA -> Configurações do FancyMenu** inclui essas configurações, caso você queira fazer perguntas em um [chat de IA](/export-for-ai).
