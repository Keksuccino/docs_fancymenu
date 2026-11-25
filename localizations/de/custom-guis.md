---
title: Benutzerdefinierte GUIs
description: >-
  Erstelle eigene Menüs von Grund auf, öffne sie mit Schaltflächen, Tasten oder
  Befehlen, zeige sie als Pop-ups an und ersetze andere Menüs durch sie.
sourceBlobSha: 0b336708473ae2964b3d9e777498c6cd40eaffc6
---

# Benutzerdefinierte GUIs

Benutzerdefinierte GUIs sind Menüs, die du selbst erstellst, zum Beispiel einen Informationsbildschirm für ein Modpack, eine Server-Lobby oder eine Regelseite. Sie sind zunächst leer und werden wie jedes andere Menü mit einem [Layout](/layout-editor) gestaltet. Anschließend lassen sie sich mit Schaltflächen, Tasten und Befehlen öffnen.

<img width="800" alt="Ein Klick auf die Schaltfläche Modpack-Info im Titelbildschirm öffnet eine benutzerdefinierte GUI als Pop-up über dem unscharfen Titelbildschirm. Die Zurück-Schaltfläche schließt sie wieder." src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_popup.gif?raw=true">

# Eine benutzerdefinierte GUI erstellen

<img width="800" alt="Benutzerdefinierte GUIs verwalten öffnen, auf Neue GUI klicken, die Kennung modpack_info eingeben, den Pop-up-Modus aktivieren und die neue benutzerdefinierte GUI öffnen" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_new.gif?raw=true">

