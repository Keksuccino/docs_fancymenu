---
title: Globale Anpassungen
description: 'Wende globale FancyMenu-Anpassungen an, die alle Bildschirme betreffen.'
---

# Globale Anpassungen

Globale Anpassungen wenden gemeinsame UI- und Start-Einstellungen an, ohne jedes einzelne Bildschirm-Layout zu bearbeiten. Sie funktionieren auch dann, wenn die normale Bildschirm-Anpassung deaktiviert ist.

Typische Beispiele:

- Einen gemeinsamen Button- und Slider-Stil für alle Bildschirme verwenden.
- Menü-Hintergrund, Panorama und Menü-Musik global ersetzen.
- Globales Start-/Fensterverhalten anwenden (GUI-Skalierung, Vollbild, Fenstertitel/-symbol).
- Vanilla-Button-Texturen global ohne Resource Pack ersetzen.
- Vanilla-Menü-Musik global ohne Resource Pack ersetzen.

# Wo du sie findest

Öffne die **Menüleiste** von FancyMenu, während du **nicht** im Layout-Editor bist, dann **Anpassung -> Globale Anpassungen**.

# Was du anpassen kannst

## Globales Verhalten und Start

- [**Spiel-Intro**](./game-intro) (ein Intro-Video oder eine Animation, die vor dem Titelscreen abgespielt wird)
- **Welt-Symbole im Einzelspieler-Bildschirm**
- **Server-Symbole im Mehrspieler-Bildschirm**
- [**Nahtloses Weltladen**](./seamless-world-loading) (verwendet einen aktuellen Weltscreenshot als Hintergrund des Ladebildschirms)
- [**Benutzerdefiniertes Fenstersymbol**](./window-customization#custom-icon)
- [**Benutzerdefinierter Fenstertitel**](./window-customization#custom-title)
- **Standard-GUI-Skalierung**
- **Beim Starten Vollbild erzwingen**

## Button-Design

- **Benutzerdefinierte Button-Texturen** (Normal-/Hover-/Inaktiv-Zustand, transparenter Modus, [Nine-Slice](./nine-slicing-and-tiling) + Randgrößen)
- **Button-Beschriftungen** (Unterstreichung bei Hover, Basis-/Hover-Farbe, Skalierung, Schatten)

## Slider-Design

- **Benutzerdefinierte Slider-Texturen**
- **Slider-Hintergrundtextur** (Textur, transparenter Modus, [Nine-Slice](./nine-slicing-and-tiling) + Randgrößen)
- **Slider-Grifftexturen** (Normal-/Hover-/Inaktiv-Zustand, [Nine-Slice](./nine-slicing-and-tiling) + Randgrößen)
- **Slider-Beschriftungen** (Unterstreichung bei Hover, Basis-/Hover-Farbe, Skalierung, Schatten)

## Menü-Design und Audio

- [**Benutzerdefinierte Menü-Hintergrundtextur**](./menu-backgrounds)
- [**Benutzerdefiniertes Menü-Hintergrundpanorama**](./panoramas)
- **Vanilla-Menü-Musik abspielen** (Abspielen der Vanilla-Menü-Musik aktivieren/deaktivieren)
- [**Benutzerdefinierte Menü-Musiktitel**](./background-music)
- **Benutzerdefinierter Klick-Sound für Button/Slider**

# Benutzerdefinierte Menü-Musiktitel

Verwende **Benutzerdefinierte Menü-Musiktitel**, um eine zufällige Titelliste für Menüs zu erstellen.

> [!IMPORTANT]
> Globale benutzerdefinierte Menü-Titel werden nur abgespielt, wenn keine Welt geladen ist, z. B. auf dem Titelscreen. Verwende ein [**Audio**-Element](./elements#audio) für Menü-Audio innerhalb einer Welt.

Konfigurierte Titel verwenden den Musik-Soundkanal und ersetzen die Vanilla-Menü-Musik in unterstützten Menüs ohne geladene Welt.

- Der erste Titel startet nach etwa fünf Sekunden.
- Weitere Titel starten nach einer zufälligen Verzögerung von etwa ein bis dreißig Sekunden.
- Titel werden zufällig ausgewählt.
- Bei mehreren Titeln wird der vorherige Titel nicht zweimal hintereinander ausgewählt.

Verwalte die Titelliste über **Benutzerdefinierte Menü-Musiktitel**:

- Öffne **Benutzerdefinierte Menü-Musiktitel**, um **Menü-Musiktitel verwalten** zu öffnen.
- Verwende **Titel hinzufügen**, um Audioquellen hinzuzufügen.
- Verwende **Titel entfernen**, um einen Eintrag zu entfernen.
- Verwende **Titel löschen**, um alle Einträge zu entfernen.
