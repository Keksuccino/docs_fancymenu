---
title: Button- und Slider-Vorlagen
description: >-
  Wie Button-/Slider-Vorlagen verwendet werden, um ein bestimmtes
  Button-/Slider-Design auf ALLE Buttons gleichzeitig anzuwenden.
---

# Button-Elemente als Vorlagen für Buttons und Slider verwenden

Es ist möglich, ein Button-Element als Vorlage für andere Buttons und sogar Slider zu verwenden. Dadurch können Sie ein bestimmtes Button-/Slider-Design auf ALLE Buttons/Slider in einem Menü oder sogar auf alle Menüs gleichzeitig anwenden, wenn Sie ein universelles Layout verwenden.

> [!IMPORTANT]
> Verwenden Sie nach Möglichkeit [Globale Anpassungen](./global-customizations) für eine umfassende Standard-Button- und Slider-Formatierung. Nutzen Sie Button-/Slider-Vorlagen, wenn das Verhalten layoutspezifisch sein muss.

# Wichtig, bevor Sie beginnen

Für einen einzelnen Button oder Slider: **Klicken Sie ihn im Editor mit der rechten Maustaste an** und bearbeiten Sie direkt seine **Hintergrund-Texturen** oder die Texturen des Slider-Griffs.

# Was ist ein Vorlagen-Button?

Ein Vorlagen-Button ist eine spezielle Art von benutzerdefiniertem Button in FancyMenu, mit der Sie steuern können, wie andere Buttons und Slider aussehen und funktionieren. Es ist so, als würden Sie ein Master-Design erstellen, dem viele andere Elemente folgen.

Wenn Sie einen Vorlagen-Button erstellen, können Sie dafür sorgen, dass viele Buttons oder Slider dieselben Eigenschaften teilen:
- Größe (Breite und Höhe)
- Position
- Sichtbarkeit
- Opazität (wie durchsichtig sie sind)
- Textbeschriftungen
- **Button-Texturen** (werden automatisch gemeinsam genutzt, wenn benutzerdefinierte Texturen gesetzt sind)

Das ist sehr hilfreich, wenn Ihr Menü einheitlich aussehen soll oder wenn Sie viele Buttons auf einmal aktualisieren müssen!

# Wer kann Vorlagen verwenden?

Nur **benutzerdefinierte Buttons** können als Vorlagen verwendet werden. Diese Vorlagen können jedoch auf folgende Elemente angewendet werden:
- Vanilla-Buttons (die Standard-Minecraft-Buttons)
- Benutzerdefinierte Buttons (Buttons, die Sie in FancyMenu erstellen)
- Vanilla-Slider (z. B. Lautstärkeregler)
- Benutzerdefinierte Slider (Slider, die Sie in FancyMenu erstellen)

# So erstellen Sie einen Vorlagen-Button

1. Öffnen Sie den FancyMenu-Editor für den Bildschirm, den Sie anpassen möchten
2. Fügen Sie Ihrem Layout ein neues benutzerdefiniertes Button-Element hinzu
3. Klicken Sie mit der rechten Maustaste auf Ihren neuen Button
4. Wählen Sie im Menü "Template Settings" aus
5. Klicken Sie auf "Is Template: ON", um den Vorlagenmodus zu aktivieren

Ihr Button ist nun als Vorlage für andere Buttons und Slider bereit!

# Optionen für das Teilen von Vorlagen

Sie können auswählen, auf welche Elementtypen Ihre Vorlage angewendet wird:
- **Buttons** - Ihre Vorlage betrifft nur Buttons (sowohl Vanilla- als auch benutzerdefinierte Buttons)
- **Sliders** - Ihre Vorlage betrifft nur Slider (sowohl Vanilla- als auch benutzerdefinierte Slider)

So stellen Sie diese Option ein:
1. Klicken Sie mit der rechten Maustaste auf Ihren Vorlagen-Button
2. Gehen Sie zu "Template Settings"
3. Klicken Sie auf "Share With: [Current Option]", um zwischen den Optionen zu wechseln

> [!WARNING]
> **Wichtig**: Sie können zwei Vorlagen gleichzeitig aktiv haben – eine für Buttons UND eine für Slider. Das bedeutet, dass Sie auf demselben Bildschirm getrennte Vorlagen-Designs für verschiedene Elementtypen erstellen können!


# Was kann per Vorlage übernommen werden

Sie können genau steuern, welche Eigenschaften Ihre Vorlage an andere Elemente weitergibt:

## Eigenschaften, die ein- und ausgeschaltet werden können:

