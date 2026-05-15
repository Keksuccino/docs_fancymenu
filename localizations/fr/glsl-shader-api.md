---
title: API des shaders GLSL
description: >-
  Écrivez des shaders GLSL FancyMenu pour les arrière-plans, les éléments et les
  overlays de décoration.
---

# API des shaders GLSL de FancyMenu

Ce document décrit l’environnement d’exécution GLSL utilisé par :

- le fond de menu `GLSL`
- l’élément `GLSL`
- l’overlay de décoration `GLSL`

Il couvre les modes de compilation, le routage multipasse, les uniforms pris en charge et des modèles pratiques de création de shaders.

## 1. Vue d’ensemble de l’environnement d’exécution

FancyMenu rend les shaders avec un pipeline OpenGL interne (`#version 150`) et prend en charge :

- les shaders à passe unique (`Image` uniquement)
- les shaders multipasses (`Buffer A` / `B` / `C` / `D` + `Image`)
- les points d’entrée de type Shadertoy (`mainImage`)
- les points d’entrée fragment directs (`main`)

Les sources des shaders sont des champs de texte intégrés :

- `Shader Source` (passe Image, requise pour afficher)
- `Buffer A Source` (optionnel)
- `Buffer B Source` (optionnel)
- `Buffer C Source` (optionnel)
- `Buffer D Source` (optionnel)

Si la source Image est vide, le rendu échoue avec une erreur « no source ».

## 2. Modes de compilation

FancyMenu prend en charge trois modes de compilation :

- `Auto`
- `Direct Fragment`
- `Shadertoy`

### 2.1 Mode Shadertoy

Point d’entrée attendu :

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord)
```

FancyMenu l’encapsule dans `main()` et transmet les coordonnées de la zone locale :

```glsl
mainImage(fmColor_FancyMenu, gl_FragCoord.xy - fmAreaOffset);
```

L’encapsuleur multiplie l’alpha de sortie par `fmOpacity`.

### 2.2 Mode Direct

Point d’entrée attendu :

```glsl
void main()
```

Comportement de compatibilité :

- une variante compatible avec `gl_FragColor` est tentée
- une variante sans compatibilité est aussi tentée (pour les shaders modernes avec `out vec4` explicite)

En mode direct, `fmOpacity` n’est pas appliqué automatiquement à votre sortie. Appliquez-le manuellement si nécessaire.

### 2.3 Mode Auto

Le mode Auto essaie successivement des variantes compatibles (Shadertoy/direct) et utilise la première qui compile.

## 3. Prétraitement de la source et macros intégrées

Avant la compilation, FancyMenu normalise la source :

- supprime le BOM UTF-8
- convertit CRLF/CR en LF
- supprime les lignes `#version ...`
- supprime les lignes `precision ...;`

Le préambule injecté à l’exécution inclut :

- `#version 150`
- `in vec2 fmUv_FancyMenu` (UV plein écran dans `[0,1]`, origine en bas à gauche)
- `#define iGlobalTime iTime`
- `#define texture2D texture`
- `#define textureCube texture`

Remarque :

- Si votre source déclare déjà un nom d’uniform connu (par exemple `iTime`), FancyMenu évite d’injecter une déclaration en double.
- FancyMenu essaie tout de même d’envoyer les valeurs à ce nom à l’exécution.
- `textureCube` n’est ici qu’une macro d’alias ; `iChannel0..3` sont des uniforms `sampler2D`.

## 4. Système de passes (Image + Buffer A-D)

FancyMenu dispose de 5 emplacements de passes :

- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`
- `Image` (passe finale à l’écran)

Comportement :

- les passes Buffer ne s’exécutent que si leur source n’est pas vide
- la passe Image doit être présente pour produire un rendu
- les buffers sont rendus dans des textures flottantes (`GL_RGBA16F`), puis alternés (ping-pong lecture/écriture à chaque frame)

### 4.1 Routage des canaux par passe

Chaque passe expose le routage de `iChannel0..3`. Pour chaque canal, vous pouvez sélectionner :

- `None`
- `Resource 0`
- `Resource 1`
- `Resource 2`
- `Resource 3`
- `Buffer A`
- `Buffer B`
- `Buffer C`
- `Buffer D`

Les canaux de ressource proviennent des réglages `iChannel# Resource`.

