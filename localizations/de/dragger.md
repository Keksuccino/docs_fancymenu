---
title: Dragger
description: >-
  Lass Spieler ein Panel, eine Notiz oder ein anderes Element in deinen Menüs
  greifen und an eine beliebige Stelle verschieben.
sourceBlobSha: 5cfe57388c5b839c5a98045d0086a94df6b4110c
---

# Dragger

Ein Dragger ist ein unsichtbarer Bereich, den Spieler mit der Maus greifen und verschieben können. Alles, was daran verankert ist, bewegt sich mit – etwa ein Panel mit Patchnotes oder eine Notiz mit Serverregeln. Das Menü merkt sich, wo Spieler das Element abgelegt haben, sogar nach einem Neustart.

<img width="800" alt="Ein Spieler greift das Patchnotes-Banner am Ledergriff seiner Stange und zieht es von der linken auf die rechte Seite des Titelbildschirms, öffnet die Optionen, kehrt zurück und sieht, dass das Banner immer noch rechts ist" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_hero.gif?raw=true">

Spieler können es nur außerhalb des Layout-Editors verschieben. Im Editor ist der Dragger ein roter Kasten mit seinem Namen (**Farbe im Editor** im Rechtsklickmenü ändert die Farbe), und alles bleibt an der Stelle, die das Layout vorgibt.

# Etwas verschiebbar machen

<img width="800" alt="Einen Dragger über Neues Element hinzufügen, auf die Größe des Banners vergrößern, auf das Banner ziehen und zwei Ebenen nach unten verschieben; anschließend das Banner vom Dragger weg und wieder zurückziehen und dort halten, bis der Balken voll ist, um das Banner daran zu verankern" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_setup.gif?raw=true">

1. Erstelle das Element, das verschoben werden soll, zum Beispiel ein Bannerbild mit einem Textelement darauf.
2. Klicke im Layout-Editor mit der rechten Maustaste auf eine freie Stelle und dann auf **Neues Element -> Dragger**.
3. Vergrößere den Dragger auf die Größe des Banners und verschiebe ihn auf das Banner.
4. Klicke mit der rechten Maustaste auf den Dragger und dann auf **Eine Ebene nach unten verschieben**, bis er unter allen Elementen des Banners liegt. Ausgewählte Elemente werden immer ganz oben angezeigt. Klicke also auf eine freie Stelle, um die Änderung zu sehen.
5. Verankere das Banner am Dragger: Ziehe das Banner ein Stück vom Dragger weg und wieder zurück, und halte es dort, bis der Balken voll ist. Weitere Informationen findest du unter [Elemente positionieren](/positioning-elements#anchoring-elements-to-other-elements).
6. Speichere das Layout und probiere es außerhalb des Editors aus.

Elemente, die an etwas Beweglichem verankert sind, bewegen sich ebenfalls mit. Im GIF ist der Text am Banner verankert, daher muss nur das Banner mit dem Dragger verbunden werden.

Um mehrere Elemente gleichzeitig zu verankern, klicke vor Schritt 4 mit der rechten Maustaste auf den Dragger und dann auf **Element-ID kopieren**. Wähle anschließend die Elemente aus, klicke mit der rechten Maustaste auf eines davon, wähle **Ankerpunkt -> Anderes Element** und füge die ID ein.

> [!TIP]
> Spieler können den Dragger nicht sehen. Zeige ihnen daher, wo sie zugreifen können, zum Beispiel mit einer Titelleiste oder einem Griff.

# Position speichern

Die Option **Benutzerverschiebung speichern** im Rechtsklickmenü des Draggers ist bei neuen Draggers aktiviert.

- **Aktiviert**: Die Position wird gespeichert, sobald der Spieler das Element loslässt. Sie bleibt auch nach dem Schließen des Bildschirms und einem Neustart des Spiels erhalten.
- **Deaktiviert**: Beim erneuten Öffnen des Bildschirms sowie bei Änderungen der Fenstergröße oder der GUI-Skalierung kehrt alles an die Position im Layout zurück.

Wenn du die Option im Editor deaktivierst, wird auch die von Spielern gespeicherte Position dieses Draggers vergessen.

Die Positionen werden für jeden Dragger anhand seiner [Element-ID](/element-identifiers) in `fancymenu_data/dragger_metas.json` gespeichert. Dieser Ordner gehört nicht zu den [Profilen](/profiles). Deshalb landen die Positionen, die du beim Testen verschoben hast, nicht im Ordner `config/fancymenu/` deines Modpacks. Weitere Informationen findest du unter [Speicherorte für Daten](/data-storage-locations#instance-data).

Um alle Dragger wieder an ihre Position im Layout zu setzen, lösche bei geschlossenem Spiel die Datei `dragger_metas.json`.

# Was Spieler greifen können

Spieler greifen den Dragger dort, wo kein darüberliegendes Element den Klick abfängt:

- Bilder darüber lassen den Klick durch, sodass Spieler das Banner selbst greifen können.
- Schaltflächen und der Text von Textelementen darüber fangen den Klick ab. So funktionieren sie weiterhin auf einem verschiebbaren Panel.
- Dort, wo der Dragger über einer Schaltfläche liegt, erhält die Schaltfläche keine Klicks. Deshalb wird der Dragger in den obigen Schritten unter das Banner gelegt.

Wenn die [Bedingungen](/element-visibility#showing-elements-only-sometimes) den Dragger ausblenden, können Spieler ihn nicht greifen.

# Auf dem Bildschirm bleiben

Die Option **Auf dem Bildschirm bleiben** ist bei neuen Elementen aktiviert. Sie stoppt den Dragger an den Bildschirmrändern, sodass Spieler ihn nicht aus dem sichtbaren Bereich ziehen können. Wenn der Dragger so groß wie das ganze Banner ist, hält auch das Banner am Rand an.

Ein Dragger, der nur einen Teil abdeckt, zum Beispiel eine Titelleiste, funktioniert ebenfalls. Die daran verankerten Elemente haben jedoch ihre eigene Option **Auf dem Bildschirm bleiben**: Am Rand halten sie selbst an, während sich der Dragger weiterbewegt, und das Panel fällt auseinander. Deaktiviere die Option für diese Elemente, damit sie sich mit dem Dragger bewegen und nur die Titelleiste auf dem Bildschirm bleibt.
