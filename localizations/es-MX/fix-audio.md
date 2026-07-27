---
title: Corregir archivos de audio
description: Soluciona archivos de audio que FancyMenu no puede reproducir.
---

# Cómo corregir archivos de audio

Si un archivo de audio se reproduce en otros lugares pero no en FancyMenu, vuelve a codificarlo como OGG o WAV PCM. Para WAV, prueba audio de 48 kHz y 16 bits.

Puedes usar FFmpeg u otro convertidor de audio de confianza. Volver a codificar es útil incluso cuando la extensión actual del archivo y la configuración que reporta ya parecen correctas.

# Verificaciones

- Confirma que el archivo recodificado se reproduzca en otro reproductor de audio.
- Evita usar archivos de audio muy grandes en pantallas sensibles al uso de memoria.
- Verifica el canal de sonido seleccionado por el [elemento Audio](./elements#audio) o por la acción.
- Revisa el volumen general de Minecraft y el volumen del canal seleccionado.
- Si el audio aún falla, prueba sin otros mods que reemplacen o procesen el audio de Minecraft.
