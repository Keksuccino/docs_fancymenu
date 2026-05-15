---
title: Ressourcen
description: >-
  Wie Ressourcen in FancyMenu funktionieren. Deckt Ressourcenorte, lokale
  Ressourcen und Web-Ressourcen ab.
---

# Ressourcen

Das Ressourcen-System von FancyMenu ermöglicht es dir, Ressourcen aus Minecrafts eigenem Resource-Loader (**Ressourcenpakete**), **lokalen** Ressourcen (Dateien vom Client-System) und **Web-Quellen** (online gespeicherte Dateien) zu verwenden.

Fast alle Ressourceneingaben – egal ob Bilder, Audio, Video oder Text – werden über den Ressourcen-Auswahldialog von FancyMenu festgelegt. Es gibt einige Ausnahmen, etwa wenn ein Quellpfad für einen Platzhalter oder eine Aktion gesetzt wird, aber in den meisten Fällen legst du Ressourcen über dieselbe Ressourcen-Auswahloberfläche fest.

Wenn du eine Ressourceneingabe über die Ressourcen-Auswahloberfläche festlegst, wählst du im Grunde eine sogenannte „Ressourcenquelle“ (so nennt FancyMenu sie), die je nach Quellentyp ein Pfad, ein Link oder eine Ressourcenadresse sein kann.

FancyMenu 3.9.0 fügt dem Ressourcen-Auswahldialog einen Minecraft-Ressourcenbrowser hinzu. Damit kannst du über Ressourcenpakete geladene Ressourcen wie ein Verzeichnis durchsuchen, anstatt jede Ressourcenadresse manuell einzugeben.

# Minecraft-Ressourcen (Ressourcenpakete)

Minecraft verwendet sogenannte „Ressourcenadressen“, um auf eine Ressource zu „verweisen“.

Als Text geschriebene Ressourcenadressen bestehen aus zwei Teilen, getrennt durch einen Doppelpunkt (`:`).
Der erste Teil ist der **Namespace** und der zweite Teil ist der Rest des **Pfads zur Ressource**, einschließlich des Ressourcennamens mit Dateiendung.

Der **Namespace** einer Ressourcenadresse ist immer einfach das **oberste Verzeichnis/der oberste Ordner** des vollständigen Pfads zur Ressource.

Nehmen wir also an, du lädst ein Ressourcenpaket mit einer Ressource namens `image.png`, die unter `/assets/custom_resources/images/image.png` gespeichert ist.
In diesem Fall wäre der **Namespace** der Ressourcenadresse `custom_resources`, weil `/assets/` nur der Ort ist, von dem aus Minecraft alle seine Ressourcen lädt. `custom_resources` ist also das **oberste Verzeichnis** der Ressource.
Das bedeutet, dass `images/image.png` der **Rest des Pfads** zur Ressource ist.

Die korrekte Ressourcenadresse für die Ressource `image.png` wäre also:
`custom_resources:images/image.png`

> **Fun Fact**: Da Minecraft den Großteil seiner Ressourcen unter `/assets/minecraft/` speichert, ist der **Namespace** der meisten Minecraft-Ressourcen `minecraft`.
{.is-info}

# Lokale Ressourcen

Der einfachste Weg, Ressourcen zu laden, ist, einfach lokale Dateien zu verwenden, die auf dem Client gespeichert sind (und in den meisten Fällen mit Modpacks ausgeliefert werden).

FancyMenu erlaubt das Laden lokaler Ressourcen nur aus `/config/fancymenu/assets/`, also stelle sicher, dass du alle deine Ressourcen dort speicherst!

Das macht es außerdem sehr einfach, [lokale Ressourcen mit deinen Modpacks auszuliefern](./modpacks), da die meisten Modpack-Systeme (CurseForge, Modrinth usw.) das Ausliefern von Mod-Konfigurationsordnern standardmäßig unterstützen.

# Web-Ressourcen

Wenn du Ressourcen dynamisch ändern möchtest, ohne dein Modpack aktualisieren zu müssen, sind **Web**-Ressourcen die beste Wahl.

Eine Web-Ressource ist im Grunde einfach die **URL** zu einer auf einem Server gespeicherten Datei, also zum Beispiel `https://example-domain.net/image.png`.

Achte darauf, immer **DIREKTE URLs** zu verwenden, also URLs, die mit dem **Dateinamen und der Dateiendung** der Ressource enden, genau wie die Beispiel-URL oben.
Die Verwendung nicht-direkter URLs verschlechtert die Leistung und führt eher zu Fehlern.

# Platzhalter in Ressourcenquellen

Es ist möglich, FancyMenus Platzhalter in Ressourcenquellen zu verwenden, etwa im Pfad zu einer lokalen Quelle, in der URL zu einer Web-Quelle oder in der Ressourcenadresse zu einer Minecraft-Ressource.

Dadurch kannst du Quellen dynamisch aktualisieren, zum Beispiel die Bildquelle eines Menü-Hintergrunds ändern, wenn du eine FancyMenu-Variable setzt, um je nach Wert der Variable einen anderen Hintergrund anzuzeigen.

Du kannst die Quelle manuell bearbeiten, indem du auf die Schaltfläche **Im Editor öffnen** rechts neben dem Eingabefeld der Ressourcenquelle klickst.

> Beachte, dass dies nur für Ressourceneingaben gilt, die die normale Ressourcen-Auswahloberfläche verwenden. Es ist möglich, dass *einige* Ressourceneingaben, die den Auswahldialog nicht verwenden, Platzhalter **NICHT** unterstützen oder sich nicht dynamisch aktualisieren, wenn sich der Platzhalter ändert.
{.is-warning}
