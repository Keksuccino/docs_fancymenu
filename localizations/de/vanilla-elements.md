---
title: Vanilla-Elemente
description: 'Wie man Elemente anpasst, die standardmäßig Teil von Bildschirmen sind.'
---

# Vanilla-Elemente

FancyMenu ermöglicht es dir nicht nur, neue Elemente zu Bildschirmen hinzuzufügen, sondern auch bestehende Elemente aus dem Basisspiel (Vanilla) und sogar aus anderen Mods anzupassen.

## Vanilla-Buttons und -Slider (Widgets)

Um vorhandene Vanilla-/Mod-Widgets anzupassen, erstelle einfach ein neues Layout **„für den aktuellen Bildschirm“** (NICHT universell!) und **klicke mit der rechten Maustaste** im Editor auf die Elemente, genau wie bei benutzerdefinierten Elementen.

Du kannst ihre **Beschriftungen und Texturen** anpassen, genau wie bei benutzerdefinierten Buttons und Slidern.

Das Einzige, was du bei Vanilla-/Mod-Widgets **nicht** ändern kannst, ist ihr **Aktionsskript** (also z. B. was sie beim Interagieren tun). Das ist nur bei benutzerdefinierten Buttons und Slidern möglich.

## Automatische Klicks

Vanilla- und Mod-Widgets besitzen die Eigenschaft **Automatische Klicks**. Setze sie auf eine ganze Zahl größer als `0`, um beim Laden des Bildschirms so oft das ursprüngliche Linksklick-Verhalten des Widgets auszulösen. Wenn du zum Beispiel `2` einstellst, wird das Widget beim ersten Update jedes neu geöffneten Bildschirms zweimal geklickt. Der Standardwert `0` deaktiviert automatische Klicks.

Das sind echte Widget-Klicks: Jeder Klick kann den Wert eines Sliders oder eines Zyklus-Buttons ändern, den normalen Callback des Widgets ausführen oder sogar einen anderen Bildschirm öffnen. Teste das Ergebnis sorgfältig, besonders wenn du mehr als einen Klick konfigurierst.

Um Vanilla-/Mod-Widgets zu **verschieben** und **zu skalieren**, musst du ihnen zuerst einen Ankerpunkt zuweisen. Klicke dazu mit der **rechten Maustaste** darauf und dann auf **Ankerpunkt**. Setze ihn auf etwas anderes als **Original**, denn das ist der Standard-Ankerpunkt von Vanilla-/Mod-Elementen.

Du kannst Vanilla-/Mod-Widgets auch einfach **ausblenden**, indem du sie mit der **rechten Maustaste** anklickst und auf **Löschen** klickst. Sie werden dabei nicht wirklich gelöscht, sondern nur ausgeblendet, und du kannst sie wiederherstellen, indem du auf **Menüleiste -> Element -> Gelöschte Vanilla-Elemente** klickst und dann auf die Elemente **links klickst**, die wieder sichtbar werden sollen.

> [!WARNING]
> Das **Copyright**-Widget im Titelbildschirm ist das einzige, das du **NICHT** ausblenden/löschen kannst. Das ist absichtlich so vorgesehen. Bitte entferne keine Copyright-Hinweise.

## Elemente des Titelbildschirms

Der Titelbildschirm enthält Elemente, die keine normalen Widgets sind (wie das Logo, der Splash-Text usw.) und nicht verschoben oder angepasst werden können. Diese sollen gelöscht und durch benutzerdefinierte Elemente ersetzt werden (z. B. ein Bild-Element für das Logo oder ein benutzerdefiniertes Splash-Text-Element für den Vanilla-Splash-Text).

Um sie zu löschen, klicke einfach mit der rechten Maustaste darauf. Wenn du sie später wiederherstellen möchtest, klicke einfach auf **Menüleiste -> Element -> Gelöschte Vanilla-Elemente** und **links auf das Element**, das wieder sichtbar werden soll.

## Fehlerbehebung: Vanilla-Elemente sind im Editor nicht sichtbar

Wenn du Vanilla-Elemente im Editor nicht sehen kannst, liegt das wahrscheinlich daran, dass du ein **universelles Layout** verwendest statt eines **für den aktuellen Bildschirm**. Achte darauf, ein Layout für den aktuellen Bildschirm zu erstellen. Layouts für den aktuellen Bildschirm kannst du nur erstellen, wenn für diesen Bildschirm Anpassungen aktiviert sind.

## Fehlerbehebung: Anpassungen werden nicht angewendet

Wenn Anpassungen an Vanilla-Elementen außerhalb des Editors nicht übernommen werden, liegt das meistens daran, dass eine andere Mod das übergeordnete Menü der Vanilla-Elemente überschreibt oder verändert.

Ein gutes Beispiel für eine Mod, die einen Bildschirm/ein Menü überschreibt, ist **Ice and Fire**, das den Titelbildschirm überschreibt.

Dass Anpassungen nicht auf Menüs angewendet werden, betrifft nicht nur Vanilla-Elemente. Benutzerdefinierte Elemente, die zu Bildschirmen hinzugefügt werden, werden vermutlich ebenfalls nicht auf Menüs angewendet, wenn eine Mod sie überschreibt oder verändert.
