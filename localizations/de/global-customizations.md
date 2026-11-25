---
title: Globale Anpassungen
description: >-
  Ändere die Buttons, Schieberegler, Menü-Hintergründe, Musik und das Fenster
  aller Bildschirme gleichzeitig – ganz ohne Layouts.
sourceBlobSha: cafc7ed87ce931e406fb14b7a605085b565ce1a7
---

# Globale Anpassungen

Mit globalen Anpassungen änderst du alle Bildschirme gleichzeitig: Buttons, Schieberegler, Menü-Hintergründe, Musik, das Spielfenster und vieles mehr. Dafür ist kein Layout nötig. Sie funktionieren auch auf Bildschirmen, deren Anpassung deaktiviert ist.

Du findest sie auf jedem Bildschirm außerhalb des Layout-Editors über **Menüleiste -> Anpassung -> Globale Anpassungen**. Änderungen werden sofort übernommen und automatisch gespeichert.

<img width="800" alt="Der Titelbildschirm, die Optionen und Musik & Töne ohne Layout, alle mit denselben Holz-Buttons, Messinggriffen an den Schiebereglern, Beschriftungen, die beim Darüberfahren mit der Maus golden werden, und einem Nachthintergrund" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/global_customizations_tour.gif?raw=true">

> [!TIP]
> Um nur bestimmte Bildschirme zu ändern, verwende [Layouts](/layout-editor). Wenn die Buttons bestimmter Layouts ein eigenes Aussehen haben sollen, nutze [Button- und Schieberegler-Vorlagen](/button-slider-templates).

# Buttons und Schieberegler

Diese Einstellungen ändern alle Buttons und Schieberegler auf allen Bildschirmen, auch die von anderen Mods.

- Buttons und Schieberegler, die über ein [Layout](/layout-editor) oder eine [Vorlage](/button-slider-templates) eigene Texturen oder Beschriftungseinstellungen erhalten haben, behalten diese.
- Buttons, die nur aus einem Bild bestehen, wie der Button des Rezeptbuchs, behalten ihr Aussehen.

## Button-Texturen

Unter **Benutzerdefinierte Button-Texturen** kannst du für jeden Zustand eines Buttons eine Textur festlegen:

- **Normal**
- **Hover**: wenn sich die Maus über dem Button befindet oder er per Tastatur ausgewählt ist.
- **Inaktiv**: wenn der Button nicht angeklickt werden kann.

Lege alle drei Texturen fest. Für Zustände ohne Textur wird der Minecraft-Button angezeigt.

Weitere Einstellungen im selben Menü:

- **Transparenter Hintergrund** blendet den Hintergrund aller Buttons aus, sodass nur ihre Beschriftungen angezeigt werden. Diese Einstellung hat Vorrang vor den Texturen.
- **Neun-Slice-Button-Hintergründe** sorgt dafür, dass die Ränder der Texturen bei jeder Button-Größe scharf bleiben. Die vier Randbreiten kannst du darunter einstellen. Siehe [Neun-Slicing und Kachelung](/nine-slicing-and-tiling).

> [!TIP]
> Ohne Neun-Slicing werden die Texturen auf die Größe jedes Buttons gestreckt. Minecraft-Buttons sind 20 Pixel hoch und meistens 200 oder 150 Pixel breit. Mit Neun-Slicing passt eine kleine Textur für alle.

## Schieberegler-Texturen

Unter **Benutzerdefinierte Schieberegler-Texturen** gibt es zwei Bereiche:

- **Hintergrundtextur des Schiebereglers**: der Balken des Schiebereglers. Lege die Textur über **Textur festlegen** fest. **Transparenter Hintergrund** und **Neun-Slice-Hintergrund des Schiebereglers** funktionieren wie bei den Buttons.
- **Griff-Texturen des Schiebereglers**: der Teil, den du ziehst. Hier kannst du Texturen für **Normal**, **Hover** und **Inaktiv** sowie **Neun-Slice-Griff des Schiebereglers** festlegen.

