---
title: Minecraft-Optionen setzen/abrufen
description: >-
  Wie man Minecraft-Optionen wie Lautstärke, FOV, Renderdistanz usw. setzt und
  ausliest.
---

# Mit Minecraft-Optionen in FancyMenu arbeiten

FancyMenu ermöglicht es dir, Minecraft-Spieloptionen (Options) über verschiedene UI-Elemente auszulesen und zu setzen. Diese Anleitung zeigt dir, wie du Schaltflächen, Schieberegler und Ticker verwendest, um mit Minecraft-Optionen in deinen eigenen Menü-Layouts zu arbeiten.

# Minecraft-Optionen verstehen

Minecraft hat viele integrierte Optionen, die alles von Grafikeinstellungen bis zur Lautstärke steuern. FancyMenu lässt dich auf diese Optionen über ihren Namen zugreifen.

Einige häufige Optionsnamen sind:
- `soundCategory_master` - Hauptlautstärke
- `soundCategory_music` - Musiklautstärke
- `soundCategory_ambient` - Lautstärke der Umgebungsgeräusche
- `soundCategory_players` - Lautstärke von Spielersounds
- `soundCategory_blocks` - Lautstärke von Blockgeräuschen
- `fov` - Sichtfeld
- `gamma` - Helligkeit
- `renderDistance` - Renderdistanz

# Optionswerte anzeigen

Du kannst den aktuellen Wert jeder Minecraft-Option mit einem speziellen Platzhalter anzeigen.

Der Platzhalter sieht so aus:
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

Ersetze `option_name` durch den tatsächlichen Namen der Option, die du anzeigen möchtest.

# Optionen mit Schaltflächen setzen

Schaltflächen können verwendet werden, um Minecraft-Optionen auf bestimmte Werte zu setzen.

## So richtest du eine Schaltfläche ein:

1. Erstelle ein neues Schaltflächen-Element
2. Setze die Beschriftung der Schaltfläche (das, was auf der Schaltfläche angezeigt wird)
3. Füge eine Aktion hinzu: Rechtsklick auf die Schaltfläche → Action Script bearbeiten → Aktion hinzufügen → Minecraft-Optionswert setzen
4. Im Fenster „Minecraft-Optionswert setzen“:
   - Name: Gib den Optionsnamen ein (z. B. `renderDistance`)
   - Wert: Gib den zu setzenden Wert ein (z. B. `16`)

## Beispiel: 

Eine Schaltfläche erstellen, die die Renderdistanz auf 16 Chunks setzt:
- Optionsname: `renderDistance`
- Wert: `16`
- Beschriftung: „Renderdistanz auf 16 Chunks setzen“

# Optionen mit Schiebereglern setzen

Schieberegler eignen sich perfekt für Optionen mit einem Wertebereich, wie Lautstärkeeinstellungen oder Helligkeit.

## So richtest du einen Schieberegler ein:

1. Erstelle ein neues Schieberegler-Element
2. Setze den Schieberegler-Typ:
   - Für ganze Zahlen (z. B. Renderdistanz): Wähle „Integer Range“
   - Für Dezimalzahlen (z. B. Lautstärke): Wähle „Decimal Range“
3. Lege den Minimal- und Maximalwert fest
4. Füge eine Aktion hinzu, um die Minecraft-Option zu setzen:
   - Rechtsklick → Action Script bearbeiten → Aktion hinzufügen → Minecraft-Optionswert setzen
   - Name: Der Optionsname
   - Wert: `$$value` (diese spezielle Variable enthält den aktuellen Wert des Schiebereglers)
5. Setze den voreingestellten Wert auf den aktuellen Optionswert:
   - Setze „Pre-Selected Value“ auf `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

## Beispiel für Beschriftungsformate von Schiebereglern:

Um den aktuellen Optionswert in der Beschriftung des Schiebereglers anzuzeigen, verwende:
```
Lautstärke: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

