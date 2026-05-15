---
title: Planer
description: 'FancyMenu-Aktionsskripte zeitgesteuert ausführen, sogar im Hintergrund.'
---

# Planer

Planer führen ein Aktionsskript nach einem Timer aus.

Sie sind global (also nicht an einen bestimmten Bildschirm gebunden) und können daher weiterlaufen, selbst wenn keine GUI geöffnet ist.

Verwende Planer, wenn du Automatisierung über die Zeit hinweg statt einer einmaligen Aktion möchtest.
Sie sind nützlich für wiederholte Aufgaben, verzögerte Aufgaben und Hintergrundlogik.

Typische Beispiele:

- Variablen oder Textelemente alle paar Sekunden aktualisieren (zum Beispiel eine benutzerdefinierte Uhr-/Statusanzeige).
- Regelmäßige Prüfungen ausführen und Aktionen auslösen, wenn Bedingungen erfüllt sind.
- Menüeffekte, Sounds oder anderes skriptgesteuertes Verhalten in einer zeitgesteuerten Schleife starten.
- Eine Aktion verzögern und später ausführen, ohne dass ein Bildschirm geöffnet bleiben muss.

# Wo du sie findest

Öffne die **Menüleiste** von FancyMenu, während du dich **nicht** im Layout-Editor befindest, dann **Anpassung -> Planer verwalten**.

# Schnellstart

1. Öffne **Anpassung -> Planer verwalten**.
2. Klicke auf **Planer hinzufügen**.
3. Erstelle das **Aktionsskript** des Planers (dies wird bei jedem Planer-Tick einmal ausgeführt).
4. Wähle den Planer aus und klicke auf **Einstellungen bearbeiten**.
5. Konfiguriere:
   - **Planer-ID** (eindeutiger Planername; wird von Start-/Stopp-Aktionen und Anforderungen verwendet; erlaubt: `a-z`, `0-9`, `.`, `_`, `-`)
   - **Startverzögerung (ms)** (Wartezeit, bevor der erste Tick ausgeführt wird)
   - **Tick-Verzögerung (ms)** (Wartezeit zwischen den Ticks; `0` = jeder Spieltick)
   - **Ticks ausführen** (wie viele Ticks ausgeführt werden sollen, bevor automatisch gestoppt wird; `0` = dauerhaft)
   - **Beim Start laden** (startet diesen Planer automatisch, wenn FancyMenu geladen wird)
6. Verwende **Jetzt starten**, um ihn sofort auszuführen.
7. Verwende **Jetzt stoppen**, um ihn zu beenden.

# Planer steuern und überwachen

Es gibt Aktionen und Anforderungen, um Planer zu steuern und ihren laufenden Status zu prüfen.

## Aktionen

- **Planer starten** nimmt die ID des Planers und startet ihn, falls er nicht bereits läuft.
- **Planer stoppen** nimmt ebenfalls die ID des Planers und beendet ihn.

## Anforderung

Um zu prüfen, ob ein Planer aktuell läuft, verwende die Anforderung **Planer läuft**, die die ID des Planers verwendet.

# Tipps

1. Verwende klare IDs wie `hud_update`, `menu_animation`, `music_fade`.
2. Beginne mit einer höheren Tick-Verzögerung (zum Beispiel `200`-`1000` ms) und reduziere sie nur bei Bedarf, um Leistung zu sparen.
3. Klicke in der Planerliste mit der rechten Maustaste auf einen Planer, um seine Aktionen schnell zu bearbeiten.
4. Doppelklicke in der Planerliste auf eine Planer-ID, um sie umzubenennen.
