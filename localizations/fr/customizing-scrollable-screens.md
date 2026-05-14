---
title: Écrans défilants
description: Comment personnaliser les écrans défilants.
---

# Personnalisation des écrans défilants

Personnaliser des écrans défilants comme les écrans d’options peut être un peu délicat, car FancyMenu ne peut pas « voir » ni personnaliser le contenu à l’intérieur des zones de défilement.

Depuis FancyMenu v3.6.0+, il est possible de rendre CERTAINS de ces écrans personnalisables en exposant automatiquement les widgets à l’intérieur des zones de défilement d’un écran spécifique. C’est très puissant, mais aussi assez expérimental, donc cela ne fonctionnera pas sur tous les écrans.

Pour activer la fonction d’exposition pour un écran spécifique, cliquez sur **menu bar -> Customization -> Expose Scroll Area Content Of Current Screen**. Il n’est pas possible d’activer cette fonction pour tous les écrans en même temps, et certains écrans ne vous permettront pas de l’activer du tout, comme les menus Solo et Multijoueur.

L’activation de cette fonction empilera tous les widgets trouvés dans les zones de défilement dans le coin supérieur gauche de l’écran. C’est voulu et ce n’est pas un bug. Vous pouvez ensuite ouvrir une disposition **pour l’écran actuel** et devriez pouvoir voir et modifier (déplacer, redimensionner, etc.) ces widgets dans l’éditeur.

La chose la plus importante à garder à l’esprit lors de l’utilisation de cette fonction est que l’exposition des widgets de la zone de défilement SUPPRIMERA la zone de défilement originale de l’écran, et tout ce qui se trouve à l’intérieur de la zone de défilement et qui n’est pas un widget normal (les widgets sont des boutons et des curseurs) sera PERDU ; il ne sera donc pas visible ni interactif tant que la fonction d’exposition est activée.
