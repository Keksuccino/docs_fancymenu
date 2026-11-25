---
title: Curseur personnalisé
description: Comment utiliser un curseur de souris personnalisé dans les menus.
sourceBlobSha: 6ccd4932bed99ab10c094adffd503bd0a44d9edd
---

# Curseur de souris personnalisé

Ajoutez un [élément **Curseur**](/elements#cursor) à une disposition pour remplacer le curseur système sur cet écran :

1. Sélectionnez **Nouvel élément -> Curseur**.
2. Définissez une texture PNG avec des couleurs RGBA.
3. Réglez **Point actif X** et **Point actif Y** sur le pixel de la texture où les clics doivent être effectués.
4. Activez l’aperçu de l’éditeur pour vérifier l’apparence du curseur pendant l’édition.
5. Utilisez une [disposition universelle](/universal-layouts) si le même curseur doit apparaître sur plusieurs écrans compatibles.

Il est recommandé d’utiliser de petites textures de curseur, par exemple `32×32` ou `64×64`. L’apparence et le comportement du curseur peuvent varier selon le système d’exploitation.
