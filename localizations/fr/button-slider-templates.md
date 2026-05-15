---
title: Modèles de boutons et de curseurs
description: >-
  Comment utiliser des modèles de boutons/curseurs pour appliquer un design
  spécifique de bouton/curseur à TOUS les boutons en une seule fois.
---

# Utiliser des éléments bouton comme modèles pour les boutons et les curseurs

Il est possible d’utiliser un élément Bouton comme modèle pour d’autres boutons et même pour des curseurs. En procédant ainsi, vous pouvez appliquer un design spécifique de bouton/curseur à TOUS les boutons/curseurs d’un menu, voire à tous les menus à la fois lorsque vous utilisez une disposition universelle.

> [!IMPORTANT]
> Depuis FancyMenu 3.9.0, il est recommandé d’utiliser les [Personnalisations globales](/global-customizations) plutôt que les modèles de boutons/curseurs dès que possible, car elles peuvent remplacer globalement les textures vanilla des boutons et des curseurs sans utiliser de pack de ressources. Utilisez les personnalisations globales pour un style large de l’interface vanilla, et les modèles uniquement lorsque vous avez besoin d’un comportement spécifique à une disposition.

# Important avant de commencer

Si vous souhaitez uniquement modifier la texture d’un seul bouton ou curseur, il est plus simple et recommandé de simplement faire un **clic droit** sur le bouton ou le curseur (vanilla ou personnalisé) dans l’éditeur. Une option permet de définir les **textures d’arrière-plan** (et les textures de poignée de curseur) pour les boutons et les curseurs.

# Qu’est-ce qu’un bouton modèle ?

Un bouton modèle est un type spécial de bouton personnalisé dans FancyMenu qui vous permet de contrôler l’apparence et le comportement d’autres boutons et curseurs. C’est un peu comme créer un design maître que de nombreux autres éléments suivront.

Lorsque vous créez un bouton modèle, vous pouvez faire en sorte que de nombreux boutons ou curseurs partagent les mêmes éléments :
- Taille (largeur et hauteur)
- Position
- Visibilité
- Opacité (niveau de transparence)
- Libellés de texte
- **Textures du bouton** (partagées automatiquement lorsque des textures personnalisées sont définies)

C’est très utile lorsque vous voulez donner un aspect cohérent à votre menu ou lorsque vous devez mettre à jour plusieurs boutons en même temps !

# Qui peut utiliser les modèles ?

Seuls les **boutons personnalisés** peuvent servir de modèles. Cependant, ces modèles peuvent être appliqués à :
- Boutons vanilla (les boutons Minecraft par défaut)
- Boutons personnalisés (les boutons que vous créez dans FancyMenu)
- Curseurs vanilla (comme les contrôles de volume)
- Curseurs personnalisés (les curseurs que vous créez dans FancyMenu)

# Comment créer un bouton modèle

1. Ouvrez l’éditeur FancyMenu pour l’écran que vous souhaitez personnaliser
2. Ajoutez un nouvel élément bouton personnalisé à votre disposition
3. Faites un clic droit sur votre nouveau bouton
4. Sélectionnez "Template Settings" dans le menu
5. Cliquez sur "Is Template: ON" pour activer le mode modèle

Votre bouton est maintenant prêt à servir de modèle pour d’autres boutons et curseurs !

# Options de partage du modèle

Vous pouvez choisir quels types d’éléments seront affectés par votre modèle :
- **Buttons** - Votre modèle n’affectera que les boutons (vanilla et personnalisés)
- **Sliders** - Votre modèle n’affectera que les curseurs (vanilla et personnalisés)

Pour définir cette option :
1. Faites un clic droit sur votre bouton modèle
2. Allez dans "Template Settings"
3. Cliquez sur "Share With: [Current Option]" pour faire défiler les options

> **Important** : Vous pouvez avoir deux modèles actifs en même temps — un pour les boutons ET un pour les curseurs. Cela signifie que vous pouvez créer des designs de modèle distincts pour différents types d’éléments sur le même écran !
{.is-warning}


# Ce qui peut être modélisé

