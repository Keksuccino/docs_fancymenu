---
title: Ice & Fire Hauptmenü
description: So deaktivierst du das benutzerdefinierte Hauptmenü von Ice and Fire.
---

# Ice & Fire Hauptmenü

Um den benutzerdefinierten Titelbildschirm im Ice-and-Fire-Mod zu deaktivieren, musst du die Konfiguration ändern. So geht’s:

## 1. Die Konfigurationsdatei finden
- **Dateiname:** Die Einstellung befindet sich in der Datei **`iceandfire-client.toml`**.
- **Ordnerpfad:** Diese Datei liegt normalerweise in **`<game-directory>/config/`**, wobei `<game-directory>` das Instanz-/Profilverzeichnis deines aktiven Launchers ist.

## 2. Die Konfigurationsdatei bearbeiten
- **Datei öffnen:** Öffne `iceandfire-client.toml` mit einem beliebigen einfachen Texteditor (z. B. Notepad unter Windows oder TextEdit unter macOS).
- **Einstellung suchen:** Scrolle nach unten, bis du eine Option zum benutzerdefinierten Hauptmenü findest. Sie kann auskommentiert sein und etwa so aussehen:
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Wert ändern:** Setze diese Option auf **false**, indem du die Zeile in Folgendes änderst:
  ```toml
  B:"Custom main menu"=false
  ```
  Diese Änderung teilt dem Mod mit, dass er sein benutzerdefiniertes Hauptmenü nicht rendern soll (oft mit Drachen oder anderen thematischen Elementen).

## 3. Speichern und neu starten
- **Datei speichern:** Nachdem du die Änderung vorgenommen hast, speichere die Datei.
- **Minecraft neu starten:** Schließe Minecraft und starte es neu, damit die Änderungen wirksam werden. Beim Laden des Spiels sollte nun das Standard-Hauptmenü anstelle des benutzerdefinierten Menüs des Mods verwendet werden.

## Zusätzliche Tipps
- **Prüfe, ob du die richtige Datei bearbeitest:** Es kann eine separate allgemeine Konfigurationsdatei geben. Stelle also sicher, dass du **`iceandfire-client.toml`** bearbeitest (die clientseitige Konfiguration, nicht die allgemeine).
- **Vorher sichern:** Es ist immer eine gute Idee, vor Änderungen eine Sicherungskopie der ursprünglichen Konfigurationsdatei zu erstellen.
- **Modpacks:** Wenn du ein Modpack verwendest, kann sich die Konfigurationsdatei innerhalb der Ordnerstruktur des Packs befinden, aber das Prinzip bleibt dasselbe.

Wenn du diese Schritte befolgst, solltest du das benutzerdefinierte Hauptmenü des Mods deaktivieren können, sodass du stattdessen den Hauptmenü-Hintergrund deines Texture Packs verwenden kannst.