Um einen Prozentsatz anzuzeigen (nützlich für Lautstärke):
```
Lautstärke: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# Optionen mit Tickern setzen

Ticker sind unsichtbare Elemente, die Optionen automatisch nach einem Zeitplan ändern können.

## So richtest du einen Ticker ein:

1. Erstelle ein neues Ticker-Element
2. Konfiguriere die Tick-Einstellungen:
   - Tick Mode: Wähle, wann die Option aktualisiert werden soll
   - Tick Delay: Lege fest, wie oft aktualisiert wird (in Millisekunden)
3. Füge die Aktion zum Setzen einer Minecraft-Option hinzu:
   - Rechtsklick → Action Script bearbeiten → Aktion hinzufügen → Minecraft-Optionswert setzen
   - Setze Optionsname und Wert

## Beispiel:

Gamma (Helligkeit) beim Laden des Menüs auf Maximum setzen:
- Tick Mode: On Load Screen
- Name: `gamma`
- Wert: `1.0`

# Häufige Anwendungsfälle

Hier sind einige typische Möglichkeiten, was du mit FancyMenu beim Setzen und Auslesen von Minecraft-Optionen tun kannst.

## Eigene Lautstärke-Schieberegler erstellen

Lautstärke-Schieberegler sind ein häufiger Anwendungsfall für die Minecraft-Optionsintegration. So erstellst du einen eigenen Musiklautstärke-Regler:

1. Erstelle ein neues Schieberegler-Element
2. Setze den „Slider Type“ auf „Decimal Range“
3. Setze den „Minimum Range Value“ auf „0.0“
4. Setze den „Maximum Range Value“ auf „1.0“
5. Action Script bearbeiten → Aktion hinzufügen → Minecraft-Optionswert setzen
   - Setze Name auf `soundCategory_music`
   - Setze Wert auf `$$value`
6. Setze „Pre-Selected Value“ auf `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`
7. Um die Lautstärke als Prozentsatz anzuzeigen, setze die Beschriftung auf: 
   ```
   Musik: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

Du kannst ähnliche Schieberegler für andere Sound-Kategorien erstellen:
- Hauptlautstärke: `soundCategory_master`
- Musik: `soundCategory_music`
- Umgebungsgeräusche: `soundCategory_ambient`
- Blöcke: `soundCategory_blocks`
- Spieler: `soundCategory_players`
- Wetter: `soundCategory_weather`

## Einen eigenen FOV-Schieberegler erstellen

Das Sichtfeld (FOV) ist eine wichtige Grafikeinstellung, die bestimmt, wie weit dein Blick im Spiel ist. Die FOV-Option verwendet intern Werte von -1.0 bis 1.0, wird aber in der UI als 30 bis 110 angezeigt.

### Die FOV-Wertzuordnung verstehen
- Interner Wertebereich: -1.0 bis 1.0
- Angezeigter Wertebereich: 30 bis 110
- Zuordnungsformel: `(internal_value + 1) * 40 + 30`

### Schritt 1: Ein Ticker-Element erstellen, um den FOV-Text zu aktualisieren

Zuerst benötigen wir einen Ticker, der den aktuellen FOV-Wert prüft und eine Variable mit der passenden Beschreibung setzt:

1. Erstelle ein neues Ticker-Element
2. Setze den „Tick Mode“ auf „Normal“ (damit er fortlaufend aktualisiert)
3. Setze den „Tick Delay“ auf etwa „10“ (Millisekunden), um übermäßige Prüfungen zu vermeiden

Jetzt müssen wir Aktionen für die FOV-Beschriftungen einrichten. So sollte die Struktur deines Action Scripts aussehen:

```
▶ Action Script
│
├─▶ IF (gemapptes FOV = 70)
│  └─■ Variablenwert setzen: fov_text:Normal
│
├─▶ ELSE-IF (gemapptes FOV = 110)
│  └─■ Variablenwert setzen: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Variablenwert setzen: fov_text:[berechneter numerischer Wert]
```

So richtest du die einzelnen Teile ein:

#### Das FOV-Label „Normal“ einrichten:
1. Rechtsklick → Action Script bearbeiten → Aktion hinzufügen
2. Klicke auf „IF Statement“, um einen bedingten Block hinzuzufügen
3. Setze die Bedingung auf „Is Number“ mit:
   - Compare Mode: „equals“
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: „70“
4. Füge innerhalb dieses IF-Blocks die Aktion „Set Variable Value (FM Variable)“ hinzu mit:
   - Wert: `fov_text:Normal`