Vous pouvez contrôler précisément quelles propriétés votre modèle partagera avec d’autres éléments :

## Propriétés pouvant être activées/désactivées :

1. Faites un clic droit sur votre bouton modèle
2. Allez dans "Template Settings" 
3. Activez ou désactivez chacune de ces options :
   - **Width** - Donne à tous les éléments concernés la même largeur que votre modèle
   - **Height** - Donne à tous les éléments concernés la même hauteur que votre modèle
   - **X Position** - Place tous les éléments concernés sur la même coordonnée X que votre modèle
   - **Y Position** - Place tous les éléments concernés sur la même coordonnée Y que votre modèle
   - **Opacity** - Donne à tous les éléments concernés la même transparence que votre modèle
   - **Visibility** - Contrôle si les éléments concernés sont affichés ou masqués
   - **Label** - Fait en sorte que tous les éléments concernés utilisent le même texte que votre modèle

## Propriétés toujours partagées :

- **Textures du bouton** - Lorsque vous définissez des textures personnalisées sur votre modèle, elles seront automatiquement appliquées à tous les éléments concernés
  - Contrairement aux autres propriétés, le partage des textures ne peut pas être désactivé
  - Les textures ne sont appliquées que lorsque des textures personnalisées sont réellement définies sur le modèle
  - Si aucune texture personnalisée n’est définie, les textures d’origine de l’élément seront utilisées

# Personnaliser l’apparence du modèle

Votre bouton modèle peut être personnalisé comme n’importe quel autre bouton :

1. Faites un clic droit sur votre bouton modèle
2. Vous pouvez définir :
   - Textures du bouton (états normal, survolé et inactif)
   - Libellés (normal et survolé)
   - Sons (survol et clic)
   - Infobulles

Pour les boutons, vous pouvez définir des textures personnalisées pour différents états :
- Arrière-plan normal (lorsqu’il n’y a pas d’interaction)
- Arrière-plan au survol (lorsque votre souris est dessus)
- Arrière-plan inactif (lorsque le bouton est désactivé)

Pour les curseurs, vous pouvez aussi définir :
- Textures de la poignée du curseur
- Textures d’arrière-plan du curseur

# Conseils importants

1. **Les boutons modèles n’apparaîtront pas dans le jeu** - Ils ne sont visibles que dans l’éditeur, donc placez-les où cela vous convient.

2. **Vous pouvez avoir deux modèles actifs simultanément** - Un modèle pour les boutons et un modèle pour les curseurs peuvent être actifs en même temps.

3. **Un seul modèle par type est actif** - Si vous avez plusieurs modèles de boutons, seul celui qui est en haut dans la liste de vos éléments sera utilisé pour les boutons. La même chose s’applique aux modèles de curseurs.

4. **Les modifications du modèle sont appliquées instantanément** - Lorsque vous modifiez votre modèle, tous les boutons et curseurs concernés se mettront à jour immédiatement.

5. **Utilisez le bon mode de partage** - N’oubliez pas que le mode "Buttons" n’affectera pas les curseurs, et que le mode "Sliders" n’affectera pas les boutons.

6. **Appliquez les propriétés de manière sélective** - Vous n’êtes pas obligé d’appliquer toutes les propriétés. Par exemple, vous pourriez vouloir ne modéliser que les textures et la taille, tout en laissant les éléments conserver leurs positions d’origine.

7. **Les textures sont toujours partagées lorsqu’elles sont définies** - Contrairement aux autres propriétés, toutes les textures personnalisées que vous appliquez au modèle seront automatiquement partagées avec les éléments correspondants. Vous n’avez pas besoin d’activer ou de désactiver cette fonctionnalité.

# Exemples d’utilisation

- Créer un style cohérent pour tous les boutons d’un écran
- Faire correspondre tous les curseurs à votre thème personnalisé avec un modèle séparé
- Créer un « mode masqué » où vous pouvez afficher/masquer plusieurs boutons à la fois
- Modifier la taille de nombreux boutons avec une seule modification
- Donner à tous les boutons de votre menu les mêmes textures et sons personnalisés
