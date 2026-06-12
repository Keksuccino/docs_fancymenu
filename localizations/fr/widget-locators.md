---
title: Localisateurs de widgets
description: Ce que sont les localisateurs de widgets et comment les trouver.
---
# Localisateurs de widgets

Les localisateurs de widgets servent à pointer vers un widget Vanilla/mod spécifique (bouton, curseur, champ de saisie de texte) dans un menu, ce qui est nécessaire pour certaines fonctionnalités de FancyMenu qui doivent interagir avec un widget d’une manière ou d’une autre.

# Obtenir le localisateur d’un widget

Il existe deux façons d’obtenir le localisateur d’un widget Vanilla/mod.

La première consiste à activer la **superposition de débogage** dans le menu qui contient le widget, en appuyant sur **CTRL + ALT + D**, puis à **faire un clic droit sur le widget**, ce qui ouvrira un menu contextuel avec une option permettant de copier le localisateur dans le presse-papiers.

La seconde consiste à ouvrir l’**éditeur de disposition** du menu qui contient le widget, puis à **faire un clic droit sur l’élément du widget**, ce qui ouvrira également un menu contextuel avec une option permettant de copier le localisateur dans le presse-papiers.

>[!WARNING]
>Si vous ne pouvez **pas faire de clic droit** sur le widget via la superposition de débogage, ou s’il **n’apparaît pas** dans l’éditeur de disposition, il est probablement invisible pour FancyMenu, ce qui signifie qu’il n’a pas de localisateur dans ce cas. Cela arrive surtout pour les boutons de mods qui sont ajoutés aux menus d’une manière inhabituelle.
