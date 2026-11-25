---
title: Bildschirmkennungen
description: >-
  Informationen zu Bildschirmkennungen und dazu, wie du die Kennung eines
  Bildschirms findest.
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# Bildschirmkennungen

FancyMenu verwendet Bildschirmkennungen für Layouts, Vanilla-Widgets, [Bildschirmaktionen](/action-scripts#open-screen-or-custom-gui) und [Überschreibungen benutzerdefinierter GUIs](/custom-guis#overriding-an-existing-screen). Bei Kennungen wird zwischen Groß- und Kleinschreibung unterschieden. Kopiere sie daher exakt aus dem Debug-Overlay.

Integrierte Bildschirme verwenden normalerweise eine kurze, universelle Kennung wie `title_screen`. Für Bildschirme anderer Mods kann der Name ihrer Java-Klasse verwendet werden. Benutzerdefinierte GUIs verwenden die Kennung, die in ihrem Manager eingetragen wurde. Dies sind FancyMenu-Bildschirmkennungen und keine Minecraft-Ressourcen-IDs.

# Kennung eines Bildschirms finden

Mit dem **Debug-Overlay** kannst du die Kennung des aktuell aktiven Menüs anzeigen lassen.
Es zeigt die Kennung des aktuellen Bildschirms an. Ein Linksklick darauf kopiert sie in die Zwischenablage.

>[!TIP]
>Du kannst das **Debug-Overlay** mit **STRG + ALT + D** aktivieren, solange du dich **nicht** im Layout-Editor befindest.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Bildschirme öffnen

Die Aktion [**Bildschirm oder benutzerdefinierte GUI öffnen**](/action-scripts#open-screen-or-custom-gui) kann nur Bildschirme öffnen, die FancyMenu im aktuellen Spielzustand erstellen kann. Für manche Bildschirme müssen eine Welt, eine Verbindung, ein Spieler oder der ursprüngliche übergeordnete Bildschirm geladen sein.

Kann FancyMenu die angegebene Kennung nicht verarbeiten, wird eine Fehlermeldung angezeigt. Verwende für das Widget, das den Bildschirm normalerweise öffnet, die Aktion [**Vanilla-/Mod-Button nachahmen**](/action-scripts#mimic-vanillamod-button).
