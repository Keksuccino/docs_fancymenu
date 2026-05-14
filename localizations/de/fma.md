---
title: Animationen (FMA/AFMA)
description: Wie man FancyMenu-Animationsdateien erstellt und verwendet.
---

# Animationen

AFMA/FMA-Dateien sind spezielle animierte Texturdateien, die für FancyMenu erstellt wurden.
Sie sind im Grunde dasselbe wie APNGs, aber deutlich stärker für FancyMenu optimiert.

# AFMA-Dateien

FancyMenu 3.9.0 führt **AFMA** (Advanced FancyMenu Animation) ein, den Nachfolger der klassischen FMA-Dateien.

AFMA-Dateien sind keine ZIP-Dateien mehr. Sie verwenden das neuere Animationsformat von FancyMenu mit kleineren Dateigrößen, geringerem Speicherverbrauch und besserer Leistung.

Für neue große oder komplexe animierte Texturen solltest du **AFMA** statt klassischem FMA verwenden.

Um eine AFMA-Datei zu erstellen, gehe so vor:

1. Öffne die Menüleiste von FancyMenu.
2. Gehe zu **Tools -> AFMA Creator**.
3. Importiere/konvertiere deine Frames mit dem Creator.

> [!IMPORTANT]
> AFMA-Dateien können nicht manuell wie klassische FMA-Dateien gepackt werden. Du musst den **AFMA Creator** verwenden, um sie zu packen/erstellen.

Klassische FMA-Dateien werden weiterhin unterstützt und wurden in FancyMenu 3.9.0 optimiert, sodass vorhandene Layouts nicht sofort konvertiert werden müssen.

# Klassische FMA-Dateien

## Ein FMA erstellen

Eine FMA-Datei zu erstellen ist so einfach wie das Erstellen einer ZIP-Datei! Naja, das liegt hauptsächlich daran, dass sie unter der Haube _eine_ ZIP-Datei ist.

### Dateiendungen

Du musst Dateiendungen sehen können, um dieser Dokumentation folgen zu können. Stelle also sicher, dass du **DATEIENDUNGEN AKTIVIEREN** bevor du beginnst.

Unter Windows öffnest du dazu einen beliebigen Ordner und klickst dann oben rechts auf den Pfeil, um das Menü darunter zu erweitern.

Wechsle dann zum Reiter **Ansicht** und aktiviere **Dateinamenerweiterungen**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Vorbereitung

Beginnen wir damit, einen neuen Ordner für den Inhalt der FMA-Datei zu erstellen.
In diesem Beispiel nennen wir den Ordner `fancymenu_animation`.

Erstelle in diesem Ordner zwei weitere Ordner. Der erste Ordner **muss** `frames` heißen und der zweite Ordner **muss** `intro_frames` heißen.

Erstelle nun im selben Ordner eine neue TXT-Datei und benenne sie in `metadata.json` um.
Bitte achte darauf, dass die Datei keine TXT-Datei bleibt. Du **musst** die Dateiendung auf `json` ändern.