#### Das FOV-Label „Quake Pro“ einrichten:
1. Füge im Action Script ein „ELSE-IF Statement“ hinzu
2. Setze die Bedingung auf „Is Number“ mit:
   - Compare Mode: „equals“
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: „110“
3. Füge innerhalb dieses ELSE-IF-Blocks die Aktion „Set Variable Value (FM Variable)“ hinzu mit:
   - Wert: `fov_text:Quake Pro`

#### Das numerische FOV-Label einrichten:
1. Füge einen „ELSE Statement“-Block hinzu
2. Füge innerhalb dieses ELSE-Blocks die Aktion „Set Variable Value (FM Variable)“ hinzu mit:
   - Wert: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="FOV Slider Action Script" style="max-width: 600px; height: auto;">

### Schritt 2: Den FOV-Schieberegler erstellen

1. Erstelle ein neues Schieberegler-Element
2. Setze den „Slider Type“ auf „Decimal Range“
3. Setze den „Minimum Range Value“ auf „-1.0“
4. Setze den „Maximum Range Value“ auf „1.0“
5. Action Script bearbeiten → Aktion hinzufügen → Minecraft-Optionswert setzen
   - Setze Name auf `fov`
   - Setze Wert auf `$$value`
6. Setze „Pre-Selected Value“ auf `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`

### Schritt 3: Die Schieberegler-Beschriftung festlegen

Setze die Beschriftung des Schiebereglers so, dass einfach die FOV-Textvariable angezeigt wird:

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

Diese Beschriftung zeigt:
- „FOV: Normal“ an, wenn der Wert 70 ist
- „FOV: Quake Pro“ an, wenn der Wert 110 ist  
- „FOV: 85“ (oder jede andere Zahl) für alle anderen Werte

### Tipps für FOV-Schieberegler

- Der interne Wertebereich des Schiebereglers ist -1.0 bis 1.0 und muss für die Anzeige auf 30 bis 110 abgebildet werden
- Die Umrechnungsformel lautet: `(internal_value + 1) * 40 + 30`
- Nur zwei Werte haben spezielle Bezeichnungen: 70 (Normal) und 110 (Quake Pro)
- Das Standard-FOV in Minecraft ist 70 (was dem internen Wert 0.0 entspricht)
- Die Variable `fov_text` enthält automatisch entweder das spezielle Label oder den numerischen Wert

## Optionswerte in Text-Elementen anzeigen

Du kannst aktuelle Optionswerte auch in Text-Elementen anzeigen:

1. Erstelle ein Text-Element
2. Verwende für den Textinhalt den Platzhalter: `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

Um beispielsweise die aktuelle Renderdistanz anzuzeigen:
```
Aktuelle Renderdistanz: {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} Chunks
```

# Optionsnamen finden

Du kannst die Namen aller verfügbaren Optionen so finden:

  1. Eine Schaltfläche erstellen
  2. Mit Rechtsklick darauf klicken
  3. Auf „Action Script bearbeiten“ klicken
  4. Die Aktion „Minecraft-Optionswert setzen“ hinzufügen
  5. Beim Bearbeiten des Aktionswerts die Dropdown-Vorschläge ansehen, sobald du im Feld „Name“ zu tippen beginnst
  
# Wichtige Tipps

- **Gültige Werte**: Nicht alle Optionen akzeptieren alle Werte. Zum Beispiel:
  - Lautstärkeoptionen akzeptieren Werte von 0.0 bis 1.0
  - Die Renderdistanz akzeptiert normalerweise ganze Zahlen von 2 bis 32
  - Boolesche Optionen (true/false) wie `pauseOnLostFocus` akzeptieren „true“ oder „false“

- **Testen**: Teste deine Einstellungen immer, um sicherzustellen, dass sie wie erwartet funktionieren!

- **Visuelles Feedback**: Gib den Nutzern visuelles Feedback über den aktuellen Wert mit den oben beschriebenen Platzhaltern.
