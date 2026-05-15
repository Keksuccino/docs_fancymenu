---
title: Vídeos (MP4)
description: O que saber sobre o uso de vídeos no FancyMenu.
---

# Vídeos

O FancyMenu suporta reproduzir vídeos MP4 como elementos, fundos de menu e conteúdo de introdução do jogo.

O FancyMenu 3.9.0 adiciona um novo elemento nativo **Vídeo** e um novo fundo de menu **Vídeo**, com tecnologia Watermedia V3. O antigo tipo de elemento/fundo **Video [MCEF]** está descontinuado e deve ser mantido apenas para layouts antigos que ainda dependam dele.

Também existem as seguintes **ações** para controlar fundos e elementos de vídeo:

- **Definir volume do elemento de vídeo** para definir o volume de um elemento de vídeo
- **Definir tempo de reprodução do elemento de vídeo** para avançar ou retroceder um elemento de vídeo para um carimbo de data/hora em milissegundos
- **Alternar estado de pausado do elemento de vídeo** para alternar o estado de pausa de um elemento de vídeo
- **Definir volume do fundo de vídeo** para definir o volume de um fundo de menu de vídeo
- **Definir tempo de reprodução do fundo de vídeo** para avançar ou retroceder um fundo de menu de vídeo para um carimbo de data/hora em milissegundos
- **Alternar estado de pausado do fundo de vídeo** para alternar o estado de pausa de um fundo de menu de vídeo

E os seguintes **placeholders** para obter informações sobre fundos e elementos de vídeo:

- **Volume do elemento de vídeo** para obter o volume de um elemento de vídeo
- **Duração do elemento de vídeo** para obter a duração de um elemento de vídeo
- **Tempo de reprodução do elemento de vídeo** para obter o tempo de reprodução atual (progresso) de um elemento de vídeo
- **Estado de pausado do elemento de vídeo** para obter o estado de pausa (true/false) de um elemento de vídeo
- **Volume do fundo de vídeo** para obter o volume de um fundo de menu de vídeo
- **Duração do fundo de vídeo** para obter a duração de um fundo de menu de vídeo
- **Tempo de reprodução do fundo de vídeo** para obter o tempo de reprodução atual (progresso) de um fundo de menu de vídeo
- **Estado de pausado do fundo de vídeo** para obter o estado de pausa (true/false) de um fundo de menu de vídeo

Os placeholders de duração e tempo de reprodução retornam `MM:SS` por padrão. Defina `output_as_timestamp` como `true` quando precisar de carimbos de data/hora em milissegundos. Os placeholders de tempo de reprodução ainda podem usar `show_percentage` para valores de progresso de 0 a 100.

O FancyMenu 3.9.0 também adiciona o listener **On Video Playback Status Changed**, que pode reagir a `PLAYING`, `PAUSED`, `STOPPED` e `FINISHED`.

## Requisitos

Para usar o novo elemento nativo de Vídeo e o tipo de fundo de menu, você precisa instalar:

- **Watermedia V3**
- **Watermedia Binaries V3**

Essas são dependências opcionais, então precisam ser adicionadas manualmente à instância se você quiser suporte a vídeos.

O tipo descontinuado **Video [MCEF]** ainda usa MCEF. Para novos layouts, use o tipo nativo de Vídeo com Watermedia em vez disso.

## Vídeos nas telas de carregamento

O suporte a vídeos NÃO funciona nas telas de carregamento (tela de carregamento do jogo/recurso e tela de carregamento do mundo).

Isso também significa que você NÃO deve adicionar vídeos à tela de carregamento do jogo via **Drippy Loading Screen**, pois isso não funcionará na maioria dos casos.

Em vez disso, você deve usar arquivos AFMA/FMA curtos e simples nas telas de carregamento, já que os usuários geralmente não percebem quando eles são recarregados, desde que a animação seja simples e curta o suficiente.

## Solução de problemas

Se você estiver tendo problemas com o suporte nativo a vídeos, primeiro confirme que tanto o Watermedia V3 quanto o Watermedia Binaries V3 estão instalados e correspondem à sua versão do Minecraft/modloader.
