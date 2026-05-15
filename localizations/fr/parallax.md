---
title: Effet Parallaxe
description: Comment appliquer un effet de parallaxe au fond du menu et aux éléments.
---

# Qu’est-ce que l’effet de parallaxe ?

L’effet de parallaxe est une astuce visuelle sympa qui donne de la profondeur à vos arrière-plans et éléments de menu. Lorsque vous déplacez votre curseur de souris, les éléments avec la parallaxe activée bougent légèrement, créant une illusion d’espace 3D dans votre menu 2D.

Imaginez quand vous êtes en voiture : les objets plus proches de vous (comme les panneaux de signalisation) semblent se déplacer plus vite que les objets lointains (comme les montagnes). Dans FancyMenu, cette même idée crée une expérience plus dynamique et interactive.

# Où pouvez-vous utiliser la parallaxe dans FancyMenu ?

Dans FancyMenu, vous pouvez utiliser l’effet de parallaxe à deux endroits principaux :

1. **Arrière-plans du menu** : faire bouger légèrement tout l’arrière-plan de votre menu avec votre curseur de souris
2. **Éléments** : faire bouger indépendamment des éléments individuels (comme des images, des boutons ou du texte)

# Comment utiliser la parallaxe pour les arrière-plans du menu

Ajouter un effet de parallaxe à l’arrière-plan de votre menu est très simple :

1. Ouvrez l’éditeur de menu en appuyant sur **CTRL+ALT+C** pour afficher la barre de menu, puis allez dans **Personnalisation**
2. Créez une nouvelle disposition ou modifiez-en une existante
3. Cliquez sur **Disposition → Propriétés** 
4. Ouvrez **Arrière-plans du menu**
5. Choisissez **Image** comme type d’arrière-plan
6. Configurez votre arrière-plan image :
   - Choisissez une image (locale ou depuis le web)
   - Activez **Effet de parallaxe** en cliquant sur le bouton bascule
   - Réglez l’**Intensité X de l’effet de parallaxe** et l’**Intensité Y de l’effet de parallaxe** (entre 0,0 et 1,0)
   - Vous pouvez aussi activer **Inverser le mouvement de parallaxe** pour changer la direction

> **Astuce** : plus la valeur d’intensité est élevée, plus votre arrière-plan bougera. FancyMenu 3.9.0 vous permet de définir les intensités X et Y séparément, afin de rendre le mouvement plus fort horizontalement que verticalement, ou l’inverse.
{.is-info}

# Comment utiliser la parallaxe pour des éléments individuels

Vous pouvez aussi ajouter la parallaxe à des éléments individuels pour créer des effets en couches :

1. Sélectionnez n’importe quel élément dans l’éditeur en cliquant dessus
2. Faites un clic droit sur l’élément pour ouvrir le menu contextuel
3. Faites défiler vers le bas et trouvez **Effet de parallaxe : Activé/Désactivé**
4. Basculez sur **Activé**
5. Ajustez les valeurs **Intensité de parallaxe X** et **Intensité de parallaxe Y** (entre 0,0 et 1,0)
6. Vous pouvez aussi activer **Inverser la parallaxe** pour changer la direction du mouvement

# Conseils pour créer de superbes effets de parallaxe

## Superposez vos éléments

Créez de la profondeur en utilisant différentes valeurs d’intensité de parallaxe pour différents éléments. Vous pouvez ajuster X et Y séparément :

- **Arrière-plan** : intensité plus faible (0,1-0,3)
- **Éléments de la couche intermédiaire** : intensité moyenne (0,3-0,6)
- **Éléments du premier plan** : intensité plus élevée (0,6-0,9)

Cela crée un effet 3D convaincant lorsque vous déplacez votre souris !

## Combinez parallaxe normale et inversée

Essayez de définir certains éléments sur **Inverser le mouvement de parallaxe : Activé** et d’autres sur **Désactivé**. Cela fait bouger les éléments dans des directions opposées, renforçant l’effet de profondeur.

## N’en faites pas trop

Trop de mouvement peut être distrayant. Utilisez l’effet de parallaxe avec parcimonie, surtout avec des valeurs d’intensité élevées.

# Dépannage

## La parallaxe ne fonctionne pas ?

1. Assurez-vous d’avoir activé l’effet de parallaxe
2. Vérifiez que l’intensité de la parallaxe n’est pas réglée sur 0
4. Confirmez que l’option "Slide Wide Images From Left To Right" est désactivée (cette option entre en conflit avec la parallaxe)

## Le mouvement de parallaxe est trop rapide/lent ?

Ajustez les valeurs **Intensité de parallaxe X/Y** :
- Valeurs plus faibles (plus proches de 0) = mouvement plus lent et plus subtil
- Valeurs plus élevées (plus proches de 1) = mouvement plus rapide et plus spectaculaire

# Réflexions finales

L’effet de parallaxe est une merveilleuse façon de rendre vos menus Minecraft plus vivants et interactifs. Expérimentez différentes combinaisons de parallaxe pour l’arrière-plan et les éléments afin de créer des dispositions superbes et dynamiques qui réagissent aux mouvements de votre souris !

N’oubliez pas : les meilleurs effets sont souvent subtils — un léger mouvement suffit pour créer une expérience immersive.
