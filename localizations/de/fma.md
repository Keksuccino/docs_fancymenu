---
title: Animationen (FMA/AFMA)
description: Wie man FancyMenu-Animationsdateien erstellt und verwendet.
---

# Animationen

AFMA- und FMA-Dateien sind animierte Texturformate, die für FancyMenu erstellt wurden.

# AFMA-Dateien

**AFMA** (Advanced FancyMenu Animation) ist der Nachfolger der klassischen FMA-Dateien.

AFMA verwendet ein Nicht-ZIP-Format mit kleineren Dateien, geringerem Speicherverbrauch und besserer Leistung als klassisches FMA.

Für große oder komplexe animierte Texturen solltest du **AFMA** statt klassischem FMA verwenden.

Erstelle AFMA-Dateien mit dem integrierten Ersteller:

1. Öffne die Menüleiste von FancyMenu.
2. Gehe zu **Tools -> AFMA Creator**.
3. Importiere/konvertiere deine Frames mit dem Ersteller.

> [!IMPORTANT]
> AFMA-Dateien können nicht manuell gepackt werden. Verwende **Tools -> AFMA Creator**.

Klassische FMA-Dateien werden weiterhin unterstützt, daher müssen vorhandene Layouts nicht sofort konvertiert werden.

# Klassische FMA-Dateien

## Ein FMA erstellen

Eine klassische FMA-Datei ist ein ZIP-Archiv mit der Erweiterung `.fma`.

### Dateiendungen

Aktiviere die Dateiendungen in deinem Dateimanager, bevor du die folgenden Dateien erstellst oder umbenennst.

Unter Windows öffne den Datei-Explorer und aktiviere **Ansicht -> Dateinamenerweiterungen**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Vorbereitung

Erstelle einen Ordner mit dem Namen `fancymenu_animation` für den Inhalt des Archivs.

Erstelle darin ein erforderliches Verzeichnis `frames` und optional ein Verzeichnis `intro_frames`.

Erstelle im selben Ordner `metadata.json`. Achte darauf, dass die Dateiendung `.json` ist und nicht `.txt`.

Der Ordner muss nun `frames/`, `intro_frames/` und `metadata.json` enthalten.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### Die Metadata-JSON

Öffne `metadata.json` in einem Texteditor und verwende diese Vorlage:

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

Passe die Werte nach Bedarf an.

#### `loop_count`

Steuert, wie oft die Animation abgespielt wird. Verwende `0` für eine Endlosschleife. Ein positiver Wert spielt die Animation so oft ab und hält dann beim letzten Frame an.

#### `frame_time`

Legt fest, wie lange jeder normale Frame in Millisekunden sichtbar bleibt.

#### `frame_time_intro`

Legt die Frame-Zeit für optionale **Intro**-Frames fest.

#### `custom_frame_times`

Überschreibt optional die Dauer einzelner normaler Frames. Dieses Beispiel hält die Frames `0` und `1` für `5000` Millisekunden sichtbar, während andere Frames `frame_time` verwenden:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Frame-Indizes beginnen bei 0: Der erste Frame ist `0`, der zweite ist `1` und so weiter.

Füge nach jedem Eintrag für benutzerdefinierte Frame-Zeiten ein Komma hinzu, außer nach dem letzten.

#### `custom_frame_times_intro`

Verwendet dasselbe Format wie `custom_frame_times`, gilt aber für optionale Intro-Frames.

Speichere `metadata.json`.

### Die Frames

> [!CAUTION]
> Halte klassische FMA-Animationen bei maximal 200 Frames und 1080p oder darunter. Verwende [Video](./video) für lange Inhalte oder Inhalte mit hoher Bildrate.

Lege normale Frames in `frames/` ab. Sie müssen PNG-Dateien sein und fortlaufend ab `0.png` benannt werden, also zum Beispiel `0.png`, `1.png` und `2.png`. Andere Formate und Namen werden nicht unterstützt.

Um Frames aus einem Video zu extrahieren, siehe [Frames mit FFmpeg extrahieren](./ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### Das Intro

Lege optionale Intro-Frames in `intro_frames/` ab. Sie folgen denselben PNG-Benennungsregeln wie normale Frames, werden einmal vor der normalen Sequenz abgespielt und nicht in einer Schleife wiederholt.

### Das FMA-Datei packen

Erstelle ein ZIP-Archiv mit dem Inhalt des Ordners. `metadata.json`, `frames/` und das optionale Verzeichnis `intro_frames/` müssen sich im ZIP-Stammverzeichnis befinden, nicht in einem weiteren Ordner.

Unter Windows wähle den Inhalt von `fancymenu_animation` aus, klicke mit der rechten Maustaste auf die Auswahl und wähle **Senden an -> ZIP-komprimierter Ordner**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Suche die resultierende ZIP-Datei.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Der Inhalt im Stammverzeichnis sollte so aussehen:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Benenne die Datei in `fancymenu_animation.fma` um und ersetze dabei die `.zip`-Erweiterung. Der Basisname kann geändert werden, aber die Erweiterung `.fma` ist erforderlich.

Das umbenannte Archiv ist nun als FMA-Datei verwendbar.

# AFMA- und FMA-Dateien in FancyMenu verwenden

> [!IMPORTANT]
> AFMA/FMA-Dateien sind animierte Texturen, daher füge sie über [**Bild**-Eingaben](./elements#image) hinzu. Fast alles, was Bilder akzeptiert, akzeptiert auch AFMA- und FMA-Dateien.

Verwende AFMA-/FMA-Dateien überall dort, wo ein Bild akzeptiert wird, einschließlich [Bildelementen](./elements#image) und [Bild-Menühintergründen](./menu-backgrounds).

Speichere die AFMA-/FMA-Datei in `<game-directory>/config/fancymenu/assets/`, damit sie im lokalen Ressourcen-Auswahldialog von FancyMenu erscheint.
