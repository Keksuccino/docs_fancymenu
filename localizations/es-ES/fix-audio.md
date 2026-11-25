---
title: Solucionar problemas con archivos de audio
description: Soluciona problemas con archivos de audio que FancyMenu no puede reproducir.
sourceBlobSha: ca4c2e0bf2c12f28f0f74b5b3011a949e1a99413
---

# Solucionar problemas con archivos de audio

Si un archivo de audio se reproduce en otros sitios, pero no en FancyMenu, vuelve a codificarlo como OGG o WAV PCM. Para WAV, prueba con audio a 48 kHz y 16 bits.

Puedes usar FFmpeg u otro conversor de audio de confianza. Volver a codificar el archivo puede ser útil aunque la extensión y los ajustes que aparecen actualmente parezcan correctos.

# Comprobaciones

- Confirma que el archivo recodificado se reproduce en otro reproductor de audio.
- Evita usar archivos de audio muy grandes en pantallas con limitaciones de memoria.
- Comprueba el canal de sonido seleccionado en el [elemento de audio](/elements#audio) o en la acción.
- Comprueba el volumen principal de Minecraft y el del canal seleccionado.
- Si el audio sigue sin funcionar, prueba sin otros mods que sustituyan o procesen el audio de Minecraft.
