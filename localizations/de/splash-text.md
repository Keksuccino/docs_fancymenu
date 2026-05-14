---
title: Splash-Text
description: Wie man benutzerdefinierte Splash-Texte in FancyMenu erstellt.
---

# Benutzerdefiniertes Splash-Text-Element

Das Splash-Text-Element in FancyMenu ist ein vollständig anpassbares Upgrade von Minecrafts hüpfenden Titelsprüchen. Es behält das bekannte Hüpfen bei und gibt dir gleichzeitig Kontrolle darüber, was angezeigt wird, wie es aussieht und wann es aktualisiert wird.

> Beachte, dass du das ursprüngliche Vanilla-Splash-Text-Element im Titelscreen nicht wirklich anpassen kannst. Du solltest es also **löschen** und stattdessen ein benutzerdefiniertes Splash-Text-Element verwenden.
{.is-warning}

## Element hinzufügen und auswählen
- Öffne den Layout-Editor und füge das Element namens `Splash Text` hinzu.
- Linksklicke es einmal, um es auszuwählen und das Begrenzungsfeld anzuzeigen, klicke dann mit der rechten Maustaste, um das Kontextmenü zu öffnen. Alle Konfigurationsoptionen befinden sich in diesem Menü.

## Wählen, woher der Splash-Text kommt
- `Source Mode: Vanilla` behält die klassischen zufälligen Splashes bei, die mit Minecraft mitgeliefert werden.
- `Source Mode: Direct Input` erlaubt es dir, eigenen Text über `Input Splash Text` einzugeben. Dies unterstützt nur eine einzelne Splash-Text-Zeile, die Zeile kann aber Platzhalter enthalten.
- `Source Mode: Text File` lädt eine zufällige Zeile aus einer `.txt`-Datei, die du mit `Set Source Text File` auswählst. Jede nicht-leere Zeile kann zum aktiven Splash werden.
- Das Wechseln des Modus setzt den aktiven Text zurück, sodass du sicher experimentieren kannst. Wenn der Text festzuhängen scheint, schalte einen anderen Modus um oder klicke `Refresh On Screen Load: Enabled`, um bei jedem Öffnen des Menüs ein erneutes Auslosen zu erzwingen.

## Beispiel für eine Textdatei
Wenn du den Quellenmodus „Text File“ verwendest, speichere deine Splash-Liste als Klartext (UTF-8 ohne BOM). Jede Zeile ist ein möglicher Splash:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Ersetze `your_placeholder_id_here` durch den Platzhalter, den du zur Laufzeit auflösen möchtest. FancyMenu wählt bei jeder Aktualisierung des Splashs eine zufällige nicht-leere Zeile aus.

## Das Aussehen nach deinen Wünschen anpassen
- Verwende `Set Scale` und `Set Rotation`, um Größe und Rotationswinkel zu steuern.
- `Set Text Color` akzeptiert einen Hex-Wert (zum Beispiel `#FFFF00`), damit es zu deinem Thema passt.
- `Shadow: Enabled` fügt Minecrafts Schlagschatten hinzu; schalte es aus für flachen Text.
- `Bouncing: Enabled` behält die vertraute Hüpfbewegung bei; deaktiviere es für eine statische Beschriftung.
- FancyMenu rendert den Splash als vollständige Minecraft-Komponente, daher funktionieren Farbcodes und andere Textdekorationen wie erwartet.

## Dynamische Textfunktionen
- Platzhalter werden vor dem Rendern aufgelöst, sodass du im Splash-Text Spielernamen, Datumsangaben oder andere unterstützte Werte verwenden kannst.
- Da das Element Minecrafts serialisiertes Komponenten-JSON akzeptiert, kannst du fortgeschrittene JSON-Snippets in Direct Input oder in deine Textdatei einfügen. Das Element deserialisiert sie automatisch und fällt auf normalen Text zurück, wenn etwas schiefgeht.

## Fehlerbehebung
- Leerer Text in Direct Input zeigt beim Bearbeiten `< empty splash element >` an. Gib irgendetwas ein (sogar ein Leerzeichen), um die Warnung zu entfernen.
- Wenn eine Textdatei keine gültigen Zeilen enthält, zeigt das Element `ERROR: SPLASH FILE IS EMPTY` an. Füge mindestens eine nicht-leere Zeile hinzu und öffne den Bildschirm erneut.
- Serialisierte JSON-Fehler fallen auf normalen Text zurück. Halte dich an Mojangs standardmäßige JSON-Struktur oder teste Snippets mit dem Vanilla-Befehl `/tellraw`, bevor du sie einfügst.
