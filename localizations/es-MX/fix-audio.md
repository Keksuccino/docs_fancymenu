---
title: Corregir archivos de audio
description: >-
  Cómo corregir archivos de audio en caso de que FancyMenu no pueda
  reproducirlos.
---

# Corrigiendo archivos de audio

Minecraft es un poco exigente con los archivos de audio que reproduce.
A veces pasa que los archivos de audio funcionan bien en otros reproductores, pero FancyMenu no puede reproducirlos.
Si ese es el caso, puedes intentar corregir el archivo de audio para que funcione en Minecraft.

# Archivos OGG

En la mayoría de los casos, es bastante fácil corregir archivos OGG.

El 90% de los problemas con archivos de audio se solucionan simplemente volviendo a convertir el archivo.

1. Ve a https://convertio.co/ogg-mp3/ y convierte tu archivo OGG a MP3.
2. Ve a https://convertio.co/mp3-ogg/ y convierte el MP3 que obtuviste en el paso anterior de nuevo a OGG.

El archivo debería funcionar bien ahora.
Si todavía no funciona, asegúrate de que no sea un archivo de audio demasiado grande y revisa si el archivo se reproduce en otros reproductores de audio.

# Archivos WAV

En los archivos WAV, por lo general el problema es una frecuencia de muestreo no compatible y cosas similares que hacen que el audio no funcione correctamente en Minecraft.

Asegúrate de que tu audio:

- Tenga una frecuencia de muestreo de 48KHz
- Tenga una profundidad de bits de 16 bits
- Sea un archivo WAV válido que funcione fuera de MC

Puedes (re)convertir fácilmente tu audio al formato, la profundidad de bits y la frecuencia de muestreo correctos usando este sitio web:
https://audio.online-convert.com/convert-to-wav

**IMPORTANTE:**
Incluso si crees que tu audio ya tiene el formato, la profundidad de bits y la frecuencia de muestreo correctos, por favor vuelve a convertirlo de todos modos usando el sitio web mencionado arriba.

# Otras causas

A veces no es el archivo el que está dañado, sino otras cosas que no están configuradas correctamente, etc.

## Volumen demasiado bajo

Puede que el volumen de Minecraft esté demasiado bajo como para que puedas oír el audio.
Asegúrate de que el canal MASTER y todos los demás canales tengan suficiente volumen.

## Conflicto con otro mod

Puede que otro mod sea incompatible con el sistema de audio que usan mis mods.
En ese caso, por favor abre un problema en GitHub, muchas gracias.
