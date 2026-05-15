---
title: Formatage du texte
description: >-
  Comment formater du texte avec Markdown et les codes de formatage de
  Minecraft.
---

# Formatage du texte

FancyMenu propose de nombreuses fonctionnalités pour rendre le contenu textuel des interfaces *plus élégant* !

Les éléments de texte prennent en charge **Markdown** avec quelques ajouts intéressants, et la plupart des autres contenus textuels prennent en charge le système de **formatage de texte de Minecraft**. Même les libellés des boutons prennent en charge les **composants de texte Minecraft**, ce qui vous permet d’utiliser des polices personnalisées et bien plus encore.

# Markdown

Les **éléments de texte** de FancyMenu prennent entièrement en charge Markdown, ce qui signifie que vous pouvez formater du texte en y ajoutant des caractères spéciaux.

Par exemple, pour mettre du texte en gras, ajoutez `**` avant et après le texte en gras ; ainsi `**Some bold text that's very bold.**` s’affichera comme ceci :
**Some bold text that's very bold.**

Le Markdown de FancyMenu a même quelques fonctions spéciales qui le rendent encore plus puissant !

> Markdown ne **FONCTIONNE PAS** pour les autres contenus textuels, comme les libellés des boutons. Il fonctionne uniquement pour les **ÉLÉMENTS DE TEXTE**. Pour tout le reste, veuillez utiliser [les codes de formatage de Minecraft](/text-formatting#minecraft-text-formatting).
{.is-danger}

## Polices

Vous pouvez afficher du texte avec une police personnalisée chargée via un pack de ressources en ajoutant `%!!<font_name>%` avant le texte et `%!!%` après.

Une police valide incluse dans le jeu de base est `uniform`. Pour afficher du texte avec la police `uniform`, faites ceci :
`%!!uniform%this is a custom font%!!%`

Cela affichera `this is a custom font` dans la police `uniform`.

## Couleur du texte (HEX)

Il est possible d’afficher du texte dans une couleur HEX spécifique en ajoutant `%<HEX_color>%` avant le texte et `%#%` après.

Une couleur HEX valide pour le vert est `#77fc03`. Pour afficher du texte dans cette couleur, faites ceci :
`%#77fc03%this text is green!%#%`

Cela affichera `this text is green!` en `#77fc03` (vert).

Assurez-vous que la couleur HEX commence bien par `#` !

FancyMenu 3.9.0 prend également en charge des noms de couleurs courants de type HTML avec ce même code de formatage de couleur :

```
%#red%This text is red!%#%
```

Noms pris en charge : `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` et `transparent`.

## Alignement du texte

Vous pouvez aligner des lignes de texte en commençant une ligne par le code de formatage d’alignement correspondant, puis rien d’autre, puis les lignes de texte que vous souhaitez afficher avec cet alignement, puis de nouveau le code d’alignement sur une ligne supplémentaire.

Tout le contenu textuel est **aligné à gauche par défaut** ; il n’existe donc des codes de formatage que pour le **centrage** et l’**alignement à droite**.

### Centré

Pour centrer des lignes de texte, utilisez le code de formatage `^^^`.

Exemple :
```
This text is not centered.

^^^
This text is centered.
This text is also centered.
^^^

This text is not centered anymore.
```

### Aligné à droite

Pour afficher des lignes de texte alignées à droite, utilisez le code de formatage `|||`.

Exemple :
```
This text is not right-aligned.

|||
This text is right-aligned.
This text is also right-aligned.
|||

This text is not right-aligned anymore.
```

## Titres

Pour afficher **une ligne de texte** sous forme de titre (plus grande et soulignée), ajoutez `# ` (très grand), `## ` (grand) ou `### ` (petit) avant la ligne de texte.

Exemple :
`## Big Headline`

## Gras

Ajoutez `**` avant et après le texte pour le mettre en **gras**.

Exemple :
`**bold text content**`

## Italique

Ajoutez `_` OU `*` avant et après le texte pour le mettre en *italique*.

Exemple :
`*italic text content*`

## Barré

Ajoutez `~` avant et après le texte pour le rendre ~~barré~~.

Exemple :
`~strikethrough text content~`

## Hyperliens

Vous pouvez ajouter des hyperliens à du texte, qui ouvriront un site web lorsqu’on clique dessus.

Le texte qui doit apparaître comme [hyperlien](https://google.com) doit être entouré de `[ ]`, suivi du lien réel entouré de `( )`.

Donc si vous voulez rendre `example text content` cliquable et ouvrir `https://example-website.net`, faites ceci :
`[example text content](https://example-website.net)`

## Événements au clic et au survol

FancyMenu 3.9.0 ajoute des événements Markdown de clic et de survol pour les éléments de texte et les autres textes Markdown.

Les événements de clic utilisent le préfixe `click:` :

```
[some clickable text](click:unique_text_click_event_id)
```

Les événements de survol utilisent le préfixe `hover:` :

```
[some hoverable text](hover:unique_text_hover_event_id)
```

Utilisez les écouteurs **On Markdown Text Clicked** et **On Markdown Text Hovered** pour réagir à ces événements. Les deux écouteurs exposent l’identifiant de l’événement via `$$text_event_id`.

## Images

Markdown prend en charge l’affichage d’images dans le contenu textuel.

FancyMenu prend en charge les ressources Minecraft, les ressources locales et les ressources web dans Markdown.

Pour ajouter une image, commencez une ligne de texte par `![](`, puis indiquez [l’URL, l’emplacement de ressource ou le chemin vers la ressource](/resources), puis `)`.

Par exemple, pour afficher la ressource web `https://example-website.net/image.png`, faites ceci :
`![](https://example-website.net/image.png)`

Les images peuvent aussi être des **hyperliens** en entourant toute la ligne d’image dans un **hyperlien** comme ceci :
`[![](https://example-website.net/image.png)](https://example-website.net)`

> Les ressources locales doivent se trouver dans `/config/fancymenu/assets/` !
{.is-warning}

## Citation

Pour formater du texte en citation, commencez une ligne par `> `.
Cela formatte toutes les lignes suivantes comme une citation jusqu’à ce qu’une ligne **vide** soit rencontrée.

Exemple :
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## Listes à puces

Pour afficher du texte sous forme de liste à puces comme ceci :
- Entrée 1
- Entrée 2
  - Sous-entrée

Il suffit de commencer une ligne par `- `.

Exemple :
```
- Entrée 1
- Entrée 2
  - Sous-entrée
```

## Ligne de séparation

Pour ajouter une ligne de séparation à votre texte, sur toute la largeur d’une ligne, commencez simplement une ligne par `---` sans rien ajouter d’autre.

Elle ressemblera alors à ceci :

---

## Blocs de code

Les blocs de code peuvent vous aider à afficher du texte en `texte brut` sans que Markdown essaie de le formater, ou simplement à l’afficher dans un style de type code sans retour automatique à la ligne.

Un bloc de code sur une seule ligne (entre deux morceaux de texte) commence et se termine par \` , ce qui est en fait vraiment difficile à montrer dans du texte Markdown…

Une ligne de texte contenant un bloc de code sur une seule ligne ressemble à ceci :

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Les blocs de code multilignes regroupent plusieurs lignes dans un grand bloc de code et commencent par une ligne contenant uniquement \`\`\`, puis le contenu du texte, puis à nouveau \`\`\` :

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texte brut

Le code de formatage de texte brut contourne tous les autres codes de formatage qu’il contient.

Il fonctionne un peu comme les blocs de code, mais il ne le formate pas comme un bloc de code. À la place, il s’affiche comme du texte normal, mais sans aucun formatage.

Pour entourer une partie de texte dans une ligne avec un code de formatage de texte brut, vous devez ajouter `;;` avant et après la partie de texte que vous voulez afficher en texte brut, comme ceci :

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

Le texte brut fonctionne aussi comme un code d’encadrement multilignes. Pour entourer des lignes entières, ajoutez `;;;` avant et après la ou les lignes que vous voulez afficher en texte brut, comme ceci :

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Formatage du texte Minecraft

Minecraft dispose lui-même d’un système de formatage assez efficace, similaire à Markdown, dans lequel vous ajoutez des caractères spéciaux à votre texte pour le formater.

Pour en savoir plus sur le système de formatage de Minecraft, veuillez consulter [cette page du wiki Minecraft](https://minecraft.wiki/w/Formatting_codes).

> Le wiki indiquera que le préfixe du code de formatage est `§`, mais dans FancyMenu vous devez le remplacer par `&`. Le reste ne change pas.
{.is-warning}

> Les **éléments de texte** sont très complexes et, pour prendre en charge Markdown, le compromis a été de **casser les codes de formatage Vanilla de Minecraft** ; ces codes ne fonctionneront donc pas bien dans les éléments de texte (seul le premier mot sera formaté après le code de formatage, etc.). Vous devriez plutôt utiliser les codes de formatage Markdown dans les éléments de texte.
{.is-danger}

# Composants de texte Minecraft (système de composants bruts)

Le système de composants de texte de Minecraft est très puissant pour le contenu textuel **sur une seule ligne**, comme les **libellés de boutons**.

Dans le Minecraft Vanilla, vous pouvez l’utiliser dans les commandes `/tellraw` et `/title` (et probablement à d’autres endroits).
Il s’agit de texte formaté sérialisé en JSON, ce qui vous permet d’ajouter des attributs de formatage au contenu textuel.

Pour en savoir plus sur les composants de texte en détail, veuillez consulter [cette page du wiki Minecraft](https://minecraft.wiki/w/Raw_JSON_text_format).
Pour en savoir plus sur les polices dans Minecraft, consultez [cette page du wiki Minecraft](https://minecraft.wiki/w/Resource_pack#Fonts).

Pour faire reconnaître à FancyMenu un libellé de bouton comme un **composant de texte**, ne mettez rien d’autre que le texte sérialisé du composant comme libellé, comme ceci :
`{"text":"Button Label Text","font":"uniform"}`

L’exemple ci-dessus affichera le libellé du bouton `Button Label Text` dans la police `uniform`.

> Vous pouvez utiliser les espaces réservés de FancyMenu dans la valeur `text` des composants.
{.is-info}
