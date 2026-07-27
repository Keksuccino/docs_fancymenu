---
title: Bildschirm-IDs
description: Über Bildschirm-IDs und wie man die ID eines Bildschirms findet.
---
# Bildschirm-IDs

FancyMenu verwendet Bildschirm-IDs für Layouts, Vanilla-Widgets, [Bildschirmaktionen](./action-scripts#open-screen-or-custom-gui-opengui) und [Custom-GUI-Overrides](./custom-guis#overriding-an-existing-screen). IDs sind groß-/kleinschreibungssensitiv, also kopiere sie exakt aus dem Debug-Overlay.

Integrierte Bildschirme verwenden normalerweise eine kurze, universelle ID wie `title_screen`. Andere Mod-Bildschirme können ihren Java-Klassennamen verwenden. Custom GUIs verwenden die ID, die im Manager eingegeben wurde. Das sind FancyMenu-Bildschirm-IDs, nicht Minecraft-Resource-Locations.

# Die ID eines Bildschirms finden

Du kannst die ID des aktuell aktiven Menüs über das **Debug-Overlay** sehen.
Es enthält die ID des aktuellen Bildschirms und ermöglicht es dir, sie mit einem Linksklick in die Zwischenablage zu kopieren.

>[!TIP]
>Du kannst das **Debug-Overlay** aktivieren, indem du **STRG + ALT + D** drückst, während du **nicht** im Layout-Editor bist.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Bildschirme öffnen

Die [**Bildschirm oder Custom GUI öffnen**-Aktion](./action-scripts#open-screen-or-custom-gui-opengui) kann nur Bildschirme öffnen, die FancyMenu im aktuellen Spielzustand erstellen kann. Manche Bildschirme erfordern eine geladene Welt, eine Verbindung, einen Spieler oder den ursprünglichen übergeordneten Bildschirm.

Wenn FancyMenu die ID nicht erstellen kann, wird ein Fehler angezeigt. Verwende [**Vanilla/Mod-Button nachahmen**](./action-scripts#mimic-vanillamod-button-mimicbutton) für das Widget, das den Bildschirm normalerweise öffnet.
