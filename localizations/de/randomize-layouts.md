---
title: Layouts zufällig auswählen
description: Wie vollständige Layouts oder Teile davon zufällig ausgewählt werden.
---

# Zufallsauswahl

FancyMenu bietet viele Funktionen, mit denen du Layouts oder Teile davon zufällig auswählen kannst.

Das kann zum Beispiel nützlich sein, wenn Nutzer bei jedem Öffnen eines Bildschirms unterschiedliche Hintergrundbilder sehen sollen oder wenn im Ladebildschirm zufällige Tipps angezeigt werden sollen.

# Layouts zufällig auswählen

In FancyMenu gibt es eine Funktion, mit der du eine Gruppe von Layouts erstellen kannst, aus der das System automatisch ein zufälliges Layout auswählt. Auf diese Weise kannst du im Grunde bei jedem Start des Spiels oder beim Öffnen eines Bildschirms ein komplett anderes, zufällig ausgewähltes Menülayout anzeigen. Du kannst damit aber auch nur Teile des Bildschirms ändern, zum Beispiel den Hintergrund.

## Zufallsmodus

Um Layouts zufällig auszuwählen, musst du für jedes Layout, das als möglicher Kandidat für die Zufallsauswahl dienen soll, den **Zufallsmodus** aktivieren. Klicke dazu mit der **rechten Maustaste** auf den **Editor-Hintergrund** und suche nach dem Eintrag **Random Mode**.

<br>

<img width="351" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/ef0f22d5-2f48-47cd-b526-d12415d8e099">

## Zufallsgruppen-ID

Nachdem du den Zufallsmodus aktiviert hast, musst du die **Random Group Identifier** festlegen.
Diese Zahl muss für alle Layouts, die zur **gleichen Gruppe** gehören sollen, **dieselbe** sein.

<br>

<img width="301" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/dde0c94e-9729-4251-9aca-32a55c3dfd02">

<br>

<img width="377" alt="Screenshot_8" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/25e7777c-0503-4e54-b866-e85647241eee">

## Verhalten der Zufallsauswahl

Wenn das System nur **einmal pro Spielsitzung** ein zufälliges Layout aus der Gruppe auswählen soll, aktiviere **Randomize Only First Time**. Dadurch wird beim ersten Öffnen des Bildschirms ein Layout ausgewählt und danach immer dasselbe Layout verwendet, das beim ersten Mal gewählt wurde. Wenn diese Option deaktiviert ist, wird bei jedem Öffnen des Bildschirms ein zufälliges Layout ausgewählt.

<br>

<img width="305" alt="Screenshot_9" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/355e49eb-73b0-4646-aeb2-c6f113f6ce3b">

# Beispiel 1: Hintergrund

Angenommen, du möchtest den Hintergrund des Titelscreens zufällig auswählen.

Dazu musst du **ein Layout pro Hintergrund** erstellen und _**NUR**_ den Hintergrund in diesen Layouts ändern sowie den Zufallsmodus mit der korrekten Zufallsgruppen-ID aktivieren.

In diesem Beispiel verwenden wir die Zufallsgruppen-ID **10**. Diese ID muss für jedes Layout dieser zufälligen Layoutgruppe gesetzt werden.

Am einfachsten geht das, indem du ein Layout mit der richtigen Zufallsgruppen-ID vorbereitest und dann einfach **Speichern unter** verwendest. Ändere den Hintergrund jedes Mal, wenn du das Layout unter einem neuen Namen speicherst. So erhältst du mehrere Layouts mit unterschiedlichen Hintergründen, und eines dieser Layouts wird jedes Mal ausgewählt, wenn du den Bildschirm öffnest oder einmal pro Spielsitzung.

# Beispiel 2: Element

Ein weiterer häufiger Anwendungsfall ist die Zufallsauswahl eines Text- oder Bildelements.

Genauso wie beim Hintergrund erstellst du für jede Variante des Elements, die zufällig ausgewählt werden soll, ein eigenes Layout. Füge dem Layout nur das Element hinzu und nichts anderes. Nimm keine weiteren Anpassungen vor und füge keine anderen Elemente hinzu.

Speichere dann alle Layouts mit derselben Zufallsgruppen-ID, und beim Öffnen des Bildschirms oder Starten des Spiels wird ein Layout aus der Gruppe ausgewählt.
