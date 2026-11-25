---
title: Menühintergründe
description: >-
  Gib einem Menü einen eigenen Hintergrund – zum Beispiel ein Bild, ein
  Panorama, ein Video, eine Farbe oder einen Shader – und lege mehrere
  übereinander.
sourceBlobSha: 934e0cbcce41f049826fcd7b96715e3cb0e27214
---

# Menühintergründe

Ein Layout kann seinem Bildschirm einen eigenen Hintergrund geben: ein Bild, eine Animation, ein Panorama, eine Diashow, ein Video, eine Farbe, eine Website oder einen Shader. Er ersetzt den normalen Hintergrund des Bildschirms, etwa das Panorama des Titelbildschirms, die Unschärfe anderer Menüs oder die Welt hinter dem Pausenmenü.

<img width="800" alt="Der Titelbildschirm mit einem Pixel-Art-Hintergrund eines verschneiten Tals bei Nacht, mit Polarlicht, Vollmond und einer Hütte mit beleuchteten Fenstern" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_hero.png?raw=true">

> [!TIP]
> Um allen Menüs denselben Hintergrund zu geben, ohne Layouts zu erstellen, verwende [Globale Anpassungen](/global-customizations#menu-backgrounds).

# Einen Hintergrund festlegen

<img width="800" alt="Ein Rechtsklick auf den Editorhintergrund des Titelbildschirms öffnet Menühintergründe und Bild. Hintergrund anzeigen wird aktiviert und über Bild auswählen ein Bild festgelegt" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_image.gif?raw=true">

1. Öffne ein Layout des Bildschirms im [Layout-Editor](/layout-editor).
2. Klicke mit der rechten Maustaste auf den Editorhintergrund und öffne **Menühintergründe**. Du findest die Option auch unter **Menüleiste -> Layout -> Layouteigenschaften**.
3. Öffne einen Hintergrundtyp, zum Beispiel **Bild**.
4. Klicke auf **Hintergrund anzeigen**, um die Option auf **Aktiviert** zu setzen.
5. Richte den Hintergrund ein, zum Beispiel über **Bild auswählen** für einen Bildhintergrund.

<img width="800" alt="Das Menü Menühintergründe mit einem Häkchen vor Bild und einem Kreuz vor allen anderen Typen sowie den Einstellungen für alle Hintergründe darunter" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_menu.png?raw=true">

Im Menü **Menühintergründe** steht vor jedem aktivierten Typ ein ✔ und vor jedem deaktivierten Typ ein ✖. Fahre mit der Maus über einen Typ, um zu sehen, was er bewirkt.

Um den normalen Hintergrund des Bildschirms wiederherzustellen, setze **Hintergrund anzeigen** für den jeweiligen Typ wieder auf **Deaktiviert**. Die Einstellungen bleiben erhalten, sodass du den Hintergrund später wieder aktivieren kannst.

# Hintergrundtypen

## Bild

Ein Bild aus deinen Dateien, von einer Website oder aus den Ressourcen des Spiels, das über den ganzen Bildschirm gestreckt wird. Auch animierte Bilder werden abgespielt. Eine Liste der unterstützten Dateien findest du unter [Bilder](/images).

- **Bild auswählen**: das Bild. Mögliche Quellen: [Ressourcen](/resources).
- **Ersatzbild auswählen**: wird angezeigt, solange das Bild nicht geladen werden kann, zum Beispiel ein Webbild, wenn du offline bist.
- **Animierte Texturen beim Öffnen des Bildschirms neu starten**: startet ein [animiertes Bild](/animations) bei jedem Öffnen des Bildschirms von vorn. Andernfalls wird die Wiedergabe an der Stelle fortgesetzt, an der sie zuvor war.
- **Textur wiederholen**: kachelt das Bild über den Bildschirm, statt es zu strecken. Siehe [Neunerteilung und Kachelung](/nine-slicing-and-tiling).
- **Breite Bilder von links nach rechts verschieben**: ein breites Bild, zum Beispiel ein Foto einer ganzen Landschaft, füllt die Bildschirmhöhe aus und gleitet langsam von einer Seite zur anderen. An jedem Ende hält es kurz an.
- **Parallax-Effekt** und die zugehörigen Einstellungen: Das Bild bewegt sich leicht mit der Maus. Siehe [Parallax-Effekt](/parallax#menu-backgrounds).

**Breite Bilder von links nach rechts verschieben** kann nicht gleichzeitig mit **Textur wiederholen** oder **Parallax-Effekt** aktiviert sein.

## Farbe

Eine Farbe über den ganzen Bildschirm.

- **Farbe [HEX]**: die Farbe, zum Beispiel `#1B2440`. Mit zwei zusätzlichen Ziffern wird sie transparent, zum Beispiel `#1B2440C8`. Hier kann auch ein [Platzhalter](/placeholders) verwendet werden.

Die Farbe liegt unter allen anderen Hintergründen des Layouts und füllt daher deren transparente Bereiche aus. Siehe [Hintergründe übereinanderlegen](#hintergründe-übereinanderlegen).

## Kugelpanorama

Ein Panorama, das sich langsam dreht, wie das des Titelbildschirms. Panoramen erstellst du in `config/fancymenu/panoramas/`. Siehe [Panoramen](/panoramas).

- **Panoramaname**: öffnet **Panorama auswählen**, wo du eines deiner Panoramen auswählen und eine Vorschau davon ansehen kannst.
- **Panorama entfernen**: entfernt das Panorama.

Ohne Panorama zeigt der Hintergrund die violette und schwarze fehlende Textur von Minecraft.

## Diashow

Zeigt nacheinander die Bilder einer Diashow an. Diashows erstellst du in `config/fancymenu/slideshows/`. Siehe [Diashows](/slideshows).

- **Name der Diashow**: öffnet **Diashow auswählen**, wo du eine deiner Diashows auswählen kannst.
- **Diashow entfernen**: entfernt die Diashow.

Ohne Diashow zeigt der Hintergrund ebenfalls die fehlende Textur von Minecraft.

## Video

Spielt ein Video aus deinen Dateien, von einer Website oder aus den Ressourcen des Spiels ab. Dafür wird Watermedia benötigt. Siehe [Videos](/video#requirements). Ohne Watermedia wird im Hintergrund ein Hinweis mit Downloadlinks angezeigt.

- **Videoquelle**: das Video.
- **Video wiederholen**, **Lautstärke** und **Tonkanal**: legen fest, wie das Video abgespielt wird.
- **Parallax-Effekt** und die zugehörigen Einstellungen: wie bei Bildhintergründen.
- **Video im Layout-Editor abspielen**: ist die Option deaktiviert, bleibt das Video im Layout-Editor pausiert.

Mit [Aktionen](/video) kannst du das Video pausieren und seine Lautstärke sowie Wiedergabezeit ändern. Dafür wird die ID des Hintergrunds benötigt: Klicke in seinen Einstellungen auf **Hintergrundkennung kopieren**.

## Browser

Eine Website über den ganzen Bildschirm, wie beim [Browser-Element](/elements#browser).

> [!IMPORTANT]
> Für den Browser wird die Mod [Rinku](https://modrinth.com/mod/rinku) benötigt. Ohne sie ist der Hintergrund rot und weist darauf hin, dass Rinku fehlt.

- **URL**: die Website. Sie kann [Platzhalter](/placeholders) enthalten.
- **Mausklicks verarbeiten**, **Maus-Scrollen verarbeiten** und **Tastatureingaben verarbeiten**: ermöglichen es Spielern, auf der Website zu klicken, zu scrollen und zu schreiben. Die Website erhält beim Öffnen des Bildschirms sofort die Tastatureingaben.
- **Mausklicks verbrauchen**, **Maus-Scrollen verbrauchen** und **Tastatureingaben verbrauchen**: fangen Klicks, Scrollen und Tastenanschläge auf der Website ab, damit der Bildschirm selbst nicht darauf reagiert.
- **Browser stummschalten**, **Audio-/Videolautstärke**, **Videos wiederholen** und **Videosteuerung ausblenden**: Einstellungen für Medien auf der Website.

Schaltflächen und Elemente vor dem Hintergrund erhalten Klicks immer zuerst. Im Layout-Editor wird der Hintergrund mit Streifen statt mit der Website angezeigt.

## GLSL-Shader

Zeichnet einen Shader – ein kleines Programm für die Grafikkarte –, zum Beispiel animierte Wellen, Sterne oder Muster. Shader von Shadertoy funktionieren ebenfalls.

- **Shaderquelle**: der Shader-Code.
- **Kompilierfehler anzeigen**: zeigt Fehler im Code auf dem Bildschirm an. Deaktiviere diese Option bei fertigen Layouts.

Alle anderen Einstellungen, etwa zusätzliche Durchläufe, Texturen und Zeit, werden in der [GLSL-Shader-API](/glsl-shader-api) erklärt.

## Video [Rinku]

Ein älterer Videohintergrund, für den Rinku benötigt wird. Er erscheint nur dann in der Liste, wenn er aktiviert ist, etwa in Layouts aus älteren Versionen. Verwende stattdessen **Video**.

# Einstellungen für alle Hintergründe

Unter den Hintergrundtypen findest du in **Menühintergründe** Einstellungen, die für alle Hintergründe des Layouts gelten:

- **Seitenverhältnis des Hintergrunds beibehalten**: behält die Proportionen von Bild-, Diashow- und Videohintergründen bei. Sie füllen weiterhin den ganzen Bildschirm aus; nicht passende Bereiche werden abgeschnitten. Ist die Option deaktiviert, werden sie auf den Bildschirm gestreckt.
- **Dunkle Überlagerung auf benutzerdefiniertem Hintergrund anzeigen**: legt die dunkle, durchsichtige Ebene der Minecraft-Menüs über die Hintergründe, damit Schaltflächen und Text besser hervorstechen.
- **Vanilla-Hintergrundunschärfe anwenden**: verwischt die Hintergründe, so wie Minecraft die Welt hinter Menüs unscharf macht. Wie stark die Unschärfe ist, hängt von der Einstellung **Menühintergrundunschärfe** des Spielers unter **Barrierefreiheitseinstellungen** in Minecraft ab. Bei `0` gibt es keine Unschärfe.

<img width="800" alt="Derselbe Hintergrund dreimal nebeneinander: im Original, dunkler mit Dunkle Überlagerung auf benutzerdefiniertem Hintergrund anzeigen und unscharf mit Vanilla-Hintergrundunschärfe anwenden" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_effects.png?raw=true">

Von links nach rechts: keine Einstellung, **Dunkle Überlagerung auf benutzerdefiniertem Hintergrund anzeigen** und **Vanilla-Hintergrundunschärfe anwenden**.

# Hintergründe übereinanderlegen

Du kannst in einem Layout mehrere Typen aktivieren. Sie werden in dieser Reihenfolge übereinander gezeichnet, von unten nach oben:

1. Farbe
2. Kugelpanorama
3. Bild
4. Diashow
5. Video
6. Video [Rinku]
7. Browser
8. GLSL-Shader

Von anderen Mods hinzugefügte Typen werden zuletzt und damit ganz oben gezeichnet.

FancyMenu zeichnet hinter den Hintergründen Schwarz, sodass transparente Bereiche eines Bildes schwarz erscheinen. Ein darunterliegender Farbhintergrund füllt diese Bereiche mit einer Farbe aus:

<img width="800" alt="Eine Pixel-Art-Landschaft mit transparentem Himmel. Auf der linken Hälfte ist der Himmel schwarz. Auf der rechten Hälfte füllt ein blauer Farbhintergrund den Himmel aus" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_backgrounds_stacking.png?raw=true">

Links ist nur das Bild aktiviert. Rechts füllt ein Farbhintergrund den Himmel aus.

- Ein transparentes Bild, eine Diashow oder ein Shader über einem Kugelpanorama funktioniert genauso wie ein Rahmen um ein sich drehendes Panorama.
- Ein Videohintergrund ist nie durchsichtig. Er verdeckt alles darunter, auch in den Bereichen, die das Video nicht ausfüllt.

## Mehrere Layouts

Sind auf einem Bildschirm mehrere Layouts aktiv, etwa ein [universelles Layout](/universal-layouts) und das Layout des Bildschirms, werden auch ihre Hintergründe übereinandergelegt:

- Das Layout mit dem höheren **Layoutindex [Mehrlayout-Reihenfolge]** liegt oben. Lege ihn im Rechtsklickmenü des Editorhintergrunds fest.
- Wenn eines der Layouts eine [Einstellung für alle Hintergründe](#einstellungen-für-alle-hintergründe) aktiviert, gilt sie für die Hintergründe aller Layouts.
- Der Layout-Editor zeigt nur die Hintergründe des Layouts an, das du gerade bearbeitest.

# Wissenswertes

- Elemente des Layouts liegen immer vor seinen Hintergründen.
- **Hintergrundkennung kopieren** kopiert in den Einstellungen jedes Typs die ID des Hintergrunds. Diese ID wird für Aktionen und Platzhalter benötigt, mit denen der Hintergrund gesteuert wird, etwa für [Videohintergründe](/video).
- **Für KI exportieren** kopiert in den Einstellungen jedes Typs den Hintergrund für einen [KI-Chat](/export-for-ai).
- Kopf- und Fußzeilen von Bildschirmen mit Listen, etwa der Weltenliste, haben eigene Texturen: Klicke mit der rechten Maustaste auf den Editorhintergrund und öffne **Kopf-/Fußzeilenanpassungen**.
