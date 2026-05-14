---
title: Panoramen
description: Wie man benutzerdefinierte Hintergrund-Panoramen erstellt und verwendet.
---

# Kubische Panoramen

FancyMenu unterstützt das Laden benutzerdefinierter 6-Bild-Panorama-Würfel als Hintergrund für Menüs.

Diese Panoramen sind ein spezielles kubisches Panoramaformat, das von Minecraft als Hintergrund im Titelscreen verwendet wird und aus 6 Bildern (Seiten) besteht, die als Würfel (genauer gesagt als Skybox) gerendert werden.

> **WICHTIG**: Wenn du Windows verwendest, vergiss nicht, [Dateiendungen](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png) zu aktivieren, da du sonst später wichtige Teile von Dateinamen nicht sehen kannst!
{.is-warning}

# Ein Panorama erstellen

Wenn du nicht weißt, wie Minecraft seine Hintergrund-Panoramen handhabt und wie man sie erstellt, solltest du dir [dieses Video](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t) ansehen.
Es wird dir ein sehr gutes Verständnis dafür geben, wie Minecrafts Panoramen funktionieren und wie man eines erstellt!

Nachdem du das Video angesehen hast, wirst du feststellen, dass das Erstellen dieser Panoramen etwas zeitaufwendig sein kann.
Um dir etwas Zeit zu sparen, kannst du vielleicht ein Mod verwenden, das sie für dich erstellt.
Du kannst einige davon finden, indem du nach `minecraft panorama mod` suchst, aber eines davon ist [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica) (von mir erstellt).

# Das Panorama vorbereiten

Nachdem du deine 6 Panorama-Bilder hast, musst du sie an den richtigen Ort verschieben!

Das Panoramen-Verzeichnis von FancyMenu befindet sich unter `.minecraft/config/fancymenu/panoramas`.
Dies ist das Verzeichnis für alle Panoramen, die du im Mod verwenden möchtest.

## Der Panorama-Ordner

Jedes Panorama hat seinen eigenen Ordner.
Du musst einen neuen Ordner in `.minecraft/config/fancymenu/panoramas` erstellen, wenn du ein neues Panorama hinzufügen möchtest.
In meinem Beispiel nenne ich den Ordner `mypanorama`.

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## Inhalt des Ordners

Nachdem du den Ordner erstellt hast, musst du ihn befüllen.

### Properties-Datei
Jedes Panorama benötigt eine Properties-Datei, damit es funktioniert.
Diese Datei muss immer `properties.txt` heißen und einige wichtige Angaben enthalten.

Der Inhalt einer Panorama-Properties-Datei sollte immer so aussehen:
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
Nur die Variablen innerhalb des `panorama-meta`-Abschnitts können geändert werden!

#### name
Das muss der **eindeutige** Name deines Panoramas sein.
Es ist nicht möglich, zwei Panoramen mit demselben Namen zu laden!
Diesen Namen verwendest du später, um dein Panorama zu identifizieren.

#### speed
Die Geschwindigkeit, mit der sich dein Panorama dreht.
Dieser Wert ist ein Geschwindigkeitsmultiplikator. Zum Beispiel ist `1.0` die Standardgeschwindigkeit, `2.0` verdoppelt die Geschwindigkeit und `0.5` halbiert sie.
Negative Werte werden nicht unterstützt; verwende Dezimalwerte, um die Geschwindigkeit zu verringern.

#### fov
Das Sichtfeld.
Das Standard-FOV ist `85.0`.
Zu große oder zu kleine Werte können das Panorama beschädigen. Experimentiere einfach ein wenig, um das gewünschte FOV zu finden.

#### angle
Der vertikale Winkel, aus dem das Panorama betrachtet wird.
Der Standardwinkel ist `25.0`.

#### start_rotation
Der Drehwinkel (horizontal), bei dem das Panorama beginnen soll. Wert zwischen 0 und 360.

<br>

### Panorama-Bildordner

Das zweite notwendige Element, das dein Panorama-Ordner benötigt, ist der eigentliche Bildordner mit deinen Panorama-Bildern.

Der Name dieses Ordners muss `panorama` sein.

Lege dort alle deine Panorama-Bilder ab, aber vergiss nicht, sie korrekt zu benennen, wie im oben verlinkten [Video](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t) gezeigt!

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> Als Panorama-Bilder werden nur PNGs unterstützt!
{.is-warning}

### Panorama-Overlay

Der letzte Schritt ist **optional** und kann übersprungen werden, wenn du kein Overlay über deinem Panorama möchtest.

Wenn du deinem Panorama eine Vignette oder andere Arten von Overlays hinzufügen möchtest, kannst du eine Datei mit dem Namen `overlay.png` hinzufügen.
Beachte, dass für das Overlay nur PNG unterstützt wird und der Dateiname immer `overlay.png` sein muss!

### Alles noch einmal überprüfen

Du solltest jetzt einen Ordner unter `.minecraft/config/fancymenu/panoramas` haben, der eine `properties.txt`-Datei, einen weiteren Ordner namens `panorama` und eventuell ein Overlay namens `overlay.png` enthält.

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# Das Panorama verwenden

Nachdem du das Spiel neu gestartet oder FancyMenu über **Anpassung -> FancyMenu neu laden** neu geladen hast, solltest du nun dein Panorama als Menü-Hintergrund setzen können. Klicke dazu im Hintergrund des Layout-Editors mit der rechten Maustaste und dann auf **Menü-Hintergrund**.
