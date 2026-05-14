---
title: Animateur d’éléments
description: >-
  Comment animer des éléments avec des images clés à l’aide de l’Animateur
  d’éléments.
---

# Animateur d’éléments

L’**Animateur** est un élément qui vous permet d’animer d’autres éléments. Avec cet élément, vous pouvez modifier en douceur la taille, la position et le point d’ancrage d’un autre élément au fil du temps à l’aide d’images clés. Les images clés sont comme des instantanés qui capturent l’apparence que l’élément doit avoir à un moment précis. L’élément Animateur lit ensuite ces instantanés dans l’ordre pour créer un mouvement fluide.

> L’**Animateur d’éléments** vous permet de contrôler la **position, la taille et le point d’ancrage** des éléments. Il est **impossible** de contrôler d’autres paramètres des éléments, comme l’opacité, la visibilité, la rotation, etc. !
{.is-warning}

# Tutoriel vidéo

Comme beaucoup d’entre vous étaient un peu perdus sur le fonctionnement de l’animateur, j’ai réalisé une petite vidéo qui montre comment l’utiliser.

[FancyMenu | Comment utiliser l’éditeur d’éléments - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Ajouter l’élément Animateur

1. **Clique droit sur l’arrière-plan :**  
   Dans l’éditeur de mise en page, faites un clic droit sur l’arrière-plan.

2. **Sélectionnez Nouvel élément -> Animateur d’éléments :**  
   Dans le menu qui apparaît, allez dans **Nouvel élément** et cliquez sur **Animateur d’éléments**. Cela ajoute l’élément Animateur à votre mise en page.

3. **Configurez-le :**  
   Après l’ajout, l’élément Animateur apparaît avec ses paramètres par défaut. Vous pouvez modifier des options comme la boucle ou la couleur en faisant un clic droit sur l’Animateur et en choisissant dans le menu.

# Gérer les images clés

Les images clés sont comme des marque-pages qui indiquent à l’Animateur à quoi l’élément doit ressembler à un moment donné.

## Ouvrir l’éditeur d’images clés

- **Ouvrir l’éditeur :**  
  Faites un clic droit sur l’élément Animateur et choisissez **Modifier les images clés** (ou **Gérer les images clés**). Cela ouvre un écran où vous pouvez ajouter, modifier ou supprimer des images clés.

## Enregistrer et ajouter des images clés

- **Démarrer l’enregistrement :**  
  Dans l’éditeur d’images clés, appuyez sur la touche **`R`** pour commencer l’enregistrement. Pendant l’enregistrement, la boîte d’aperçu change de couleur pour montrer qu’elle est active.
  
- **Modifier l’aperçu :**  
  Déplacez ou redimensionnez la boîte d’aperçu pour définir l’apparence souhaitée. En mode décalage, l’aperçu reste centré sur une croix afin que les changements soient affichés comme des décalages.
  
- **Ajouter une image clé :**  
  Appuyez sur la touche **`K`** pour enregistrer l’apparence actuelle comme image clé. Cette image clé sauvegarde la position, la taille et les paramètres d’ancrage de l’aperçu.

## Modifier les images clés

- **Sélectionner une image clé :**  
  Cliquez sur un marqueur d’image clé dans la timeline. Vous pouvez aussi maintenir **Ctrl** enfoncé et cliquer pour en sélectionner plusieurs.
  
- **Déplacer une image clé :**  
  Faites glisser le marqueur de l’image clé vers la gauche ou la droite pour changer son moment. Vous pouvez aussi utiliser :
  - **Flèche gauche :** pour la déplacer 100 ms plus tôt.
  - **Flèche droite :** pour la déplacer 100 ms plus tard.
  
- **Ajuster finement l’aperçu :**  
  Lorsqu’une image clé est sélectionnée, ajustez la boîte d’aperçu en la déplaçant ou en la redimensionnant. Utilisez **Ctrl + Z** pour annuler et **Ctrl + Y** pour rétablir les modifications si nécessaire.

## Supprimer des images clés

- **Supprimer une image clé :**  
  Sélectionnez une image clé et appuyez sur la touche **Suppr** pour la supprimer.
  
- **Supprimer plusieurs images clés :**  
  Vous pouvez sélectionner plusieurs images clés (par exemple avec **Ctrl + A** pour tout sélectionner) puis appuyer sur Suppr pour toutes les supprimer.

## Lissage des images clés

Le lissage des images clés est une fonctionnalité qui vous aide à répartir uniformément vos images clés. Cela rend votre animation plus régulière et plus fluide.

- **Sélectionner plusieurs images clés :**  
  Commencez par sélectionner deux images clés ou plus que vous souhaitez lisser (utilisez **Ctrl + clic** ou **Ctrl + A**).

- **Cliquer sur le bouton de lissage :**  
  Dans la barre d’outils inférieure de l’éditeur d’images clés, cliquez sur le bouton **Distance Smoothing**.

- **Entrer une nouvelle distance :**  
  Une petite boîte de saisie apparaît. Saisissez une valeur (en millisecondes) pour définir le même intervalle de temps entre chaque image clé sélectionnée.

- **Appliquer le lissage :**  
  Appuyez sur Entrée pour appliquer le lissage. Les images clés seront ajustées afin que l’écart de temps entre elles soit régulier.

# Prévisualiser votre animation

Après avoir enregistré des images clés, vous pouvez voir à quoi ressemblera votre animation :

- **Lire l’animation :**  
  Dans l’éditeur d’images clés, appuyez sur la touche **`P`** ou cliquez sur le bouton de lecture. L’aperçu démarre depuis le début et montre comment la boîte d’aperçu évolue au fil du temps.
  
- **Remarque sur la boucle :**  
  Lors de la prévisualisation dans l’éditeur d’images clés, l’animation **ne boucle pas**. Cela signifie qu’elle se lit du début à la fin une seule fois. La boucle ne sera active que lorsque l’élément Animateur sera appliqué à un élément cible dans la mise en page finale.
  
- **Mettre l’aperçu en pause :**  
  Appuyez de nouveau sur la touche **`P`** pour mettre l’animation en pause si vous souhaitez vous arrêter à un moment précis.
  
- **Faire glisser la barre de progression :**  
  Si disponible, vous pouvez faire glisser le repère de la timeline pour vérifier l’apparence de l’animation à un moment précis.

# Choisir des éléments cibles

Après avoir configuré vos images clés, vous devez choisir quels éléments de la mise en page seront animés :

1. **Ouvrir le gestionnaire de cibles :**  
   Faites un clic droit sur l’élément Animateur et choisissez **Gérer les cibles**.
  
2. **Ajouter des cibles :**  
   Cliquez sur **Ajouter une cible** pour afficher une liste des éléments disponibles. Choisissez ceux que vous voulez animer.
  
3. **Supprimer des cibles :**  
   Pour supprimer une cible, ouvrez le gestionnaire et cliquez sur **Supprimer la cible**.

Lorsque l’animation se joue dans la mise en page finale, l’Animateur utilise vos images clés pour modifier la taille, la position et d’autres paramètres des éléments choisis. La boucle sera appliquée ici si vous l’avez activée.

# Raccourcis clavier

Utilisez ces raccourcis dans l’éditeur d’images clés pour travailler plus rapidement :

- **Touche `R` :** Démarrer ou arrêter l’enregistrement.
- **Touche `T` :** Mettre l’enregistrement en pause ou le reprendre.
- **Touche `P` :** Lire ou mettre en pause l’aperçu de l’animation.
- **Touche `K` :** Ajouter une nouvelle image clé à l’instant actuel.
- **Touches Flèche gauche/droite :**  
  - **Flèche gauche :** Déplacer une image clé 100 ms plus tôt.
  - **Flèche droite :** Déplacer une image clé 100 ms plus tard.
- **Touche Suppr :** Supprimer la ou les images clés sélectionnées.
- **Ctrl + A :** Sélectionner toutes les images clés.
- **Ctrl + Z :** Annuler votre dernière modification.
- **Ctrl + Y :** Rétablir la modification que vous venez d’annuler.
- **Ctrl + glisser une image clé** : Déplacer plusieurs images clés sélectionnées à la fois.

# Paramètres supplémentaires et conseils

- **Boucler l’animation :**  
  Vous pouvez configurer l’Animateur pour boucler. Lorsque la boucle est activée, l’animation recommence après la dernière image clé — mais notez que cela ne se produit que pour l’élément cible final. Dans l’aperçu de l’éditeur d’images clés, la boucle ne se produit pas.
  
- **Ignorer taille/position :**  
  Si vous ne voulez pas que les images clés modifient la taille ou la position d’un élément, désactivez ces options.

- **Décalages temporels :**
  FancyMenu 3.9.0 ajoute des décalages temporels pour les éléments contrôlés. Vous pouvez décaler individuellement des éléments cibles, ou utiliser des décalages temporels aléatoires dans une plage configurée, afin qu’une même animation puisse commencer à des moments légèrement différents pour chaque cible.
  
- **Mode décalage :**  
  En mode décalage, les animations sont appliquées comme des changements à partir de l’emplacement d’origine de l’élément. L’aperçu est affiché centré sur une croix.
  
- **Annuler et rétablir :**  
  Utilisez **Ctrl + Z** pour annuler et **Ctrl + Y** pour rétablir les modifications.
  
- **Vérifier l’ordre :**  
  Assurez-vous que vos images clés sont dans le bon ordre chronologique. Le système les trie automatiquement, mais si vous en déplacez une, vérifiez à nouveau l’ordre.
  
- **Prévisualiser les changements :**  
  Utilisez le bouton de lecture ou la touche **`P`** pour voir votre animation en action avant de l’enregistrer.

# Conclusion

En suivant ces étapes simples, vous pouvez ajouter un élément Animateur à votre mise en page et créer des animations fluides. Que vous enregistriez des changements en direct avec l’aperçu, ajustiez les images clés au clavier, choisissiez quels éléments animer ou prévisualisiez votre animation pour voir son rendu, l’élément Animateur vous offre un moyen simple de donner vie à vos menus personnalisés.

Bonne animation !
