---
title: Vanilla-Elemente
description: 'Wie man Elemente anpasst, die standardmäßig Teil von Bildschirmen sind.'
---

# Vanilla-Elemente

FancyMenu ermöglicht es dir nicht nur, neue Inhalte zu Bildschirmen hinzuzufügen, sondern auch bestehende Elemente aus dem Basisspiel (Vanilla) und sogar aus anderen Mods anzupassen.

## Vanilla-Buttons und -Slider (Widgets)

Um vorhandene Vanilla-/Mod-Widgets anzupassen, erstelle einfach ein neues Layout **"for the current screen"** (NICHT universal!) und **klicke die Elemente im Editor mit der rechten Maustaste an**, genau wie bei benutzerdefinierten Elementen.

Du kannst ihre **Beschriftungen und Texturen** genauso anpassen wie bei benutzerdefinierten Buttons und Slidern.

Das Einzige, was du mit Vanilla-/Mod-Widgets **nicht** tun kannst, ist ihr **Aktionsskript** anzupassen (also zu ändern, was sie beim Interagieren tun). Das ist nur bei benutzerdefinierten Buttons und Slidern möglich.

Um Vanilla-/Mod-Widgets zu **verschieben** und **in der Größe zu ändern**, musst du ihnen zuerst einen Ankerpunkt zuweisen. Klicke dazu mit der **rechten Maustaste** darauf und dann auf **Anchor Point**. Stelle ihn auf etwas anderes als **Original**, da dies der Standard-Ankerpunkt von Vanilla-/Mod-Elementen ist.

Du kannst Vanilla-/Mod-Widgets auch **ausblenden**, indem du einfach mit der **rechten Maustaste** darauf klickst und dann auf **Delete** klickst. Sie werden dabei nicht wirklich gelöscht, sondern nur verborgen. Du kannst sie wiederherstellen, indem du auf **menu bar -> Element -> Deleted Vanilla Elements** klickst und dann mit der **linken Maustaste** auf die Elemente klickst, die wieder sichtbar werden sollen.

> Das **Copyright**-Widget auf dem Titelbildschirm ist das einzige, das du **NICHT** ausblenden/löschen **kannst**. Das ist absichtlich so vorgesehen. Bitte entferne keine Copyright-Hinweise.
{.is-warning}

## Elemente des Titelbildschirms

Der Titelbildschirm hat Elemente, die keine normalen Widgets sind (wie das Logo, der Splash-Text usw.) und nicht verschoben oder angepasst werden können. Sie sind dafür gedacht, gelöscht und durch benutzerdefinierte Elemente ersetzt zu werden (zum Beispiel ein Image-Element für das Logo oder ein benutzerdefiniertes Splash-Text-Element für den Vanilla-Splash-Text).

Um sie zu löschen, klicke einfach mit der rechten Maustaste darauf. Wenn du sie später wiederherstellen möchtest, klicke einfach auf **menu bar -> Element -> Deleted Vanilla Elements** und **links-klicke** auf das Element, das wieder sichtbar werden soll.

## Fehlerbehebung: Vanilla-Elemente sind im Editor nicht sichtbar

Wenn du im Editor keine Vanilla-Elemente sehen kannst, liegt das wahrscheinlich daran, dass du ein **universelles Layout** anstelle eines Layouts **für den aktuellen Bildschirm** verwendest. Achte darauf, ein Layout für den aktuellen Bildschirm zu erstellen. Layouts für den aktuellen Bildschirm kannst du nur erstellen, wenn für diesen Bildschirm Anpassungen aktiviert sind.

## Fehlerbehebung: Anpassungen werden nicht übernommen

Wenn Anpassungen an Vanilla-Elementen außerhalb des Editors nicht übernommen werden, liegt das meist daran, dass ein anderes Mod das übergeordnete Menü der Vanilla-Elemente überschreibt oder verändert.

Ein ziemlich gutes Beispiel für ein Mod, das einen Bildschirm/ein Menü überschreibt, ist **Ice and Fire**, das den Titelbildschirm überschreibt.

Dass Anpassungen nicht auf Menüs angewendet werden, betrifft nicht nur Vanilla-Elemente. Benutzerdefinierte Elemente, die zu Bildschirmen hinzugefügt wurden, werden wahrscheinlich ebenfalls nicht auf Menüs angewendet, wenn ein Mod diese überschreibt oder verändert.
