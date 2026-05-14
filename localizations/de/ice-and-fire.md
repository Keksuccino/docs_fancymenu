---
title: Ice & Fire Hauptmenü
description: Wie man das benutzerdefinierte Hauptmenü von Ice and Fire deaktiviert.
---

Um den benutzerdefinierten Titelscreen im Mod Ice and Fire zu deaktivieren, musst du seine Konfiguration ändern. So geht’s:

## 1. Die Konfigurationsdatei finden
- **Dateiname:** Die Einstellung befindet sich in der Datei **`iceandfire-client.toml`**.
- **Ordnerpfad:** Diese Datei liegt normalerweise in deinem **`.minecraft/config`**-Ordner (oder im entsprechenden Konfigurationsverzeichnis, wenn du einen anderen Launcher oder ein Modpack verwendest).

## 2. Die Konfigurationsdatei bearbeiten
- **Datei öffnen:** Öffne `iceandfire-client.toml` mit einem beliebigen einfachen Texteditor (z. B. Editor unter Windows oder TextEdit unter macOS).
- **Einstellung suchen:** Scrolle nach unten, bis du eine Option findest, die mit dem benutzerdefinierten Hauptmenü zu tun hat. Sie kann auskommentiert sein und etwa so aussehen:
  ```toml
  # Ob der Drache im Hauptmenü angezeigt werden soll oder nicht [Standard: true]
  B:"Custom main menu"=true
  ```
- **Wert ändern:** Setze diese Option auf **false**, indem du die Zeile so änderst:
  ```toml
  B:"Custom main menu"=false
  ```
  Diese Änderung teilt dem Mod mit, dass er sein benutzerdefiniertes Hauptmenü nicht darstellen soll (das oft den Drachen oder andere thematische Elemente zeigt).

## 3. Speichern und neu starten
- **Datei speichern:** Nachdem du die Änderung vorgenommen hast, speichere die Datei.
- **Minecraft neu starten:** Schließe Minecraft und starte es neu, damit die Änderungen wirksam werden. Beim Laden des Spiels sollte nun wieder das Standard-Hauptmenü angezeigt werden, statt des benutzerdefinierten Menüs des Mods.

## Zusätzliche Tipps
- **Prüfe, ob du die richtige Datei bearbeitest:** Es kann eine separate gemeinsame Konfigurationsdatei geben. Stelle also sicher, dass du **`iceandfire-client.toml`** bearbeitest (das ist die clientseitige Konfiguration, nicht die gemeinsame).
- **Vorher sichern:** Es ist immer eine gute Idee, vor Änderungen eine Sicherungskopie der ursprünglichen Konfigurationsdatei zu erstellen.
- **Modpacks:** Wenn du ein Modpack verwendest, befindet sich die Konfigurationsdatei möglicherweise innerhalb der Ordnerstruktur des Packs, aber das Vorgehen bleibt dasselbe.

Diese Methode wurde von Nutzern aus der Community bestätigt — zum Beispiel erwähnten mehrere Nutzer in den Foren von Feed The Beast, dass das Finden und Ändern der Option `"Custom main menu"` in **`iceandfire-client.toml`** ihr Problem gelöst hat. (Siehe die Diskussion, in der ein Nutzer bemerkte: „set the ice and fire config to not display it in iceandfire-client.toml“ und dass sich die Datei im config-Ordner befindet.) citeturn0search1

Wenn du diese Schritte befolgst, sollte das benutzerdefinierte Hauptmenü des Mods deaktiviert sein, sodass du den Hintergrund deines Texture Packs für das Hauptmenü verwenden kannst.
