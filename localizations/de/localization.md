---
title: Layouts lokalisieren
description: Text und andere Layout-Inhalte lokalisieren.
---

# Layouts lokalisieren

Verwende den [**Text lokalisieren**-Platzhalter](./placeholders#localize-text-local) für übersetzbaren Text:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu prüft zuerst die aktive Sprachdatei von Minecraft. Wenn der Schlüssel dort nicht vorhanden ist, werden die benutzerdefinierten Lokalisierungsdateien von FancyMenu geprüft. Wenn keine der beiden Quellen den Schlüssel enthält, wird der Schlüssel selbst angezeigt.

# Benutzerdefinierte Lokalisierungsdateien von FancyMenu

Lege die Dateien unter folgendem Pfad ab:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Erstelle ein Unterverzeichnis für deine Lokalisierungsdateien:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Lege Lokalisierungsdateien in mindestens einem Unterverzeichnis von `custom_locals` ab; Dateien, die direkt im Root von `custom_locals` liegen, werden nicht geladen. Verschachtelte Unterverzeichnisse werden unterstützt.

Unterstützte UTF-8-Formate:

| Erweiterung | Format |
|---|---|
| `.json` | JSON-Objekt; verschachtelte Objekte werden zu durch Punkte getrennten Schlüsseln |
| `.lang` | `key=value`-Zeilen |
| `.properties` | Java-Properties-Syntax |

JSON-Beispiel:

```json
{
  "modpack": {
    "menu": {
      "play": "Play"
    }
  }
}
```

Dies definiert `modpack.menu.play`.

FancyMenu kombiniert die unterstützten Dateien aus diesen Unterverzeichnissen zu einem einzigen benutzerdefinierten Lokalisierungswörterbuch. Verwende jeden Schlüssel nur in einer Datei. Benutzerdefinierte Lokalisierungsdateien wechseln nicht mit der von Minecraft ausgewählten Sprache; verwende die unten beschriebene Resource-Pack-Methode, wenn du automatisches Sprachwechseln benötigst.

Starte den Client nach dem Bearbeiten der benutzerdefinierten Lokalisierungsdateien neu.

# Sprachspezifischer Text

Für automatisches Wechseln mit der von Minecraft ausgewählten Sprache stelle normale Minecraft-Sprachdateien über ein [Resource Pack](./resources#minecraft-resources-resource-packs) bereit:

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Verwende in jeder Sprachdatei dieselben Schlüssel, aktiviere das Resource Pack und lies sie dann mit dem [**Text lokalisieren**-Platzhalter](./placeholders#localize-text-local) aus.

# Bilder und Elemente lokalisieren

Verwende die [**Ist Spielsprache**-Bedingung](./conditions#is-game-language-fancymenu_loading_requirement_is_language), um je nach Sprachcode unterschiedliche Elemente oder Layouts anzuzeigen, z. B. `en_us` und `de_de`.
