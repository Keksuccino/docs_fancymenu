---
title: Menü-Hintergrundmusik
description: Wie man die in Menüs abgespielte Musik anpasst.
---

# Menü-Hintergrundmusik

Es ist möglich, die standardmäßige Menü-Hintergrundmusik von Minecraft durch eigene Titel zu ersetzen oder die normale Vanilla-Musik, die in Menüs abgespielt wird, einfach zu deaktivieren.

# Vanilla-Musik deaktivieren

FancyMenu bietet mehrere Möglichkeiten, die Vanilla-Menümusik zu deaktivieren. Das kann nützlich sein, wenn du andere Audiodateien in Bildschirmen abspielen möchtest oder einfach in einigen Bildschirmen überhaupt keine Musik hören willst.

## Global

Wenn du in Menüs überhaupt keine Musik möchtest, ist dies der einfachste Weg.

Um die Vanilla-Menümusik in FancyMenu 3.9.0+ global zu deaktivieren oder zu ersetzen, gehe in der Menüleiste oben in den Bildschirmen auf **Customization -> Global Customizations**. Globale Anpassungen können Menümusik ersetzen, ohne dass ein Resource Pack erforderlich ist und ohne dass Anpassungen für jeden Bildschirm aktiviert werden müssen.

<br>
<img width="600" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/d829a35e-f23f-42a9-ad79-193de73b499b">

> Das Deaktivieren der Standardmusik von Minecraft deaktiviert sie in jedem Bildschirm, nicht nur im aktuellen.
{.is-info}

## Pro Bildschirm

Wenn du mehr Kontrolle darüber haben möchtest, wo Vanilla-Menümusik abgespielt werden soll, solltest du das Element **Music Controller** verwenden. Dieses Element wird wie jedes andere Element zu Layouts hinzugefügt, indem du **mit der rechten Maustaste auf den Hintergrund des Editors klickst** und dann auf **New Element -> Music Controller** klickst.

Durch **Rechtsklick** auf das Element kannst du festlegen, welche Arten von Musik, die in Menüs abgespielt werden, deaktiviert werden sollen (normale Menümusik und Weltmusik, die in Bildschirmen weiterläuft, in denen das Spiel nicht pausiert, wie z. B. der Inventarbildschirm).

> Dieses Element unterstützt **Ladeanforderungen**, sodass du noch mehr Kontrolle darüber hast, wann Vanilla-Musik abgespielt werden soll!
{.is-info}


# Eigene Musik hinzufügen

Jetzt können wir die eigentliche benutzerdefinierte Hintergrundmusik hinzufügen.

Wenn du in allen Bildschirmen dieselbe eigene Musik abspielen möchtest und Kontrolle auf Layout-Ebene benötigst, solltest du ein **universelles Layout** verwenden, das in jedem Bildschirm geladen wird, in dem Anpassungen aktiviert sind. Für einen einfachen globalen Ersatz der Menümusik verwende stattdessen [Globale Anpassungen](/global-customizations).

Bei Verwendung eines universellen Layouts wird die Musik **weiter abgespielt**, wenn du von einem Menü mit aktiviertem Layout zu einem anderen mit demselben aktivierten Layout wechselst.

Wenn du pro Bildschirm unterschiedliche Musik abspielen möchtest, verwende normale Layouts.

In diesem Beispiel verwenden wir **universelle Layouts**.

Füge dem universellen Layout ein neues **Audio**-Element hinzu, das als unser Hintergrundmusik-Player dient.

<br>
<img width="400" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/bddf8f46-47c5-4a00-a6f7-b5ca1df8ae67">

Füge ihm nun Musikstücke hinzu, die im Hintergrund abgespielt werden sollen.

<br>
<img width="300" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/824dcb90-3bd5-4c0b-96d0-e581a7c2f9f7">

Das war im Grunde schon alles.
Du kannst das Audio-Element bei Bedarf auch auf den Shuffle-Modus setzen und seinen Sound-Kanal ändern.

Speichere das Layout und verlasse den Editor.

# Anpassungen für alle Menüs aktivieren

Wir haben in diesem Beispiel ein **universelles Layout** verwendet, weil wir möchten, dass unsere Hintergrundmusik in mehreren Bildschirmen abgespielt wird.

Da Layouts nur in Bildschirmen geladen werden, in denen **Anpassungen aktiviert** sind, müssen wir sie jetzt für jeden Bildschirm aktivieren, auf dem unsere Musik abgespielt werden soll.

Klicke dazu auf **Customization** und aktiviere **Current Screen Customization**.

<br>
<img width="320" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/2f6527b7-ae14-4e82-abc6-3572cc6490b2">

Wiederhole dies für jeden Bildschirm, auf dem deine benutzerdefinierte Hintergrundmusik abgespielt werden soll.

Und das war's! Du hast jetzt eigene Hintergrundmusik in deinen Minecraft-Menüs!
