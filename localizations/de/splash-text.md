---
title: Splash-Text
description: So erstellst du benutzerdefinierte Splash-Texte in FancyMenu.
---

# Benutzerdefiniertes Splash-Text-Element

Das Splash-Text-Element in FancyMenu ist eine vollständig anpassbare Weiterentwicklung der hüpfenden Titel-Splashes aus Minecraft. Es behält das vertraute Springen bei, gibt dir aber Kontrolle darüber, was angezeigt wird, wie es aussieht und wann es aktualisiert wird.

> [!WARNING]
> Beachte, dass du das originale Vanilla-Splash-Text-Element im Titelscreen nicht wirklich anpassen kannst. Du solltest es daher **löschen** und stattdessen ein benutzerdefiniertes Splash-Text-Element verwenden.

## Element hinzufügen und auswählen
- Öffne den Layout-Editor und füge das Element `Splash Text` hinzu.
- Linksklicke es einmal, um es auszuwählen und den Begrenzungsrahmen anzuzeigen. Klicke dann mit der rechten Maustaste, um das Kontextmenü zu öffnen. Alle Konfigurationsoptionen befinden sich in diesem Menü.

## Wählen, woher das Splash-Text kommt
- `Source Mode: Vanilla` verwendet die klassischen zufälligen Splashes, die mit Minecraft geliefert werden.
- `Source Mode: Direct Input` erlaubt dir, deinen eigenen Text über `Input Splash Text` einzugeben. Dies unterstützt nur eine einzelne Splash-Text-Zeile, aber die Zeile kann Platzhalter enthalten.
- `Source Mode: Text File` lädt eine zufällige Zeile aus einer `.txt`-Datei, die du mit `Set Source Text File` auswählst. Jede nicht leere Zeile kann als aktives Splash verwendet werden.
- Das Umschalten des Modus setzt den aktiven Text zurück, sodass du gefahrlos experimentieren kannst. Wenn der Text festzuhängen scheint, wechsle kurz in einen anderen Modus oder klicke `Refresh On Screen Load: Enabled`, um bei jedem Öffnen des Menüs ein neues Ergebnis zu erzwingen.

## Beispiel-Textdatei
Wenn du den Quellmodus „Text File“ verwendest, speichere deine Splash-Liste als Klartext (UTF-8 ohne BOM). Jede Zeile ist ein mögliches Splash:

```
Willkommen bei FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"Dies ist goldener und fetter Text.","color":"gold","bold":true}
&6Verwende &lMinecraft-Formatierungscodes!
```

Ersetze `your_placeholder_id_here` durch den Platzhalter, der zur Laufzeit aufgelöst werden soll. FancyMenu wählt bei jeder Aktualisierung des Splash-Texts eine zufällige nicht leere Zeile aus.

## So sieht es aus, wie du es möchtest
- Verwende `Set Scale` und `Set Rotation`, um Größe und Drehwinkel zu steuern.
- `Set Text Color` akzeptiert einen Hex-Wert (zum Beispiel `#FFFF00`), um zu deinem Design zu passen.
- `Shadow: Enabled` fügt Minecrafts Schlagschatten hinzu; schalte es aus für flachen Text.
- `Bouncing: Enabled` behält die vertraute hüpfende Bewegung bei; deaktiviere es für ein statisches Label.
- FancyMenu rendert das Splash als vollständige Minecraft-Komponente, daher funktionieren Farbcodes und andere Textdekorationen wie erwartet.

## Dynamische Textfunktionen
- Platzhalter werden vor dem Rendern aufgelöst, sodass du im Splash-Text auf Spielernamen, Daten oder andere unterstützte Werte verweisen kannst.
- Da das Element Minecrafts serialisiertes Komponenten-JSON akzeptiert, kannst du erweiterte JSON-Snippets in Direct Input oder in deine Textdatei einfügen. Das Element deserialisiert sie automatisch und fällt auf Literaltext zurück, wenn etwas schiefgeht.

## Fehlerbehebung
- Leerer Text in Direct Input zeigt beim Bearbeiten `< empty splash element >` an. Gib irgendetwas ein (sogar ein Leerzeichen), um die Warnung zu entfernen.
- Wenn eine Textdatei keine gültigen Zeilen enthält, zeigt das Element `ERROR: SPLASH FILE IS EMPTY` an. Füge mindestens eine nicht leere Zeile hinzu und öffne den Bildschirm erneut.
- Fehler in serialisiertem JSON fallen auf Klartext zurück. Halte dich an Mojangs standardmäßige JSON-Struktur oder teste Snippets mit dem Vanilla-Befehl `/tellraw`, bevor du sie einfügst.