Valeurs par défaut :

- tous les routages `iChannel` sont `None` par défaut
- aucune passe buffer n’est active tant que la source de ce buffer n’est pas non vide

Important :

- Le routage vers la même passe buffer (feedback) lit les données de la frame précédente (texture de lecture ping-pong).
- Si une source routée est absente/inactive, une texture de repli est liée et `iChannelResolution[n].z` devient `0.0`.

## 5. Coordonnées et sémantique de la zone

Les shaders s’exécutent dans un rectangle de zone :

- fond de menu : zone plein écran
- élément GLSL : rectangle de l’élément

Conventions de coordonnées :

- les uniforms de pixels sont exprimés en pixels locaux à la zone
- l’origine Y est en bas à gauche pour les coordonnées de pixels visibles par le shader
- les coordonnées de la souris ne sont pas bornées ; les valeurs peuvent être hors de la zone si le curseur est à l’extérieur

Champs spéciaux :

- `fmAreaOffset` : position en pixels du coin inférieur gauche de la zone dans l’espace écran
- `fmAreaTopLeft` : position en pixels du coin supérieur gauche de la zone dans l’espace écran
- `fmAreaSize` : taille de la zone en pixels

## 6. Référence de l’API des uniforms

Tous les uniforms ci-dessous sont disponibles pour les shaders de fond et d’élément.

## 6.1 Uniforms compatibles Shadertoy

| Uniform | Type | Signification |
|---|---|---|
| `iResolution` | `vec3` | `(largeurZonePx, hauteurZonePx, 1.0)` |
| `iTime` | `float` | Temps accumulé du shader en secondes |
| `iTimeDelta` | `float` | Delta de temps du dernier rendu, affecté par le gel/l’échelle de temps |
| `iFrameRate` | `float` | FPS de secours du runtime Minecraft |
| `iFrame` | `int` | Compteur de frames du runtime |
| `iMouse` | `vec4` | Voir les détails ci-dessous |
| `iDate` | `vec4` | `(année, mois, jour, secondesDuJourAvecFraction)` |
| `iSampleRate` | `float` | Constante `44100.0` |
| `iChannelTime[4]` | `float[4]` | Actuellement tous réglés sur `iTime` |
| `iChannelResolution[4]` | `vec3[4]` | `(largeur, hauteur, indicateurValide)` par canal |
| `iChannel0..3` | `sampler2D` | Entrées de texture routées |

### Détails de `iMouse`

`iMouse = vec4(x, y, z, w)`

- `x`, `y` : position actuelle du pointeur en pixels locaux à la zone, ou comportement de maintien/gel si l’option est activée
- `z`, `w` : origine du clic gauche
  - positif pendant que le bouton gauche est maintenu
  - négatif après le relâchement

Comportement contrôlé par une option :

- `Update iMouse Position Only While Holding LMB = Off` :
  - `iMouse.xy` se met à jour en continu
- `... = On` :
  - `iMouse.xy` se met à jour uniquement lorsque LMB est enfoncé, puis reste sur la dernière position maintenue

Valeur par défaut :

- `Off` (mises à jour continues)

## 6.2 Uniforms spécifiques à FancyMenu

