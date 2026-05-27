---
title: Effet de parallaxe
description: >-
  Comment appliquer un effet de parallaxe à l’arrière-plan du menu et aux
  éléments.
---
# Qu’est-ce que l’effet de parallaxe ?

L’effet de parallaxe est une astuce visuelle sympa qui donne l’impression que les arrière-plans et les éléments de votre menu ont de la profondeur. Lorsque vous déplacez votre curseur de souris, les éléments avec la parallaxe activée bougent légèrement, créant une illusion d’espace en 3D dans votre menu en 2D.

Imaginez quand vous êtes en voiture : les choses qui sont proches de vous (comme les panneaux de signalisation) semblent se déplacer plus vite que les choses éloignées (comme les montagnes). Dans FancyMenu, ce même principe crée une expérience plus dynamique et interactive.

# Où peut-on utiliser la parallaxe dans FancyMenu ?

Dans FancyMenu, vous pouvez utiliser l’effet de parallaxe à deux endroits principaux :

1. **Arrière-plans du menu** : faites légèrement bouger l’arrière-plan entier de votre menu avec le curseur de la souris
2. **Éléments** : faites bouger indépendamment des éléments individuels (comme des images, des boutons ou du texte)

# Comment utiliser la parallaxe pour les arrière-plans du menu

Ajouter un effet de parallaxe à l’arrière-plan de votre menu est très simple :

1. Ouvrez l’éditeur de menu en appuyant sur **CTRL+ALT+C** pour afficher la barre de menu, puis allez dans **Personnalisation**
2. Créez une nouvelle mise en page ou modifiez-en une existante
3. Cliquez sur **Mise en page → Propriétés** 
4. Ouvrez **Arrière-plans du menu**
5. Choisissez **Image** comme type d’arrière-plan
6. Configurez votre arrière-plan d’image :
   - Choisissez une image (locale ou depuis le web)
   - Activez **Effet de parallaxe** en cliquant sur le bouton bascule
   - Réglez **Intensité de l’effet de parallaxe X** et **Intensité de l’effet de parallaxe Y** (entre 0.0 et 1.0)
   - Vous pouvez aussi activer **Inverser le mouvement de parallaxe** pour changer la direction

> **Astuce** : plus la valeur d’intensité est élevée, plus votre arrière-plan bougera. FancyMenu 3.9.0 vous permet de définir séparément l’intensité en X et en Y, afin de renforcer le mouvement horizontal plutôt que vertical, ou l’inverse.
{.is-info}

# Comment utiliser la parallaxe pour les éléments individuels

Vous pouvez aussi ajouter la parallaxe à des éléments individuels pour créer des effets de superposition :

1. Sélectionnez un élément dans l’éditeur en cliquant dessus
2. Faites un clic droit sur l’élément pour ouvrir le menu contextuel
3. Faites défiler vers le bas et trouvez **Effet de parallaxe : Activé/Désactivé**
4. Basculez-le sur **Activé**
5. Ajustez les valeurs **Intensité de parallaxe X** et **Intensité de parallaxe Y** (entre 0.0 et 1.0)
6. Vous pouvez aussi activer **Inverser la parallaxe** pour changer la direction du mouvement

# Conseils pour créer de superbes effets de parallaxe

## Superposez vos éléments

Créez de la profondeur en utilisant différentes valeurs d’intensité de parallaxe pour différents éléments. Vous pouvez régler X et Y séparément :

- **Arrière-plan** : intensité plus faible (0.1-0.3)
- **Éléments de la couche intermédiaire** : intensité moyenne (0.3-0.6)
- **Éléments de premier plan** : intensité plus élevée (0.6-0.9)

Cela crée un effet 3D convaincant lorsque vous déplacez votre souris !

## Combinez parallaxe normale et inversée

Essayez de mettre certains éléments sur **Inverser le mouvement de parallaxe : Activé** et d’autres sur **Désactivé**. Cela fait bouger les éléments dans des directions opposées, ce qui renforce l’effet de profondeur.

## N’en abusez pas

Trop de mouvement peut distraire. Utilisez l’effet de parallaxe avec modération, surtout avec des valeurs d’intensité élevées.

# Dépannage

## La parallaxe ne fonctionne pas ?

1. Assurez-vous d’avoir activé l’effet de parallaxe
2. Vérifiez que l’intensité de la parallaxe n’est pas réglée sur 0
4. Confirmez que l’option "Slide Wide Images From Left To Right" est désactivée (cette option entre en conflit avec la parallaxe)

## Le mouvement de parallaxe est trop rapide/lent ?

Ajustez les valeurs **Intensité de parallaxe X/Y** :
- Valeurs plus faibles (plus proches de 0) = mouvement plus lent et plus subtil
- Valeurs plus élevées (plus proches de 1) = mouvement plus rapide et plus spectaculaire

## La parallaxe semble saccadée ou lente ?

C’est une limitation de l’effet de parallaxe, car Minecraft utilise des coordonnées entières (nombres entiers). Il est donc possible que l’effet donne un peu l’impression que les éléments "sautent", mais cela ne devrait pas être trop visible si vous utilisez des intensités de parallaxe "normales" et non des valeurs très faibles ou très élevées.
