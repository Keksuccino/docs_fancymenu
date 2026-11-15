---
title: FAQ
description: Häufig gestellte Fragen.
sourceBlobSha: 405be9869106a7871195d6e03828f428cc20b4a1
---
# FAQ

### Ich brauche Hilfe bei einem Problem. Welche Informationen sollte ich bereitstellen?

Um die bestmögliche Hilfe zu erhalten, stelle bitte so viele Informationen wie möglich bereit:
1.  **Eine klare Beschreibung des Problems:** Was hast du erwartet, und was ist tatsächlich passiert?
2.  **Deine `latest.log`-Datei:** Du findest sie unter `<game-directory>/logs/latest.log`. **Sende kein Crash-Log**, außer du wirst ausdrücklich darum gebeten; die `latest.log` enthält normalerweise den benötigten Kontext. Verwende beim Posten eine Seite wie https://gist.github.com.
3.  **Deine Minecraft-Version:** (z. B. 1.20.1)
4.  **Dein Mod-Loader und dessen Version:** (z. B. Forge 47.2.0, Fabric 0.15.7)
5.  **Deine FancyMenu-Version:** (z. B. 3.5.2)
6.  **Screenshots oder Videos** des Problems können ebenfalls sehr hilfreich sein.

### Wie ändere ich die Ebenenreihenfolge von Elementen (etwas vor oder hinter ein anderes verschieben)?

*   **Benutzerdefiniert vs. benutzerdefiniert:** Öffne **Fenster -> Editor-Widgets -> Ebenen** und ziehe die Elemente in der Hierarchie. Du kannst auch mit der rechten Maustaste auf ein Element klicken und **Eine Ebene nach oben/unten verschieben** verwenden. Siehe [Ebenen und Gruppen](./layers-and-groups).
*   **Benutzerdefiniert vs. Vanilla:** Um alle deine benutzerdefinierten Elemente hinter allen Vanilla-Elementen zu rendern (z. B. um ein Hintergrundbild hinter die Standard-Schaltflächen zu setzen), **klicke mit der rechten Maustaste auf den Editor-Hintergrund** und aktiviere die Option **„Benutzerdefinierte Elemente hinter Vanilla rendern“**.

### Kann ich bestimmte Schaltflächen aus einer universellen Schaltflächenvorlage ausschließen?

**Nein. Wenn für eine Vorlagen-Schaltfläche benutzerdefinierte Texturen festgelegt sind, werden diese Texturen immer mit allen betroffenen Elementen geteilt. Einzelne Schaltflächen können nicht ausgeschlossen werden.**

### Wie kann ich eine Schaltfläche beim Anklicken eine Aktion ausführen lassen?