| Uniform | Type | Signification |
|---|---|---|
| `fmAreaOffset` | `vec2` | Décalage en pixels du coin inférieur gauche de la zone dans l’espace écran |
| `fmAreaSize` | `vec2` | Taille de la zone en pixels |
| `fmAreaPosition` | `vec2` | Identique à `fmAreaOffset` |
| `fmAreaTopLeft` | `vec2` | Décalage en pixels du coin supérieur gauche de la zone dans l’espace écran |
| `fmScreenSize` | `vec2` | Taille totale de l’écran en pixels |
| `fmGuiScale` | `float` | Échelle GUI actuelle |
| `fmMouse` | `vec4` | `(localPxX, localPxYBottom, localNormX, localNormY)` |
| `fmMouseDelta` | `vec2` | Delta de la souris en pixels de la zone (Y est inversé vers le haut du shader) |
| `fmMouseButtons` | `ivec4` | États d’appui des boutons `0..3` |
| `fmMouseClickCount` | `ivec4` | Comptes cumulés des pressions pour les boutons `0..3` |
| `fmMouseReleaseCount` | `ivec4` | Comptes cumulés des relâchements pour les boutons `0..3` |
| `fmMouseScroll` | `vec2` | Delta de défilement depuis le rendu précédent de ce runtime |
| `fmMouseScrollTotal` | `vec2` | Totaux cumulés du défilement |
| `fmKeyEvent` | `ivec4` | `(lastKeyCode, lastScanCode, lastModifiers, lastAction)` |
| `fmKeyEventCount` | `int` | Compteur cumulé d’événements clavier |
| `fmCharEvent` | `ivec4` | `(lastCodePoint, lastModifiers, 0, 0)` |
| `fmCharEventCount` | `int` | Compteur cumulé d’événements de saisie de caractères |
| `fmDateParts` | `ivec4` | `(année, mois, jour, jourDeLaSemaineIso1To7)` |
| `fmTimeParts` | `ivec4` | `(heure, minute, seconde, millisecondePartie0To999)` |
| `fmDayOfYear` | `int` | Jour de l’année |
| `fmWeekOfYear` | `int` | Semaine ISO de l’année |
| `fmUnixTimeSeconds` | `int` | Secondes depuis l’époque Unix |
| `fmUnixTimeMilliseconds` | `int` | Partie millisecondes de l’heure actuelle (`0..999`) |
| `fmPartialTick` | `float` | Tick partiel actuel |
| `fmGameDeltaTicks` | `float` | Delta de ticks de jeu Minecraft |
| `fmRealtimeDeltaTicks` | `float` | Delta de ticks en temps réel Minecraft |
| `fmInWorld` | `int` | `1` lorsqu’on est dans un monde, sinon `0` |
| `fmIsPaused` | `int` | `1` lorsque le jeu est en pause, sinon `0` |
| `fmOpacity` | `float` | Multiplicateur d’opacité effectif (`0..1`) |
| `fmVariableCount` | `int` | Quantité actuelle de variables FancyMenu |

Valeurs d’action des touches (`fmKeyEvent.w`) :

- `0` = relâchement
- `1` = pression
- `2` = répétition

## 6.3 API des uniforms de variables FancyMenu

Les variables FancyMenu sont exposées directement comme uniforms d’exécution (pour les shaders de fond, d’élément et d’overlay de décoration) sans recompilation du shader lorsque les valeurs changent.

### Nommage

Pour chaque variable `<name>`, FancyMenu expose :

- `fmVarFloat_<name>`
- `fmVarInt_<name>`
- `fmVarBool_<name>`
- `fmVarVec2_<name>`
- `fmVarVec3_<name>`
- `fmVarVec4_<name>`
- `fmVarExists_<name>` (`1` = la variable existe actuellement, `0` = absente/supprimée)

Assainissement du suffixe d’uniform pour `<name>` :

- les caractères autorisés sont `[A-Za-z0-9_]`
- tous les autres caractères sont convertis en `_`
- si le premier caractère est un chiffre, `_` est préfixé

Exemples :

- variable `player_hp` -> suffixe `player_hp`
- variable `player-hp` -> suffixe `player_hp`
- variable `2nd_phase` -> suffixe `_2nd_phase`

Important :

- ces uniforms de variables dynamiques **ne sont pas déclarés automatiquement** dans la source du shader (déclarez manuellement ceux que vous utilisez)
- évitez les noms de variables qui se nettoient vers le même suffixe, car ils sont alors associés au même nom d’uniform GLSL

### Conversion des valeurs

Pour une valeur textuelle de variable `v` :

