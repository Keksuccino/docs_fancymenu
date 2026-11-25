---
title: Corriger les fichiers audio
description: Résoudre les problèmes liés aux fichiers audio que FancyMenu ne peut pas lire.
sourceBlobSha: ca4c2e0bf2c12f28f0f74b5b3011a949e1a99413
---

# Corriger les fichiers audio

Si un fichier audio est lu ailleurs, mais pas dans FancyMenu, réencodez-le au format OGG ou PCM WAV. Pour le format WAV, essayez un son à 48 kHz et 16 bits.

Vous pouvez utiliser FFmpeg ou un autre convertisseur audio fiable. Le réencodage peut être utile même si l’extension actuelle du fichier et les paramètres indiqués semblent déjà corrects.

# Vérifications

- Vérifiez que le fichier réencodé est lu dans un autre lecteur audio.
- Évitez de charger de très gros fichiers audio dans les écrans sensibles à la mémoire.
- Vérifiez le canal audio sélectionné dans l’[élément audio](/elements#audio) ou l’action.
- Vérifiez le volume principal de Minecraft ainsi que celui du canal sélectionné.
- Si le problème persiste, faites un essai sans les autres mods qui remplacent ou traitent l’audio de Minecraft.
