---
title: Glyph de l’écran titre
description: >-
  Comment masquer/supprimer le petit losange ou émeraude (icône verte ou bleue)
  sur l’écran titre.
---

# Icône Émeraude/Diamant dans l’écran titre

Si vous avez du mal à masquer la petite icône qui apparaît sans cesse sur votre écran titre et qui ressemble à un petit diamant ou à une émeraude (petite icône verte ou bleue), il s’agit le plus souvent de la notification de mise à jour du mod Mod Menu (mod Fabric) ou de Forge (fonction intégrée du chargeur de mods).

Dans certains cas, cela peut aussi faire partie du bouton Realms de Minecraft Vanilla (pour afficher des notifications).

# Masquer l’icône de Mod Menu

Pour masquer le glyph de Mod Menu, vous devez désactiver l’« indicateur de mise à jour » dans ses paramètres.

Cliquez sur le bouton **Mods** -> Survolez l’icône du mod Mod Menu dans la liste des mods -> Cliquez dessus -> Réglez « Update Indicator » sur « Hidden ».

# Masquer l’icône de Forge

Forge utilise un vérificateur de version intégré pour afficher cette icône d’émeraude lorsque des mods sont obsolètes. Vous pouvez le désactiver :

1. Ouvrez votre fichier config/fml.toml.
2. Recherchez le paramètre `versionCheck`.
3. Réglez-le sur `false` : `versionCheck = false`
4. Enregistrez puis redémarrez Minecraft.

Cela désactive entièrement la vérification de version, ce qui masque également le glyph d’émeraude au lancement.

Une autre façon de masquer l’icône est simplement de masquer tout le bouton Mods via FancyMenu. Masquer le bouton masquera aussi le glyph.

# Masquer les icônes Realms de Vanilla

Si ce n’est ni le glyph de Mod Menu ni celui de Forge, il s’agit probablement des icônes de notification Realms de Minecraft lui-même. Ces icônes apparaissent approximativement à l’emplacement du bouton Realms et peuvent être masquées avec FancyMenu dans l’éditeur de disposition. Vous devez créer une disposition « pour l’écran actuel » (l’écran titre dans ce cas), puis vous verrez les icônes Realms comme un élément distinct dans l’éditeur. Pour le masquer, faites simplement un **clic droit** dessus puis cliquez sur **Delete**.

Les icônes Realms peuvent être une icône de journal, un glyph de diamant et d’autres éléments, comme un cercle rouge avec un compteur de notifications.