Der Griff von Minecraft-Schiebereglern ist 8 Pixel breit und so hoch wie der Schieberegler, meistens also 20 Pixel. Ohne Neun-Slicing werden die Griff-Texturen auf diese Größe gestreckt.

## Beschriftungen

Für **Button-Beschriftungen** und **Schieberegler-Beschriftungen** gelten dieselben Einstellungen:

| Einstellung | Beschreibung |
|---|---|
| **Beschriftung bei Hover unterstreichen** | Unterstreicht die Beschriftung, wenn sich die Maus darüber befindet. |
| **Grundfarbe der Beschriftung** | Die Farbe der Beschriftung. Lege sie über die Farbauswahl oder als HEX-Code fest, zum Beispiel `#FFF1D6`. |
| **Hover-Farbe der Beschriftung** | Die Farbe, wenn sich die Maus über der Beschriftung befindet. |
| **Größe der Beschriftung** | Die Größe der Beschriftung. `1` entspricht der normalen Größe. |
| **Ausrichtung der Beschriftung** | **Links**, **Zentriert** oder **Rechts**. |
| **Schatten der Beschriftung** | Der dunkle Schatten hinter der Beschriftung. Ist die Einstellung deaktiviert, haben keine Beschriftungen einen Schatten – auch nicht die aus Layouts. |

Beschriftungen mit eigenen Einstellungen aus einem Layout oder einer Vorlage behalten diese. Bei **Größe der Beschriftung** und **Ausrichtung der Beschriftung** gilt die globale Einstellung nur für Beschriftungen in normaler Größe und mit **Zentriert**-Ausrichtung.

## Klicksound

- **Benutzerdefinierter Button-Klicksound** ersetzt den Klicksound von Minecraft-Buttons und -Schiebereglern. Buttons mit einem eigenen Klicksound aus einem Layout behalten diesen.
- **Lautstärke des benutzerdefinierten Button-Klicksounds** lässt sich von 0 % bis 100 % einstellen. Zusätzlich gilt der Lautstärkeregler des Soundkanals in den Minecraft-Soundeinstellungen.
- **Soundkanal des benutzerdefinierten Button-Klicksounds** legt fest, über welchen Soundkanal der Sound abgespielt wird, zum Beispiel Musik. Standardmäßig ist die Gesamtlautstärke eingestellt, über die alle Sounds laufen.

# Menü-Hintergründe

**Benutzerdefinierte Menü-Hintergrundtextur** ist ein Bild hinter allen Menüs außer dem Titelbildschirm:

- Sie wird auch hinter dem Pausenmenü und den Optionen während des Spielens angezeigt und verdeckt dort die Spielwelt. Inventare, Schilder und Bücher bleiben durchsichtig.
- **Seitenverhältnis der Hintergrundtextur beibehalten** erhält die Proportionen des Bildes. Es füllt weiterhin den gesamten Bildschirm aus, wobei überstehende Teile abgeschnitten werden. Ist die Einstellung deaktiviert, wird das Bild auf Bildschirmgröße gestreckt.

**Benutzerdefiniertes Menü-Hintergrundpanorama** ersetzt das Minecraft-Panorama auf dem Titelbildschirm und in allen Menüs, bevor du einer Welt beitrittst:

- **Panorama auswählen** wählt eines deiner [Panoramen](/panoramas) aus.
- **Panorama zurücksetzen** stellt das Minecraft-Panorama wieder her.
- **Aktuelles Panorama** zeigt an, welches Panorama eingestellt ist.

Wenn beides eingestellt ist, liegt die Textur über dem Panorama. Das Panorama ist dann nur auf dem Titelbildschirm zu sehen.

Bildschirme, deren Layout einen eigenen [Menü-Hintergrund](/menu-backgrounds) hat, zeigen stattdessen diesen an.

# Menümusik

