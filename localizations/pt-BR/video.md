---
title: Vídeos (MP4)
description: O que saber sobre o uso de vídeos no FancyMenu.
---
# Vídeos

O FancyMenu suporta a reprodução de vídeos MP4 como [elementos](./elements#video), [planos de fundo de menu](./menu-backgrounds) e conteúdo de [Intro do Jogo](./game-intro).

O [**elemento Vídeo**](./elements#video) nativo e o plano de fundo de menu **Vídeo** usam o Watermedia V3. Os antigos tipos **Video [Rinku]** estão obsoletos e devem permanecer apenas em layouts que ainda precisem deles.

Também existem as seguintes **ações** para controlar planos de fundo e elementos de vídeo:

- [**Definir Volume do Elemento de Vídeo**](./action-scripts#set-video-element-volume-set_video_element_volume) define o volume de um elemento de vídeo.
- [**Definir Tempo de Reprodução do Elemento de Vídeo**](./action-scripts#set-video-element-play-time-set_video_element_play_time) avança um elemento de vídeo para um timestamp em milissegundos.
- [**Alternar Estado de Pausa do Elemento de Vídeo**](./action-scripts#toggle-video-element-paused-state-toggle_video_element_pause_state) alterna o estado de pausa de um elemento de vídeo.
- [**Definir Volume do Plano de Fundo de Vídeo**](./action-scripts#set-video-background-volume-set_video_menu_background_volume) define o volume de um plano de fundo de menu de vídeo.
- [**Definir Tempo de Reprodução do Plano de Fundo de Vídeo**](./action-scripts#set-video-background-play-time-set_video_menu_background_play_time) avança um plano de fundo de menu de vídeo para um timestamp em milissegundos.
- [**Alternar Estado de Pausa do Plano de Fundo de Vídeo**](./action-scripts#toggle-video-background-paused-state-toggle_video_menu_background_pause_state) alterna o estado de pausa de um plano de fundo de menu de vídeo.

E os seguintes **placeholders** para obter informações sobre planos de fundo e elementos de vídeo:

- [**Volume do Elemento de Vídeo**](./placeholders#video-element-volume-video_element_vol) retorna o volume de um elemento de vídeo.
- [**Duração do Elemento de Vídeo**](./placeholders#video-element-duration-video_element_duration) retorna a duração de um elemento de vídeo.
- [**Tempo de Reprodução do Elemento de Vídeo**](./placeholders#video-element-play-time-video_element_playtime) retorna o progresso atual de um elemento de vídeo.
- [**Estado de Pausa do Elemento de Vídeo**](./placeholders#video-element-paused-state-video_element_paused_state) retorna se um elemento de vídeo está pausado.
- [**Volume do Plano de Fundo de Vídeo**](./placeholders#video-background-volume-video_background_vol) retorna o volume de um plano de fundo de menu de vídeo.
- [**Duração do Plano de Fundo de Vídeo**](./placeholders#video-background-duration-video_background_duration) retorna a duração de um plano de fundo de menu de vídeo.
- [**Tempo de Reprodução do Plano de Fundo de Vídeo**](./placeholders#video-background-play-time-video_background_playtime) retorna o progresso atual de um plano de fundo de menu de vídeo.
- [**Estado de Pausa do Plano de Fundo de Vídeo**](./placeholders#video-background-paused-state-video_background_paused_state) retorna se um plano de fundo de menu de vídeo está pausado.

Os placeholders de duração e tempo de reprodução retornam `MM:SS` por padrão. Defina `output_as_timestamp` como `true` quando precisar de timestamps em milissegundos. Os placeholders de tempo de reprodução ainda podem usar `show_percentage` para valores de progresso de 0 a 100.

Os valores de volume e estado de pausa são metadados do controlador associados ao identificador. Os valores de duração e tempo de reprodução exigem que o elemento ou plano de fundo de vídeo correspondente esteja ativo e pronto na tela atual.

O [**listener Alterado o Status da Reprodução do Vídeo**](./listeners#on-video-playback-status-changed-video_playback_status_changed) pode реагir a `PLAYING`, `PAUSED`, `STOPPED` e `FINISHED`.

## Requisitos

Para usar o novo tipo nativo de elemento Vídeo e plano de fundo de menu, você precisa instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Essas são dependências opcionais, então precisam ser adicionadas manualmente à instância se você quiser suporte a vídeo.

A reprodução nativa de vídeo também requer um renderizador OpenGL. A reprodução do Watermedia não fica disponível enquanto o Minecraft estiver usando Vulkan; mude para OpenGL para usar elementos de vídeo, planos de fundo de menu de vídeo e [Intros do Jogo em vídeo](./game-intro).

O tipo obsoleto **Video [Rinku]** ainda usa [Rinku](https://modrinth.com/mod/rinku). Para novos layouts, use em vez disso o tipo nativo de Vídeo com Watermedia.

## Vídeos nas Telas de Carregamento

O suporte a vídeo NÃO funciona nas telas de carregamento (tela de carregamento do jogo/recurso e tela de carregamento do mundo).

Isso também significa que você NÃO deve adicionar vídeos à tela de carregamento do jogo via **Drippy Loading Screen**, pois na maioria dos casos isso não funcionará.

Em vez disso, use animações curtas e simples de [AFMA/FMA](./fma) nas telas de carregamento.

## Solução de problemas

Se o vídeo nativo não reproduzir, confirme se o Watermedia V3 e o Watermedia Binaries V3 correspondem à sua versão do Minecraft/modloader e se o Minecraft está usando OpenGL em vez de Vulkan.
