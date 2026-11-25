---
title: Vídeos (MP4)
description: O que você precisa saber sobre o uso de vídeos no FancyMenu.
sourceBlobSha: bd34c5c21a6c08d6b66a7b2acdaf9bd12739732f
---
# Vídeos

O FancyMenu permite reproduzir vídeos MP4 como [elementos](/elements#video), [planos de fundo de menu](/menu-backgrounds#video) e conteúdo de [introdução do jogo](/game-intro).

O elemento nativo [**Video**](/elements#video) e o plano de fundo de menu **Video** usam o Watermedia V3. Os tipos antigos **Video [Rinku]** foram descontinuados e devem ser mantidos apenas em layouts que ainda precisem deles.

Também existem as seguintes [ações](/action-scripts) para controlar planos de fundo e elementos de vídeo:

- [**Set Video Element Volume**](/action-scripts#set-video-element-volume) define o volume de um elemento Video.
- [**Set Video Element Play Time**](/action-scripts#set-video-element-play-time) avança ou retrocede um elemento Video até um instante especificado em milissegundos.
- [**Toggle Video Element Paused State**](/action-scripts#toggle-video-element-paused-state) alterna o estado de pausa de um elemento Video.
- [**Set Video Background Volume**](/action-scripts#set-video-background-volume) define o volume de um plano de fundo de menu Video.
- [**Set Video Background Play Time**](/action-scripts#set-video-background-play-time) avança ou retrocede um plano de fundo de menu Video até um instante especificado em milissegundos.
- [**Toggle Video Background Paused State**](/action-scripts#toggle-video-background-paused-state) alterna o estado de pausa de um plano de fundo de menu Video.

E os seguintes [placeholders](/placeholders) para obter informações sobre planos de fundo e elementos de vídeo:

- [**Video Element Volume**](/placeholders#video-element-volume) retorna o volume de um elemento Video.
- [**Video Element Duration**](/placeholders#video-element-duration) retorna a duração de um elemento Video.
- [**Video Element Play Time**](/placeholders#video-element-play-time) retorna o progresso atual de um elemento Video.
- [**Video Element Paused State**](/placeholders#video-element-paused-state) informa se um elemento Video está pausado.
- [**Video Background Volume**](/placeholders#video-background-volume) retorna o volume de um plano de fundo de menu Video.
- [**Video Background Duration**](/placeholders#video-background-duration) retorna a duração de um plano de fundo de menu Video.
- [**Video Background Play Time**](/placeholders#video-background-play-time) retorna o progresso atual de um plano de fundo de menu Video.
- [**Video Background Paused State**](/placeholders#video-background-paused-state) informa se um plano de fundo de menu Video está pausado.

Por padrão, os placeholders de duração e tempo de reprodução retornam `MM:SS`. Defina `output_as_timestamp` como `true` quando precisar de valores em milissegundos. Os placeholders de tempo de reprodução também podem usar `show_percentage` para retornar valores de progresso entre 0 e 100.

Os valores de volume e de estado de pausa são metadados do controlador associados ao identificador. Os valores de duração e tempo de reprodução exigem que o elemento Video ou o plano de fundo correspondente esteja ativo e pronto na tela atual.

O [listener **Video Playback Status Changed**](/listeners#video-playback-status-changed) pode reagir aos estados `PLAYING`, `PAUSED`, `STOPPED` e `FINISHED`.

## Requisitos

Para usar o novo elemento Video nativo e o tipo de plano de fundo de menu, é necessário instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Essas dependências são opcionais, então precisam ser adicionadas manualmente à instância para habilitar o suporte a vídeos.

A reprodução nativa de vídeos também exige um renderizador OpenGL. A reprodução pelo Watermedia não está disponível enquanto o Minecraft usa Vulkan. Mude para OpenGL para usar elementos Video, planos de fundo de menu Video e [introduções do jogo com vídeo](/game-intro).

O tipo descontinuado **Video [Rinku]** ainda usa o [Rinku](https://modrinth.com/mod/rinku). Para novos layouts, use o tipo nativo Video, que é baseado no Watermedia.

## Vídeos nas telas de carregamento

O suporte a vídeos NÃO funciona nas telas de carregamento (tela de carregamento do jogo/recursos e tela de carregamento do mundo).

Isso também significa que você NÃO deve adicionar vídeos à tela de carregamento do jogo pelo **Drippy Loading Screen**, pois isso não funcionará na maioria dos casos.

Em vez disso, use [animações](/animations) curtas e simples (APNG ou GIF) nas telas de carregamento.

## Solução de problemas

Se o vídeo nativo não for reproduzido, confirme se o Watermedia V3 e o Watermedia Binaries V3 são compatíveis com a sua versão do Minecraft/loader de mods e se o Minecraft está usando OpenGL, e não Vulkan.
