---
title: API des shaders GLSL
description: >-
  Écrivez des shaders GLSL FancyMenu pour les arrière-plans, les éléments et les
  superpositions décoratives.
sourceBlobSha: f3da9c3fe83444dab5c59f74f5011e2d6e8cf9e6
---

# API des shaders GLSL FancyMenu

Ce document décrit l’environnement d’exécution GLSL utilisé par FancyMenu pour les éléments suivants :

- arrière-plan de menu `GLSL`
- élément `GLSL`
- superposition décorative `GLSL`

Il présente les modes de compilation, le routage multipasse, les uniformes pris en charge et des modèles pratiques pour écrire des shaders.

## 1. Présentation de l’environnement d’exécution

FancyMenu effectue le rendu des shaders à l’aide d’un pipeline OpenGL interne (`#version 150`) et prend en charge :

- les shaders à passe unique (passe `Image` uniquement)
- les shaders multipasses (`Buffer A` / `B` / `C` / `D` + `Image`)
- les points d’entrée de type Shadertoy (`mainImage`)
- les points d’entrée directs de fragment (`main`)

Les sources des shaders sont des champs de texte intégrés :

- `Shader Source` (passe Image, nécessaire au rendu)
- `Buffer A Source` (facultatif)
- `Buffer B Source` (facultatif)
- `Buffer C Source` (facultatif)
- `Buffer D Source` (facultatif)

Si la source Image est vide, le rendu échoue avec une erreur « no source ».

## 2. Modes de compilation

FancyMenu prend en charge trois modes de compilation :

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Mode Shadertoy

Point d’entrée attendu :

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu l’enveloppe dans `main()` et lui transmet les coordonnées locales de la zone :

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

L’enveloppe multiplie l’alpha de sortie par `fmOpacity`.

### 2.2 Mode direct

Point d’entrée attendu :

```glsl
void main()
```

Comportement de compatibilité :

- Une variante de compatibilité `gl_FragColor` est essayée.
- Une variante sans compatibilité est également essayée (pour les shaders modernes utilisant une sortie explicite `out vec4`).

En mode direct, `fmOpacity` n’est pas appliqué automatiquement à votre sortie. Appliquez-le manuellement si nécessaire.

### 2.3 Mode Auto

Le mode Auto essaie les variantes compatibles dans l’ordre (Shadertoy/direct) et utilise la première qui compile.

## 3. Prétraitement des sources et macros intégrées

Avant la compilation, FancyMenu normalise la source :

- supprime le BOM UTF-8
- convertit les fins de ligne CRLF/CR en LF
- supprime les lignes `#version ...`
- supprime les lignes `precision ...;`

Le préambule injecté à l’exécution comprend :

- `#version 150`
- `in vec2 fmUv_FancyMenu` (coordonnées UV plein écran dans `[0,1]`, origine en bas à gauche)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Remarque :

- Si votre source déclare déjà un nom d’uniforme connu (par exemple `iTime`), FancyMenu évite d’injecter une déclaration en double.
- FancyMenu tente tout de même de téléverser des valeurs pour ce nom à l’exécution.
- `textureCube` n’est ici qu’une macro alias ; `iChannel0..3` sont des uniformes `sampler2D`.

## 4. Système de passes (Image + Buffer A-D)

FancyMenu dispose de 5 emplacements de passe :

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (passe finale affichée à l’écran)

Comportement :

- Les passes Buffer ne sont exécutées que si leur source n’est pas vide.
- La passe Image doit être présente pour produire un rendu.
- Les buffers sont rendus dans des textures à virgule flottante (`GL_RGBA16F`), puis utilisés en ping-pong (échange des textures de lecture et d’écriture à chaque frame).

### 4.1 Routage des canaux par passe

Chaque passe expose le routage de `iChannel0..3`. Pour chaque canal, vous pouvez sélectionner :

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Les canaux Resource proviennent des paramètres `iChannel# Resource`.

Valeurs par défaut :

- tous les routages `iChannel` sont définis par défaut sur `None`
- aucune passe Buffer n’est active tant que sa source n’est pas vide

