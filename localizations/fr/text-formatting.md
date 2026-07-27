---
title: Formatage du texte
description: >-
  Comment formater du texte avec Markdown et les codes de formatage de
  Minecraft.
---

# Formatage du texte

Les [éléments de texte](./elements#text) prennent en charge Markdown. Les autres champs de texte utilisent le formatage Minecraft, et les libellés de boutons peuvent utiliser les composants de texte Minecraft.

# Markdown

Les **éléments de texte** de FancyMenu prennent en charge Markdown dans son intégralité, ce qui signifie que vous pouvez formater le contenu textuel en lui ajoutant des caractères spéciaux.

Par exemple, pour mettre du texte en gras, ajoutez `**` avant et après le texte en gras, donc `**Some bold text that's very bold.**` s'affichera ainsi :
**Some bold text that's very bold.**

FancyMenu prend également en charge les extensions documentées ci-dessous.

> [!CAUTION]
> Markdown fonctionne uniquement dans les **éléments de texte**. Pour les libellés de boutons et les autres champs de texte, utilisez [les codes de formatage de Minecraft](#minecraft-text-formatting).

## Polices

Vous pouvez afficher du texte dans une police personnalisée chargée via un pack de ressources en ajoutant `%!!<nom_de_police>%` avant le texte et `%!!%` après.

Une police valide incluse dans le jeu de base est `uniform`. Pour afficher du texte dans la police `uniform`, faites ceci :
`%!!uniform%this is a custom font%!!%`

Cela affichera `this is a custom font` dans la police `uniform`.

## Couleur du texte (HEX)

Il est possible d'afficher du texte dans une couleur HEX spécifique en ajoutant `%<couleur_HEX>%` avant le texte et `%#%` après.

Une couleur HEX valide pour le vert est `#77fc03`. Pour afficher du texte dans cette couleur, faites ceci :
`%#77fc03%this text is green!%#%`

Cela affichera `this text is green!` en `#77fc03` (vert).

Assurez-vous que la couleur HEX commence bien par `#` !

Les noms de couleurs courants de type HTML sont pris en charge dans le même code de formatage de couleur :

```
%#red%This text is red!%#%
```

Noms pris en charge : `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` et `transparent`.

## Alignement du texte

Vous pouvez aligner des lignes de texte en commençant une ligne par le code de formatage d’alignement spécifique, sans rien d’autre, puis les lignes de texte que vous souhaitez afficher avec cet alignement, et enfin en répétant le code d’alignement sur une ligne supplémentaire.

Tout le contenu textuel est **aligné à gauche par défaut**, il n’existe donc que des codes de formatage pour le **centré** et l’**alignement à droite**.

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

Pour afficher **une ligne de texte** comme titre (plus grand et souligné), ajoutez `# ` (très grand), `## ` (grand) ou `### ` (petit) avant la ligne de texte.

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

## Liens hypertextes

Vous pouvez ajouter des liens hypertextes au contenu textuel, qui ouvrent un site web lorsqu’on clique dessus.

Le texte à afficher comme [lien hypertexte](https://google.com) doit être entouré de `[ ]`, suivi du lien réel entouré de `( )`.

Donc, si vous voulez rendre `example text content` cliquable et ouvrir `https://example-website.net`, faites ceci :
`[example text content](https://example-website.net)`

## Événements de clic et de survol

Les événements Markdown de clic et de survol sont disponibles pour les [éléments de texte](./elements#text) et les autres textes Markdown. Utilisez [**On Markdown Text Clicked**](./listeners#on-markdown-text-clicked-text_clicked) et [**On Markdown Text Hovered**](./listeners#on-markdown-text-hovered-text_hovered) pour y réagir.

Les événements de clic utilisent le préfixe `click:` :

```
[some clickable text](click:unique_text_click_event_id)
```

Les événements de survol utilisent le préfixe `hover:` :

```
[some hoverable text](hover:unique_text_hover_event_id)
```

Les deux écouteurs exposent l’ID de l’événement sous la forme `$$text_event_id`.

## Images

Markdown prend en charge l’affichage d’images dans le contenu textuel.

FancyMenu prend en charge les ressources Minecraft, les ressources locales et les ressources web dans Markdown.

Pour ajouter une image, commencez une ligne de texte par `![](`, puis ajoutez [l’URL, l’emplacement de ressource ou le chemin vers la ressource](./resources), puis `)`.

Donc, pour afficher la ressource web `https://example-website.net/image.png`, faites ceci :
`![](https://example-website.net/image.png)`

Les images peuvent également être des **liens hypertextes** en enveloppant toute la ligne de l’image dans un **lien hypertexte** comme ceci :
`[![](https://example-website.net/image.png)](https://example-website.net)`

> [!WARNING]
> Les ressources locales doivent se trouver dans `<répertoire_du_jeu>/config/fancymenu/assets/` !

## Citation

Pour formater du texte comme une citation, commencez une ligne de texte par `> `.
Cela formatera toutes les lignes suivantes comme une citation jusqu’à ce qu’il trouve une ligne **vide**.

Exemple :
```
This will not look like a quote.

> This will look like a quote.
This will also look like a quote.

This will not look like a quote anymore.
```

## Listes à puces

Pour afficher du texte sous forme de liste à puces comme ceci :
- Entry 1
- Entry 2
  - Sub-Entry

Il vous suffit de commencer une ligne par `- `.

Exemple :
```
- Entry 1
- Entry 2
  - Sub-Entry
```

## Ligne de séparation

Pour ajouter une ligne de séparation à votre texte, de la largeur d’une ligne entière de texte, commencez simplement une ligne par `---` sans rien ajouter d’autre.

Elle ressemblera alors à ceci :

---

## Blocs de code

Les blocs de code peuvent vous aider à afficher du texte en tant que `texte brut` sans que Markdown tente de le formater, ou simplement à afficher du texte dans un style de type code sans retour automatique à la ligne.

Un bloc de code sur une seule ligne (au milieu d’un autre texte) commence et se termine par \` , ce qui est en fait assez difficile à montrer dans un texte Markdown.

Une ligne de texte contenant un bloc de code sur une seule ligne ressemble à ceci :

![single_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/e78fd38b-7b1a-4f00-9b11-797d964b3b43)

Les blocs de code multilignes enveloppent plusieurs lignes dans un grand bloc de code et commencent par une ligne ne contenant que \`\`\`, puis le contenu du texte, puis \`\`\` à nouveau :

![multi_line_code_block](https://github.com/Keksuccino/FancyMenu/assets/35544624/bf8c77eb-a97e-48cd-9270-8302c2995856) 

## Texte brut

Le code de formatage de texte brut contournera tous les autres codes de formatage qu’il contient.

Il fonctionne un peu comme les blocs de code, mais ne le formate pas comme un bloc de code. Il s’affiche plutôt comme du texte normal, mais sans aucune mise en forme.

Pour envelopper une partie de texte dans une ligne avec un code de formatage de texte brut, vous devez ajouter `;;` avant et après la partie du texte que vous souhaitez afficher en texte brut, comme ceci :

```
This is a line of text with ;;**this part**;; showing as unformatted text with visible ** (bold) formatting code and _this part_ as normal formatted italic text.
```

Le texte brut fonctionne aussi comme un code d’encadrement multilignes. Pour envelopper des lignes entières, ajoutez `;;;` avant et après la ou les lignes que vous souhaitez afficher en texte brut, comme ceci :

```
;;;
This line will show **unformatted** with visible ** (bold) formatting codes.
This line will also show _unformatted_ with visible _ (italic) formatting codes.
;;;

This line will look **normal** again with the "normal" formatted as bold text.
```

# Formatage du texte Minecraft

Les codes de formatage Minecraft fonctionnent dans les champs de texte formatés pris en charge dans FancyMenu. Utilisez `&` à la place du préfixe `§` de Minecraft ; par exemple, `&cWarning` affiche du texte rouge.

Consultez la [référence des codes de formatage du Minecraft Wiki](https://minecraft.wiki/w/Formatting_codes) pour connaître les couleurs et styles disponibles.

> [!CAUTION]
> Les codes de formatage Minecraft sont peu fiables dans les **éléments de texte**, car ces éléments analysent Markdown. Utilisez plutôt le formatage Markdown décrit ci-dessus.

# Composants de texte Minecraft (système de composants bruts)

Le système de composants de texte de Minecraft est très puissant pour le contenu textuel **sur une seule ligne**, comme les **libellés de boutons**.

Dans Minecraft Vanilla, vous pouvez l’utiliser dans les commandes `/tellraw` et `/title` (et probablement à d’autres endroits).
Il s’agit de texte formaté sérialisé en JSON, vous pouvez donc ajouter des attributs de formatage au contenu textuel.

Pour en savoir plus sur les composants de texte en détail, veuillez consulter [cette page du wiki Minecraft](https://minecraft.wiki/w/Raw_JSON_text_format).
Pour en savoir plus sur les polices dans Minecraft, consultez [cette page du wiki Minecraft](https://minecraft.wiki/w/Resource_pack#Fonts).

Pour que FancyMenu détecte un libellé de bouton comme un **composant de texte**, ne mettez rien d’autre que le texte sérialisé du composant comme libellé, comme ceci :
`{"text":"Button Label Text","font":"uniform"}`

L’exemple ci-dessus affichera le libellé du bouton `Button Label Text` dans la police `uniform`.

> [!NOTE]
> Vous pouvez utiliser les espaces réservés de FancyMenu dans la valeur `text` des composants.
