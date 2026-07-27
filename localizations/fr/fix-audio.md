---
title: Corriger les fichiers audio
description: Résoudre les problèmes liés aux fichiers audio que FancyMenu ne peut pas lire.
---

# Correction des fichiers audio

Si un fichier audio se lit ailleurs mais pas dans FancyMenu, ré-encodez-le en OGG ou en WAV PCM. Pour le WAV, essayez un audio en 48 kHz, 16 bits.

Vous pouvez utiliser FFmpeg ou un autre convertisseur audio de confiance. Le ré-encodage est utile même lorsque l’extension du fichier actuel et les paramètres indiqués semblent déjà corrects.

# Vérifications

- Confirmez que le fichier ré-encodé se lit dans un autre lecteur audio.
- Évitez d’utiliser de très gros fichiers audio sur des écrans sensibles à la mémoire.
- Vérifiez le canal audio sélectionné par l’[élément Audio](./elements#audio) ou l’action.
- Vérifiez le volume principal de Minecraft et le volume du canal sélectionné.
- Si l’audio échoue toujours, testez sans autres mods qui remplacent ou traitent l’audio de Minecraft.
