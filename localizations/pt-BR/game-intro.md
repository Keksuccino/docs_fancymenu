---
title: Introdução do jogo
description: >-
  Reproduza uma animação ou um vídeo sempre que o jogo iniciar, antes de a tela
  de título aparecer.
sourceBlobSha: 2f40eb874b4aebaf4b32ffa2b8980310d71510b7
---

# Introdução do jogo

A Introdução do jogo reproduz uma animação ou um vídeo quando o jogo inicia, logo após a tela de carregamento do Minecraft. Quando termina, ela dá lugar à tela de título com uma transição gradual. Foi criada para modpacks: um logotipo, uma abertura de estúdio ou um trailer curto.

<img width="800" alt="A introdução de Skyhaven: a noite vira amanhecer sobre uma ilha flutuante e o logotipo aparece, letra por letra; em seguida, a introdução dá lugar à tela de título, que tem a mesma ilha como plano de fundo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

Os jogadores podem ignorá-la com qualquer tecla ou um clique. A Introdução do jogo é uma das [Personalizações globais](/global-customizations), então não precisa de um layout.

# Configurando a introdução

<img width="800" alt="Abrindo Personalizações globais e Introdução do jogo na barra de menus, selecionando skyhaven_intro.apng com Definir introdução do jogo, reproduzindo-a com Reproduzir introdução do jogo novamente e ignorando-a com a barra de espaço" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. Coloque sua animação ou seu vídeo em `<game-directory>/config/fancymenu/assets/`.
2. Abra **barra de menus -> Personalização -> Personalizações globais -> Introdução do jogo**.
3. Clique em **Definir introdução do jogo**. Com **Tipo de origem** definido como **Local**, clique em **Escolher arquivo de recurso local**, selecione seu arquivo e clique em **OK**.
4. Clique em **Reproduzir introdução do jogo novamente** para assisti-la imediatamente.

Para remover a introdução, passe o mouse sobre **Definir introdução do jogo** e clique em **Restaurar padrão**.

## Animações e vídeos

- **Animações:** arquivos APNG ou GIF. Saiba como criá-las em [Animações](/animations).
- **Vídeos:** arquivos MP4. Eles precisam dos mods Watermedia V3 e Watermedia Binaries V3. Consulte [Vídeos](/video#requirements). Sem eles, uma introdução em vídeo mostra apenas um aviso em vermelho com links para download por alguns segundos.
- Arquivos da sua instância e de pacotes de recursos funcionam; links da web não. Consulte [Recursos](/resources).

A introdução ocupa a tela inteira e mantém suas proporções. Por isso, partes dela ficam cortadas em telas com proporções diferentes. A maioria das telas usa a proporção 16:9; portanto, faça sua introdução também em 16:9, como 1920x1080. As partes transparentes ficam pretas.

> [!TIP]
> Os jogadores veem a introdução sempre que o jogo inicia. Por isso, mantenha-a curta, com cerca de 5 a 10 segundos.

## Exemplo gratuito de introdução

A introdução de Skyhaven que aparece nos GIFs desta página é gratuita para usar em testes e nos seus modpacks:

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true): a introdução, com resolução de 1280x720 e 5,4 segundos de duração. Ela é reproduzida uma vez.
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true): a cena final, sem o logotipo, com resolução de 1280x720. Defina-a como [plano de fundo de imagem](/menu-backgrounds#image) de um layout da tela de título. Assim, a introdução dará lugar a um menu correspondente, como no primeiro GIF.

# Configurações

Todas as configurações ficam em **barra de menus -> Personalização -> Personalizações globais -> Introdução do jogo**:

| Configuração | O que faz |
|---|---|
| **Definir introdução do jogo** | Define a animação ou o vídeo. |
| **Permitir pular introdução do jogo** | Qualquer tecla ou clique pula a introdução, e a mensagem **Pressione qualquer tecla para pular** aparece na parte inferior. Se desativada, a introdução é reproduzida até o fim. |
| **Transição da introdução do jogo** | Faz a transição gradual da introdução para a tela de título quando ela termina. Se desativada, a tela de título aparece imediatamente. |
| **Ignorar repetições da introdução do jogo** | Encerra a introdução depois que a animação é reproduzida uma vez, mesmo que ela esteja em loop. Se desativada, a introdução reproduz todos os ciclos da animação. Os vídeos são sempre reproduzidos uma vez. |
| **Texto personalizado para pular** | Substitui **Pressione qualquer tecla para pular**, por exemplo, por `Pressione qualquer tecla para começar sua aventura`. Uma chave de localização de um pacote de recursos, como `skyhaven.intro.skip`, exibe o texto no idioma do jogador. |
| **Volume da introdução do jogo** | Define o volume de uma introdução em vídeo, de 0% a 100%. |
| **Canal de som da introdução do jogo** | Define o canal de som das introduções em vídeo, como Música. O volume desse canal e o volume principal nas configurações de som do Minecraft também se aplicam. |
| **Reproduzir introdução do jogo novamente** | Reproduz a introdução imediatamente, sobre a tela atual. |

**Permitir pular introdução do jogo**, **Transição da introdução do jogo** e **Ignorar repetições da introdução do jogo** ficam ativadas por padrão.

> [!WARNING]
> Se **Permitir pular introdução do jogo** e **Ignorar repetições da introdução do jogo** estiverem desativadas, uma animação em loop infinito nunca terminará, e os jogadores não conseguirão chegar à tela de título.

# Informações úteis

- A introdução é reproduzida uma vez a cada início do jogo, antes da primeira tela exibida após a tela de carregamento. Normalmente, essa tela é a tela de título.
- Para alterar a tela de carregamento do Minecraft exibida antes dela, consulte [Tela de carregamento](/loading-screen).
- A origem da introdução pode conter [marcadores de posição](/resources#placeholders-in-resource-sources).
- As configurações da Introdução do jogo são salvas no arquivo `options.txt` do FancyMenu e, por isso, pertencem ao [perfil](/profiles) carregado. Os modpacks que incluem `config/fancymenu/` vêm com a introdução e seu arquivo em `assets/`. Consulte [Modpacks](/modpacks).
