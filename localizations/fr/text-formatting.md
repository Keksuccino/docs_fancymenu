---
title: Mise en forme du texte
description: >-
  Comment mettre en forme du texte avec Markdown, les codes de mise en forme
  Minecraft et les composants de texte.
sourceBlobSha: c6ddde5939e929b3d4c04541f0b104ee6ee795bc
---
# Mise en forme du texte

FancyMenu vous propose trois façons de mettre en forme du texte :

- **Markdown** pour les [éléments Texte et Info-bulle](/text-in-menus) : titres, listes, couleurs, images, tableaux et bien plus.
- **Les codes de mise en forme Minecraft**, comme `&c`, pour appliquer rapidement des couleurs. Ils fonctionnent dans presque tous les champs de texte, y compris les textes Markdown.
- **Les composants de texte Minecraft** pour les libellés des boutons et des curseurs.

> [!TIP]
> Cette page explique *comment écrire* du texte mis en forme. Pour apprendre à ajouter du texte à vos menus, à modifier son apparence ou à le faire défiler, consultez [Texte dans les menus](/text-in-menus).

<img width="800" alt="Markdown dans un élément Texte" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_showcase.png?raw=true">

# Markdown

Markdown met en forme le texte en utilisant quelques caractères spéciaux autour de celui-ci. Par exemple, `**gras**` devient du texte en **gras**.