Nun solltest du einen Ordner namens `fancymenu_animation` haben und in diesem Ordner einen Ordner namens `frames`, einen Ordner namens `intro_frames` und eine JSON-Datei namens `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### Die Metadata-JSON

Diese Datei teilt FancyMenu mit, wie mit deiner FMA-Textur umgegangen werden soll.
Sie enthält Informationen wie die Frame-Zeiten (wie lange ein Frame sichtbar ist) und die Loop-Anzahl.

Bitte öffne die Datei `metadata.json` mit einem Texteditor.

Kopiere diesen Text in die Datei:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

Das ist die grundlegende Vorlage, wie die Datei aussehen sollte.
Jetzt kannst du sie nach deinen Wünschen anpassen.

#### `loop_count`

Damit steuerst du, wie oft die Textur loopen soll (die Animation neu startet).

Wenn du dies auf `0` setzt, wird sie unendlich oft wiederholt. Sie wird *niemals aufhören*.

Jeder Wert größer als `0` gibt an, wie oft die Textur abgespielt wird. Wenn du den Wert zum Beispiel auf `1` setzt, wird die Textur nur einmal abgespielt und bleibt dann beim letzten Frame stehen; `2` bedeutet, dass sie zweimal abgespielt wird und dann beim letzten Frame stoppt *und so weiter*.

#### `frame_time`

Dies ist die allgemeine Frame-Zeit in **Millisekunden** für die Frames der animierten Textur.
Die Frame-Zeit gibt an, wie lange ein Frame sichtbar ist, bevor die Animation zum nächsten Frame wechselt.

#### `frame_time_intro`

Das ist im Grunde dasselbe wie `frame_time`, aber für die **Intro**-Frames deiner animierten Textur.
Intro-Frames sind **optional** und du erfährst später mehr darüber.

#### `custom_frame_times`

Dies ist **optional** und kann verwendet werden, um die Frame-Zeit für bestimmte (nicht-Intro-)Frames zu überschreiben.
Zum Beispiel möchtest du, dass alle Frames `41` Millisekunden lang angezeigt werden, also setzt du `frame_time` auf `41`, aber die ersten beiden Frames sollen `5000` Millisekunden lang angezeigt werden.

In diesem Fall würdest du Folgendes machen:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    0: 5000,
    1: 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Frames beginnen bei 0, das heißt: Der erste Frame der Animation ist `0`, der zweite ist `1` und so weiter.

Am Ende jedes Eintrags für benutzerdefinierte Frame-Zeiten muss ein **Komma** stehen, **außer** beim letzten Eintrag!

#### `custom_frame_times_intro`

Das ist genau dasselbe wie `custom_frame_times`, aber in diesem Fall für die **Intro**-Frames. Intro-Frames sind **optional** und du erfährst später mehr darüber.

Das war's für die Datei `metadata.json`. Speichere sie jetzt und schließe den Texteditor.

### Die Frames

> Es wird empfohlen, pro Animation **maximal 200 Frames** bei einer **maximalen Auflösung von 1080p** zu verwenden, da Animationen viel Speicher verbrauchen und keine Videos sind. Sie sind für kurze animierte Loops gedacht, nicht um komplette Videos mit 24 FPS abzuspielen.
{.is-danger}

Die Frames deiner animierten Textur kommen in den Ordner `frames`.

Frames müssen **PNG-DATEIEN** sein! Es gibt **KEINE UNTERSTÜTZUNG FÜR JPEG UND ANDERE FORMATE**!

Jeder Frame **muss** einfach nach seiner Nummer und der Dateiendung benannt sein.
Der erste Frame sollte `0.png` heißen, der zweite `1.png`, der dritte `2.png` und so weiter.
Die Textur wird **NICHT FUNKTIONIEREN**, wenn die Frames ungültige Dateinamen haben!

Um **Frames aus Videos zu extrahieren**, wirf bitte einen Blick auf [diese Doku-Seite](/ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### Das Intro

Diese Funktion ist **OPTIONAL**.

Die **Intro**-Funktion von FMA-Dateien ist eine spezielle Möglichkeit, einige Frames **vor** den eigentlichen Frames aus dem Ordner `frames` abzuspielen. 

Das Intro wird **niemals geloopt** und spielt nur beim allerersten Abspielen der Animation, wodurch du zum Beispiel eine Fade-in-Animation abspielen kannst, bevor die eigentliche Animation in einer Schleife startet.

Intro-Frames kommen in den Ordner `intro_frames` und funktionieren genauso wie normale Frames:

Frames müssen **PNG-DATEIEN** sein! Es gibt **KEINE UNTERSTÜTZUNG FÜR JPEG UND ANDERE FORMATE**!

Jeder Frame **muss** einfach nach seiner Nummer und der Dateiendung benannt sein.
Der erste Frame sollte `0.png` heißen, der zweite `1.png`, der dritte `2.png` und so weiter.
Die Textur wird **NICHT FUNKTIONIEREN**, wenn die Frames ungültige Dateinamen haben!

### Das FMA packen

Jetzt ist alles Wichtige im Ordner `fancymenu_animation`, also kannst du deine FMA-Datei jetzt packen!

FMA zu packen bedeutet im Grunde nur, den Ordnerinhalt in eine ZIP-Datei zu packen.
Der Inhalt muss im **ROOT** der ZIP-Datei liegen, darf also nicht in einem zusätzlichen Ordner innerhalb der ZIP sein.

Unter Windows ist der einfachste Weg, den FMA-Inhalt in eine ZIP-Datei zu packen, alles im Ordner `fancymenu_animation` auszuwählen und dann die Datei `metadata.json` **rechtszuklicken**. Klicke im sich öffnenden Kontextmenü auf **Senden an -> ZIP-komprimierter Ordner**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Jetzt sollte sich im Ordner `fancymenu_animation` eine neue ZIP-Datei namens `metadata.zip`, `frames.zip` oder `intro_frames.zip` befinden.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Wenn du diese Datei öffnest, sollte ihr Inhalt so aussehen:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Jetzt musst du die Datei in `fancymenu_animation.fma` umbenennen. Achte darauf, dass du `.zip` durch `.fma` **ERSETZT**, damit es keine ZIP-Datei mehr ist.

Natürlich kannst du den Teil `fancymenu_animation` in etwas Beliebiges ändern, aber achte darauf, dass es eine `.fma`-Datei bleibt!

Das war's! Jetzt hast du eine (hoffentlich) funktionierende FMA-Datei!

# AFMA- und FMA-Dateien in FancyMenu verwenden

> [!IMPORTANT]
> AFMA/FMA-Dateien gelten als **animierte Texturen**, daher fügst du sie über **Bild**-Eingaben hinzu. Fast alles, was Bilder akzeptiert (PNG, JPEG, GIF usw.), akzeptiert auch FMA- und AFMA-Dateien.

Du kannst AFMA/FMA-Dateien wie jedes andere animierte Textur-/Bildformat verwenden. FancyMenu behandelt sie als normales Bild, sodass du sie überall verwenden kannst, wo du eine Textur zuweisen kannst, zum Beispiel bei **Bildelementen oder Bild-Menühintergründen**.

Stelle sicher, dass sich die AFMA-/FMA-Datei im Ordner `/config/fancymenu/assets/` befindet, da FancyMenu Texturen und andere Ressourcen nur aus seinem `assets`-Ordner laden kann.
