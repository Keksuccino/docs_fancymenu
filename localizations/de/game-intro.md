---
title: Spiel-Intro
description: >-
  Spiele bei jedem Spielstart eine Animation oder ein Video ab, bevor der
  Titelbildschirm erscheint.
sourceBlobSha: 2f40eb874b4aebaf4b32ffa2b8980310d71510b7
---

# Spiel-Intro

Das Spiel-Intro spielt eine Animation oder ein Video ab, sobald das Spiel startet – direkt nach dem Minecraft-Ladebildschirm. Am Ende wird es sanft in den Titelbildschirm überblendet. Es ist für Modpacks gedacht: ein Logo, ein Studio-Intro oder ein kurzer Trailer.

<img width="800" alt="Das Skyhaven-Intro: Die Nacht wird über einer schwebenden Insel zum Morgen, und das Logo erscheint Buchstabe für Buchstabe. Anschließend wird das Intro sanft in den Titelbildschirm überblendet, dessen Hintergrund dieselbe Insel zeigt." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

Spieler können das Intro mit einer beliebigen Taste oder einem Klick überspringen. Das Spiel-Intro gehört zu den [globalen Anpassungen](/global-customizations) und benötigt daher kein Layout.

# Intro einrichten

<img width="800" alt="Über die Menüleiste die globalen Anpassungen und das Spiel-Intro öffnen, mit Spiel-Intro festlegen skyhaven_intro.apng auswählen, mit Spiel-Intro erneut auslösen abspielen und mit der Leertaste überspringen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. Lege deine Animation oder dein Video unter `<game-directory>/config/fancymenu/assets/` ab.
2. Öffne **Menüleiste -> Anpassung -> Globale Anpassungen -> Spiel-Intro**.
3. Klicke auf **Spiel-Intro festlegen**. Stelle **Quelltyp** auf **Lokal**, klicke auf **Lokale Ressourcendatei auswählen**, wähle deine Datei aus und klicke auf **OK**.
4. Klicke auf **Spiel-Intro erneut auslösen**, um es sofort anzusehen.

Um das Intro zu entfernen, bewege die Maus auf **Spiel-Intro festlegen** und klicke auf **Auf Standard zurücksetzen**.

## Animationen und Videos

- **Animationen:** APNG- oder GIF-Dateien. So erstellst du sie: [Animationen](/animations).
- **Videos:** MP4-Dateien. Dafür werden die Mods Watermedia V3 und Watermedia Binaries V3 benötigt. Siehe [Videos](/video#requirements). Ohne diese Mods wird bei einem Video-Intro nur einige Sekunden lang ein roter Hinweis mit Download-Links angezeigt.
- Dateien aus deiner Instanz und aus Ressourcenpaketen funktionieren, Weblinks jedoch nicht. Siehe [Ressourcen](/resources).

Das Intro füllt den ganzen Bildschirm aus und behält seine Proportionen bei. Deshalb werden auf Bildschirmen mit anderen Seitenverhältnissen Teile abgeschnitten. Die meisten Bildschirme haben ein Seitenverhältnis von 16:9. Erstelle dein Intro daher ebenfalls im Format 16:9, zum Beispiel mit 1920 × 1080 Pixeln. Transparente Bereiche werden schwarz angezeigt.

> [!TIP]
> Spieler sehen das Intro bei jedem Spielstart. Halte es daher kurz – etwa 5 bis 10 Sekunden.

## Kostenloses Beispiel-Intro

Das Skyhaven-Intro aus den GIFs auf dieser Seite darf kostenlos verwendet werden, sowohl zum Testen als auch in deinen Modpacks:

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true): das Intro, 1280 × 720 Pixel, 5,4 Sekunden lang. Es wird einmal abgespielt.
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true): die letzte Szene ohne Logo, 1280 × 720 Pixel. Verwende sie als [Bildhintergrund](/menu-backgrounds#image) für ein Titelbildschirm-Layout. So wird das Intro in ein passendes Menü überblendet, wie im ersten GIF.

# Einstellungen

Alle Einstellungen findest du unter **Menüleiste -> Anpassung -> Globale Anpassungen -> Spiel-Intro**:

| Einstellung | Funktion |
|---|---|
| **Spiel-Intro festlegen** | Die Animation oder das Video. |
| **Spiel-Intro überspringen** | Mit einer beliebigen Taste oder einem Klick lässt sich das Intro überspringen. Am unteren Bildschirmrand wird **Beliebige Taste zum Überspringen drücken** angezeigt. Beim Überspringen endet das Intro sofort, ohne Überblendung. Ist diese Option deaktiviert, wird das Intro immer bis zum Ende abgespielt. |
| **Spiel-Intro ausblenden** | Blendet das Intro am Ende in den Titelbildschirm über. Ist diese Option deaktiviert, erscheint der Titelbildschirm sofort. |
| **Schleifen des Spiel-Intros ignorieren** | Beendet das Intro, nachdem die Animation einmal abgespielt wurde – auch wenn sie in einer Schleife läuft. Ist diese Option deaktiviert, werden alle Animationsschleifen abgespielt. Videos werden immer einmal abgespielt. |
| **Benutzerdefinierter Überspringen-Text** | Ersetzt **Beliebige Taste zum Überspringen drücken**, zum Beispiel durch `Drücke eine beliebige Taste, um dein Abenteuer zu beginnen`. Ein Lokalisierungsschlüssel aus einem Ressourcenpaket, zum Beispiel `skyhaven.intro.skip`, zeigt den Text in der Sprache des Spielers an. |
| **Lautstärke des Spiel-Intros** | Die Lautstärke eines Video-Intros, von 0 % bis 100 %. |
| **Soundkanal des Spiel-Intros** | Der Soundkanal für Video-Intros, zum Beispiel Musik. Die Lautstärke dieses Kanals sowie die Gesamtlautstärke in den Minecraft-Soundeinstellungen werden zusätzlich angewendet. |
| **Spiel-Intro erneut auslösen** | Spielt das Intro sofort über dem gerade angezeigten Bildschirm ab. |

**Spiel-Intro überspringen**, **Spiel-Intro ausblenden** und **Schleifen des Spiel-Intros ignorieren** sind standardmäßig aktiviert.

> [!WARNING]
> Sind **Spiel-Intro überspringen** und **Schleifen des Spiel-Intros ignorieren** beide deaktiviert, endet eine endlos wiederholte Animation nie, und Spieler können den Titelbildschirm nicht erreichen.

# Gut zu wissen

- Das Intro wird einmal pro Spielstart abgespielt, vor dem ersten Bildschirm nach dem Ladebildschirm. Normalerweise ist das der Titelbildschirm.
- Wie du den Minecraft-Ladebildschirm davor änderst, erfährst du unter [Ladebildschirm](/loading-screen).
- Die Quelle des Intros kann [Platzhalter](/resources#placeholders-in-resource-sources) enthalten.
- Die Einstellungen des Spiel-Intros werden in FancyMenus `options.txt` gespeichert und gehören daher zum geladenen [Profil](/profiles). Modpacks, die `config/fancymenu/` enthalten, bringen das Intro zusammen mit der zugehörigen Datei in `assets/` mit. Siehe [Modpacks](/modpacks).
