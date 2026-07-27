---
title: Benutzerdefinierte GUIs
description: Neue GUI-Bildschirme erstellen und konfigurieren.
---

# Benutzerdefinierte GUIs

Benutzerdefinierte GUIs sind neue Bildschirme, die du mit FancyMenu-[Elementen](./elements) füllen kannst.

> [!CAUTION]
> Benutzerdefinierte GUIs können Aktionen ausführen. Importiere sie nur aus Quellen, denen du vertraust.

# Eine benutzerdefinierte GUI erstellen

1. Öffne **Anpassung -> Benutzerdefinierte GUIs -> Benutzerdefinierte GUIs verwalten**.
2. Wähle **Neue GUI**.
3. Gib eine Kennung ein und konfiguriere die Bildschirmeinstellungen.
4. Wähle **Fertig** und öffne dann die neue GUI im Manager.
5. Erstelle und bearbeite ihr Layout wie bei jedem anderen Bildschirm.

Kennungen dürfen Kleinbuchstaben, Ziffern, `.`, `_` und `-` enthalten. Sie dürfen keine Leerzeichen enthalten und müssen eindeutig sein. Leere, ungültige oder doppelte Kennungen können nicht gespeichert werden.

Benutzerdefinierte GUIs haben die Bildschirmanpassung immer aktiviert; ihr Schalter zur Anpassung kann nicht deaktiviert werden.

# Bildschirmeinstellungen

| Einstellung | Verhalten |
|---|---|
| ESC erlauben | Ermöglicht es der Escape-Taste, die GUI zu schließen und zum übergeordneten Bildschirm zurückzukehren |
| Spiel/Welt pausieren | Pausiert den Einzelspieler-Modus, während die GUI geöffnet ist |
| Welt-Hintergrund rendern | Zeigt die geladene Welt hinter der GUI an |
| Welt-Hintergrund-Overlay | Fügt der Welt das standardmäßige Unschärfe-/Dunkel-Overlay hinzu |
| Popup-Modus | Lässt den übergeordneten Bildschirm hinter der benutzerdefinierten GUI sichtbar |
| Popup-Hintergrund-Overlay | Fügt im Popup-Modus Unschärfe/Tönung über dem übergeordneten Bildschirm hinzu |

Der Popup-Modus verbindet die beiden Bildschirme nicht. Die benutzerdefinierte GUI bleibt der aktive Bildschirm, während ihr übergeordneter Bildschirm dahinter dargestellt wird. Das Schließen der benutzerdefinierten GUI führt zurück zu diesem übergeordneten Bildschirm, sofern einer vorhanden ist.

# Eine benutzerdefinierte GUI öffnen

Verwende die genaue Kennung der benutzerdefinierten GUI mit entweder:

- der Aktion [**Bildschirm oder benutzerdefinierte GUI öffnen**](./action-scripts#open-screen-or-custom-gui-opengui).
- dem Befehl [`/openguiscreen`](./commands#openguiscreen).

# Einen vorhandenen Bildschirm überschreiben

Eine benutzerdefinierte GUI kann einen Vanilla- oder Mod-Bildschirm ersetzen, sobald dieser geöffnet wird.

1. Erstelle die ersetzende benutzerdefinierte GUI.
2. Öffne den Bildschirm, den du ersetzen möchtest.
3. Aktiviere **Anpassung -> Einstellungen -> Erweiterter Anpassungsmodus**.
4. Wähle **Anpassung -> Benutzerdefinierte GUIs -> Aktuellen Bildschirm mit benutzerdefinierter GUI überschreiben**.
5. Wähle die ersetzende benutzerdefinierte GUI aus.

Verwalte gespeicherte Überschreibungen über **Anpassung -> Benutzerdefinierte GUIs -> Überschriebene Bildschirme verwalten**.

Eine Überschreibung umgeht den ursprünglichen Bildschirm. Teste daher die Navigation und alle Funktionen, die vom Verhalten des ursprünglichen Bildschirms abhängen.
