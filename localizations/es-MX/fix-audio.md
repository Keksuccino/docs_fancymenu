---
title: Solucionar problemas con archivos de audio
description: Soluciona problemas con archivos de audio que FancyMenu no puede reproducir.
sourceBlobSha: ca4c2e0bf2c12f28f0f74b5b3011a949e1a99413
---

# Solucionar problemas con archivos de audio

Si un archivo de audio se reproduce en otros programas, pero no en FancyMenu, vuelve a codificarlo como OGG o WAV PCM. Para WAV, prueba con audio de 48 kHz y 16 bits.

Puedes usar FFmpeg u otro convertidor de audio de confianza. Volver a codificar el archivo puede ser útil incluso si la extensión actual y la configuración que se muestra parecen correctas.

# Comprobaciones

- Confirma que el archivo convertido se reproduzca en otro reproductor de audio.
- Evita usar archivos de audio muy grandes en pantallas que tengan poca memoria disponible.
- Verifica el canal de sonido seleccionado en el [elemento de audio](/elements#audio) o la acción.
- Revisa el volumen principal de Minecraft y el volumen del canal seleccionado.
- Si el audio sigue sin funcionar, haz una prueba sin otros mods que reemplacen o procesen el audio de Minecraft.
