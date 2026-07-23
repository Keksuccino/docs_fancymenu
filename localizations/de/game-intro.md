---
title: Spiel-Intro
description: >-
  Animierte Inhalte abspielen, bevor das Spiel zum ersten Mal den
  Titelbildschirm anzeigt.
---
# Spiel-Intros

Spiel-Intros spielen ein animiertes Bild oder Video ab, bevor der Titelbildschirm zum ersten Mal erscheint.

# Einrichtung

Öffne [**Globale Anpassungen**](./global-customizations) über **Anpassung -> Globale Anpassungen** und konfiguriere dann diese Einstellungen:

| Einstellung | Verhalten |
|---|---|
| Spiel-Intro festlegen | Wählt ein animiertes Bild oder Video von lokal, aus dem Web oder aus Minecraft-Ressourcen aus |
| Spiel-Intro überspringen | Erlaubt es, das Intro mit einer beliebigen Taste oder einem Mausklick zu überspringen |
| Spiel-Intro ausblenden | Blendet das Intro in den Zielbildschirm über |
| Benutzerdefinierter Überspringen-Text | Ersetzt die Standardaufforderung zum Überspringen durch Klartext oder einen Lokalisierungsschlüssel |
| Spiel-Intro-Lautstärke | Legt die Grundlautstärke von `0.0` bis `1.0` fest |
| Spiel-Intro-Soundkanal | Wählt die Minecraft-Soundkategorie aus |
| Spiel-Intro erneut auslösen | Spielt das konfigurierte Intro zum Testen erneut ab |

Video-Intros erfordern **Watermedia V3**, **Watermedia Binaries V3** und einen OpenGL-Renderer. Die Videowiedergabe von Watermedia ist mit Vulkan nicht verfügbar. Wenn die Wiedergabe nicht verfügbar ist, zeigt FancyMenu eine Erklärung über dem Intro-Bildschirm an. Siehe [Videos](./video#requirements).

<br>
<img width="700" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/71cec75b-33f1-4a21-9f18-d0adc7ceebb6">
