---
title: Modèles de boutons et de curseurs
description: >-
  Comment utiliser des modèles de boutons/curseurs pour appliquer un design
  spécifique à TOUS les boutons en une seule fois.
---

# Utiliser des éléments bouton comme modèles pour les boutons et les curseurs

Il est possible d'utiliser un élément Bouton comme modèle pour d'autres boutons et même des curseurs. En procédant ainsi, vous pouvez appliquer un design spécifique de bouton/curseur à TOUS les boutons/curseurs d'un menu, ou même à tous les menus d'un coup lorsque vous utilisez une disposition universelle.

> [!IMPORTANT]
> Préférez les [Personnalisations globales](./global-customizations) pour un style large des boutons et curseurs Vanilla. Utilisez les modèles de boutons/curseurs lorsque le comportement doit dépendre de la disposition.

# Important avant de commencer

Pour un seul bouton ou curseur, faites simplement un **clic droit** dessus dans l'éditeur et modifiez directement ses **Textures d'arrière-plan** ou les textures de la poignée du curseur.

# Qu'est-ce qu'un bouton modèle ?

Un bouton modèle est un type spécial de bouton personnalisé dans FancyMenu qui vous permet de contrôler l'apparence et le comportement des autres boutons et curseurs. C'est comme créer un design maître que de nombreux autres éléments suivront.

Lorsque vous créez un bouton modèle, vous pouvez faire en sorte que plusieurs boutons ou curseurs partagent les mêmes éléments :
- Taille (largeur et hauteur)
- Position
- Visibilité
- Opacité (le niveau de transparence)
- Libellés de texte
- **Textures du bouton** (partagées automatiquement lorsque des textures personnalisées sont définies)

C'est très utile lorsque vous voulez rendre votre menu cohérent ou lorsque vous devez mettre à jour de nombreux boutons en même temps !

# Qui peut utiliser les modèles ?

Seuls les **boutons personnalisés** peuvent servir de modèles. Cependant, ces modèles peuvent être appliqués à :
- Boutons Vanilla (les boutons Minecraft par défaut)
- Boutons personnalisés (les boutons que vous créez dans FancyMenu)
- Curseurs Vanilla (comme les réglages de volume)
- Curseurs personnalisés (les curseurs que vous créez dans FancyMenu)

# Comment créer un bouton modèle

1. Ouvrez l'éditeur FancyMenu pour l'écran que vous souhaitez personnaliser
2. Ajoutez un nouvel élément bouton personnalisé à votre disposition
3. Faites un clic droit sur votre nouveau bouton
4. Sélectionnez "Template Settings" dans le menu
5. Cliquez sur "Is Template: ON" pour activer le mode modèle

Votre bouton est maintenant prêt à servir de modèle pour d'autres boutons et curseurs !

# Options de partage du modèle

Vous pouvez choisir quels types d'éléments votre modèle affectera :
- **Buttons** - Votre modèle n'affectera que les boutons (vanilla et personnalisés)
- **Sliders** - Votre modèle n'affectera que les curseurs (vanilla et personnalisés)

Pour définir cette option :
1. Faites un clic droit sur votre bouton modèle
2. Allez dans "Template Settings"
3. Cliquez sur "Share With: [Current Option]" pour faire défiler les options

> [!WARNING]
> **Important** : Vous pouvez avoir deux modèles actifs en même temps - un pour les boutons ET un pour les curseurs. Cela signifie que vous pouvez créer des designs de modèle distincts pour différents types d'éléments sur le même écran !

# Ce qui peut être modélisé

Vous pouvez contrôler précisément quelles propriétés votre modèle partagera avec d'autres éléments :

## Propriétés pouvant être activées/désactivées :

1. Faites un clic droit sur votre bouton modèle
2. Allez dans "Template Settings" 
3. Activez ou désactivez l'une de ces options :
   - **Width** - Rend tous les éléments concernés aussi larges que votre modèle
   - **Height** - Rend tous les éléments concernés aussi hauts que votre modèle
   - **X Position** - Place tous les éléments concernés à la même coordonnée X que votre modèle
   - **Y Position** - Place tous les éléments concernés à la même coordonnée Y que votre modèle
   - **Opacity** - Donne à tous les éléments concernés la même transparence que votre modèle
   - **Visibility** - Contrôle si les éléments concernés sont affichés ou masqués
   - **Label** - Fait en sorte que tous les éléments concernés utilisent le même texte que votre modèle

## Propriétés toujours partagées :

- **Textures du bouton** - Lorsque vous définissez des textures personnalisées sur votre modèle, elles seront automatiquement appliquées à tous les éléments concernés
  - Contrairement aux autres propriétés, le partage des textures ne peut pas être désactivé
  - Les textures ne sont appliquées que lorsque des textures personnalisées sont réellement définies sur le modèle
  - Si aucune texture personnalisée n'est définie, les textures d'origine de l'élément seront utilisées

# Personnaliser l'apparence du modèle

Votre bouton modèle peut être personnalisé comme n'importe quel autre bouton :

1. Faites un clic droit sur votre bouton modèle
2. Vous pouvez définir :
   - Les textures du bouton (états normal, survolé et inactif)
   - Les libellés (normal et survolé)
   - Les sons (survol et clic)
   - Les info-bulles

Pour les boutons, vous pouvez définir des textures personnalisées pour différents états :
- Arrière-plan normal (quand il n'y a pas d'interaction)
- Arrière-plan au survol (quand la souris est dessus)
- Arrière-plan inactif (quand le bouton est désactivé)

Pour les curseurs, vous pouvez également définir :
- Les textures de la poignée du curseur
- Les textures d'arrière-plan du curseur

# Conseils importants

1. **Les boutons modèles n'apparaîtront pas en jeu** - Ils ne sont visibles que dans l'éditeur, donc placez-les où c'est le plus pratique.

2. **Vous pouvez avoir deux modèles actifs simultanément** - Un modèle pour les boutons et un modèle pour les curseurs peuvent être actifs en même temps.

3. **Un seul modèle par type est actif** - Si vous avez plusieurs modèles de boutons, seul celui situé le plus haut dans votre liste d'éléments sera utilisé pour les boutons. La même règle s'applique aux modèles de curseurs.

4. **Les modifications du modèle sont mises à jour instantanément** - Lorsque vous modifiez votre modèle, tous les boutons et curseurs concernés se mettent à jour immédiatement.

5. **Utilisez le bon mode de partage** - N'oubliez pas que le mode "Buttons" n'affecte pas les curseurs, et que le mode "Sliders" n'affecte pas les boutons.

6. **Appliquez les propriétés de manière sélective** - Vous n'êtes pas obligé d'appliquer toutes les propriétés. Par exemple, vous pouvez vouloir ne modéliser que les textures et la taille, tout en laissant les éléments conserver leurs positions d'origine.

7. **Les textures sont toujours partagées lorsqu'elles sont définies** - Contrairement aux autres propriétés, toutes les textures personnalisées que vous appliquez au modèle seront automatiquement partagées avec les éléments correspondants. Vous n'avez pas besoin d'activer ou de désactiver cette fonctionnalité.

# Exemples d'utilisation

- Créer un style cohérent pour tous les boutons d'un écran
- Faire correspondre tous les curseurs à votre thème personnalisé avec un modèle séparé
- Créer un "mode caché" où vous pouvez afficher/masquer plusieurs boutons à la fois
- Modifier la taille de nombreux boutons en une seule édition
- Donner à tous les boutons de votre menu les mêmes textures et sons personnalisés
