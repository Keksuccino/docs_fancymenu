---
title: Corrigir Arquivos de Áudio
description: >-
  Solucione problemas com arquivos de áudio que o FancyMenu não consegue
  reproduzir.
---
# Corrigindo Arquivos de Áudio

Se um arquivo de áudio toca em outros lugares, mas não no FancyMenu, reencode-o como OGG ou WAV PCM. Para WAV, tente áudio de 48 kHz, 16 bits.

Você pode usar o FFmpeg ou outro conversor de áudio confiável. Reencodar é útil mesmo quando a extensão atual do arquivo e as configurações informadas já parecem corretas.

# Verificações

- Confirme que o arquivo reencodado toca em outro reprodutor de áudio.
- Mantenha arquivos de áudio muito grandes fora de telas sensíveis ao uso de memória.
- Verifique o canal de som selecionado pelo [elemento de Áudio](./elements#audio) ou pela ação.
- Verifique o volume Master do Minecraft e o volume do canal selecionado.
- Se o áudio ainda falhar, teste sem outros mods que substituam ou processem o áudio do Minecraft.
