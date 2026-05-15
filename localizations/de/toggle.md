---
title: Layout-Teile ein- und ausblenden
description: Wie man Teile von Layouts durch Benutzereingaben ein- und ausblendet.
---

# Layout-Teile ein- und ausblenden

Manchmal ist es gut, die Wahl zu haben! Vielleicht mögen es manche deiner Nutzer nicht, ständig Rick Astley als Menümusik zu hören, oder sie möchten ein anderes niedliches Anime-Mädchen als Menühintergrund.

Kein Problem! Du kannst es so einrichten, dass deine Nutzer Teile deiner Layouts ein- und ausblenden oder zwischen mehreren Versionen dieser Teile wechseln können.

# Ein-/Ausblenden

Um zum Beispiel die Sichtbarkeit eines Elements per Klick auf einen Button umzuschalten, brauchst du eine Variable, die beim Klick auf den Button gesetzt wird, und das Element, das du umschalten willst, muss in seinen Ladeanforderungen prüfen, ob diese Variable den richtigen Wert hat.

## Die Variable

Der erste Schritt besteht darin, die Variable zu erstellen, mit der du den Sichtbarkeitsstatus des Elements speicherst, das du umschalten möchtest.

Um eine neue Variable hinzuzufügen, gehe in der Menüleiste zum Tab **Customization** und klicke auf **Variables -> Manage Variables**. Füge dann eine neue Variable mit einem **eindeutigen** Namen hinzu! Achte darauf, wirklich einen **einzigartigen** Namen zu verwenden, der noch nicht existiert.

Nachdem du die Variable erstellt hast, setze ihren Wert auf `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## Das Element

Der nächste Schritt besteht darin, das Element hinzuzufügen, das du ein- und ausblenden möchtest.

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

Klicke nun mit der rechten Maustaste auf das Element und dann auf **Loading Requirements**.
Dadurch öffnet sich der Bildschirm **Manage Requirements**. Klicke auf **Add Requirement**.

Suche nach der Anforderung **Is Variable Value**, wähle sie aus und klicke auf **Edit Requirement Value**.

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

Gib nun den Namen der Variable ein, die du zuvor erstellt hast, und stelle die Anforderung so ein, dass als Wert `true` geprüft wird.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Das war's schon für diesen Teil. Jetzt ist dein Element sichtbar, wenn der Wert der Variable `true` ist.

## Der Button

Jetzt müssen wir ein neues Button-Element hinzufügen.

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

Klicke nach dem Hinzufügen mit der rechten Maustaste darauf und dann auf **Edit Action Script**.
Dadurch öffnet sich der Bildschirm **Manage Action Script** des Buttons.

Klicke auf **Add IF Statement**, füge die Anforderung **Is Variable Value** hinzu und setze den Modus der Anforderung auf **OPPOSITE**.

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

Klicke nun auf **Edit Requirement Value**, genau wie zuvor beim Element, und gib einfach denselben Variablennamen und denselben zu prüfenden Wert ein.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Da wir den Anforderungsmodus auf **OPPOSITE** gesetzt haben, wird jetzt geprüft, ob der Variablenwert **nicht** `true` ist, und genau das wollen wir.

Zurück im Bildschirm **Edit Action Script** siehst du nun die IF-Anweisung, die wir gerade hinzugefügt haben.

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

Klicke nun auf **Add Action**, suche nach der Aktion **Set Variable Value**, wähle sie aus und klicke dann auf **Edit Action Value**.

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

Gib als Aktionswert zuerst den Namen deiner Variable und danach den Wert ein, auf den sie gesetzt werden soll. Trenne Name und Wert mit `:`.
In diesem Fall möchten wir unseren Wert auf `true` setzen, weil diese Aktion später ausgeführt wird, wenn der Wert **nicht** `true` ist.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

Hänge die Aktion nun an die IF-Anweisung an, indem du sie darauf ziehst und dort ablegst, damit sie nur ausgeführt wird, wenn der Wert unserer Variable **nicht** `true` ist.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

Wähle danach die IF-Anweisung aus und klicke dann auf **Append ELSE Statement**.

Füge nun eine weitere Aktion **Set Variable Value** hinzu, aber setze den Variablenwert diesmal nicht auf `true`, sondern auf `false`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

Hänge nun die zweite Aktion an die ELSE-Anweisung an, damit sie ausgeführt wird, wenn der Variablenwert **true** ist.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

Und das war's! Beim ersten Mal wirken es vielleicht nach vielen Schritten, aber sobald man sich daran gewöhnt hat, ist es eigentlich ziemlich einfach und schnell erledigt.

Jetzt kannst du dein Layout speichern, den Editor verlassen und den Button drücken, um zu sehen, ob es funktioniert!

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

Du kannst dieselbe Variable gern auch für andere Elemente verwenden, damit du durch Drücken des Buttons **mehrere Elemente gleichzeitig ein- und ausblendest**.

Du kannst sogar ganze Layouts ein- und ausblenden, indem du die **Layout-Wide Loading Requirements** verwendest. Um layoutweite Anforderungen zu konfigurieren, klicke mit der rechten Maustaste auf den Hintergrund des Editors. Achte nur darauf, den Button in einem anderen Layout hinzuzufügen, nicht in dem, das du umschalten möchtest.

# Durchschalten

Anders als beim Umschalten zwischen zwei Werten muss die Aktionsskript-Logik beim Durchschalten zwischen mehr als zwei Werten wechseln können.

Die Logik des Aktionsskripts ist der beim Umschalten sehr ähnlich, daher halte ich es hier kurz. Lies dir auf jeden Fall auch den Abschnitt über das Umschalten durch.

Ich habe 3 Bilder hinzugefügt. Das erste Bild ist sichtbar, wenn der Variablenwert `1` ist, das zweite, wenn der Wert `2` ist, und das dritte, wenn der Wert `3` ist.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

Danach habe ich den Durchschalt-Button hinzugefügt und so eingerichtet, dass der Variablenwert von `1` auf `2` auf `3` und wieder auf `1` wechselt.

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

Und das war's. Speichere jetzt das Layout, verlasse den Editor und prüfe, ob der Durchschalt-Button korrekt funktioniert.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