1. Klicken Sie mit der rechten Maustaste auf Ihren Vorlagen-Button
2. Gehen Sie zu "Template Settings"
3. Aktivieren oder deaktivieren Sie eine dieser Optionen:
   - **Width** - Macht alle betroffenen Elemente so breit wie Ihre Vorlage
   - **Height** - Macht alle betroffenen Elemente so hoch wie Ihre Vorlage
   - **X Position** - Setzt alle betroffenen Elemente auf dieselbe X-Koordinate wie Ihre Vorlage
   - **Y Position** - Setzt alle betroffenen Elemente auf dieselbe Y-Koordinate wie Ihre Vorlage
   - **Opacity** - Gibt allen betroffenen Elementen dieselbe Transparenz wie Ihre Vorlage
   - **Visibility** - Steuert, ob betroffene Elemente angezeigt oder ausgeblendet werden
   - **Label** - Veranlasst alle betroffenen Elemente, denselben Text wie Ihre Vorlage zu verwenden

## Eigenschaften, die immer übernommen werden:

- **Button-Texturen** - Wenn Sie auf Ihrer Vorlage benutzerdefinierte Texturen festlegen, werden diese automatisch auf alle betroffenen Elemente angewendet
  - Anders als bei anderen Eigenschaften kann das Teilen von Texturen nicht deaktiviert werden
  - Texturen werden nur angewendet, wenn auf der Vorlage tatsächlich benutzerdefinierte Texturen gesetzt sind
  - Wenn keine benutzerdefinierten Texturen gesetzt sind, werden die ursprünglichen Element-Texturen verwendet

# Das Erscheinungsbild der Vorlage anpassen

Ihr Vorlagen-Button kann wie jeder andere Button angepasst werden:

1. Klicken Sie mit der rechten Maustaste auf Ihren Vorlagen-Button
2. Sie können Folgendes festlegen:
   - Button-Texturen (Normal-, Hover- und Inaktiv-Zustand)
   - Beschriftungen (normal und Hover)
   - Sounds (Hover und Klick)
   - Tooltips

Für Buttons können Sie benutzerdefinierte Texturen für verschiedene Zustände festlegen:
- Normale Hintergrundtextur (wenn nicht interagiert wird)
- Hover-Hintergrundtextur (wenn sich die Maus darüber befindet)
- Inaktive Hintergrundtextur (wenn der Button deaktiviert ist)

Für Slider können Sie außerdem festlegen:
- Texturen des Slider-Griffs
- Texturen des Slider-Hintergrunds

# Wichtige Tipps

1. **Vorlagen-Buttons erscheinen nicht im Spiel** - Sie sind nur im Editor sichtbar, platzieren Sie sie also dort, wo es praktisch ist.

2. **Sie können zwei Vorlagen gleichzeitig aktiv haben** - Eine Vorlage für Buttons und eine Vorlage für Slider können gleichzeitig aktiv sein.

3. **Nur eine Vorlage pro Typ ist aktiv** - Wenn Sie mehrere Button-Vorlagen haben, wird nur die oberste in Ihrer Elementliste für Buttons verwendet. Dasselbe gilt für Slider-Vorlagen.

4. **Änderungen an der Vorlage werden sofort übernommen** - Wenn Sie Ihre Vorlage bearbeiten, werden alle betroffenen Buttons und Slider sofort aktualisiert.

5. **Verwenden Sie den richtigen Freigabemodus** - Denken Sie daran, dass der Modus "Buttons" keine Slider betrifft und der Modus "Sliders" keine Buttons betrifft.

6. **Eigenschaften gezielt anwenden** - Sie müssen nicht alle Eigenschaften übernehmen. Zum Beispiel könnten Sie nur Texturen und Größe per Vorlage festlegen, während Elemente ihre ursprünglichen Positionen behalten.

7. **Texturen werden immer übernommen, wenn sie gesetzt sind** - Anders als bei anderen Eigenschaften werden alle benutzerdefinierten Texturen, die Sie auf der Vorlage festlegen, automatisch mit passenden Elementen geteilt. Sie müssen diese Funktion nicht ein- oder ausschalten.

# Anwendungsbeispiele

- Einen einheitlichen Stil für alle Buttons auf einem Bildschirm erstellen
- Alle Slider mit einer separaten Vorlage an Ihr eigenes Design anpassen
- Einen "Unsichtbar-Modus" erstellen, in dem Sie mehrere Buttons gleichzeitig ein- oder ausblenden können
- Die Größe vieler Buttons mit nur einer Änderung anpassen
- Allen Buttons in Ihrem Menü dieselben benutzerdefinierten Texturen und Sounds geben
