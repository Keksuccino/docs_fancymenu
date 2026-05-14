---
title: Button- und Slider-Vorlagen
description: >-
  Wie man Button-/Slider-Vorlagen verwendet, um ein bestimmtes
  Button-/Slider-Design auf ALLE Buttons gleichzeitig anzuwenden.
---

# Verwendung von Button-Elementen als Vorlagen für Buttons und Slider

Es ist möglich, ein Button-Element als Vorlage für andere Buttons und sogar Slider zu verwenden. Dadurch kannst du ein bestimmtes Button-/Slider-Design auf ALLE Buttons/Slider in einem Menü oder sogar auf alle Menüs gleichzeitig anwenden, wenn du ein universelles Layout verwendest.

> [!IMPORTANT]
> Seit FancyMenu 3.9.0 wird empfohlen, nach Möglichkeit [Globale Anpassungen](/global-customizations) statt Button-/Slider-Vorlagen zu verwenden, da sich damit Standard-Button- und Slider-Texturen global ohne Resource Pack ersetzen lassen. Verwende globale Anpassungen für umfassendes Vanilla-UI-Styling und Vorlagen nur dann, wenn du layout-spezifisches Verhalten benötigst.

# Wichtig, bevor du beginnst

Wenn du nur die Textur eines einzelnen Buttons oder Sliders ändern möchtest, ist es am einfachsten und empfohlen, im Editor einfach per **Rechtsklick** auf den Button oder Slider (Vanilla und Custom) zu klicken. Dort gibt es eine Option zum Festlegen der **Hintergrundtexturen** (und der Slider-Grifftexturen) für Buttons und Slider.

# Was ist ein Vorlagen-Button?

Ein Vorlagen-Button ist eine besondere Art von Custom-Button in FancyMenu, mit der du steuern kannst, wie andere Buttons und Slider aussehen und sich verhalten. Es ist, als würdest du ein Master-Design erstellen, dem viele andere Elemente folgen.

Wenn du einen Vorlagen-Button erstellst, können viele Buttons oder Slider dieselben Eigenschaften teilen:
- Größe (Breite und Höhe)
- Position
- Sichtbarkeit
- Deckkraft (wie durchsichtig sie sind)
- Textbeschriftungen
- **Button-Texturen** (werden automatisch übernommen, wenn benutzerdefinierte Texturen gesetzt sind)

Das ist extrem hilfreich, wenn du dein Menü einheitlich gestalten möchtest oder wenn du viele Buttons auf einmal aktualisieren musst!

# Wer kann Vorlagen verwenden?

Nur **Custom-Buttons** können als Vorlagen dienen. Diese Vorlagen können jedoch angewendet werden auf:
- Vanilla-Buttons (die Standard-Minecraft-Buttons)
- Custom-Buttons (Buttons, die du in FancyMenu erstellst)
- Vanilla-Slider (z. B. Lautstärkeregler)
- Custom-Slider (Slider, die du in FancyMenu erstellst)

# So erstellst du einen Vorlagen-Button

1. Öffne den FancyMenu-Editor für den Bildschirm, den du anpassen möchtest
2. Füge deinem Layout ein neues Custom-Button-Element hinzu
3. Klicke mit der rechten Maustaste auf deinen neuen Button
4. Wähle im Menü "Template Settings"
5. Klicke auf "Is Template: ON", um den Vorlagenmodus zu aktivieren

Dein Button ist nun bereit, als Vorlage für andere Buttons und Slider zu dienen!

# Optionen zum Teilen der Vorlage

Du kannst auswählen, welche Elementtypen deine Vorlage beeinflussen soll:
- **Buttons** - Deine Vorlage beeinflusst nur Buttons (sowohl Vanilla als auch Custom)
- **Sliders** - Deine Vorlage beeinflusst nur Slider (sowohl Vanilla als auch Custom)

So stellst du diese Option ein:
1. Klicke mit der rechten Maustaste auf deinen Vorlagen-Button
2. Gehe zu "Template Settings"
3. Klicke auf "Share With: [Current Option]", um zwischen den Optionen zu wechseln

> **Wichtig**: Du kannst zwei Vorlagen gleichzeitig aktiv haben - eine für Buttons UND eine für Slider. Das bedeutet, dass du auf demselben Bildschirm getrennte Vorlagendesigns für verschiedene Elementtypen erstellen kannst!
{.is-warning}


# Was kann per Vorlage übernommen werden

Du kannst genau steuern, welche Eigenschaften deine Vorlage mit anderen Elementen teilt:

## Eigenschaften, die ein-/ausgeschaltet werden können:

1. Klicke mit der rechten Maustaste auf deinen Vorlagen-Button
2. Gehe zu "Template Settings" 
3. Schalte eine der folgenden Optionen um:
   - **Breite** - Macht alle betroffenen Elemente so breit wie deine Vorlage
   - **Höhe** - Macht alle betroffenen Elemente so hoch wie deine Vorlage
   - **X-Position** - Platziert alle betroffenen Elemente auf derselben X-Koordinate wie deine Vorlage
   - **Y-Position** - Platziert alle betroffenen Elemente auf derselben Y-Koordinate wie deine Vorlage
   - **Deckkraft** - Gibt allen betroffenen Elementen dieselbe Transparenz wie deine Vorlage
   - **Sichtbarkeit** - Steuert, ob betroffene Elemente angezeigt oder ausgeblendet werden
   - **Beschriftung** - Lässt alle betroffenen Elemente denselben Text wie deine Vorlage verwenden

## Eigenschaften, die immer geteilt werden:

- **Button-Texturen** - Wenn du auf deiner Vorlage benutzerdefinierte Texturen festlegst, werden sie automatisch auf alle betroffenen Elemente angewendet
  - Anders als bei anderen Eigenschaften kann die Texturweitergabe nicht deaktiviert werden
  - Texturen werden nur angewendet, wenn auf der Vorlage tatsächlich benutzerdefinierte Texturen gesetzt sind
  - Wenn keine benutzerdefinierten Texturen gesetzt sind, werden die ursprünglichen Elementtexturen verwendet

# Das Aussehen der Vorlage anpassen

Deinen Vorlagen-Button kannst du genau wie jeden anderen Button anpassen:

1. Klicke mit der rechten Maustaste auf deinen Vorlagen-Button
2. Du kannst festlegen:
   - Button-Texturen (Normal-, Hover- und Inaktiv-Zustand)
   - Beschriftungen (Normal und Hover)
   - Sounds (Hover und Klick)
   - Tooltips

Für Buttons kannst du benutzerdefinierte Texturen für verschiedene Zustände festlegen:
- Normaler Hintergrund (wenn keine Interaktion stattfindet)
- Hover-Hintergrund (wenn sich die Maus darüber befindet)
- Inaktiver Hintergrund (wenn der Button deaktiviert ist)

Für Slider kannst du außerdem festlegen:
- Slider-Grifftexturen
- Slider-Hintergrundtexturen

# Wichtige Tipps

1. **Vorlagen-Buttons erscheinen nicht im Spiel** - Sie sind nur im Editor sichtbar, also platziere sie dort, wo es praktisch ist.

2. **Du kannst zwei Vorlagen gleichzeitig aktiv haben** - Eine Vorlage für Buttons und eine für Slider kann gleichzeitig aktiv sein.

3. **Nur eine Vorlage pro Typ ist aktiv** - Wenn du mehrere Button-Vorlagen hast, wird nur die oberste in deiner Elementliste für Buttons verwendet. Dasselbe gilt für Slider-Vorlagen.

4. **Änderungen an der Vorlage werden sofort übernommen** - Wenn du deine Vorlage bearbeitest, werden alle betroffenen Buttons und Slider sofort aktualisiert.

5. **Verwende den richtigen Freigabemodus** - Beachte, dass der Modus "Buttons" keine Slider beeinflusst und der Modus "Sliders" keine Buttons beeinflusst.

6. **Eigenschaften gezielt anwenden** - Du musst nicht alle Eigenschaften übernehmen. Du kannst zum Beispiel nur Texturen und Größe als Vorlage verwenden, während die Elemente ihre ursprünglichen Positionen behalten.

7. **Texturen werden immer geteilt, wenn sie gesetzt sind** - Im Gegensatz zu anderen Eigenschaften werden alle benutzerdefinierten Texturen, die du auf die Vorlage anwendest, automatisch mit passenden Elementen geteilt. Du musst diese Funktion nicht ein- oder ausschalten.

# Anwendungsbeispiele

- Einen einheitlichen Stil für alle Buttons auf einem Bildschirm erstellen
- Alle Slider mit einer separaten Vorlage an dein benutzerdefiniertes Theme anpassen
- Einen "Versteckmodus" erstellen, in dem du mehrere Buttons gleichzeitig ein- oder ausblenden kannst
- Die Größe vieler Buttons mit nur einer einzigen Änderung anpassen
- Allen Buttons in deinem Menü dieselben benutzerdefinierten Texturen und Sounds geben