- `fmVarFloat_*` : float analysé (`0.0` en secours)
- `fmVarInt_*` : int analysé (`0` en secours)
- `fmVarBool_*` : interprétation booléenne/int (`true/yes/on/enabled` => `1`, `false/no/off/disabled` => `0`, sinon valeur numérique non nulle => `1`)
- le parsing des vecteurs accepte les séparateurs : espace, `,`, `;`, `|`
  - `fmVarVec2_*` : les 2 premières composantes analysées
  - `fmVarVec3_*` : les 3 premières composantes analysées
  - `fmVarVec4_*` : les 4 premières composantes analysées
  - s’il y a moins de composantes, la dernière composante analysée est répétée pour les emplacements manquants
  - si aucune composante numérique n’est présente, toutes les composantes du vecteur utilisent la valeur de secours scalaire

Si une variable est supprimée :

- `fmVarExists_*` devient `0`
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

FancyMenu suit globalement les entrées et en prend un instantané à chaque rendu :

- déplacement/drag de la souris
- appui/relâchement de la souris
- défilement
- pression/relâchement/répétition des touches
- saisie de caractères

Robustesse de la souris :

- le runtime recoupe les états des boutons avec le sondage GLFW à chaque frame pour éviter les états de bouton bloqué.

Si `Pass Input Events To Shader` est désactivé :

- les uniforms d’entrée sont réinitialisés à des valeurs neutres à chaque frame
- les compteurs et événements sont remis à zéro dans les données visibles par le shader

## 8. Détails sur les entrées de texture

Les canaux de ressource (`iChannel# Resource`) attendent des textures 2D.

État de texture par canal :

- ressource valide : texture liée, vraie largeur/hauteur, `iChannelResolution[n].z = 1.0`
- absent/inactif/None : texture de repli, `iChannelResolution[n].xyz = (0,0,0)`

Textures buffer :

- format interne : `RGBA16F` (flottant)
- filtrage : linéaire
- wrap : clamp-to-edge

C’est adapté aux données multipasses (y compris des valeurs hors de `[0,1]`).

## 9. Notes sur le rendu et le blending

- Les passes Buffer sont rendues hors écran sans blending.
- La passe Image finale utilise le paramètre `Enable Blending` pour le compositing.
- L’encapsuleur Shadertoy applique automatiquement `fmOpacity` à l’alpha.
- Les shaders directs doivent appliquer `fmOpacity` manuellement si nécessaire.

## 10. Modèles pratiques

## 10.1 Shader minimal de type Shadertoy

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec3 col = vec3(uv, 0.5 + 0.5 * sin(iTime));
    fragColor = vec4(col, 1.0);
}
```

## 10.2 Shader fragment direct minimal

```glsl
out vec4 FragColor;

void main() {
    vec2 uv = gl_FragCoord.xy - fmAreaOffset;
    uv /= iResolution.xy;

    vec3 col = vec3(uv.x, uv.y, 0.5 + 0.5 * sin(iTime));
    FragColor = vec4(col, fmOpacity);
}
```

## 10.3 Multipasse de feedback minimal

### Source de Buffer A

Routage : `Buffer A iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    vec4 prev = texture(iChannel0, uv);
    vec4 seed = vec4(uv, 0.0, 1.0);
    fragColor = mix(prev, seed, 0.02);
}
```

### Source de l’Image

Routage : `Image iChannel0 Input -> Buffer A`

```glsl
void mainImage(out vec4 fragColor, in vec2 fragCoord) {
    vec2 uv = fragCoord / iResolution.xy;
    fragColor = texture(iChannel0, uv);
}
```

## 11. Liste de vérification pour le dépannage

- Pas de sortie :
  - vérifiez que la source Image n’est pas vide
  - vérifiez que le mode de compilation correspond à votre point d’entrée (`mainImage` vs `main`)
- Textures violettes/invalides :
  - vérifiez les liaisons de ressources et le routage des canaux
  - vérifiez `iChannelResolution[n].z` (`0.0` signifie invalide/indisponible)
- Mauvaises coordonnées dans un shader direct :
  - utilisez `gl_FragCoord.xy - fmAreaOffset` pour obtenir les coordonnées locales de la zone
- Comportement de drag incorrect :
  - utilisez l’option `Update iMouse Position Only While Holding LMB`
- Opacité non appliquée dans un shader direct :
  - multipliez vous-même l’alpha par `fmOpacity`
