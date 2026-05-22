---
title: Glyph de l’écran titre
description: >-
  Comment masquer/supprimer le petit losange ou glyphe/icone émeraude (vert ou
  bleu) sur l’écran titre.
---
# Icône Émeraude/Diamant dans l’Écran titre

Si vous avez du mal à masquer la petite icône qui apparaît sans cesse sur votre écran titre et qui ressemble à un petit diamant ou à une émeraude (petite icône verte ou bleue), il s’agit le plus souvent de la notification de mise à jour d’un mod, soit pour Mod Menu (mod Fabric), soit pour Forge (fonction intégrée au chargeur de mods).

Dans certains cas, cela peut aussi faire partie du bouton Realms de Minecraft Vanilla (pour afficher des notifications).

# Masquer l’icône de Mod Menu

Pour masquer le glyphe de Mod Menu, vous devez désactiver l’« indicateur de mise à jour » dans ses paramètres.

Cliquez sur le bouton **Mods** -> Survolez l’icône du mod Mod Menu dans la liste des mods -> Cliquez dessus -> Réglez « Update Indicator » sur « Hidden ».

# Masquer l’icône de Forge

Forge utilise un vérificateur de version intégré pour afficher cette icône émeraude lorsque des mods sont obsolètes. Vous pouvez le désactiver :

1. Ouvrez votre fichier `/config/fml.toml`.
2. Recherchez le paramètre `versionCheck`.
3. Définissez-le sur `false` : `versionCheck = false`
4. Enregistrez et redémarrez Minecraft.

Cela désactive complètement la vérification de version, ce qui masque aussi le glyphe émeraude au lancement.

Une autre façon de masquer l’icône consiste simplement à cacher entièrement le bouton Mods via FancyMenu. Masquer le bouton masquera également le glyphe.

# Masquer l’icône de NeoForge

Pour NeoForge, cela fonctionne exactement comme pour Forge classique.

1. Ouvrez votre fichier `/config/fml.toml`.
2. Recherchez le paramètre `versionCheck`.
3. Définissez-le sur `false` : `versionCheck = false`
4. Enregistrez et redémarrez Minecraft.

# Masquer les icônes Realms de Vanilla

Si ce n’est ni le glyphe de Mod Menu ni celui de Forge, il s’agit probablement des icônes de notification Realms de Minecraft lui-même. Ces icônes apparaissent approximativement à l’emplacement du bouton Realms et peuvent être masquées avec FancyMenu dans l’éditeur de mise en page. Vous devez créer une mise en page « pour l’écran actuel » (l’écran titre dans ce cas), puis vous verrez les icônes Realms comme un élément dédié dans l’éditeur. Pour le masquer, faites simplement un **clic droit** dessus et cliquez sur **Delete**.

Les icônes Realms peuvent être une icône de journal, un glyphe en forme de diamant et d’autres, comme un cercle rouge avec un compteur de notification.
