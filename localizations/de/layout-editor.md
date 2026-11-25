---
title: Layout-Editor
description: >-
  So öffnest du den Layout-Editor, wählst Elemente aus, verschiebst und
  skalierst sie, ordnest sie mit Ebenen und Gruppen an, speicherst dein Layout
  und nutzt alle Tastenkürzel des Editors.
sourceBlobSha: c247d44a67ac209f2a0b638cb4748b408c7e7b13
---

# Layout-Editor

Im Layout-Editor erstellst du [Layouts](/home#your-first-layout): Du fügst Elemente hinzu, verschiebst und skalierst sie und änderst das Menü um sie herum. Das Menü wird so angezeigt, wie Spieler es sehen. So siehst du sofort, wie es aussieht.

<img width="800" alt="Einen Titel verschieben, verbreitern und leicht versetzen, dann zwei Schaltflächen auswählen, kopieren und einfügen, die Kopien nach unten ziehen und den Vorgang rückgängig machen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_basics.gif?raw=true">

# Editor öffnen

1. Öffne das Menü, das du ändern möchtest, zum Beispiel den Titelbildschirm.
2. Klicke auf **Menüleiste -> Anpassung -> Anpassung des aktuellen Bildschirms**, sodass **Aktiviert** angezeigt wird.
3. Klicke auf **Menüleiste -> Anpassung -> Layouts -> Neu -> Für aktuellen Bildschirm**.

- Mit **Für alle Bildschirme [Universal]** erstellst du ein [universelles Layout](/universal-layouts), das in jedem Menü angezeigt wird.
- Deine vorhandenen Layouts werden ebenfalls unter **Layouts** aufgelistet. Bewege den Mauszeiger über eines davon und klicke auf **Layout bearbeiten**.
- In jedem Menü öffnet `Ctrl + Alt + L` das Layout, das du zuletzt bearbeitet hast. Siehe [Tastenkürzel der Menüleiste](/home#menu-bar-shortcuts).

# Der Editor auf einen Blick

<img width="800" alt="Der Layout-Editor mit einer ausgewählten Schaltfläche zum Beitreten eines Servers, der Menüleiste oben und dem Ebenen-Widget rechts" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_overview.png?raw=true">

- Klicke mit der rechten Maustaste auf den Hintergrund, um die Einstellungen des gesamten Layouts aufzurufen und über **Neues Element** Elemente hinzuzufügen.
- Klicke mit der rechten Maustaste auf ein Element, um dessen Einstellungen aufzurufen. Siehe [Elemente](/elements#settings-of-all-elements).
- Unter **Ebenen** rechts werden alle Elemente des Layouts aufgelistet. Siehe [Ebenen und Gruppen](#layers-and-groups).
- Die Menüleiste oben:

| Menü | Inhalt |
|---|---|
| **Layout** | **Neu**, **Öffnen**, **Speichern**, **Speichern unter**, **Layout für KI exportieren**, **Layouteigenschaften** (wie im Rechtsklickmenü des Hintergrunds), **Einstellungen** und **Editor schließen** |
| **Bearbeiten** | **Rückgängig**, **Wiederholen**, **Kopieren**, **Einfügen** und **Alles auswählen** |
| **Element** | **Neu**, um Elemente hinzuzufügen, und **Gelöschte Vanilla-Elemente**, um [gelöschte Vanilla-Elemente wiederherzustellen](/deleted-vanilla-elements) |
| **Fenster** | **Editor-Widgets**, das [Raster](#grid-and-anchor-overlay), die [Anker-Überlagerung](#grid-and-anchor-overlay), **Steuerung der Elementrotation** und **Steuerung der Elementneigung** |

## Layouteinstellungen

Im Rechtsklickmenü des Hintergrunds findest du alles, was das Layout selbst betrifft, zum Beispiel:

- [**Menühintergründe**](/menu-backgrounds) und [**Dekorationsüberlagerungen**](/decoration-overlays)
- **Benutzerdefinierter Bildschirmtitel** für den Text oben in einigen Menüs, zum Beispiel „Optionen“. Darin funktionieren [Platzhalter](/placeholders).
- **Anpassungen von Kopf- und Fußzeile** für [scrollbare Bildschirme](/customizing-scrollable-screens)
- **Layout-Index [Reihenfolge mehrerer Layouts]** und **Zufallsmodus** für [mehrere Layouts in einem Menü](/randomize-layouts)
- **Ladeanforderungen [für das gesamte Layout]**; siehe [Anforderungen](/conditions#layout-wide-requirements)
- **Aktionsskript „Bildschirm öffnen“ bearbeiten** und **Aktionsskript „Bildschirm schließen“ bearbeiten**; siehe [Aktionsskripte](/action-scripts)
- **Optionen für universelle Layouts**, nur in [universellen Layouts](/universal-layouts)

# Mit Elementen arbeiten

## Auswählen

- Klicke auf ein Element, um es auszuwählen. Klicke auf den Hintergrund, um die Auswahl aufzuheben.
- Ziehe mit gedrückter Maustaste über den Hintergrund, um alle Elemente innerhalb des Rechtecks auszuwählen.
- `Ctrl` + Klick fügt ein Element zur Auswahl hinzu oder entfernt ein bereits ausgewähltes Element daraus.
- `Ctrl + A` wählt alle Elemente aus.

Klicks, Rechtecke und `Ctrl + A` berücksichtigen keine Elemente, die du [in den Ebenen ausgeblendet hast](#hiding-and-renaming).

## Verschieben

- Ziehe ein Element, um es zu verschieben. Um mehrere ausgewählte Elemente zu verschieben, halte beim Beginn des Ziehens `Ctrl` gedrückt. Ohne `Ctrl` wird nur das angeklickte Element ausgewählt.
- Mit den Pfeiltasten verschiebst du ausgewählte Elemente um ein Pixel.
- Während des Ziehens werden die Ankerpunkte angezeigt. Halte das Element über einem anderen Ankerpunkt oder Element, um es daran auszurichten. Siehe [Elemente positionieren](/positioning-elements).
- Ziehe ein Element auf einen [scrollbaren Bereich](/scrollable-areas), um es dort einzufügen.

## Größe ändern

Ziehe an einer Kante oder Ecke eines ausgewählten Elements. Halte `Shift` gedrückt, um das Seitenverhältnis beizubehalten.

Die Größe kann nur geändert werden, wenn ein einzelnes Element ausgewählt ist.

## Drehen und Neigen

Bei ausgewählten Elementen, die diese Funktion unterstützen, werden Steuerelemente zum [Drehen und Neigen](/rotating-elements) angezeigt. Halte beim Ziehen `Shift` gedrückt, um die Bewegung in festen Schritten einzurasten: 45° beim Drehen und 15° beim Neigen.

Mit **Fenster -> Steuerung der Elementrotation** und **Steuerung der Elementneigung** blendest du diese Steuerelemente aus.

## Kopieren, Einfügen und Löschen

- `Ctrl + C` kopiert die ausgewählten Elemente, `Ctrl + V` fügt sie ein. Die Kopien werden über den Originalen eingefügt und ausgewählt, damit du sie direkt wegziehen kannst.
- Du kannst Elemente auch in ein anderes Layout einfügen, solange das Spiel nicht geschlossen wurde.
- `Delete` löscht die ausgewählten Elemente. Vanilla-Elemente werden nur ausgeblendet: Stelle sie über **Element -> Gelöschte Vanilla-Elemente** wieder her.
- Beim Löschen eines scrollbaren Bereichs wirst du gefragt, ob auch dessen Inhalt gelöscht werden soll oder im Layout bleiben darf.

## Rückgängig machen und wiederholen

Mit `Ctrl + Z` machst du die letzte Änderung rückgängig, mit `Ctrl + Y` stellst du sie wieder her. Beide Befehle findest du auch im Menü **Bearbeiten**.

## Unsichtbare Elemente

Spieler können die Elemente [Audio](/elements#audio), [Dragger](/dragger), [Element Animator](/element-animator), [Music Controller](/elements#music-controller) und [Ticker](/elements#ticker) nicht sehen. Im Editor werden sie als farbige Kästen mit ihrem Namen angezeigt, damit du sie finden, verschieben und skalieren kannst.

- Mit **Farbe im Editor** im Rechtsklickmenü kannst du die Farbe des Kastens ändern, zum Beispiel um mehrere Ticker voneinander zu unterscheiden. Farben werden als `#RRGGBB` oder mit Transparenz als `#RRGGBBAA` angegeben: Eine durchscheinende Farbe wie `#E30E2366` lässt erkennen, was sich hinter dem Kasten befindet.
- Der Name im Kasten ist der Ebenenname des Elements; siehe [Ausblenden und Umbenennen](#hiding-and-renaming).

Spieler sehen den Kasten, seine Farbe und seinen Namen niemals.

# Ebenen und Gruppen

Unter **Ebenen** werden alle Elemente des Layouts aufgelistet, beginnend mit dem obersten: Ein Element wird vor allen Elementen angezeigt, die in der Liste darunter stehen. Mit **Fenster -> Editor-Widgets -> Ebenen** kannst du die Liste ein- und ausblenden.

<img width="800" alt="Die Ebene News Background unter News Text ziehen, damit die Patchnotizen nach dem Aufheben der Auswahl sichtbar werden; dann eine Gruppe hinzufügen, beide Ebenen hineinziehen, die Gruppe über ihr Augensymbol aus- und einblenden und zuklappen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/layout_editor_layers.gif?raw=true">

## Reihenfolge ändern

- Klicke auf eine Ebene, um ihr Element auszuwählen, und ziehe sie nach oben oder unten. Eine Linie zeigt an, wo sie abgelegt wird. Alle ausgewählten Ebenen werden gemeinsam verschoben.
- Oder klicke mit der rechten Maustaste auf ein Element oder seine Ebene und wähle **Eine Ebene nach oben verschieben** oder **Eine Ebene nach unten verschieben**.

Im Editor werden ausgewählte Elemente immer vor den anderen angezeigt. Hebe die Auswahl auf, um die tatsächliche Reihenfolge zu sehen.

In einigen Minecraft-Versionen werden [Spieler-Entität](/elements#player-entity)- und [Gegenstand](/elements#item)-Elemente unabhängig von ihrer Ebene vor allen anderen angezeigt. Siehe [Bekannte Probleme](/known-issues#1-player-entity--item-elements-are-always-in-front-of-everything).

## Vanilla-Elemente

Die Zeile **Vanilla-Elemente** steht für alle Elemente des Menüs selbst, zum Beispiel dessen Schaltflächen. Ihre Reihenfolge lässt sich nicht ändern. Mit der Schaltfläche rechts neben der Zeile kannst du jedoch alle deine Elemente hinter oder vor ihnen platzieren. Das entspricht der Option **Benutzerdefinierte Elemente hinter Vanilla-Elementen** im Rechtsklickmenü des Hintergrunds.

## Ausblenden und Umbenennen

- Über das Augensymbol einer Ebene blendest du ihr Element im Editor aus, damit es dir bei der Arbeit an anderen Elementen nicht im Weg ist. Klicke erneut darauf, um das Element wieder einzublenden.
- Ausgeblendete Elemente können nicht angeklickt, verschoben, kopiert oder gelöscht werden. Spieler sehen sie weiterhin; sie sind nur im Editor ausgeblendet. Das Layout merkt sich, welche Elemente du ausgeblendet hast.
- Klicke mit der rechten Maustaste auf eine Ebene und wähle **Ebene umbenennen**, um ihr einen aussagekräftigeren Namen zu geben, zum Beispiel `News Panel`. Das entspricht dem **Anzeigenamen im Editor** des Elements und ist für Spieler nicht sichtbar.

## Gruppen

Mit Gruppen kannst du zusammengehörige Ebenen unter einem Namen zusammenfassen, zum Beispiel alle Teile eines Nachrichtenfelds. Sie dienen nur zur Sortierung in der Liste: Die Elemente werden weiterhin wie zuvor angezeigt und funktionieren unverändert.

- Klicke mit der rechten Maustaste in den Bereich **Ebenen** und wähle **Gruppe hinzufügen**. Die Gruppe wird unter den Ebenen angezeigt.
- Ziehe Ebenen auf die Gruppe, um sie hinzuzufügen. Ziehe sie wieder heraus, um sie aus der Gruppe zu entfernen.
- Klicke auf eine Gruppe, um alle ihre Elemente auszuwählen. Ziehe die Gruppe, um alle Elemente gleichzeitig nach oben oder unten zu verschieben.
- Mit dem Pfeil einer Gruppe klappst du ihre Ebenen ein oder aus. Über das Augensymbol blendest du alle Elemente der Gruppe aus oder ein.
- Klicke mit der rechten Maustaste auf eine Gruppe, um sie umzubenennen, eine Ebene nach oben oder unten zu verschieben oder zu löschen. **Gruppe löschen** behält die enthaltenen Elemente bei.

Mit **Eine Ebene nach oben verschieben** und **Eine Ebene nach unten verschieben** bleibt ein Element innerhalb seiner Gruppe. Um es aus der Gruppe zu entfernen, ziehe seine Ebene aus der Gruppe heraus.

Das Layout speichert seine Gruppen und welche davon eingeklappt sind.

## Scrollbare Bereiche

Die Elemente in einem [scrollbaren Bereich](/scrollable-areas) werden eingerückt unter der Ebene des Bereichs angezeigt.

- Ziehe eine Ebene auf die untere Hälfte der Ebene eines Bereichs, um das Element dort einzufügen. Ziehe sie zwischen andere Ebenen, um sie wieder herauszunehmen. Das Element bleibt an seiner Position auf dem Bildschirm.
- Mit dem Pfeil einer Bereichsebene klappst du die zugehörigen Elemente ein oder aus.
- Elemente in einem Bereich gehören zu keiner Gruppe. Sie werden zusammen mit dem Bereich verschoben.

# Raster und Anker-Überlagerung

Im Menü **Fenster** findest du Einstellungen für die Hilfsfunktionen des Editors:

- **Raster** zeigt Rasterlinien an; mit `Ctrl + G` schaltest du sie ein oder aus. **Rastergröße** legt den Abstand zwischen den Linien fest.
- **Am Raster einrasten** sorgt dafür, dass ein gezogenes Element an den Rasterlinien einrastet, wenn das Raster angezeigt wird. Mit **Stärke des Rasterfangs** legst du fest, wie stark es einrastet.
- **Sichtbarkeit der Anker-Überlagerung** legt fest, wann die Ankerpunkte angezeigt werden:
  - **Beim Ziehen von Elementen anzeigen**: während du Elemente ziehst.
  - **Immer sichtbar**: dauerhaft.
  - **Bei Tastendruck anzeigen (Taste „O“)**: solange du `O` gedrückt hältst.
  - **Deaktiviert**: nie.
- Mit **Ankerbereich beim Darüberfahren** legst du fest, ob ein Anker eines Elements geändert wird, wenn du es über einen Ankerpunkt hältst. **Elemente beim Darüberfahren als Anker verwenden** fügt andere Elemente zu den Ankerpunkten hinzu. Diese Funktion ist nur verfügbar, wenn auch **Ankerbereich beim Darüberfahren** aktiviert ist.

# Speichern und schließen

- Mit `Ctrl + S` oder **Layout -> Speichern** speicherst du das Layout. Beim ersten Speichern bittet dich FancyMenu um einen Dateinamen.
- **Layout -> Speichern unter** speichert das Layout als neue Datei.
- Solange Änderungen nicht gespeichert sind, wird in der Menüleiste **\* Ungespeicherte Änderungen! \*** angezeigt.
- Über das X rechts in der Menüleiste oder **Layout -> Editor schließen** schließt du den Editor. Bei ungespeicherten Änderungen wirst du zuerst gefragt, ob du fortfahren möchtest.

# Tastenkürzel

Unter macOS verwendest du `Cmd` statt `Ctrl`.

| Tastenkürzel | Funktion |
|---|---|
| `Ctrl + S` | Speichern |
| `Ctrl + Z` | Rückgängig |
| `Ctrl + Y` | Wiederholen |
| `Ctrl + C` | Ausgewählte Elemente kopieren |
| `Ctrl + V` | Einfügen |
| `Ctrl + A` | Alle Elemente auswählen |
| `Delete` | Ausgewählte Elemente löschen |
| Pfeiltasten | Ausgewählte Elemente um ein Pixel verschieben |
| `Ctrl` + Klick | Ein Element zur Auswahl hinzufügen oder daraus entfernen |
| `Ctrl` + Ziehen | Mehrere ausgewählte Elemente verschieben |
| `Shift` + Größenänderung | Seitenverhältnis beibehalten |
| `Shift` + Drehen oder Neigen | In festen Schritten einrasten |
| `Ctrl + G` | Raster ein- oder ausblenden |
| `O` gedrückt halten | Ankerpunkte anzeigen, wenn **Bei Tastendruck anzeigen (Taste „O“)** ausgewählt ist |

> [!TIP]
> Der Texteditor hat eigene Tastenkürzel; siehe [Text in Menüs](/text-in-menus#the-text-editor). Fenster wie [Aktionsskripte](/action-scripts#shortcuts) listen ihre Tastenkürzel auf den jeweiligen Seiten auf.
