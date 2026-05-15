---
title: Corregir archivos de audio
description: >-
  Cómo arreglar archivos de audio en caso de que FancyMenu no pueda
  reproducirlos.
---

# Cómo corregir archivos de audio

Minecraft es un poco quisquilloso con los archivos de audio que reproduce.
A veces ocurre que los archivos de audio funcionan bien en otros reproductores, pero FancyMenu no puede reproducirlos.
Si ese es el caso, puedes intentar corregir el archivo de audio para que funcione en Minecraft.

# Archivos OGG

En la mayoría de los casos, es bastante fácil corregir archivos OGG.

El 90 % de los problemas con archivos de audio se solucionan simplemente volviendo a convertir el archivo.

1. Ve a https://convertio.co/ogg-mp3/ y convierte tu OGG a MP3.
2. Ve a https://convertio.co/mp3-ogg/ y convierte el MP3 que obtuviste en el paso anterior de nuevo a OGG.

El archivo debería funcionar bien ahora.
Si aún no funciona, asegúrate de que no sea un archivo de audio extremadamente grande y comprueba si el archivo se reproduce en otros reproductores de audio.

# Archivos WAV

En el caso de los archivos WAV, normalmente el problema es una frecuencia de muestreo no compatible y cosas similares, que hacen que el audio no funcione correctamente en Minecraft.

Asegúrate de que tu audio:

- Tenga una frecuencia de muestreo de 48 kHz
- Tenga una profundidad de bits de 16 bits
- Sea un archivo WAV válido que funcione fuera de MC

Puedes (re)convertir fácilmente tu audio al valor correcto de bits y frecuencia de muestreo usando este sitio web:
https://audio.online-convert.com/convert-to-wav

**IMPORTANTE:**
Aunque creas que tu audio ya tiene el formato, la profundidad de bits y la frecuencia de muestreo correctos, vuelve a convertirlo igualmente usando el sitio web mencionado arriba.

# Otras causas

A veces no es el archivo lo que está dañado, sino otras cosas que no están configuradas correctamente, etc.

## Volumen demasiado bajo

Puede que el volumen de Minecraft sea demasiado bajo para que oigas el audio.
Asegúrate de que el canal MASTER y todos los demás canales estén lo suficientemente altos.

## Conflicto entre mods

Puede que otro mod sea incompatible con el sistema de audio que usan mis mods.
En ese caso, por favor, abre un issue en GitHub. Muchas gracias.