Important :

- Le routage vers une même passe Buffer (rétroaction) lit les données de la frame précédente (texture de lecture ping-pong).
- Si une source routée est manquante ou inactive, une texture de secours est liée et `iChannelResolution[n].z` prend la valeur `0.0`.

## 5. Coordonnées et sémantique des zones

Les shaders s’exécutent dans une zone rectangulaire :

- arrière-plan de menu : zone couvrant tout l’écran
- élément GLSL : rectangle de l’élément

Conventions de coordonnées :

- Les uniformes de pixels sont exprimés en pixels locaux à la zone.
- Pour les coordonnées en pixels utilisées par le shader, l’origine en Y est en bas à gauche.
- Les coordonnées de la souris ne sont pas limitées ; elles peuvent se trouver hors de la zone si le curseur est à l’extérieur.

Champs spéciaux :

- `fmAreaOffset` : position du coin inférieur gauche de la zone dans l’espace de pixels de l’écran
- `fmAreaTopLeft` : position du coin supérieur gauche de la zone dans l’espace de pixels de l’écran
- `fmAreaSize` : dimensions de la zone en pixels

## 6. Référence de l’API des uniformes

Tous les uniformes ci-dessous sont disponibles pour les shaders d’arrière-plan et d’élément.

## 6.1 Uniformes compatibles avec Shadertoy