Markdown fonctionne dans les [éléments Texte](/elements#text) et les [éléments Info-bulle](/elements#tooltip). Les caractères que vous écrivez déterminent *la nature* du contenu (un titre, une liste, une citation). L'[apparence](/text-in-menus#looks-and-styles) de l'élément détermine son rendu, notamment ses couleurs et ses tailles.

## Aperçu rapide

| Vous écrivez | Vous obtenez |
|---|---|
| `**gras**` ou `__gras__` | Texte en gras |
| `*italique*` ou `_italique_` | Texte en italique |
| `++souligné++` | Texte souligné |
| `~~barré~~` | Texte barré |
| `` `code` `` | Code en ligne |
| `[Ouvrir le site](https://example.com)` | Un lien cliquable |
| `%#ff5555%texte rouge%#%` | Texte coloré |
| `# Titre` | Un titre |
| `- Élément` | Une liste à puces |
| `1. Élément` | Une liste numérotée |
| `> Texte` | Une citation |
| `> [!TIP]` | Un encadré d’information |
| `---` | Une ligne de séparation |

## Styles de texte

| Style | Syntaxe |
|---|---|
| **Gras** | `**texte**` ou `__texte__` |
| **Italique** | `*texte*` ou `_texte_` |
| **Souligné** | `++texte++` |
| **Barré** | `~~texte~~` (un seul `~` de chaque côté fonctionne aussi) |

Vous pouvez combiner les styles, par exemple avec `***gras et italique***`.

Les traits de soulignement simples à l’intérieur des mots restent tels quels : `mon_layout_génial` ne devient donc pas italique. Les noms comme `C++` restent également inchangés.

> [!TIP]
> Dans l’éditeur de texte, sélectionnez du texte et appuyez sur `Ctrl + B`, `Ctrl + I` ou `Ctrl + U` (`Cmd` sur macOS) pour le mettre en gras, en italique ou le souligner. Consultez [Raccourcis de mise en forme](/text-in-menus#formatting-shortcuts).

## Couleur du texte (HEX)

Placez `%<couleur HEX>%` avant le texte et `%#%` après celui-ci :

```
%#77fc03%Ce texte est vert !%#%
```

Le code couleur HEX doit commencer par `#`. Vous pouvez également utiliser des noms de couleur :

```
%#red%Ce texte est rouge !%#%
```

Noms pris en charge : `black`, `silver`, `gray`, `grey`, `white`, `maroon`, `red`, `purple`, `fuchsia`, `magenta`, `green`, `lime`, `olive`, `yellow`, `navy`, `blue`, `teal`, `aqua`, `cyan` et `transparent`.

## Polices

Pour afficher du texte dans une autre police, placez `%!!<nom de la police>%` avant celui-ci et `%!!%` après. La police peut provenir de Minecraft ou d’un pack de ressources.

```
%!!uniform%Ce texte utilise la police uniform%!!%
```

## Alignement du texte

Par défaut, le texte est aligné à gauche. Pour centrer des lignes ou les aligner à droite, placez le code d’alignement sur sa propre ligne, avant et après celles-ci :

- `^^^` centre les lignes.
- `|||` les aligne à droite.

```
Cette ligne est alignée à gauche.

^^^
Cette ligne est centrée.
Celle-ci aussi.
^^^

|||
Cette ligne est alignée à droite.
|||
```

> [!TIP]
> Dans l’éditeur de texte, les raccourcis `Ctrl + L`, `Ctrl + E` et `Ctrl + R` (`Cmd` sur macOS) alignent les lignes sélectionnées à gauche, au centre ou à droite.

## Titres

Commencez une ligne par `# ` (le plus grand), `## ` (grand) ou `### ` (petit) :

```
# Bienvenue !
## Actualités
### Petit titre
```

## Listes

<img width="460" alt="Listes Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_lists.png?raw=true">

### Listes à puces

Commencez une ligne par `- `. Ajoutez deux espaces devant chaque niveau d’imbrication :

```
- Premier élément
- Deuxième élément
  - Élément imbriqué
    - Niveau encore plus profond
```

### Listes numérotées

Commencez une ligne par un nombre suivi d’un point ou d’une parenthèse :

```
1. Ouvrez la barre de menu
2. Cliquez sur Personnalisation
3) Cette syntaxe fonctionne aussi
```

### Marqueurs de notes de mise à jour

Les lignes peuvent également commencer par `+`, `-`, `~` ou `*`. Chacun possède son propre marqueur, ce qui est idéal pour les notes de mise à jour et les journaux des modifications :

```
+ Ajout d’un nouveau menu principal
- Suppression de l’ancien logo
~ Modification des couleurs des boutons
* Correction d’un plantage au démarrage
```

| Marqueur | Signification |
|---|---|
| `+` | Un élément a été ajouté |
| `-` | Un élément a été supprimé |
| `~` | Un élément a été modifié |
| `*` | Un élément mérite d’être mis en évidence |

Un élément `-` n’affiche le marqueur « supprimé » que si sa liste contient aussi un élément `+`. Sinon, il s’agit d’un élément normal d’une liste à puces. Vous pouvez modifier ce comportement dans **Markdown -> Lists -> Extra Markers (+ - ~ \*) -> - Marker Used**.

> [!NOTE]
> Les nouveaux éléments Texte et Info-bulle activent par défaut les listes numérotées, les marqueurs de notes de mise à jour et les [encadrés d’information](#callouts). Ces options sont désactivées dans les éléments des anciennes mises en page afin que leur texte ne change pas soudainement. Activez-les dans le menu **Markdown** de l’élément : **Lists -> Numbered Lists**, **Lists -> Extra Markers (+ - ~ \*)** et **Callouts**.

## Citations

Commencez une ligne par `> ` pour en faire une citation. Celle-ci se poursuit jusqu’à la prochaine ligne vide :

```
> Ceci est une citation.
Cette ligne en fait aussi partie.

Cette ligne redevient du texte normal.
```

Les lignes à l’intérieur d’une citation peuvent également commencer par `>`. Une ligne contenant uniquement `>` ajoute une ligne vide à la citation :

```
> Premier paragraphe de la citation.
>
> Deuxième paragraphe de la citation.
```

## Encadrés d’information

Les encadrés d’information sont des blocs colorés avec une icône et un libellé, parfaits pour afficher des conseils et des avertissements. Écrivez une citation dont la première ligne indique le type d’encadré :

```
> [!WARNING]
> N’oubliez pas d’enregistrer votre mise en page !
```

<img width="640" alt="Encadrés d’information Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_callouts.png?raw=true">

Il existe cinq types : `[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]` et `[!CAUTION]`.

## Liens hypertexte

Placez le texte entre `[ ]`, puis ajoutez le lien entre `( )` :

```
[Visitez notre site](https://example.com)
```

Les liens peuvent contenir des parenthèses, comme `https://en.wikipedia.org/wiki/Minecraft_(video_game)`. Pour afficher des crochets dans le texte du lien, placez un `\` devant ceux-ci : `[Cliquez \[ici\]](https://example.com)`.

## Événements de clic et de survol

Le texte peut également déclencher des [écouteurs](/listeners) au lieu d’ouvrir un site Web. Utilisez le préfixe `click:` ou `hover:` suivi d’un identifiant de votre choix :

```
[texte cliquable](click:unique_text_click_event_id)
[texte survolable](hover:unique_text_hover_event_id)
```

Réagissez à ces événements avec les écouteurs [**On Markdown Text Clicked**](/listeners#on-markdown-text-clicked) et [**On Markdown Text Hovered**](/listeners#on-markdown-text-hovered). Tous deux fournissent l’identifiant sous la forme `$$text_event_id`.

## Images

Placez une image sur sa propre ligne avec `![](` + la source de l’image + `)` :

```
![](https://example.com/image.png)
```

La source peut être une URL Web, un fichier local comme `/config/fancymenu/assets/image.png` ou une image d’un pack de ressources. Consultez [Ressources](/resources) pour découvrir tous les types de sources.

Le texte entre crochets devient la légende de l’image :

```
![Ma capture d’écran géniale](/config/fancymenu/assets/screenshot.png)
```

La légende s’affiche sous l’image si l’option **Markdown -> Images -> Caption** de l’élément est activée.

Pour rendre une image cliquable, placez-la dans un lien :

```
[![](https://example.com/image.png)](https://example.com)
```

## Tableaux

Séparez les cellules avec `|`. La première ligne correspond à l’en-tête et la deuxième contient `---` pour chaque colonne :

```
| Objet | Prix |
|:---|---:|
| Épée en diamant | 10 |
| Pomme dorée | 5 |
```

Les deux-points de la deuxième ligne définissent l’alignement de la colonne : `:---` à gauche, `:---:` au centre et `---:` à droite. Pour afficher un `|` dans une cellule, écrivez `\|`.

<img width="640" alt="Tableau et code Markdown" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/markdown_table_code.png?raw=true">

## Séparateurs

Une ligne contenant uniquement `---` trace un séparateur sur toute la largeur du texte.

## Code

Le code affiche le texte tel quel, sans le mettre en forme.

- **Code en ligne :** encadrez une partie de ligne avec `` ` ``, par exemple `` `/spawn` ``.
- **Blocs de code :** ajoutez une ligne contenant `` ``` `` avant et après les lignes. Les lignes des blocs de code ne sont pas renvoyées à la ligne.

````
```
/give @p minecraft:diamond 64
```
````

Vous pouvez ajouter le nom d’un langage après le premier `` ``` ``, par exemple `` ```json ``. FancyMenu l’accepte, mais cela ne change pas l’apparence du code.

Les [espaces réservés](/placeholders) sont tout de même remplacés dans le code.

## Texte brut

Le texte brut affiche les caractères de mise en forme tels quels, sans adopter l’apparence du code. Encadrez une partie de ligne avec `;;` :

```
Ceci affiche ;;**des astérisques**;; au lieu d’un texte en gras.
```

Pour appliquer ce comportement à des lignes entières, placez `;;;` sur sa propre ligne avant et après celles-ci :

```
;;;
**Pas en gras**, _pas en italique_.
;;;
```

## Caractères d’échappement

Pour afficher un caractère de mise en forme comme du texte normal, placez un `\` devant. Par exemple, `\*pas en italique\*` affiche `*pas en italique*`.

Cela fonctionne pour `\` `` ` `` `*` `_` `{` `}` `[` `]` `(` `)` `#` `+` `-` `.` `!` `|` `>` `~` et `^`.

# Mise en forme du texte Minecraft

Les codes de mise en forme Minecraft fonctionnent dans la plupart des champs de texte de FancyMenu. Utilisez `&` à la place de `§`, le caractère utilisé par Minecraft. Par exemple, `&cAvertissement` affiche du texte rouge et `&l` met le texte en gras. `&r` réinitialise la mise en forme.

Consultez le [Wiki Minecraft](https://minecraft.wiki/w/Formatting_codes) pour découvrir tous les codes.

Les codes de mise en forme fonctionnent également dans les textes Markdown, sauf à l’intérieur du code et du texte brut. Pour les styles comme le gras et l’italique, Markdown est généralement plus lisible, mais les codes sont pratiques pour appliquer rapidement des couleurs.

# Composants de texte Minecraft (système de composants bruts)

Les composants de texte Minecraft sont des textes mis en forme au format JSON. Ils fonctionnent pour les textes **sur une seule ligne**, comme les **libellés des boutons et des curseurs**, mais pas dans les éléments Texte.

Pour en utiliser un, définissez le composant comme seul contenu du libellé :

```
{"text":"Texte du libellé du bouton","font":"uniform"}
```

Le texte `Texte du libellé du bouton` s’affiche avec la police `uniform`. Vous pouvez utiliser des [espaces réservés](/placeholders) dans la valeur `text`.

Pour en savoir plus, consultez les pages du Wiki Minecraft consacrées au [format des composants de texte](https://minecraft.wiki/w/Raw_JSON_text_format) et aux [polices](https://minecraft.wiki/w/Resource_pack#Fonts).
