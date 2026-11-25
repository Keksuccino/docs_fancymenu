---
title: Elemente ein- und ausblenden
description: >-
  So blendest du Elemente mit Bedingungen, Verzögerungen, Überblendungen und
  Deckkraft ein und aus und schaltest sie mit einer Schaltfläche um.
sourceBlobSha: 819fbc2639734fc8658f6fb65e9df6b1234e9cc5
---

# Elemente ein- und ausblenden

Elemente müssen nicht immer angezeigt werden. Sie können nur unter bestimmten Bedingungen erscheinen, etwas später eingeblendet werden, ein- und ausgeblendet werden oder sich per Schaltfläche ein- und ausschalten lassen.

<img width="800" alt="Ein Begrüßungstext wird einige Sekunden nach dem Öffnen des Bildschirms eingeblendet. Anschließend blendet eine Schaltfläche für die Serverregeln ein Regel-Panel ein und aus." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_visibility_toggle.gif?raw=true">

Im Layout-Editor werden Elemente immer angezeigt, damit du sie weiterhin bearbeiten kannst. Alles auf dieser Seite funktioniert außerhalb des Editors.

> [!TIP]
> Alle Bedingungen sind unter [Bedingungen](/conditions) aufgeführt.

# Elemente nur manchmal anzeigen

Klicke mit der rechten Maustaste auf ein Element und dann auf **Ladebedingungen**. Das Element wird nur angezeigt, wenn alle seine [Bedingungen](/conditions) erfüllt sind, zum Beispiel „die Maus befindet sich über dieser Schaltfläche“, „es ist Dezember“ oder „eine Variable hat diesen Wert“. FancyMenu prüft die Bedingungen ständig, sodass das Element sofort ein- und ausgeblendet wird.

- **Bedingungsmodus** Kehrt eine Bedingung um, zum Beispiel „NICHT Dezember“.
- Mit Gruppen kannst du „dieses ODER jenes“ festlegen.
- Auch Vanilla-Elemente haben **Ladebedingungen**. Wie du ein Element vollständig entfernst, erfährst du unter [Gelöschte Vanilla-Elemente](/deleted-vanilla-elements).

