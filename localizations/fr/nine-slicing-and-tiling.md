---
title: Découpage en neuf et mosaïque
description: Comment utiliser le découpage en neuf et la mosaïque dans FancyMenu.
---

# Découpage en neuf et mosaïque

Quand vous concevez de superbes menus dans Minecraft avec FancyMenu, vous pouvez vouloir utiliser des images qui doivent être redimensionnées correctement ou répétées en motifs. Ce guide explique comment utiliser le **découpage en neuf** et la **mosaïque** (aussi appelée textures répétées) pour rendre vos menus incroyables !

# Qu’est-ce que le découpage en neuf ?

Le découpage en neuf est une technique qui permet d’étirer une image à n’importe quelle taille sans qu’elle paraisse bizarre. Elle fonctionne en divisant votre image en neuf parties (comme un morpion). Les coins gardent la même taille, les bords s’étirent dans une seule direction et le centre s’étire dans les deux directions.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Exemple de découpage en neuf" style="max-width: 500px; height: auto;" />

## Où puis-je utiliser le découpage en neuf ?

Dans FancyMenu, le découpage en neuf est disponible pour :
- **Éléments de bouton** (à la fois les boutons personnalisés et lors de l’édition des boutons Vanilla)
- **Textures de barre de progression** (textures de barre et d’arrière-plan)

## Comment utiliser le découpage en neuf avec les boutons

1. **Créez ou sélectionnez un élément de bouton** dans votre éditeur de mise en page.
2. Faites un clic droit sur le bouton et cherchez l’option "Button Textures".
3. Définissez les textures d’arrière-plan de votre bouton (états normal, survolé, inactif).
4. Activez l’option "Nine-Slice Custom Background".
5. Définissez les **Nine-Slice Background X-Borders** (taille des bordures gauche et droite).
6. Définissez les **Nine-Slice Background Y-Borders** (taille des bordures supérieure et inférieure).

### Conseils pour le découpage en neuf des boutons

- Utilisez une image avec des bordures et des coins bien distincts.
- Les valeurs de bordure (X et Y) indiquent à FancyMenu combien de pixels à partir de chaque bord doivent être traités comme bordure.
- Une valeur typique peut être de 5 pixels pour les bordures X et Y.
- Les coins conserveront toujours la même taille, tandis que les parties centrales s’étireront pour remplir le bouton.

# Qu’est-ce que la mosaïque ?

La mosaïque (aussi appelée textures répétées) permet de remplir une grande zone avec une petite image en la répétant comme des carreaux sur un sol. C’est parfait pour les arrière-plans ou les grandes images dont vous voulez que le motif se poursuive.

## Où puis-je utiliser la mosaïque ?

Dans FancyMenu, la mosaïque est disponible pour :
- **Éléments d’image**
- **Arrière-plans de menu image**

## Comment utiliser la mosaïque avec les éléments d’image

1. **Créez ou sélectionnez un élément d’image** dans votre éditeur de mise en page.
2. Faites un clic droit sur l’image et cherchez "Image Source" pour définir votre texture.
3. Trouvez et activez l’option **"Repeat Texture"**.
4. Redimensionnez votre élément d’image pour voir la texture se répéter afin de remplir l’espace.

## Comment utiliser la mosaïque avec les arrière-plans de menu

1. Ouvrez **Menu Backgrounds** depuis le menu contextuel de l’arrière-plan dans l’éditeur de mise en page.
2. Choisissez le type d’arrière-plan **Image**.
3. Sélectionnez votre image d’arrière-plan.
4. Activez l’option **"Repeat Texture"**.
5. Votre arrière-plan répétera désormais la texture pour remplir tout l’écran.

# Créer de bonnes textures pour le découpage en neuf et la mosaïque

## Pour le découpage en neuf :
- Créez des textures avec des bordures et des coins bien marqués.
- Assurez-vous que vos bordures sont nettes et ont une largeur constante.
- Testez différentes tailles de bordures pour trouver ce qui fonctionne le mieux.
- Les boutons fonctionnent généralement bien avec des bordures de 3 à 5 pixels.

## Pour la mosaïque :
- Créez des textures sans raccord visibles, capables de se connecter entre elles sur tous les côtés.
- Gardez les motifs simples pour éviter toute confusion visuelle.
- Testez votre texture en la répétant d’abord dans une petite zone.

# Exemples

## Exemple de bouton avec découpage en neuf
Un bouton simple peut commencer comme une image de 30x30 avec des bordures de 5 pixels sur tous les côtés. Lorsque vous agrandissez le bouton, les coins restent à 5x5 pixels, tandis que les bords et le centre s’étirent pour s’adapter à la taille de votre bouton.

## Exemple d’arrière-plan en mosaïque
Une petite tuile de 64x64 avec un motif discret peut être répétée pour remplir tout l’arrière-plan de votre menu, quelle que soit la taille de l’écran.

# Problèmes courants et solutions

## Mon bouton découpé en neuf est étiré ou déformé :
- Vos valeurs de bordure sont peut-être trop petites ou trop grandes
- Essayez de modifier les valeurs de bordure pour qu’elles correspondent à votre texture réelle

## Mon arrière-plan en mosaïque présente des jonctions visibles :
- Votre texture n’est pas sans raccord
- Essayez de modifier votre image pour que les bords s’alignent parfaitement

## Mes textures sont floues lorsqu’elles sont mises à l’échelle :
- Utilisez des textures de plus haute résolution
- Gardez vos conceptions simples avec des lignes nettes

# À retenir

- **Le découpage en neuf** est parfait pour les éléments d’interface qui doivent changer de taille tout en conservant leur apparence (comme les boutons).
- **La mosaïque** est idéale pour remplir de grandes zones avec un motif (comme les arrière-plans).
- Ces deux fonctionnalités aident votre interface à rester belle à n’importe quelle résolution ou taille d’écran !

À vous de créer de superbes menus Minecraft avec des boutons parfaitement étirés et de magnifiques arrière-plans en mosaïque !
