---
title: Layouts lokalisieren
description: Texte und andere Layoutinhalte lokalisieren.
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# Layouts lokalisieren

Verwende den Platzhalter [**Text lokalisieren**](/placeholders#localize-text) für übersetzbare Texte:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

FancyMenu prüft zuerst die aktiven Sprachdaten von Minecraft. Ist der Schlüssel dort nicht vorhanden, prüft FancyMenu die benutzerdefinierten Lokalisierungsdateien. Ist der Schlüssel in keiner der beiden Quellen enthalten, wird der Schlüssel selbst angezeigt.

# Benutzerdefinierte Lokalisierungsdateien von FancyMenu

Lege Dateien unter folgendem Pfad ab:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Erstelle ein Unterverzeichnis für deine Lokalisierungsdateien:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Lege Lokalisierungsdateien in mindestens einem Unterverzeichnis von `custom_locals` ab. Dateien, die direkt im Stammverzeichnis von `custom_locals` liegen, werden nicht geladen. Verschachtelte Unterverzeichnisse werden unterstützt.

Unterstützte UTF-8-Formate:

| Erweiterung | Format |
|---|---|
| `.json` | JSON-Objekt; verschachtelte Objekte werden in durch Punkte getrennte Schlüssel umgewandelt |
| `.lang` | Zeilen im Format `key=value` |
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

Damit wird `modpack.menu.play` definiert.

FancyMenu führt die unterstützten Dateien aus diesen Unterverzeichnissen zu einem benutzerdefinierten Lokalisierungswörterbuch zusammen. Verwende jeden Schlüssel nur in einer Datei. Benutzerdefinierte Lokalisierungsdateien wechseln nicht mit der in Minecraft ausgewählten Sprache. Wenn die Sprache automatisch gewechselt werden soll, verwende die unten beschriebene Methode mit Ressourcenpaketen.

Starte den Client nach dem Bearbeiten benutzerdefinierter Lokalisierungsdateien neu.

# Sprachspezifische Texte

Damit die Sprache automatisch entsprechend der in Minecraft ausgewählten Sprache wechselt, stelle reguläre Minecraft-Sprachdateien über ein [Ressourcenpaket](/resources#minecraft-resources-resource-packs) bereit:

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Verwende in jeder Sprachdatei dieselben Schlüssel, aktiviere das Ressourcenpaket und rufe die Texte anschließend mit dem Platzhalter [**Text lokalisieren**](/placeholders#localize-text) ab.

# Bilder und Elemente lokalisieren

Verwende die Bedingung [**Spiel-Sprache ist**](/conditions#is-game-language), um für verschiedene Sprachcodes wie `en_us` und `de_de` unterschiedliche Elemente oder Layouts anzuzeigen.
