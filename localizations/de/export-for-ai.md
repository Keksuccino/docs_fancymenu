---
title: Export für KI
description: >-
  Wandle Teile deiner FancyMenu-Einrichtung in Text für KI-Assistenten wie Alice
  um, damit sie dir schneller helfen können.
sourceBlobSha: 37ce2fdd6cf8d770ca3f6f31528ac6076fe46922
---
# Export für KI

Mit **Export für KI** wandelst du einen Teil deiner FancyMenu-Einrichtung in Text um, der für KI-Assistenten wie Alice gedacht ist – den Helfer-Bot auf dem [FancyMenu-Discord-Server](https://discord.gg/rhayah27GC). Füge den Text in deinen Chat ein, und die KI sieht genau, wie alles eingerichtet ist, anstatt raten zu müssen.

<img width="800" alt="Ein Support-Beitrag auf Discord, in dem Alice um einen Export bittet, darin das Problem findet und dem Spieler hilft, seinen Button zu reparieren" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/export_for_ai_chat.gif?raw=true">

# Warum es diese Funktion gibt

Ein Screenshot zeigt, wie etwas aussieht, aber nicht, wie es eingerichtet ist. Ein Aktionsskript oder eine Anforderung von Hand aufzuschreiben dauert lange, und das entscheidende Detail geht dabei oft verloren.

Ein Export enthält alles, was die KI braucht:

- Alle Einstellungen, Aktionen, Anforderungen und Werte des exportierten Elements.
- Die Versionsnummern von FancyMenu, Minecraft, Mod-Loader, Java und deinem System.
- Kurze Erklärungen zur Funktionsweise von FancyMenu, damit die KI den Export richtig versteht.

Exporte sind immer auf Englisch, unabhängig davon, in welcher Sprache du spielst. Dein Kontoname in Dateipfaden wird durch `<user>` ersetzt, sodass du Exporte in öffentlichen Chats teilen kannst.

# Wann du die Funktion verwenden solltest

- Etwas funktioniert nicht wie erwartet, zum Beispiel ein Button, der nichts tut, oder ein Element, das nie angezeigt wird.
- FancyMenu zeigt einen Fehler oder eine Warnung an.
- Du möchtest Hilfe beim Erstellen von etwas, zum Beispiel einem Aktionsskript, einer Anforderung oder einem ganzen Menü.
- Du möchtest wissen, was in deinem Spiel möglich ist. **Alles, was FancyMenu kann** listet alle Elemente, Hintergründe, Aktionen, Anforderungen, Platzhalter und Listener auf, die dir zur Verfügung stehen – einschließlich derer aus Add-ons.

Exportiere nur das, worum es bei deiner Frage geht, zum Beispiel den einen Button, der nicht funktioniert. Kleinere Exporte helfen der KI, sich auf das Wesentliche zu konzentrieren. Erkläre anschließend, was du erwartet hast und was stattdessen passiert ist.

# So exportierst du

An jeder der unten genannten Stellen öffnet sich ein kleines Menü:

- **In Zwischenablage kopieren** kopiert den Export, damit du ihn mit `Ctrl + V` (`Cmd + V` unter macOS) in deinen Chat einfügen kannst.
- **Als Datei speichern** speichert den Export als Markdown-Datei unter `<game-directory>/fancymenu_data/ai_exports/` und öffnet diesen Ordner, damit du die Datei in deinen Chat ziehen kannst. Verwende diese Option für große Exporte, die nicht in eine Chat-Nachricht passen.

Exporte aus dem Layout-Editor sowie aus den Listener- und Scheduler-Fenstern enthalten auch Änderungen, die du noch nicht gespeichert hast.

# Wo du exportieren kannst

## Menüleiste

| Was exportiert wird | Wo du es findest |
|---|---|
| Der aktuelle Bildschirm mit seinen Widgets und den Aktionen, die FancyMenu darauf ausführt | **Menüleiste -> Anpassung -> Aktuellen Bildschirm für KI exportieren** |
| Ein Layout | **Menüleiste -> Anpassung -> Layouts**, wähle das Layout aus und klicke dann auf **Layout für KI exportieren** |
| Informationen zu deinem Spiel, deiner Hardware und deinen Mods sowie zu den Funktionen, die FancyMenu nutzen kann, zum Beispiel Video- und Browser-Unterstützung | **Menüleiste -> Hilfe -> Export für KI -> Systeminformationen** |
| Alle FancyMenu-Einstellungen, einschließlich der [globalen Anpassungen](/global-customizations) | **Menüleiste -> Hilfe -> Export für KI -> FancyMenu-Einstellungen** |
| Alle [Variablen](/variables) | **Menüleiste -> Hilfe -> Export für KI -> Alle Variablen** |
| Alle [Listener](/listeners) | **Menüleiste -> Hilfe -> Export für KI -> Alle Listener** |
| Alle [Scheduler](/schedulers) | **Menüleiste -> Hilfe -> Export für KI -> Alle Scheduler** |
| Alle [benutzerdefinierten GUIs](/custom-guis) | **Menüleiste -> Hilfe -> Export für KI -> Benutzerdefinierte GUIs** |
| Alle [Profile](/profiles) | **Menüleiste -> Hilfe -> Export für KI -> Profile** |
| Alle Elemente, Hintergründe, Aktionen, Anforderungen, Platzhalter und Listener, die in deinem Spiel verfügbar sind | **Menüleiste -> Hilfe -> Export für KI -> Alles, was FancyMenu kann** |

## Layout-Editor

| Was exportiert wird | Wo du es findest |
|---|---|
| Das Layout, das du gerade bearbeitest | **Layout -> Layout für KI exportieren** in der Menüleiste des Editors |
| Ein anderes Layout des Bildschirms | **Layout -> Öffnen** in der Menüleiste des Editors, wähle das Layout aus und klicke dann auf **Layout für KI exportieren** |
| Ein Element | Klicke mit der rechten Maustaste auf das Element und dann auf **Für KI exportieren** |
| Alle ausgewählten Elemente | **Bearbeiten -> Ausgewählte Elemente für KI exportieren** in der Menüleiste des Editors |
| Einen [Menühintergrund](/menu-backgrounds) | Klicke mit der rechten Maustaste auf den Hintergrund des Editors und dann auf **Menühintergründe**. Wähle den Hintergrund aus und klicke anschließend auf **Für KI exportieren** |
| Eine [Dekorationsüberlagerung](/decoration-overlays) | Klicke mit der rechten Maustaste auf den Hintergrund des Editors und dann auf **Dekorationsüberlagerungen**. Wähle die Überlagerung aus und klicke anschließend auf **Für KI exportieren** |

## Editoren und Fenster

| Was exportiert wird | Wo du es findest |
|---|---|
| Ein [Aktionsskript](/action-scripts) | Klicke mit der rechten Maustaste in den Aktionsskript-Editor und dann auf **Aktionsskript für KI exportieren** |
| [Anforderungen](/conditions) | Klicke mit der rechten Maustaste im Fenster **Anforderungen verwalten** und dann auf **Anforderungen für KI exportieren** |
| Einen Text, zum Beispiel den Inhalt eines Textelements | Klicke mit der rechten Maustaste im Texteditor und dann auf **Text für KI exportieren** |
| Eine oder alle Variablen | Öffne **Menüleiste -> Anpassung -> Variablen verwalten**, klicke mit der rechten Maustaste und dann auf **Variable für KI exportieren** oder **Alle Variablen für KI exportieren** |
| Einen oder alle Listener | Öffne **Menüleiste -> Anpassung -> Listener verwalten**, klicke auf **Für KI exportieren** und dann auf **Ausgewählter Listener** oder **Alle Listener** |
| Einen oder alle Scheduler | Öffne **Menüleiste -> Anpassung -> Scheduler verwalten**, klicke auf **Für KI exportieren** und dann auf **Ausgewählter Scheduler** oder **Alle Scheduler** |

## Fehler und Warnungen

Wenn FancyMenu einen Fehler oder eine Warnung anzeigt, klicke neben **OK** auf **Für KI exportieren**, um die Meldung zu exportieren.

## Server

Die [FMData](/fm-data)-Konfiguration eines Servers mit seinen Server-Listenern und Willkommensdaten lässt sich mit einem Befehl exportieren. Dafür ist Berechtigungsstufe 2 erforderlich, wie bei allen `/fmdata`-Befehlen.

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

- `copy` sendet dir eine Chat-Nachricht. Klicke darauf, um den Export zu kopieren. In der Serverkonsole wird stattdessen der vollständige Export angezeigt.
- `file` speichert den Export auf dem Server unter `fancymenu_data/ai_exports/`. Verwende diese Option, wenn der Export zu groß für den Chat ist.
