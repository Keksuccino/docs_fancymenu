---
title: Hintergrundmusik im Menü
description: Passe die in Menüs abgespielte Musik an.
---

# Hintergrundmusik im Menü

FancyMenu kann die Vanilla-Menümusik deaktivieren, eine globale Titelliste abspielen oder [Audio-Elemente](./elements#audio) für layoutspezifische Musik verwenden.

# Globale Menümusik

Öffne [**Globale Anpassungen**](./global-customizations) außerhalb des Layout-Editors über **Anpassung -> Globale Anpassungen**.

Verwende diese Einstellungen:

- **Vanilla-Menümusik abspielen** aktiviert oder deaktiviert die Vanilla-Menümusik global.
- **Benutzerdefinierte Menü-Musiktitel** verwaltet die globale Ersatz-Titelliste.

> [!IMPORTANT]
> Globale benutzerdefinierte Menütitel werden nur abgespielt, wenn keine Welt geladen ist, z. B. auf dem Titelscreen. Verwende ein [**Audio**-Element](./elements#audio) für Menüdudio innerhalb einer Welt.

Globale Titel verwenden den Musik-Soundkanal. Der erste Titel startet nach etwa fünf Sekunden; spätere Titel verwenden eine zufällige Verzögerung von etwa einer bis dreißig Sekunden. Die Auswahl ist zufällig und vermeidet bei mehr als einem konfigurierten Titel das sofortige Wiederholen des vorherigen Titels.

# Musiksteuerung pro Bildschirm

Füge einem Layout ein [**Musik-Controller**-Element](./elements#music-controller) hinzu, um die Vanilla-Musik für diesen Bildschirm zu steuern:

1. Klicke mit der rechten Maustaste auf den Hintergrund des Editors.
2. Wähle **Neues Element -> Musik-Controller**.
3. Konfiguriere Menümusik und Weltmusik separat.

Das Element unterstützt [Ladebedingungen](./conditions).

Das Deaktivieren der Menümusik mit einem Musik-Controller verhindert auch, dass die globale benutzerdefinierte Menü-Titelliste auf diesem Bildschirm abgespielt wird.

# Benutzerdefinierte Musik mit Audio-Elementen

Verwende ein [**Audio**-Element](./elements#audio), wenn du Folgendes brauchst:

- Unterschiedliche Musik auf verschiedenen Bildschirmen.
- Musik in Bildschirmen innerhalb einer Welt.
- Layout-Anforderungen, geordnete Wiedergabelisten, Shuffle-Einstellungen, Lautstärke oder Kanalsteuerung.

Platziere ein [Audio-Element](./elements#audio) in einem [universellen Layout](./universal-layouts), um denselben Player auf allen unterstützten Bildschirmen aktiv zu halten, die dieses Layout laden. Die Bildschirmanpassung muss auf jedem normalen Bildschirm aktiviert sein, auf dem das universelle Layout angewendet werden soll.