1. Öffne **Menüleiste -> Anpassung -> Benutzerdefinierte GUIs -> Benutzerdefinierte GUIs verwalten**.
2. Klicke auf **Neue GUI**.
3. Gib eine **Kennung für die benutzerdefinierte GUI** ein, zum Beispiel `modpack_info`, passe die [Einstellungen](#einstellungen) an und klicke auf **Fertig**.
4. Klicke in der Liste auf die neue benutzerdefinierte GUI und dann auf **GUI öffnen**.
5. Klicke auf **Fertig**, um **Benutzerdefinierte GUIs verwalten** zu schließen.

**Benutzerdefinierte GUIs verwalten** speichert deine Änderungen erst, wenn du auf **Fertig** oder **GUI öffnen** klickst. Mit **Abbrechen** werden sie verworfen.

## Die Kennung

Schaltflächen, Befehle und Layouts finden eine benutzerdefinierte GUI anhand ihrer Kennung.

- Erlaubt sind nur Kleinbuchstaben, Zahlen, `.`, `_` und `-`. Jede benutzerdefinierte GUI benötigt eine eigene Kennung.
- Verwende nicht die [Kennung eines anderen Bildschirms](/screen-identifiers), zum Beispiel `title_screen`. Die benutzerdefinierte GUI würde ihre Layouts mit diesem Bildschirm teilen.
- Wenn du die Kennung später änderst, können Layouts sowie Schaltflächen und Befehle mit der alten Kennung die GUI nicht mehr finden. Wenn du die Kennung wieder änderst, sind sie wieder verfügbar.

## Das Layout erstellen

1. Öffne die benutzerdefinierte GUI.
2. Klicke auf **Menüleiste -> Anpassung -> Layouts -> Neu -> Für aktuellen Bildschirm**. Die Anpassung ist für benutzerdefinierte GUIs immer aktiviert.
3. Füge Elemente hinzu und speichere das Layout. Weitere Informationen findest du im [Layout-Editor](/layout-editor).

Eine benutzerdefinierte GUI enthält zunächst nichts, nicht einmal eine Zurück-Schaltfläche. Füge ihr eine [Schaltfläche](/elements#button) mit der Aktion [**Zurück zum letzten Bildschirm**](/action-scripts#back-to-last-screen) hinzu oder lasse **GUI mit ESC schließen erlauben** aktiviert, damit Spieler sie verlassen können.

# Einstellungen

Mit **GUI bearbeiten** unter **Benutzerdefinierte GUIs verwalten** kannst du die Einstellungen der ausgewählten benutzerdefinierten GUI ändern.

| Einstellung | Funktion |
|---|---|
| **Kennung der benutzerdefinierten GUI** | Der Name der benutzerdefinierten GUI. Siehe [Die Kennung](#die-kennung). |
| **Bildschirmtitel (optional)** | Ein weißer Titel oben in der GUI. Lass das Feld leer, wenn kein Titel angezeigt werden soll. [Platzhalter](/placeholders) funktionieren. Lokalisierungsschlüssel des Spiels, von Mods und Ressourcenpaketen werden in der Sprache des Spielers angezeigt. |
| **GUI mit ESC schließen erlauben** | Mit `Esc` wird die GUI geschlossen. Standardmäßig aktiviert. |
| **Spiel/Welt pausieren** | Pausiert Einzelspielerwelten, während die GUI geöffnet ist. Standardmäßig aktiviert. |
| **Hintergrund der Welt rendern** | Zeigt während des Spielens die Welt hinter der GUI an. Außerhalb einer Welt oder wenn diese Option deaktiviert ist, wird das Minecraft-Panorama angezeigt. Standardmäßig aktiviert. |
| **Overlay für den Hintergrund der Welt rendern** | Verschwimmt und verdunkelt die Welt oder das Panorama hinter der GUI, wie im Pausenmenü. Funktioniert nur mit **Hintergrund der Welt rendern**. Ist diese Option deaktiviert, ist das Panorama immer verschwommen und dunkler. Standardmäßig aktiviert. |
| **Pop-up-Modus** | Zeigt die GUI über dem Menü an, von dem aus sie geöffnet wurde. Siehe [Pop-up-Modus](#pop-up-modus). |
| **Overlay für den Hintergrund des Pop-up-Modus** | Verschwimmt das Menü hinter dem Pop-up. Funktioniert nur mit **Pop-up-Modus**. Standardmäßig aktiviert. |

- Die Unschärfe entspricht der Option **Menühintergrund-Unschärfe** in Minecraft.
- Ein [Menühintergrund](/menu-backgrounds) im Layout überdeckt all das: die Welt, das Panorama und das Menü hinter einem Pop-up.
- Der Layout-Editor kann den Titel (**Benutzerdefinierter Bildschirmtitel**) benutzerdefinierter GUIs nicht ändern. Ändere stattdessen **Bildschirmtitel (optional)**. Wenn du einen Titel mit eigener Schriftart, Farbe oder Position möchtest, lass das Feld leer und füge ein [Textelement](/elements#text) hinzu.

## Pop-up-Modus

Im **Pop-up-Modus** bleibt das Menü, von dem aus die benutzerdefinierte GUI geöffnet wurde, mit seinem Layout im Hintergrund sichtbar. Solange das Pop-up geöffnet ist, kann das Menü nicht angeklickt werden.

- Pop-ups eignen sich besonders für kleine Elemente wie ein Infokästchen, eine Bestätigung oder ein Einstellungsfenster. Lass etwas Platz frei, damit das Menü im Hintergrund sichtbar bleibt.
- Füge dem Layout eines Pop-ups keinen Menühintergrund hinzu, sonst verschwindet das Menü im Hintergrund.
- Wird die benutzerdefinierte GUI geöffnet, während kein Menü geöffnet ist, zum Beispiel mit einer Taste während des Spielens, gibt es kein Menü, das im Hintergrund angezeigt werden kann. In diesem Fall wird der normale Hintergrund angezeigt.

# Eine benutzerdefinierte GUI öffnen

Alles, was Bildschirme öffnen kann, kann auch benutzerdefinierte GUIs öffnen – dafür wird ihre Kennung verwendet:

- **Schaltflächen:** die Aktion [**Bildschirm oder benutzerdefinierte GUI öffnen**](/action-scripts#open-screen-or-custom-gui) mit dem Wert `modpack_info`.
- **Tasten:** ein [Listener für „Bei Tastendruck“](/listeners#listener-variables) mit derselben Aktion. Damit lässt sich die benutzerdefinierte GUI sowohl in Menüs als auch während des Spielens öffnen.
- **Befehle:** `/openguiscreen modpack_info`, auch auf Servern, in Befehlsblöcken und als Questbelohnung. Siehe [Befehle](/commands#openguiscreen).
- **Eine Welt verlassen:** Die Aktion [**Welt oder Server verlassen**](/action-scripts#leave-world-or-server) öffnet mit der angegebenen Kennung die benutzerdefinierte GUI, nachdem die Welt verlassen wurde.

Benutzerdefinierte GUIs gehören zur persönlichen FancyMenu-Konfiguration jedes Spielers. Ein Server kann nur die benutzerdefinierten GUIs öffnen, die seine Spieler haben, zum Beispiel die des Modpacks.

So verlässt du eine benutzerdefinierte GUI:

- Mit `Esc` (wenn **GUI mit ESC schließen erlauben** aktiviert ist) und der Aktion **Zurück zum letzten Bildschirm** kehrst du zum Menü zurück, von dem aus die GUI geöffnet wurde. War kein Menü geöffnet, kehrt `Esc` zum Spiel zurück.
- Die Aktion [**Bildschirm schließen**](/action-scripts#close-screen) schließt die GUI. Außerhalb einer Welt wird der Titelbildschirm geöffnet.

# Einen vorhandenen Bildschirm überschreiben

Eine benutzerdefinierte GUI kann ein Menü des Spiels oder eines Mods ersetzen. Jedes Mal, wenn dieses Menü geöffnet würde, wird stattdessen die benutzerdefinierte GUI geöffnet.

> [!WARNING]
> Das ersetzte Menü wird nie geöffnet. Daher werden auch seine Funktionen nicht ausgeführt, und andere Mods, die es benötigen, können möglicherweise nicht mehr funktionieren. Ändere Menüs nach Möglichkeit mit einem normalen Layout. Ersetze ein Menü nur, wenn sich dein Vorhaben nicht mit einem Layout umsetzen lässt.

1. Aktiviere **Menüleiste -> Anpassung -> Einstellungen -> Erweiterter Anpassungsmodus**.
2. Öffne das Menü, das du ersetzen möchtest.
3. Klicke auf **Menüleiste -> Anpassung -> Benutzerdefinierte GUIs -> Aktuellen Bildschirm mit benutzerdefinierter GUI überschreiben**.
4. Bestätige den Warnhinweis und wähle unter **Benutzerdefinierte GUI auswählen** die gewünschte benutzerdefinierte GUI aus.

Die benutzerdefinierte GUI wird sofort geöffnet. Mit `Esc` und **Zurück zum letzten Bildschirm** kehrst du zum Menü zurück, das vor dem ersetzten Menü geöffnet war.

Um die Änderung rückgängig zu machen, öffne **Menüleiste -> Anpassung -> Benutzerdefinierte GUIs -> Überschriebene Bildschirme verwalten**, klicke unter dem Bildschirm auf **Überschreibungsregel löschen** und anschließend auf **Fertig**.

> [!TIP]
> Wenn du ein Menü nur in bestimmten Fällen ersetzen möchtest, zum Beispiel nur, wenn eine [Variable](/variables) gesetzt ist, verwende stattdessen einen [Listener für „Bei geöffnetem Bildschirm“](/listeners#on-screen-opened) mit einer IF-Anweisung.

# Benutzerdefinierte GUIs verwalten

- Mit **Neue GUI**, **GUI bearbeiten** und **GUI öffnen** unter **Benutzerdefinierte GUIs verwalten** kannst du benutzerdefinierte GUIs hinzufügen, ändern und öffnen.
- **GUI löschen** löscht nach einer Bestätigung die ausgewählte benutzerdefinierte GUI. Ihre Layouts bleiben erhalten und werden wieder angezeigt, wenn du eine neue benutzerdefinierte GUI mit derselben Kennung erstellst.
- Über die Suchleiste kannst du benutzerdefinierte GUIs anhand ihrer Kennung finden.
- **Menüleiste -> Hilfe -> Für KI exportieren -> Benutzerdefinierte GUIs** exportiert alle benutzerdefinierten GUIs und Überschreibungsregeln für einen [KI-Chat](/export-for-ai).

Benutzerdefinierte GUIs und Überschreibungsregeln werden in `config/fancymenu/custom_gui_screens.txt` gespeichert. Ihre Layouts befinden sich wie alle anderen unter `config/fancymenu/customization/` (siehe [Speicherorte der Daten](/data-storage-locations)). Jedes [Profil](/profiles) hat eigene benutzerdefinierte GUIs.