Verwende ein [**Aktionsskript**](./action-scripts).
1.  Klicke im Editor mit der rechten Maustaste auf die Schaltfläche.
2.  Wähle **Aktionsskript bearbeiten**.
3. Klicke auf **Aktion hinzufügen** und wähle eine Aktion aus, zum Beispiel [**Bildschirm oder benutzerdefinierte GUI öffnen**](./action-scripts#open-screen-or-custom-gui-opengui), [**Server beitreten**](./action-scripts#join-server-joinserver) oder [**Variablenwert festlegen**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Kann ich einen komplett neuen Menübildschirm von Grund auf erstellen?

Verwende eine [**benutzerdefinierte GUI**](./custom-guis).
1.  Gehe in der Menüleiste zu **Anpassung -> Benutzerdefinierte GUIs -> Benutzerdefinierte GUIs verwalten**.
2.  Klicke auf **„Neue GUI“** und gib ihr eine eindeutige Kennung.
3.  Anschließend kannst du diesen neuen leeren Bildschirm öffnen und ein Layout dafür erstellen, indem du beliebige Elemente hinzufügst.
4. Öffne die benutzerdefinierte GUI mit der Aktion [**Bildschirm oder benutzerdefinierte GUI öffnen**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mein Spiel benötigt nach dem Aktivieren des Vorladens sehr lange zum Laden.

Das ist ein erwartetes Verhalten. Das Vorladen großer Ressourcen wie Animationen mit hoher Auflösung oder Sounds während des anfänglichen Starts verlängert naturgemäß die Ladezeit des Spiels.

### Meine FMA-Animation verwendet zu viel RAM!

Klassische [FMA-Animationen](./fma) können viel Speicher verbrauchen, wenn sie viele hochauflösende Einzelbilder enthalten. AFMA eignet sich besser für große oder komplexe animierte Texturen. Halte klassische FMA-Animationen kurz; verwende [Video](./video) für die vollständige Videowiedergabe.

### Funktioniert FancyMenu mit OptiFine?

Nein. OptiFine ist **nicht kompatibel** und dafür bekannt, viele Mods einschließlich FancyMenu zu beschädigen. Es wird dringend empfohlen, moderne Alternativen wie Sodium/Embeddium + Iris/Oculus zu verwenden.
Siehe [Alternativen zu OptiFine](./optifine-alternatives).

### Mein Spiel stürzt ab. Wie finde ich heraus, ob ein Mod-Konflikt die Ursache ist?

Am besten prüfst du auf einen Mod-Konflikt, indem du **das Spiel nur mit FancyMenu und seinen Abhängigkeiten** (Konkrete, Melody) startest. Wenn der Absturz nicht mehr auftritt, kannst du deine anderen Mods in kleinen Gruppen wieder hinzufügen, bis der Absturz erneut auftritt. So lässt sich der konfliktverursachende Mod ermitteln.

### Eine Schaltfläche eines anderen Mods verschwindet oder funktioniert nicht, wenn ich versuche, sie zu bearbeiten.

Einige Mods fügen Widgets auf eine Weise hinzu, die FancyMenu nicht erkennen oder anpassen kann. Siehe [Vanilla-/Mod-Elemente](./vanilla-elements) und bei bildschirmbasierten Listen [Scrollbare Bildschirme anpassen](./customizing-scrollable-screens). Wenn das Widget weiterhin nicht erscheint, muss der Mod, der es hinzufügt, es als unterstütztes Bildschirm-Widget bereitstellen.

### Kann ich FancyMenu-Layouts auf einem Server verwenden?

Layouts und visuelle Anpassungen werden auf dem Client des Spielers gespeichert; ein Server kann sie nicht auf einem nicht konfigurierten Client erzwingen. Verteile sie als Teil eines Modpacks. Installiere FancyMenu auf dem Server, wenn du [Serverbefehle](./commands), [FM-Daten](./fm-data), [serverseitigen NBT-Zugriff](./nbt-data-placeholder#server-side-placeholder), Gamerules, Strukturen oder Server-Listener benötigst.

### Was ist der Unterschied zwischen FancyMenu v2 (für ältere MC-Versionen) und v3?

FancyMenu v3 ist eine vollständige Neuentwicklung mit vielen neuen Funktionen, einer stabileren Architektur und besserer Leistung. V2 ist veraltet, wird nicht mehr unterstützt und verfügt über viele Funktionen wie erweiterte Platzhalter und Skripting nicht. Es wird dringend empfohlen, v3 mit einer modernen Minecraft-Version (1.18.2+) zu verwenden. V2-Layouts können beim Laden automatisch in v3 konvertiert werden, allerdings sind möglicherweise einige manuelle Korrekturen erforderlich.

### Wo finde ich vorgefertigte Layouts und Vorlagen?

Die FancyMenu-Community teilt Layouts im Kanal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) des offiziellen Keksuccino's Mods Discord-Servers („Kekscord“).

### Wie kann ich die Spieler-Entität hinter anderen Elementen rendern lassen?

Normalerweise kannst du eine [Spieler-Entität](./elements#player-entity) über das [Ebenen-Widget](./layers-and-groups) nicht hinter normale 2D-Elemente zwingen. Ihr Renderer kann die normale GUI-Ebenenreihenfolge ignorieren. Entwirf das Layout unter Berücksichtigung dieser Einschränkung oder verwende ein vorgerendertes Bild, wenn eine strikt eingehaltene Ebenenreihenfolge erforderlich ist.

### Meine Spieler-Entität hat nur ein Bein! Was ist passiert?

Dies ist ein visueller Fehler, der wahrscheinlich durch einen Mod-Konflikt mit einem anderen Mod verursacht wird, der Spieleranimationen oder -modelle verändert. Überprüfe die Pose-Einstellungen der Spieler-Entität, um festzustellen, ob die Beine versehentlich gedreht oder verschoben wurden.

### Wie erstelle ich eine Verzögerung zwischen Aktionen in einem Skript?

Verwende [**Verzögerungs-** oder **Später ausführen**-Blöcke](./action-scripts#what-are-statements) für verzögerte Aktionslogik. Für sich wiederholende Hintergrundlogik kannst du [Scheduler](./schedulers) verwenden.

### Kann ich Menüs des Create-Mods anpassen?

Nein. Die Anpassung von Create-Bildschirmen ist absichtlich deaktiviert. Siehe [Bildschirme, bei denen die Anpassung absichtlich deaktiviert ist](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Welche Auflösung wird für Hintergrundbilder und Schaltflächen-Texturen empfohlen?

Hintergründe: Ein Standardbild mit 1920x1080 (1080p) ist ein guter Ausgangspunkt und wird bei den meisten Benutzern gut skaliert.
Schaltflächen: Die meisten Vanilla-Schaltflächen sind etwa 150–200 Pixel breit und 20 Pixel hoch. Benutzerdefinierte Texturen an diese Größe anzupassen, ist eine gute Praxis für ein einheitliches Erscheinungsbild.

### Gibt es eine Möglichkeit, automatisch ein Menü zu öffnen oder einen Befehl auszuführen, wenn ein Spieler ein Spielziel (z. B. eine Quest) abschließt?
FancyMenu verfügt über viele [integrierte Spielereignis-Listener](./listeners), aber keinen allgemeinen Listener für jedes Quest-System eines Drittanbieter-Mods. Wenn der Quest-Mod Befehlsbelohnungen unterstützt, kannst du damit [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) oder einen anderen passenden [FancyMenu-Befehl](./commands) ausführen.

### Wie kann ich eine Schaltfläche inaktiv oder „ausgegraut“ machen?

Du kannst den Aktivierungsstatus einer Schaltfläche mithilfe von [Ladeanforderungen](./conditions) steuern.
Klicke im Editor mit der rechten Maustaste auf die Schaltfläche und wähle **Aktivierungsstatus steuern**.
Füge eine Anforderung hinzu, die erfüllt sein muss, damit die Schaltfläche aktiv ist. Um sie dauerhaft zu deaktivieren, verwende [**Ist Zahl**](./conditions#is-number-fancymenu_visibility_requirement_is_number), um zu prüfen, ob 0 gleich 1 ist.
Die Schaltfläche verwendet nun ihre Textur für den „Inaktiven Hintergrund“ und kann nicht angeklickt werden.

### Wie kann ich die Kopf- und Fußzeile (die Leisten mit der Erdtextur) auf scrollbaren Bildschirmen entfernen?

Öffne im Layout-Editor **Layout-Eigenschaften -> Anpassungen der Kopf-/Fußzeile**. Setze die Texturen auf transparent. Diese Option ist auf einigen modifizierten Bildschirmen möglicherweise nicht verfügbar.

### Ich kann kein Layout „für den aktuellen Bildschirm“ erstellen. Die Schaltfläche ist ausgegraut.

Du musst zuerst über **Menüleiste -> Anpassung -> Anpassungen des aktuellen Bildschirms -> Aktiviert** die Anpassungen für diesen Bildschirm aktivieren.

### Ich kann beim Öffnen eines Bildschirms im Editor keine Elemente anpassen. Der Bildschirm ist einfach leer.

Das kann bedeuten, dass du ein [universelles Layout](./universal-layouts) statt eines Layouts **für den aktuellen Bildschirm** erstellt hast.

Es könnte sich auch um einen [scrollbaren Bildschirm](./customizing-scrollable-screens) handeln, den FancyMenu standardmäßig nicht anpassen kann.

Eine dritte Möglichkeit ist, dass es sich um einen Bildschirm eines Mods handelt, der Elemente auf eine nicht-Vanilla-Art hinzufügt. Dadurch kann FancyMenu diese Elemente nicht anpassen.

### Bei meinem Text-Element werden seltsame graue Kästen angezeigt.

Diese durchscheinenden Kästen sind die Scroll-Griffleisten des [Text-Elements](./elements#text) und kein Darstellungsfehler.

Wenn diese Kästen nicht sichtbar sein sollen, kannst du entweder mit der rechten Maustaste auf das Element klicken und das Scrollen vollständig deaktivieren ODER im selben Kontextmenü die Texturen der Griffleisten auf vollständig transparente Texturen setzen, wenn das Element weiterhin scrollbar bleiben soll.

### Wie kann ich das aktuelle Minecraft-Changelog in meinen Menüs anzeigen?

Es gibt ein großartiges [GitHub-Projekt](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), das Minecraft-Changelogs in mit FancyMenu kompatibles Markdown umwandelt, sodass du das aktuelle MC-Changelog in deinen Menüs anzeigen kannst! Es wird täglich aktualisiert, um neue Changelogs abzurufen.

Um es in einem [Text-Element](./elements#text) anzuzeigen, setze den **Quellmodus** auf **Ressource** und die Ressourcenquelle auf **Web**. Verwende `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Wie kann ich ein beliebiges Element am einfachsten auf die Bildschirmgröße strecken?

Die meisten Elemente verfügen in ihren Kontextmenüs, die sich per Rechtsklick öffnen, über eine Option zum horizontalen und vertikalen Strecken. Wenn du diese aktivierst, wird das Element immer auf die gesamte Breite und/oder Höhe des Bildschirms gestreckt. Die horizontale und vertikale Streckung kann unabhängig voneinander aktiviert werden.

### Ich kann keine Schaltflächen anklicken oder mit Schiebereglern interagieren, wenn sie sich hinter oder vor einem Text-Element befinden.

Das liegt daran, dass Text-Elemente standardmäßig interaktiv sind (damit die Scroll-Griffleiste verwendet oder Markdown-Hyperlinks angeklickt werden können). Daher verbrauchen sie Mausklicks und Scroll-Ereignisse. Am besten platzierst du Schaltflächen nicht hinter oder vor Text-Elementen. Wenn es sich jedoch nicht vermeiden lässt, kannst du das Text-Element nicht interaktiv machen, indem du **mit der rechten Maustaste darauf klickst** und **Interaktiv** auf **Deaktiviert** setzt. Beachte, dass das Text-Element dadurch zu statischem, nicht interaktivem Text wird und du nicht mehr darin scrollen oder Hyperlinks anklicken kannst.

### Wie kann ich verhindern, dass Schaltflächen und Schieberegler bei der Navigation mit den Pfeil- und Tab-Tasten ausgewählt oder fokussiert werden?

Damit Schaltflächen und Schieberegler nicht navigierbar sind, musst du **mit der rechten Maustaste** darauf klicken und **Navigierbar** auf **Deaktiviert** setzen. Die Schaltfläche bzw. der Schieberegler kann weiterhin angeklickt werden, aber mit der Pfeil-/Tab-Navigation nicht mehr fokussiert werden.

Dies ist auch nützlich, wenn du Schaltflächen oder Schieberegler zum Chat-Bildschirm hinzufügen möchtest. So kannst du weiterhin mit der Pfeil-nach-oben-Taste durch ältere Nachrichten scrollen, ohne versehentlich Schaltflächen oder Schieberegler auf dem Bildschirm auszuwählen.

### In einem der Kontextmenüs von FancyMenu fehlt eine Option, die dort vorhanden sein sollte.

Die Kontextmenüs von FancyMenu (die Menüs, die sich beim Rechtsklick oder bei der Interaktion mit Menüleisten öffnen) sind SCROLLBAR. Das bedeutet, dass du mit dem Mausrad scrollen kannst, während sich der Mauszeiger über dem Menü befindet. So kannst du nach oben oder unten scrollen und weitere Optionen anzeigen, die zuvor nicht sichtbar waren.

### Ich kann den Titelbildschirm nicht anpassen; beim Verlassen des Editors wird weiterhin der ursprüngliche angezeigt.

Ein anderer Mod ersetzt den ursprünglichen `title_screen`. Deaktiviere den benutzerdefinierten Titelbildschirm dieses Mods in dessen Einstellungen. Wenn es keine solche Option gibt, kann FancyMenu das Layout nicht auf den ersetzten Bildschirm anwenden.

### Wenn ich versuche, den Inventarbildschirm anzupassen, kann ich den Inventarcontainer nicht bearbeiten.

Das ist erwartetes Verhalten. FancyMenu unterstützt nicht die Bearbeitung des eigentlichen Containers irgendeines Inventarbildschirms (Spielerinventar, Kiste, Werkbank usw.), da es sehr schwierig wäre, dafür Unterstützung hinzuzufügen.

Es ist weiterhin möglich, diesen Bildschirmen neue Elemente hinzuzufügen; du kannst lediglich die Container nicht bearbeiten.

SpiffyHUD hilft hierbei übrigens ebenfalls nicht, da es zum Bearbeiten des HUDs (beispielsweise der Gegenstandsleiste) dient, aber keine Bildschirme wie Inventarbildschirme bearbeiten kann.
