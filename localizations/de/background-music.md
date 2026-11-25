---
title: Hintergrundmusik im Menü
description: 'Passe die Musik an, die in Menüs abgespielt wird.'
sourceBlobSha: 46d219f5573b915991f23082cfbc42e6ed11d132
---

# Hintergrundmusik im Menü

FancyMenu kann die Vanilla-Menümusik deaktivieren, eine globale Titelliste abspielen oder [Audio-Elemente](/elements#audio) für layoutbezogene Musik verwenden.

# Globale Menümusik

Öffne außerhalb des Layout-Editors **Anpassung -> Globale Anpassungen**, um zu den [**Globalen Anpassungen**](/global-customizations) zu gelangen.

Verwende diese Einstellungen:

- **Vanilla-Menümusik abspielen** aktiviert oder deaktiviert die Vanilla-Menümusik global.
- **Benutzerdefinierte Menümusiktitel** verwaltet die globale Ersatz-Titelliste.

> [!IMPORTANT]
> Globale benutzerdefinierte Titel werden nur abgespielt, wenn keine Welt geladen ist, zum Beispiel auf dem Titelbildschirm. Verwende ein [**Audio**-Element](/elements#audio) für Audio in Menüs innerhalb einer Welt.

Globale Titel verwenden den Musik-Soundkanal. Der erste Titel beginnt nach etwa fünf Sekunden; für spätere Titel wird eine zufällige Verzögerung von etwa einer bis dreißig Sekunden festgelegt. Die Auswahl erfolgt zufällig. Wenn mehr als ein Titel konfiguriert ist, wird der vorherige Titel nicht unmittelbar erneut abgespielt.

# Musik für einzelne Bildschirme steuern

Füge einem Layout ein [**Musik-Controller**-Element](/elements#music-controller) hinzu, um die Vanilla-Musik für diesen Bildschirm zu steuern:

1. Klicke im Editor mit der rechten Maustaste auf den Hintergrund.
2. Wähle **Neues Element -> Musik-Controller**.
3. Konfiguriere Menü- und Weltmusik getrennt.

Das Element unterstützt [Ladebedingungen](/conditions).

Wenn du die Menümusik mit einem Musik-Controller deaktivierst, wird auf diesem Bildschirm auch die Wiedergabe der globalen benutzerdefinierten Menümusiktitel verhindert.

# Benutzerdefinierte Musik mit Audio-Elementen

Verwende ein [**Audio**-Element](/elements#audio), wenn du Folgendes benötigst:

- Unterschiedliche Musik auf verschiedenen Bildschirmen.
- Musik auf Bildschirmen innerhalb einer Welt.
- Layoutbedingungen, geordnete Wiedergabelisten, Zufallswiedergabe-Einstellungen, Lautstärkeregelung oder Kanalsteuerung.

Platziere ein [Audio-Element](/elements#audio) in einem [universellen Layout](/universal-layouts), damit derselbe Player auf unterstützten Bildschirmen aktiv bleibt, auf denen dieses Layout geladen wird. Die Bildschirm-Anpassung muss auf jedem normalen Bildschirm aktiviert sein, auf den das universelle Layout angewendet werden soll.
