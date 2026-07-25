---
title: Curseur personnalisé
description: >-
  Comment faire en sorte que les menus utilisent un curseur de souris
  personnalisé.
---
# Curseur de souris personnalisé

Ajoutez un [élément **Cursor**](./elements#cursor) à une mise en page pour remplacer le curseur système sur cet écran :

1. Sélectionnez **New Element -> Cursor**.
2. Définissez une texture PNG avec couleur RGBA.
3. Réglez **Hotspot X** et **Hotspot Y** sur le pixel de la texture où les clics doivent se produire.
4. Activez l’aperçu de l’éditeur lorsque vous souhaitez vérifier le curseur pendant l’édition.
5. Utilisez une [mise en page universelle](./universal-layouts) lorsque le même curseur doit apparaître sur plusieurs écrans pris en charge.

Il est recommandé d’utiliser de petites textures de curseur, comme `32×32` ou `64×64`. L’apparence et le comportement du curseur peuvent varier selon le système d’exploitation.
