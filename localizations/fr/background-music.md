---
title: Musique d’arrière-plan du menu
description: Comment personnaliser la musique jouée dans les menus.
---

# Musique d’arrière-plan du menu

Il est possible de remplacer la musique d’arrière-plan par défaut de Minecraft par des pistes personnalisées, ou simplement de désactiver la musique Vanilla normale qui se joue dans les menus.

# Désactiver la musique Vanilla

FancyMenu propose plusieurs façons de désactiver la musique Vanilla des menus. Cela peut être utile si vous prévoyez de jouer d’autres pistes audio dans les écrans, ou si vous ne voulez tout simplement pas de musique du tout dans certains écrans.

## Globalement

Si vous ne voulez aucune musique dans les menus, c’est la méthode la plus simple.

Pour désactiver ou remplacer globalement la musique Vanilla des menus dans FancyMenu 3.9.0+, allez dans la barre de menu de FancyMenu en haut des écrans, puis cliquez sur **Customization -> Global Customizations**. Les personnalisations globales peuvent remplacer la musique des menus sans nécessiter de pack de ressources et sans activer les personnalisations pour chaque écran.

<br>
<img width="600" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/d829a35e-f23f-42a9-ad79-193de73b499b">

> Désactiver la musique par défaut de Minecraft la désactivera dans tous les écrans, pas seulement dans l’écran actuel.
{.is-info}

## Par écran

Si vous voulez plus de contrôle sur les écrans dans lesquels la musique des menus Vanilla doit se jouer, vous devez utiliser l’élément **Music Controller**. Cet élément s’ajoute aux layouts comme n’importe quel autre élément en **faisant un clic droit sur l’arrière-plan de l’éditeur**, puis en cliquant sur **New Element -> Music Controller**.

En **cliquant avec le bouton droit** sur l’élément, vous pouvez personnaliser les types de musique joués dans les menus qui doivent être désactivés (la musique normale des menus et la musique du monde qui continue à se jouer dans les écrans qui ne mettent pas le jeu en pause, comme l’écran d’inventaire).

> Cet élément prend en charge les **exigences de chargement**, ce qui vous donne encore plus de contrôle sur le moment où la musique Vanilla doit être jouée !
{.is-info}


# Ajouter une musique personnalisée

Nous pouvons maintenant ajouter la musique d’arrière-plan personnalisée proprement dite.

Si vous voulez jouer la même musique personnalisée dans tous les écrans et avoir un contrôle au niveau du layout, vous devez utiliser un **layout universel**, qui est chargé dans chaque écran où les personnalisations sont activées. Pour un simple remplacement global de la musique des menus, utilisez plutôt [Global Customizations](/global-customizations).

Lors de l’utilisation d’un layout universel, la musique **continuera à jouer** lorsque vous passerez d’un menu avec ce layout activé à un autre menu avec le même layout activé.

Si vous voulez jouer une musique différente selon l’écran, utilisez des layouts normaux.

Dans cet exemple, nous allons utiliser des **layouts universels**.

Ajoutez un nouvel élément **Audio** au layout universel, qui servira de lecteur de musique d’arrière-plan.

<br>
<img width="400" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/bddf8f46-47c5-4a00-a6f7-b5ca1df8ae67">

Ajoutez maintenant les pistes musicales qui doivent être jouées en arrière-plan.

<br>
<img width="300" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/824dcb90-3bd5-4c0b-96d0-e581a7c2f9f7">

C’est à peu près tout.
Vous pouvez aussi mettre l’élément Audio en mode aléatoire et changer son canal audio si nécessaire.

Enregistrez le layout et quittez l’éditeur.

# Activer les personnalisations pour tous les menus

Nous avons utilisé un **layout universel** dans cet exemple, car nous voulons que notre musique d’arrière-plan soit jouée dans plusieurs écrans.

Comme les layouts ne se chargent que dans les écrans où les **personnalisations sont activées**, nous devons maintenant les activer pour chaque écran dans lequel nous voulons que la musique soit jouée.

Pour cela, cliquez sur **Customization**, puis activez **Current Screen Customization**.

<br>
<img width="320" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/2f6527b7-ae14-4e82-abc6-3572cc6490b2">

Répétez cette opération pour chaque écran dans lequel vous souhaitez que votre musique d’arrière-plan personnalisée soit jouée.

Et voilà ! Vous avez maintenant une musique d’arrière-plan personnalisée dans les menus de Minecraft !
