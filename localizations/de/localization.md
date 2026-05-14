---
title: Layouts lokalisieren
description: Wie man Layout-Inhalte lokalisiert.
---

# Layouts lokalisieren

FancyMenu ermöglicht es dir, Textinhalte und sogar ganze Elemente oder Layouts zu lokalisieren!

# Textinhalt

FancyMenu erlaubt dir, eigene Übersetzungen zum Spiel hinzuzufügen.
Diese können dann mit dem Platzhalter **Localize Text** verwendet werden, um Text an die aktuelle Spielsprache anzupassen.

## Vanilla-Minecraft-Lokalisierungsschlüssel verwenden

Bevor du eigene Lokalisierungen erstellst, möchtest du vielleicht vorhandene Minecraft-Lokalisierungsschlüssel verwenden. Das spart Zeit und sorgt für Konsistenz mit dem Vanilla-Minecraft-Text.

### Vanilla-Lokalisierungsschlüssel finden

Der einfachste Weg, Minecrafts Lokalisierungsschlüssel zu finden, ist, die Asset-Dateien des Spiels online zu durchsuchen:

1. **MCAsset.cloud besuchen:**  
   Gehe zu [https://mcasset.cloud/](https://mcasset.cloud/) - diese Website ermöglicht es dir, die Minecraft-Assets zu durchsuchen, ohne sie aus dem Spiel zu extrahieren.

2. **Zu den Sprachdateien navigieren:**  
   - Wähle deine Minecraft-Version im Dropdown-Menü aus
   - Navigiere zu: `assets` → `minecraft` → `lang`
   - Öffne `en_us.json`, um alle englischen Übersetzungen zu sehen

3. **Den benötigten Schlüssel finden:**  
   - Nutze die Suchfunktion deines Browsers (Strg+F oder Cmd+F), um nach bestimmtem Text zu suchen
   - Das Format ist `"key": "text"` - der erste Teil in Anführungszeichen vor dem Doppelpunkt (`:`) ist der Schlüssel
   - Zum Beispiel: `"menu.singleplayer": "Singleplayer"` - der Schlüssel ist `menu.singleplayer`

### Mod-Lokalisierungsschlüssel verwenden

Wenn du andere Mods installiert hast, kannst du auch deren Lokalisierungsschlüssel verwenden:

1. Prüfe die Dokumentation der Mod auf verfügbare Schlüssel
2. Durchsuche die Sprachdateien der Mod, wenn sie Open Source sind

## Eigene Lokalisierungsdateien

Lokalisierungsdateien sind Textdateien mit allen Textinhalten, die in mehreren Sprachen verfügbar sein sollen. Jeder übersetzbare Text hat einen eindeutigen Schlüssel, damit Minecraft den richtigen übersetzbaren Text in den Lokalisierungsdateien finden kann.

- **Standarddatei (en_us.json):**  
  Englisch (US). Diese Datei wird verwendet, wenn keine andere Sprachdatei ausgewählt ist. Sie dient als Fallback-Sprachdatei.

- **Andere Sprachdateien:**  
  Zum Beispiel kannst du eine deutsche Datei namens `de_de.json` für Spieler erstellen, die Deutsch verwenden.

### So erstellst du eine eigene Lokalisierungsdatei

Du brauchst immer eine `en_us.json`-Datei! Ohne sie hat das Spiel keinen Fallback, wenn etwas schiefgeht oder eine nicht unterstützte Sprache eingestellt ist.

1. **Einen Texteditor öffnen:**  
   Verwende Notepad (Windows), TextEdit (Mac) oder einen beliebigen einfachen Texteditor.

2. **Deinen JSON-Code schreiben:**  
   Erstelle deine Datei mit deinen eigenen Schlüsseln. Ein Schlüssel ist ein eindeutiger Name, den Minecraft verwendet, um den Text zu finden. Zum Beispiel:
   
   ```json
   {
     "modpack_name.custom.localization.key": "Dein eigener Text hier",
     "modpack_name.another.key": "Eine weitere Nachricht"
   }
   ```

3. **Die Datei speichern:**  
   Speichere die Datei als `en_us.json` für den standardmäßigen englischen Text.

Wenn du jetzt übersetzte Versionen hinzufügen möchtest, zum Beispiel Deutsch, kopiere den Inhalt aus der Datei `en_us.json` in die neue Datei und übersetze nur den eigentlichen Text, NICHT die Schlüssel! Die Schlüssel müssen gleich bleiben, damit das Spiel den Text weiterhin finden kann.

Für Deutsch würdest du die Datei dann als `de_de.json` speichern. Für andere Sprachen prüfe bitte [diese Minecraft-Wiki-Seite](https://minecraft.wiki/w/Language) für den korrekten Sprachcode deiner Sprache und benenne die Datei entsprechend. Suche nach dem **"in-game locale code"** für deine Sprache.

## Ein Minecraft-Resource-Pack für MC 1.21.4 erstellen

Jetzt, da deine Lokalisierungsdateien bereit sind, brauchen wir eine Möglichkeit, sie in Minecraft zu laden. Dafür verwenden wir ein Resource-Pack. Wir werden das Pack so einrichten, dass es standardmäßig aktiviert ist, und wir können es sogar ausblenden, wenn wir nicht möchten, dass Modpack-Nutzer daran herumspielen.

Ein **Resource-Pack** ist eine ZIP-Datei, die Dateien enthält, welche das Aussehen und Verhalten des Spiels verändern.

### Schritte zum Erstellen deines Resource-Packs

1. **Einen neuen Ordner erstellen:**  
   Erstelle einen Ordner mit einem Namen wie `my_custom_pack`, in den du deine benutzerdefinierten Lokalisierungsdateien legst.

2. **Die Pack-Datei erstellen (`pack.mcmeta`):**  
   Erstelle in deinem Ordner eine Datei namens `pack.mcmeta` mit folgendem Inhalt:
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "Mein benutzerdefiniertes Pack mit Lokalisierungen"
     }
   }
   ```
   
   *Hinweis: `pack_format` 16 ist für Minecraft 1.21.4.*

3. **Deine Lokalisierungsdateien hinzufügen:**  
   Erstelle in deinem Resource-Pack-Ordner die folgende Ordnerstruktur:
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   Lege deine benutzerdefinierte `en_us.json` (und weitere Sprachdateien wie `de_de.json`) in den `lang`-Ordner.

4. **Das Resource-Pack als ZIP packen:**  
   Sobald dein Ordner fertig ist, **komprimiere den gesamten Ordner zu einer ZIP-Datei**. Nenne die ZIP-Datei **my_custom_pack.zip**. Das ist der Beispielname, der im gesamten Leitfaden verwendet wird.

## Wo das Resource-Pack platziert werden muss

Lege deine Datei **my_custom_pack.zip** in den **Minecraft-Ordner resourcepacks**. Dieser Ordner befindet sich normalerweise hier:

- **Windows:** `%appdata%\.minecraft\resourcepacks`
- **Mac:** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux:** `~/.minecraft/resourcepacks`

> Für Modpacks befindet sich der Ordner `resourcepacks` im Instanzverzeichnis deines Packs.
{.is-warning}

## Das Pack mit „Resource Pack Overrides“ automatisch laden

Mit dem Mod **Resource Pack Overrides** können Resource-Packs standardmäßig aktiviert werden.

### Schritte zum automatischen Laden deines Packs

1. **Den Mod installieren:**  
   Lade den Mod von [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) oder [Modrinth](https://modrinth.com/mod/resource-pack-overrides) herunter und installiere ihn.

2. **Die Konfigurationsdatei finden:**  
   Finde die Datei unter `.minecraft/config/resourcepackoverrides.json`.  
   *Falls die Datei nicht existiert, erstelle sie manuell.*

3. **Die Konfigurationsdatei bearbeiten:**  
   Öffne die Datei und füge dein Resource-Pack mit seinem Dateinamen zur Liste `default_packs` hinzu:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   Dadurch wird Minecraft angewiesen, dein Resource-Pack beim Start des Spiels automatisch zu laden.

   **Wichtig ist, das Präfix `file/` hinzuzufügen!**


*Hinweis: Die Resource-Packs in der Liste werden in umgekehrter Reihenfolge angewendet. Das bedeutet, dass das Pack ganz oben in der Liste im Resource-Pack-Menü des Spiels unter den anderen angezeigt wird.*

## Das Resource-Pack im Auswahlscreen ausblenden

Du kannst dein Resource-Pack ausblenden, damit Spieler es im Auswahlscreen für Resource-Packs nicht sehen.

### So blendest du es aus

1. **Die Konfigurationsdatei erneut bearbeiten:**  
   Füge in derselben Datei `.minecraft/config/resourcepackoverrides.json` eine Überschreibung für dein Pack hinzu:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   Diese Konfiguration blendet **my_custom_pack.zip** im Auswahlscreen aus, lädt es aber weiterhin automatisch.

## Deine neuen Lokalisierungsschlüssel mit FancyMenu verwenden

Jetzt, da deine benutzerdefinierten Lokalisierungsdateien geladen sind, kannst du deine neuen Schlüssel in FancyMenu-Layouts verwenden.

1. **Ein textbasiertes Element bearbeiten:**  
   Öffne FancyMenu und wähle ein Element wie einen Button oder ein Textelement.

2. **Auf die Schaltfläche „Placeholders“ klicken:**  
   Suche oben rechts im Texteditor nach der Schaltfläche Placeholders. (Wenn du sie nicht siehst, unterstützt das Element möglicherweise keine Platzhalter.)

3. **Den Platzhalter „Localize Text“ einfügen:**  
   Der Platzhalter Localize Text erscheint als JSON-Snippet. Er sieht so aus:
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   Ersetze `localization.key` durch deinen eigenen benutzerdefinierten Schlüssel. Wenn du zum Beispiel deinen Schlüssel aus der Lokalisierungsdatei verwenden möchtest, ändere ihn zu:
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

So, und das ist im Grunde alles! Der Platzhalter sollte durch den tatsächlichen lokalisierten Inhalt ersetzt werden, wenn du ihn nicht gerade im Texteditor bearbeitest.

Beachte, dass der Platzhalter den Textinhalt immer an die aktuelle Spielsprache anpasst.

# Kein-Text-Inhalt (Bilder usw.)

FancyMenu erlaubt es dir auch, Bilder und im Grunde jedes beliebige Element zu lokalisieren.

Dafür musst du **Ladeanforderungen** verwenden.
Genauer gesagt die Anforderung **Is Game Language**.

Die Anforderung **Is Game Language** ermöglicht es dir, Elemente oder Layouts nur dann anzuzeigen, wenn eine bestimmte Spielsprache eingestellt ist. So kannst du zum Beispiel zwei Image-Elemente erstellen, die Text enthalten, und dieses Bild auf eine Version mit japanischem Text lokalisieren, wenn die Sprache auf Japanisch eingestellt ist, oder auf eine Version mit englischem Text, wenn die Sprache auf Englisch eingestellt ist.

Um Ladeanforderungen für ein **Element** festzulegen, klicke mit der rechten Maustaste darauf und dann auf **Loading Requirements**.

Um Ladeanforderungen für **ganze Layouts** festzulegen, klicke mit der rechten Maustaste auf den Hintergrund des Layout-Editors und dann auf **Loading Requirements [Layout-Wide]**.