| Uniforme | Type | Signification |
|---|---|---|
| `iResolution` | `vec3` | `(areaWidthPx, areaHeightPx, 1.0)` |
| `iTime` | `float` | Temps cumulé du shader en secondes |
| `iTimeDelta` | `float` | Intervalle depuis le dernier rendu, affecté par le gel et l’échelle temporelle |
| `iFrameRate` | `float` | FPS du jeu Minecraft, utilisés comme FPS de secours à l’exécution |
| `iFrame` | `int` | Compteur de frames par environnement d’exécution |
| `iMouse` | `vec4` | Voir les détails ci-dessous |
| `iDate` | `vec4` | `(année, mois, jour, secondes de la journée avec fraction)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Toutes les valeurs sont actuellement définies sur `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(largeur, hauteur, indicateur de validité)` pour chaque canal |
| `iChannel0..3` | `sampler2D` | Textures d’entrée routées |

### Détails sur `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y` : position actuelle de la souris en pixels locaux à la zone, ou position maintenue/figée si l’option correspondante est activée
- `z`, `w` : origine du clic gauche
  - valeur positive tant que le bouton gauche de la souris est maintenu
  - valeur négative après son relâchement

Comportement contrôlé par l’option :

- `Update iMouse Position Only While Holding LMB = Off` :
  - `iMouse.xy` est mis à jour en continu
- `... = On` :
  - `iMouse.xy` n’est mis à jour que lorsque le bouton gauche est enfoncé, puis conserve la dernière position maintenue

Valeur par défaut :

- `Off` (mise à jour continue)

## 6.2 Uniformes propres à FancyMenu

| Uniforme | Type | Signification |
|---|---|---|
| `fmAreaOffset` | `vec2` | Décalage en pixels du coin inférieur gauche de la zone dans l’espace écran |
| `fmAreaSize` | `vec2` | Dimensions de la zone en pixels |
| `fmAreaPosition` | `vec2` | Identique à `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Décalage en pixels du coin supérieur gauche de la zone dans l’espace écran |
| `fmScreenSize` | `vec2` | Dimensions complètes de l’écran en pixels |
| `fmGuiScale` | `float` | Échelle actuelle de l’interface |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Déplacement de la souris en pixels dans la zone (Y est inversé pour pointer vers le haut dans le shader) |
| `fmMouseButtons` | `ivec4` | État enfoncé des boutons `0..3` |
| `fmMouseClickCount` | `ivec4` | Nombre cumulé d’appuis sur les boutons `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Nombre cumulé de relâchements des boutons `0..3` |
| `fmMouseScroll` | `vec2` | Déplacement de la molette depuis le rendu précédent de cet environnement d’exécution |
| `fmMouseScrollTotal` | `vec2` | Déplacement total cumulé de la molette |
| `fmKeyEvent` | `ivec4` | `(dernier code de touche, dernier code de balayage, derniers modificateurs, dernière action)` |
| `fmKeyEventCount` | `int` | Compteur cumulé d’événements clavier |
| `fmCharEvent` | `ivec4` | `(dernier point de code, derniers modificateurs, 0, 0)` |
| `fmCharEventCount` | `int` | Compteur cumulé d’événements de saisie de caractères |
| `fmDateParts` | `ivec4` | `(année, mois, jour, jour de la semaine ISO de 1 à 7)` |
| `fmTimeParts` | `ivec4` | `(heure, minute, seconde, millisecondes de 0 à 999)` |
| `fmDayOfYear` | `int` | Jour de l’année |
| `fmWeekOfYear` | `int` | Semaine ISO de l’année |
| `fmUnixTimeSeconds` | `int` | Secondes depuis l’époque Unix |
| `fmUnixTimeMilliseconds` | `int` | Partie en millisecondes de l’heure actuelle (`0..999`) |
| `fmPartialTick` | `float` | Tick partiel actuel |
| `fmGameDeltaTicks` | `float` | Ticks d’intervalle du jeu Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Ticks d’intervalle en temps réel de Minecraft |
| `fmInWorld` | `int` | `1` si le joueur est dans un monde, sinon `0` |
| `fmIsPaused` | `int` | `1` si le jeu est en pause, sinon `0` |
| `fmOpacity` | `float` | Multiplicateur d’opacité effectif (`0..1`) |
| `fmVariableCount` | `int` | Nombre actuel de variables FancyMenu |

Valeurs des actions clavier (`fmKeyEvent.w`) :

- `0` = relâchement
- `1` = appui
- `2` = répétition

## 6.3 API des uniformes de variables FancyMenu

Les variables FancyMenu sont exposées directement sous forme d’uniformes à l’exécution (pour les shaders d’arrière-plan, d’élément et de superposition décorative), sans recompilation des shaders lorsque leurs valeurs changent.

### Nommage

Pour chaque variable `<name>`, FancyMenu expose :

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = la variable existe actuellement, `0` = absente ou supprimée)

Normalisation du suffixe d’uniforme pour `<name>` :

- les caractères autorisés sont `[A-Za-z0-9_]`
- tous les autres caractères sont remplacés par `_`
- si le premier caractère est un chiffre, `_` est ajouté devant

Exemples :

- variable `player_hp` -> suffixe `player_hp`
- variable `player-hp` -> suffixe `player_hp`
- variable `2nd_phase` -> suffixe `_2nd_phase`

Important :

- ces uniformes de variables dynamiques ne sont **pas déclarés automatiquement** dans la source du shader (déclarez manuellement ceux que vous utilisez)
- évitez les noms de variables qui donnent le même suffixe après normalisation, car ils correspondent au même nom d’uniforme GLSL

### Conversion des valeurs

Pour une valeur textuelle de variable `v` :

- `fmVarFloat_*` : valeur flottante analysée (`0.0` par défaut en cas d’échec)
- `fmVarInt_*` : valeur entière analysée (`0` par défaut en cas d’échec)
- `fmVarBool_*` : interprétation booléenne/entière (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, sinon valeur numérique non nulle => `1`)
- l’analyse des vecteurs accepte les séparateurs suivants : espaces, `,`, `;`, `|`
  - `fmVarVec2_*` : les 2 premières composantes analysées
  - `fmVarVec3_*` : les 3 premières composantes analysées
  - `fmVarVec4_*` : les 4 premières composantes analysées
  - si le nombre de composantes est insuffisant, la dernière composante analysée est répétée pour les emplacements manquants
  - si aucune composante numérique n’est présente, toutes les composantes du vecteur utilisent la valeur scalaire par défaut

Les [variables de liste](/variables#text-and-list-variables) renvoient leur nombre d’entrées plutôt que leur texte :

- `fmVarFloat_*` et `fmVarInt_*` : nombre d’entrées, par exemple `3` pour une liste de 3 entrées
- `fmVarBool_*` : `1` si la liste contient des entrées, `0` si elle est vide
- `fmVarVec2_*`, `fmVarVec3_*` et `fmVarVec4_*` : nombre d’entrées dans chaque composante

Si une variable est supprimée :

- `fmVarExists_*` prend la valeur `0`
- toutes les valeurs correspondantes `fmVar*_*` sont réinitialisées à `0`

### Exemple de déclaration et d’utilisation

```glsl
uniform float fmVarFloat_player_hp;
uniform int fmVarBool_is_boss_phase;
uniform vec3 fmVarVec3_theme_color;
uniform int fmVarExists_player_hp;

