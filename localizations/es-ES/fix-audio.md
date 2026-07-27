---
title: Corregir archivos de audio
description: Soluciona archivos de audio que FancyMenu no puede reproducir.
---

# Corrección de archivos de audio

Si un archivo de audio se reproduce en otros sitios pero no en FancyMenu, vuelve a codificarlo como OGG o WAV PCM. Para WAV, prueba con audio de 48 kHz y 16 bits.

Puedes usar FFmpeg u otro conversor de audio de confianza. Volver a codificar es útil incluso cuando la extensión actual del archivo y la configuración informada ya parecen correctas.

# Comprobaciones

- Confirma que el archivo recodificado se reproduce en otro reproductor de audio.
- Evita colocar archivos de audio muy grandes en pantallas sensibles al uso de memoria.
- Verifica el canal de sonido seleccionado por el [elemento de audio](./elements#audio) o la acción.
- Comprueba el volumen general de Minecraft y el volumen del canal seleccionado.
- Si el audio sigue sin funcionar, prueba sin otros mods que sustituyan o procesen el audio de Minecraft.
