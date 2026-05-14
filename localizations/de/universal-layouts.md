---
title: Universelle Layouts
description: Wie man universelle Layouts erstellt und verwendet.
---

# Was sind universelle Layouts?

Universelle Layouts sind eine leistungsstarke Funktion in FancyMenu, mit der du Layouts erstellen kannst, die auf **mehrere Bildschirme** angewendet werden können, statt nur auf einen bestimmten Bildschirm. Dadurch sind sie unglaublich nützlich, um konsistente UI-Elemente zu erstellen, die in deinem gesamten Spiel angezeigt werden.

Stell dir universelle Layouts als "globale" Layouts vor, die überall angezeigt werden können.

# Warum universelle Layouts verwenden?

Universelle Layouts sind sehr hilfreich, wenn du:

- denselben Hintergrund auf allen Bildschirmen hinzufügen möchtest
- ein Logo oder einen Text erstellen möchtest, der auf vielen Bildschirmen erscheint
- Audio-Elemente über mehrere Bildschirme hinweg weiter abspielen lassen möchtest
- ein einheitliches Erscheinungsbild in deinem gesamten Spiel aufbauen möchtest

# Wie universelle Layouts funktionieren

Wenn du ein universelles Layout erstellst, wird es standardmäßig mit **jedem Bildschirm** im Spiel geladen. Das bedeutet, dass alle Elemente, die du zu einem universellen Layout hinzufügst (wie Buttons, Bilder oder Text), auf allen Bildschirmen erscheinen.

Aber keine Sorge! Es ist auch möglich, das universelle Layout nur auf bestimmten Bildschirmen zu laden! Scrolle dafür zu den Abschnitten **Blacklist** und **Whitelist** weiter unten.

# Ein universelles Layout erstellen

1. Öffne einen beliebigen Bildschirm im Spiel
2. Drücke **Strg+Alt+C**, um das Anpassungsmenü anzuzeigen
3. Gehe zu **Layouts → Neu → Für alle Bildschirme [Universell]**
4. Gestalte dein Layout mit Elementen wie Bildern, Text oder Buttons
5. Speichere dein Layout mit einem aussagekräftigen Namen

# Verwalten, auf welchen Bildschirmen dein universelles Layout angezeigt wird

## Die Blacklist verwenden

Mit der Blacklist kannst du festlegen, auf welchen Bildschirmen dein universelles Layout **nicht** erscheinen soll:

1. Klicke im Layout-Editor mit der rechten Maustaste auf den Hintergrund
2. Wähle **Layout-Einstellungen → Optionen für universelle Layouts**
3. Klicke auf **Bildschirm zur Blacklist hinzufügen**
4. Gib die Bildschirm-ID ein (z. B. `title_screen` für den Titelbildschirm)

Jetzt wird dein universelles Layout auf allen Bildschirmen angezeigt, **außer** auf denjenigen, die du auf die Blacklist gesetzt hast.

## Die Whitelist verwenden

Die Whitelist ist das Gegenteil – sie zeigt dein universelles Layout **nur** auf bestimmten Bildschirmen an:

1. Klicke im Layout-Editor mit der rechten Maustaste auf den Hintergrund
2. Wähle **Layout-Einstellungen → Optionen für universelle Layouts**
3. Klicke auf **Bildschirm zur Whitelist hinzufügen**
4. Gib für jeden Bildschirm, auf dem das Layout erscheinen soll, die entsprechende Bildschirm-ID ein

Wenn du eine Whitelist verwendest, wird dein universelles Layout **nur** auf den Bildschirmen angezeigt, die du aufgelistet hast.

# Bildschirm-IDs finden

Um Bildschirme zur Whitelist oder Blacklist hinzuzufügen, musst du ihre IDs kennen:

1. Gehe zu dem Bildschirm, den du identifizieren möchtest
2. Drücke **Strg+Alt+C**, um das Anpassungsmenü zu öffnen
3. Klicke auf **Anpassung → ID des aktuellen Bildschirms kopieren**
4. Die ID wurde jetzt in deine Zwischenablage kopiert

Du kannst diese ID in die Whitelist oder Blacklist einfügen.

# Anpassung für alle Bildschirme aktivieren

Es ist nicht möglich, die Anpassung für alle Bildschirme auf einmal zu aktivieren.
Das ist so beabsichtigt und verhindert, dass Leute ihr Spiel versehentlich unbrauchbar machen, weil sie die Anpassung für einen modifizierten Bildschirm aktivieren, der nicht unterstützt wird.

# Erweiterte Tipps

## Die Lade-Reihenfolge verwalten

Wenn du sowohl universelle Layouts als auch bildschirmspezifische Layouts hast, werden universelle Layouts ZUERST geladen. Das bedeutet, dass bildschirmspezifische Layouts Elemente aus universellen Layouts überschreiben können.

## Ladeanforderungen

Du kannst deinem universellen Layout Ladeanforderungen hinzufügen, sodass es nur unter bestimmten Bedingungen geladen wird:

1. Klicke im Editor mit der rechten Maustaste
2. Wähle **Layout-Einstellungen → Layout-weite Anforderungen**
3. Füge Bedingungen wie Tageszeit, Betriebssystem oder andere Anforderungen hinzu