void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;

    float hp = clamp(fmVarFloat_player_hp / 100.0, 0.0, 1.0);
    vec3 theme = fmVarVec3_theme_color;
    float boss = float(fmVarBool_is_boss_phase);

    vec3 col = mix(theme * 0.25, theme, hp);
    col += vec3(0.2, 0.0, 0.0) * boss;

    if (fmVarExists_player_hp == 0) {
        col = vec3(0.15);
    }

    fragColor = vec4(col, 1.0);
}
```

## 7. Modèle de suivi des entrées

FancyMenu suit les entrées globalement et en prend un instantané pour chaque rendu :

- déplacement/glissement de la souris
- appui/relâchement de la souris
- défilement
- appui/relâchement/répétition des touches
- saisie de caractères

Fiabilité de la souris :

- L’environnement d’exécution compare chaque frame l’état des boutons avec les données de GLFW afin d’éviter qu’un bouton reste bloqué.

Si l’option `Pass Input Events To Shader` est désactivée :

- les uniformes d’entrée sont réinitialisés à des valeurs neutres à chaque frame
- les compteurs et événements sont mis à zéro dans les données visibles par le shader

## 8. Détails sur les entrées de texture

Les canaux Resource (`iChannel# Resource`) attendent des textures 2D.

État de la texture pour chaque canal :

- ressource valide : texture liée, largeur/hauteur réelles, `iChannelResolution[n].z = 1.0`
- ressource manquante ou inactive, ou valeur None : texture de secours, `iChannelResolution[n].xyz = (0,0,0)`

Textures Buffer :

- format interne : `RGBA16F` (virgule flottante)
- filtrage : linéaire
- mode de répétition : clamp-to-edge

Ce format convient aux données multipasses (y compris aux valeurs hors de l’intervalle `[0,1]`).

## 9. Remarques sur le rendu et le mélange

- Les passes Buffer sont rendues hors écran, sans mélange.
- La passe Image finale utilise le paramètre `Enable Blending` pour la composition.
- L’enveloppe Shadertoy applique automatiquement `fmOpacity` à l’alpha.
- Les shaders directs doivent appliquer manuellement `fmOpacity` si nécessaire.

## 10. Modèles pratiques

## 10.1 Shader minimal de type Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Shader de fragment direct minimal

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Multipasse minimal avec rétroaction

### Source Buffer A

Routage : `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Source Image

Routage : `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Liste de vérification pour le dépannage

- Aucun rendu :
  - vérifiez que la source Image n’est pas vide
  - vérifiez que le mode de compilation correspond au point d’entrée (`mainImage` ou `main`)
- Textures violettes ou invalides :
  - vérifiez les liaisons de ressources et le routage des canaux
  - vérifiez `iChannelResolution[n].z` (`0.0` signifie que la ressource est invalide ou indisponible)
- Coordonnées incorrectes dans un shader direct :
  - utilisez `gl_FragCoord.xy - fmAreaOffset` pour obtenir les coordonnées locales à la zone
- Comportement de glissement incorrect :
  - utilisez l’option `Update iMouse Position Only While Holding LMB`
- Opacité non appliquée dans un shader direct :
  - multipliez vous-même l’alpha par `fmOpacity`