So fügst du Bedingungen hinzu und kombinierst sie: [Bedingungen](/conditions#adding-a-requirement).

## Einmal pro Sitzung laden

Klicke mit der rechten Maustaste auf ein Element und aktiviere **Einmal pro Sitzung laden**. Das Element wird beim ersten Öffnen des Bildschirms angezeigt. Sobald der Spieler zu einem anderen Bildschirm wechselt, bleibt es ausgeblendet, bis das Spiel neu gestartet wird.

Das ist praktisch für Hinweise, die nur einmal pro Spielstart angezeigt werden sollen, etwa „Drücke F1, um die Steuerung anzuzeigen“. Für dasselbe Prinzip in Aktionsskripten gibt es die Bedingung [**Nur einmal pro Sitzung**](/conditions#only-once-per-session).

# Elemente verzögert einblenden

## Einblenden verzögern

Klicke mit der rechten Maustaste auf ein Element und dann auf **Einblenden verzögern**:

- **Verzögerung**:
  - **Keine Verzögerung**: Das Element wird sofort angezeigt.
  - **Beim ersten Mal**: Die Verzögerung gilt nur beim ersten Einblenden des Elements nach dem Spielstart.
  - **Jedes Mal**: Die Verzögerung gilt bei jedem Öffnen des Bildschirms und jedes Mal, wenn die Bedingungen erneut erfüllt sind.
- **Verzögerung in Sekunden**: Wie lange gewartet wird, zum Beispiel `1.5`.

Wenn du die Fenstergröße änderst, beginnt die Verzögerung nicht von vorn.

## Ausblenden verzögern

Klicke mit der rechten Maustaste auf ein Element und dann auf **Ausblenden verzögern**. Wenn seine Bedingungen nicht mehr erfüllt sind, bleibt das Element noch **Verzögerung in Sekunden** lang sichtbar, bevor es verschwindet. Für **Verzögerung** gelten dieselben Optionen wie oben.

Beispielsweise bleibt ein Infokasten mit der Bedingung [**Maus über Element**](/conditions#is-element-hovered) für eine Schaltfläche noch 1 Sekunde sichtbar, nachdem die Maus die Schaltfläche verlassen hat.

# Ein- und Ausblenden

Klicke mit der rechten Maustaste auf ein Element und dann auf **Ein-/Ausblenden**:

- **Einblenden** und **Ausblenden**:
  - **Keine Überblendung**: Das Element wird sofort ein- oder ausgeblendet.
  - **Nur einmal**: Die Überblendung erfolgt nur beim ersten Mal nach dem Spielstart.
  - **Jedes Mal**: Die Überblendung erfolgt jedes Mal.
- **Einblendgeschwindigkeit** und **Ausblendgeschwindigkeit**: Bei `1` dauert eine Überblendung 2,5 Sekunden. `2` ist doppelt so schnell.

Elemente werden eingeblendet, wenn der Bildschirm geöffnet wird und wenn ihre Bedingungen erfüllt sind. Mit **Einblenden verzögern** beginnt die Überblendung erst nach Ablauf der Verzögerung.

Das Ausblenden erfolgt nur, wenn Bedingungen das Element ausblenden, nicht aber beim Schließen des Bildschirms.

# Deckkraft

Klicke mit der rechten Maustaste auf ein Element und dann auf **Deckkraft**: `1.0` bedeutet vollständig sichtbar, `0.5` halb durchsichtig und `0.0` unsichtbar. Die meisten Elemente verfügen über diese Einstellung.

Die Deckkraft unterstützt [Platzhalter](/placeholders) und [Variablen](/variables), zum Beispiel `$$panel_opacity`. Überblendungen beim Einblenden enden bei der Deckkraft des Elements.

# Elemente mit einer Schaltfläche umschalten

Mit einer Schaltfläche lassen sich Elemente ein- und ausblenden, zum Beispiel das Regel-Panel im GIF oben. Eine [Variable](/variables) speichert, ob das Panel angezeigt wird.

1. Klicke mit der rechten Maustaste auf das Panel und dann auf **Ladebedingungen**. Füge [**Variablenwert ist (FM-Variable)**](/conditions#is-variable-value-fm-variable) mit der Variable `show_rules` und dem Wert `true` hinzu.
2. Klicke mit der rechten Maustaste auf die Schaltfläche und dann auf **Aktionsskript bearbeiten**.
3. Klicke mit der rechten Maustaste auf den Skriptbereich und dann auf **IF-Anweisung hinzufügen**. Füge dieselbe Bedingung wie beim Panel hinzu.
4. Füge innerhalb der IF-Anweisung [**Variablenwert festlegen (FM-Variable)**](/action-scripts#set-variable-value-fm-variable) mit diesem Wert hinzu:

   ```
   show_rules:false
   ```

5. Klicke mit der rechten Maustaste auf die IF-Anweisung und dann auf **ELSE-Anweisung anhängen**. Füge innerhalb der ELSE-Anweisung **Variablenwert festlegen (FM-Variable)** mit diesem Wert hinzu:

   ```
   show_rules:true
   ```

Bei jedem Klick wird nun der Variablenwert umgeschaltet: Angezeigte Panels werden ausgeblendet und ausgeblendete Panels werden angezeigt. Alle Elemente mit derselben Bedingung werden gemeinsam ein- und ausgeblendet. Für einen fließenden Übergang stellst du **Einblenden** und **Ausblenden** des Panels auf **Jedes Mal**.

Weitere Informationen zu IF und ELSE findest du unter [Aktionsskripte](/action-scripts#if-else-if-and-else).

> [!NOTE]
> Variablen bleiben nach dem Schließen des Spiels erhalten, daher ist das Panel beim nächsten Start weiterhin geöffnet. Wenn es bei jedem Start geschlossen sein soll, klicke in **Variablen verwalten** mit der rechten Maustaste auf die Variable und aktiviere **Variable beim Spielstart löschen**.

## Zwischen Varianten wechseln

Mit einer Schaltfläche kannst du auch zwischen mehr als zwei Varianten wechseln, zum Beispiel zwischen drei Hintergründen:

1. Füge unter **Menüleiste -> Anpassung -> Variablen verwalten** die Textvariable `background` mit dem Wert `0` hinzu.
2. Weise den drei [Bildelementen](/elements#image) die Bedingung **Variablenwert ist (FM-Variable)** für `background` mit den Werten `0`, `1` und `2` zu.
3. Weise der Schaltfläche **Variablenwert festlegen (FM-Variable)** mit diesem Wert zu. Er durchläuft `0`, `1` und `2` und beginnt dann wieder bei `0`:

   ```
   background:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"getvariable","values":{"name":"background"}} + 1) % 3"}}
   ```

Für weitere Varianten änderst du die abschließende `3`. Informationen zur Berechnung findest du unter [**Taschenrechner**](/placeholders#calculator).

# Layouts ein- und ausschalten

So blendest du ein ganzes Layout ein oder aus:

- **Ladebedingungen [layoutweit]** im Rechtsklickmenü des Editorhintergrunds funktionieren wie die Bedingungen für Elemente. Siehe [Layoutweite Bedingungen](/conditions#layout-wide-requirements).
- Mit den Aktionen [**Layout umschalten**](/action-scripts#toggle-layout), [**Layout aktivieren**](/action-scripts#enable-layout) und [**Layout deaktivieren**](/action-scripts#disable-layout) kannst du ein Layout anhand seines Namens ein- und ausschalten.

Platziere die Schaltfläche in einem anderen Layout als dem, das sie ausschaltet. Andernfalls wird die Schaltfläche zusammen mit dem Layout ausgeblendet und kann es nicht wieder einschalten.
