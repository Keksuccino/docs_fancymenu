---
title: Diashows
description: Wie man Diashows erstellt und verwendet.
---

# Diashows

FancyMenu ermöglicht es dir, Diashows hinzuzufügen und sie in Menüs sowie als Menü-Hintergründe anzuzeigen.

> **WICHTIG**: Wenn du unter Windows arbeitest, vergiss nicht, [Dateiendungen](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10) zu aktivieren, da du sonst später wichtige Teile von Dateinamen nicht sehen kannst!
{.is-warning}

# Eine Diashow erstellen

Jede Diashow muss sich in ihrem eigenen Ordner **innerhalb** des Diashows-Verzeichnisses unter `/config/fancymenu/slideshows/` befinden.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

Damit das System eine Diashow als solche erkennt, benötigt sie eine Properties-Datei im Ordner der Diashow. Wenn du deinen Diashow-Ordner also `myslideshow` genannt hast, sollte sich die Properties-Datei unter `/config/fancymenu/slideshows/myslideshow/properties.txt` befinden.

**Diese Datei muss immer `properties.txt` heißen!**
Erstelle vorerst nur die **leere** Properties-Datei und gehe dann zum nächsten Schritt über.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## Bilder hinzufügen

Eine Diashow braucht Bilder (logisch), also fügen wir welche hinzu!

> Deine Diashow-Bilder müssen **PNG**-Dateien sein! Keine JPEGs, GIFs, APNGs oder FMAs!
{.is-danger}

Alle Bilder deiner Diashow kommen in einen zusätzlichen Ordner **innerhalb** deines Diashow-Ordners (im obigen Beispiel `myslideshow`).
Dieser Ordner muss `images` heißen.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Lege jetzt alle Bilder deiner Diashow in den `images`-Ordner.
Sie werden alphabetisch sortiert (Zahlen werden dabei berücksichtigt), benenne sie also einfach zum Beispiel `image_1.png`, `image_2.png` und so weiter.
In meinem Beispiel wird `image_1.png` zuerst angezeigt und `image_2.png` danach.

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## Inhalt zur Properties-Datei hinzufügen

Zu Beginn hast du eine leere Datei `properties.txt` in deinem Diashow-Ordner erstellt.
Diese Datei muss jetzt mit einigen wichtigen Angaben gefüllt werden.

Jede Properties-Datei für eine Diashow sollte so aussehen:

```
type = slideshow

slideshow-meta {
   name = cool_slideshow
   width = 1920
   height = 1080
   x = 0
   y = 0
   duration = 5.0
   fadespeed = 12.0
   randomize = false
}
```
Nur die Variablen innerhalb des Abschnitts `slideshow-meta` können geändert werden!

### name

Das ist der Name, oder besser die Kennung, deiner Diashow.
Diashow-Namen müssen **eindeutig** sein, daher ist es nicht möglich, zwei Diashows mit demselben Namen zu haben!

### width | height

Die Basis-`width` und -`height` deiner Diashow.
Wird von FancyMenu verwendet, um das Seitenverhältnis zu berechnen.

### x | y

Die Position `x` und `y` deiner Diashow.
Eher für Debugging-Zwecke gedacht, also setze beide einfach auf `0`.

### duration

Die Dauer in **Sekunden**, wie lange jedes Bild angezeigt wird, bevor zum nächsten gewechselt wird.
Unterstützt Dezimalwerte!

### fadespeed

Die Geschwindigkeit der Überblend-Animation beim Wechsel zum nächsten Bild.
Dieser Wert ist ein Geschwindigkeits-Multiplikator. Zum Beispiel ist `1.0` die Standardgeschwindigkeit, `2.0` verdoppelt die Geschwindigkeit und `0.5` macht sie nur halb so schnell wie standardmäßig.
Negative Werte werden nicht unterstützt.

### randomize

Legt fest, ob die Diashow-Bilder in zufälliger Reihenfolge abgespielt werden sollen (`true`) oder nicht (`false`).

# Die Diashow verwenden

Alle wichtigen Schritte sind erledigt und deine Diashow sollte jetzt bereit sein, also testen wir sie!

Um deine neue (oder bearbeitete) Diashow in FancyMenu zu laden, lade das Mod über **Anpassung -> FancyMenu neu laden** neu.

Jetzt kannst du deine Diashow im Element **Diashow** oder als Menü-Hintergrund verwenden (Rechtsklick auf den Hintergrund des Layout-Editors -> **Menü-Hintergrund**).
