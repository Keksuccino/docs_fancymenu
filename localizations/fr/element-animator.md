---
title: Animateur d’éléments
description: >-
  Comment animer des éléments avec des images-clés à l’aide de l’Animateur
  d’éléments.
---

# Animateur d’éléments

L’**Animateur** est un élément qui vous permet d’animer d’autres éléments. Avec cet élément, vous pouvez modifier en douceur la taille, la position et le point d’ancrage d’un autre élément au fil du temps à l’aide d’images-clés. Les images-clés sont comme des instantanés qui capturent l’apparence que l’élément doit avoir à un moment précis. L’élément Animateur lit ensuite ces instantanés dans l’ordre pour créer un mouvement fluide.

> [!WARNING]
> L’**Animateur d’éléments** vous permet de contrôler la **position, la taille et le point d’ancrage** des éléments. Il est **impossible** de contrôler d’autres paramètres des éléments, comme l’opacité, la visibilité, la rotation, etc. !

# Tutoriel vidéo

Comme beaucoup d’entre vous étaient un peu confus sur le fonctionnement de l’animateur, j’ai réalisé une petite vidéo qui montre comment l’utiliser.

[FancyMenu | Comment utiliser l’éditeur d’éléments - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Ajouter l’élément Animateur

1. **Faites un clic droit sur l’arrière-plan :**  
   Dans l’éditeur de mise en page, faites un clic droit sur l’arrière-plan.

2. **Sélectionnez Nouveau élément -> Animateur d’éléments :**  
   Dans le menu qui s’affiche, allez dans **New Element** puis cliquez sur **Element Animator**. Cela ajoute l’élément Animateur à votre mise en page.

3. **Configurez-le :**  
   Après l’ajout, l’élément Animateur apparaît avec ses paramètres par défaut. Vous pouvez modifier des options comme la boucle ou la couleur en faisant un clic droit sur l’Animateur et en choisissant dans le menu.

# Gérer les images-clés

Les images-clés sont comme des marque-pages qui indiquent à l’Animateur à quoi l’élément doit ressembler à un moment donné.

## Ouvrir l’éditeur d’images-clés

- **Ouvrir l’éditeur :**  
  Faites un clic droit sur l’élément Animateur et choisissez **Edit Keyframes** (ou **Manage Keyframes**). Cela ouvre un écran où vous pouvez ajouter, modifier ou supprimer des images-clés.

## Enregistrer et ajouter des images-clés

- **Démarrer l’enregistrement :**  
  Dans l’éditeur d’images-clés, appuyez sur la touche **`R`** pour commencer l’enregistrement. Pendant l’enregistrement, la boîte d’aperçu change de couleur pour indiquer qu’il est actif.
  
- **Modifier l’aperçu :**  
  Déplacez ou redimensionnez la boîte d’aperçu pour définir l’apparence souhaitée. En mode décalage, l’aperçu reste centré sur une croix afin que les changements soient affichés sous forme de décalages.
  
- **Ajouter une image-clé :**  
  Appuyez sur la touche **`K`** pour enregistrer l’apparence actuelle comme image-clé. Cette image-clé enregistre la position, la taille et les paramètres d’ancrage de l’aperçu.

## Modifier les images-clés

- **Sélectionner une image-clé :**  
  Cliquez sur un marqueur d’image-clé dans la timeline. Vous pouvez aussi maintenir **Ctrl** et cliquer pour en sélectionner plusieurs.
  
- **Déplacer une image-clé :**  
  Faites glisser le marqueur de l’image-clé vers la gauche ou vers la droite pour modifier son moment. Vous pouvez aussi utiliser :
  - **Flèche gauche :** pour la déplacer de 100 ms plus tôt.
  - **Flèche droite :** pour la déplacer de 100 ms plus tard.
  
- **Ajuster l’aperçu avec précision :**  
  Lorsqu’une image-clé est sélectionnée, ajustez la boîte d’aperçu en la déplaçant ou en la redimensionnant. Utilisez **Ctrl + Z** pour annuler et **Ctrl + Y** pour rétablir les modifications si nécessaire.

## Supprimer des images-clés

- **Supprimer une image-clé :**  
  Sélectionnez une image-clé et appuyez sur la touche **Suppr** pour la supprimer.
  
- **Supprimer plusieurs images-clés :**  
  Vous pouvez sélectionner plusieurs images-clés (par exemple avec **Ctrl + A** pour tout sélectionner) puis appuyer sur Suppr pour les supprimer toutes.

## Lissage des images-clés

Le lissage des images-clés est une fonctionnalité qui vous aide à espacer régulièrement vos images-clés. Cela rend votre animation plus cohérente et plus fluide.

- **Sélectionner plusieurs images-clés :**  
  Commencez par sélectionner deux images-clés ou plus que vous souhaitez lisser (utilisez **Ctrl + Clic** ou **Ctrl + A**).

- **Cliquer sur le bouton de lissage :**  
  Dans la barre d’outils inférieure de l’éditeur d’images-clés, cliquez sur le bouton intitulé **Distance Smoothing**.

- **Saisir une nouvelle distance :**  
  Une petite zone de saisie apparaîtra. Entrez une valeur (en millisecondes) pour définir le même intervalle de temps entre chaque image-clé sélectionnée.

- **Appliquer le lissage :**  
  Appuyez sur Entrée pour appliquer le lissage. Les images-clés seront ajustées afin que la différence de temps entre elles soit régulière.

# Prévisualiser votre animation

Après avoir enregistré des images-clés, vous pouvez voir à quoi ressemblera votre animation :

- **Lire l’animation :**  
  Dans l’éditeur d’images-clés, appuyez sur la touche **`P`** ou cliquez sur le bouton de lecture. L’aperçu commencera au début et montrera comment la boîte d’aperçu change au fil du temps.
  
- **Remarque sur la boucle :**  
  Pendant la prévisualisation dans l’éditeur d’images-clés, l’animation **ne se répétera pas**. Cela signifie qu’elle ne sera lue qu’une seule fois, du début à la fin. La boucle ne sera active que lorsque l’élément Animateur sera appliqué à un élément cible dans la mise en page finale.
  
- **Mettre l’aperçu en pause :**  
  Appuyez à nouveau sur la touche **`P`** pour mettre l’animation en pause si vous souhaitez vous arrêter à un moment précis.
  
- **Faire glisser la barre de progression :**  
  Si disponible, vous pouvez faire glisser le marqueur de la timeline pour vérifier l’apparence de l’animation à un moment précis.

# Choisir les éléments cibles

Après avoir configuré vos images-clés, vous devez choisir quels éléments de la mise en page seront animés :

1. **Ouvrir le gestionnaire de cibles :**  
   Faites un clic droit sur l’élément Animateur et choisissez **Manage Targets**.
  
2. **Ajouter des cibles :**  
   Cliquez sur **Add Target** pour afficher la liste des éléments disponibles. Choisissez ceux que vous voulez animer.
  
3. **Supprimer des cibles :**  
   Pour supprimer une cible, ouvrez le gestionnaire et cliquez sur **Remove Target**.

Lorsque l’animation est lue dans la mise en page finale, l’Animateur utilisera vos images-clés pour modifier la taille, la position et d’autres propriétés des éléments choisis. La boucle sera appliquée ici si vous l’avez activée.

# Raccourcis clavier

Utilisez ces raccourcis dans l’éditeur d’images-clés pour travailler plus vite :

- **Touche `R` :** Démarrer ou arrêter l’enregistrement.
- **Touche `T` :** Mettre l’enregistrement en pause ou le reprendre.
- **Touche `P` :** Lire ou mettre en pause l’aperçu de l’animation.
- **Touche `K` :** Ajouter une nouvelle image-clé au moment actuel.
- **Touches Flèche gauche/droite :**  
  - **Flèche gauche :** Déplacer une image-clé de 100 ms plus tôt.
  - **Flèche droite :** Déplacer une image-clé de 100 ms plus tard.
- **Touche Suppr :** Supprimer la ou les images-clés sélectionnées.
- **Ctrl + A :** Sélectionner toutes les images-clés.
- **Ctrl + Z :** Annuler votre dernière modification.
- **Ctrl + Y :** Rétablir la modification que vous venez d’annuler.
- **Ctrl + glisser une image-clé** : Faire glisser plusieurs images-clés sélectionnées à la fois.

# Paramètres et conseils supplémentaires

- **Boucler l’animation :**  
  Vous pouvez configurer l’Animateur pour qu’il boucle. Lorsque la boucle est activée, l’animation recommence après la dernière image-clé — mais notez que cela ne se produit que pour l’élément cible final. Dans l’aperçu de l’éditeur d’images-clés, la boucle n’a pas lieu.
  
- **Ignorer la taille/position :**  
  Si vous ne voulez pas que les images-clés modifient la taille ou la position d’un élément, désactivez ces options.

- **Décalages temporels :**
  Vous pouvez appliquer des décalages temporels à des éléments cibles individuels ou utiliser des décalages temporels aléatoires dans une plage configurée, afin qu’une même animation commence à des moments différents pour chaque cible.
  
- **Mode décalage :**  
  En mode décalage, les animations sont appliquées comme des changements par rapport à la position d’origine de l’élément. L’aperçu est affiché centré sur une croix.
  
- **Annuler et rétablir :**  
  Utilisez **Ctrl + Z** pour annuler et **Ctrl + Y** pour rétablir les modifications.
  
- **Vérifier l’ordre :**  
  Assurez-vous que vos images-clés sont dans le bon ordre chronologique. Le système les trie automatiquement, mais si vous en déplacez une, vérifiez à nouveau l’ordre.
  
- **Prévisualiser les changements :**  
  Utilisez le bouton de lecture ou la touche **`P`** pour voir votre animation en action avant de l’enregistrer.
