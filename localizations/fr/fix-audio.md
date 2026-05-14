---
title: Corriger les fichiers audio
description: >-
  Comment corriger des fichiers audio au cas où FancyMenu ne parvient pas à les
  lire.
---

# Correction des fichiers audio

Minecraft est un peu pointilleux sur les fichiers audio qu'il lit.
Il arrive parfois que des fichiers audio fonctionnent très bien dans d'autres lecteurs audio, mais que FancyMenu ne parvienne pas à les lire.
Si c'est le cas, vous pouvez essayer de corriger le fichier audio afin qu'il fonctionne dans Minecraft.

# Fichiers OGG

Dans la plupart des cas, il est assez facile de corriger les fichiers OGG.

90 % de vos problèmes de fichiers audio se résolvent simplement en reconvertissant le fichier.

1. Allez sur https://convertio.co/ogg-mp3/ et convertissez votre OGG en MP3.
2. Allez sur https://convertio.co/mp3-ogg/ et reconvertissez en OGG le MP3 obtenu à l'étape précédente.

Le fichier devrait maintenant fonctionner correctement.
S'il ne fonctionne toujours pas, assurez-vous qu'il ne s'agit pas d'un fichier audio extrêmement volumineux et vérifiez si le fichier audio se lit dans d'autres lecteurs audio.

# Fichiers WAV

Pour les fichiers WAV, le problème vient le plus souvent d'un taux d'échantillonnage non pris en charge ou de choses similaires qui empêchent l'audio de fonctionner correctement dans Minecraft.

Assurez-vous que votre audio :

- A un taux d'échantillonnage de 48 kHz
- A une profondeur de bits de 16 bits
- Est un fichier WAV valide qui fonctionne en dehors de MC

Vous pouvez facilement (re)convertir votre audio aux bons taux d'échantillonnage et de bits en utilisant ce site web :
https://audio.online-convert.com/convert-to-wav

**IMPORTANT :**
Même si vous pensez que votre audio a déjà le bon format, la bonne profondeur de bits et le bon taux d'échantillonnage, veuillez tout de même le reconvertir en utilisant le site mentionné ci-dessus.

# Autres causes

Parfois, ce n'est pas le fichier qui est défectueux, mais d'autres éléments qui ne sont pas configurés correctement, etc.

## Volume trop bas

Il est possible que le volume de Minecraft soit trop faible pour que vous entendiez l'audio.
Assurez-vous que le canal MASTER et tous les autres canaux sont suffisamment élevés.

## Conflit de mods

Il est possible qu'un autre mod soit incompatible avec le système audio utilisé par mes mods.
Dans ce cas, veuillez ouvrir un ticket sur GitHub, merci beaucoup.