- **Vanilla-Menümusik abspielen** schaltet die Minecraft-Musik in Menüs ein oder aus.
- **Benutzerdefinierte Menümusiktitel** öffnet **Menümusiktitel verwalten**. Mit **Titel hinzufügen** fügst du einen Sound hinzu, mit **Entfernen** entfernst du den ausgewählten Titel, mit **Alle Titel löschen** entfernst du alle Titel und mit **Fertig** speicherst du die Liste.

Die Titel werden in zufälliger Reihenfolge in Menüs abgespielt, bevor du einer Welt beitrittst, und ersetzen dabei die Minecraft-Menümusik. Mehr dazu und zur Musik auf einzelnen Bildschirmen findest du unter [Menü-Hintergrundmusik](/background-music).

# Bildschirme und Pop-ups

| Einstellung | Beschreibung |
|---|---|
| [**Spielintro**](/game-intro) | Spielt eine Animation oder ein Video ab, bevor der Titelbildschirm erscheint. |
| **Welt-Icons im Einzelspieler-Bildschirm** | Die Icons der Welten in der Weltliste. Sind sie ausgeblendet, werden sie nicht angezeigt. |
| **Server-Icons im Mehrspieler-Bildschirm** | Die Icons der Server in der Serverliste. Sind sie ausgeblendet, werden sie nicht angezeigt. |
| [**Nahtloses Laden von Welten**](/seamless-world-loading) | Erstellt beim Verlassen einer Welt oder eines Servers einen Screenshot und zeigt ihn beim erneuten Beitreten als Ladehintergrund an. |
| **Erfolgs-Pop-ups** | Die Pop-ups oben rechts, die beim Freischalten eines Erfolgs erscheinen, sowie deren Sounds. Sind sie ausgeblendet, werden sie nicht angezeigt. Erfolgsmeldungen im Chat bleiben erhalten, und der Listener [On Achievement Unlocked](/listeners#on-achievement-unlocked) funktioniert weiterhin. |

# Fenster und Spielstart

| Einstellung | Beschreibung |
|---|---|
| [**Benutzerdefiniertes Fenstersymbol**](/window-customization#custom-icon) | Das Symbol des Spielfensters. Dafür werden ein PNG-Symbol mit 16x16 und eines mit 32x32 Pixeln sowie ein macOS-Symbol benötigt. |
| [**Benutzerdefinierter Fenstertitel**](/window-customization#custom-title) | Ersetzt den Fenstertitel von Minecraft. [Platzhalter](/placeholders) funktionieren, und der Titel wird aktualisiert, sobald sich ihre Werte ändern. |
| **Standard-GUI-Skalierung** | Legt die GUI-Skalierung von Minecraft beim ersten Start der Spielinstanz einmalig fest, zum Beispiel auf `2` oder `3`. Mit `-1` wird die Einstellung deaktiviert. Für Modpacks gedacht. |
| **Beim Start Vollbild erzwingen** | Startet das Spiel jedes Mal im Vollbildmodus. |

FancyMenu merkt sich in `fancymenu_data/default_scale_set.fm`, dass die **Standard-GUI-Skalierung** festgelegt wurde. Lösche diese Datei, damit die Skalierung beim nächsten Start erneut eingestellt wird (siehe [Speicherorte der Daten](/data-storage-locations#instance-data)).

# Gut zu wissen

- Globale Anpassungen werden in FancyMenus `options.txt` gespeichert. Sie gehören daher zum geladenen [Profil](/profiles) und sind in Modpacks enthalten, die `config/fancymenu/` mitliefern.
- Texturen und Sounds können Dateien deiner Instanz, Weblinks oder Dateien aus Ressourcenpaketen sein. Siehe [Ressourcen](/resources).
- **Menüleiste -> Hilfe -> Für KI exportieren -> FancyMenu-Einstellungen** enthält auch diese Einstellungen und eignet sich für Fragen an einen [KI-Chat](/export-for-ai).
