---
title: Benutzerdefinierte GUIs
description: Wie man dem Spiel einen neuen GUI-Bildschirm hinzufügt.
---

# Benutzerdefinierte GUIs

FancyMenu erlaubt dir, bestehende GUI-Bildschirme anzupassen, aber du kannst damit auch komplett neue hinzufügen und mit Elementen füllen.

# Einen neuen Bildschirm hinzufügen

Um einen neuen Bildschirm hinzuzufügen, gehe zu **Anpassung -> Benutzerdefinierte GUIs -> Benutzerdefinierte GUIs verwalten**.

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

Klicke im nächsten Menü auf **Neue GUI**.

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

Hier musst du deiner neuen GUI eine eindeutige Kennung geben, und du kannst weitere Teile des grundlegenden Bildschirmverhaltens anpassen.
Wenn du fertig bist, drücke **Fertig**.

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

Jetzt hast du eine neue leere GUI. Um sie zu öffnen, wähle die GUI im Menü **Benutzerdefinierte GUIs verwalten** aus und klicke auf **GUI öffnen**.

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

Dadurch wird der noch ziemlich leere GUI-Bildschirm geöffnet. Um ihn weniger leer zu machen, erstelle einfach ein neues Layout dafür, so wie du es auch bei jedem anderen Bildschirm tun würdest.

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# Die GUI über eine Aktion öffnen

Der letzte Schritt besteht darin, normalen Nutzern Zugriff auf deine GUI zu geben. Der einfachste Weg dafür ist die Aktion **Bildschirm oder benutzerdefinierte GUI öffnen** mit einem Button, Slider oder Ticker zu verwenden.

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# Die GUI über einen Befehl öffnen

Du kannst deine benutzerdefinierte GUI auch über einen [In-Game-Befehl](./commands#openguiscreen) öffnen.
Das ermöglicht sogar, die GUI aus der Ferne für andere Nutzer zu öffnen!

# Popup-Modus

Ab FancyMenu v3.8.0 unterstützen benutzerdefinierte GUIs einen „Popup-Modus“, der sie so erscheinen lässt, als würde ein Popup über einem anderen Bildschirm geöffnet werden (dem vorherigen Bildschirm, von dem aus die benutzerdefinierte GUI geöffnet wurde). Diese Einstellung kann für jede benutzerdefinierte GUI in ihren Einstellungen einzeln umgeschaltet werden.

FancyMenu 3.9.0 fügt außerdem eine Option hinzu, um das Bildschirm-Hintergrund-Overlay für benutzerdefinierte GUIs innerhalb einer Welt umzuschalten. Verwende sie, wenn du die Unschärfe oder dunkle Tönung hinter einer benutzerdefinierten GUI deaktivieren oder beibehalten möchtest, die über dem Spiel geöffnet wurde.
