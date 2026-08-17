---
title: FAQ
description: Häufig gestellte Fragen.
---
# FAQ

### Ich brauche Hilfe bei einem Problem. Welche Informationen sollte ich bereitstellen?

Damit du die bestmögliche Hilfe bekommst, stelle bitte so viele Informationen wie möglich bereit:
1.  **Eine klare Beschreibung des Problems:** Was hast du erwartet, und was ist tatsächlich passiert?
2.  **Deine `latest.log`-Datei:** Du findest sie unter `<game-directory>/logs/latest.log`. **Sende kein Crash-Log**, außer du wirst ausdrücklich darum gebeten; `latest.log` enthält normalerweise den benötigten Kontext. Verwende beim Posten eine Website wie https://gist.github.com.
3.  **Deine Minecraft-Version:** (z. B. 1.20.1)
4.  **Dein Mod-Loader und dessen Version:** (z. B. Forge 47.2.0, Fabric 0.15.7)
5.  **Deine FancyMenu-Version:** (z. B. 3.5.2)
6.  **Screenshots oder Videos** des Problems können ebenfalls sehr hilfreich sein.

### Wie ändere ich die Ebenenreihenfolge von Elementen (etwas vor oder hinter ein anderes verschieben)?

*   **Custom vs. Custom:** Öffne **Window -> Editor Widgets -> Layers** und ziehe die Elemente in der Hierarchie. Du kannst auch mit der rechten Maustaste auf ein Element klicken und **Move One Layer Up/Down** verwenden. Siehe [Ebenen und Gruppen](./layers-and-groups).
*   **Custom vs. Vanilla:** Um alle deine benutzerdefinierten Elemente hinter allen Vanilla-Elementen zu rendern (z. B. um ein Hintergrundbild hinter die Standard-Schaltflächen zu setzen), **klicke mit der rechten Maustaste auf den Editor-Hintergrund** und aktiviere die Option **„Render Custom Elements Behind Vanilla“**.

### Kann ich bestimmte Schaltflächen von einer universellen Schaltflächenvorlage ausschließen?

**Nein. Wenn für eine Vorlagen-Schaltfläche benutzerdefinierte Texturen festgelegt sind, werden diese Texturen immer mit allen betroffenen Elementen geteilt. Einzelne Schaltflächen können nicht ausgeschlossen werden.**

### Wie kann ich festlegen, dass eine Schaltfläche beim Anklicken etwas tut?

Verwende ein [**Aktionsskript**](./action-scripts).
1.  Klicke im Editor mit der rechten Maustaste auf die Schaltfläche.
2.  Wähle **Edit Action Script**.
3.  Klicke auf **Add Action** und wähle eine Aktion aus, z. B. [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) oder [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Kann ich einen vollständig neuen Menübildschirm von Grund auf erstellen?

Verwende eine [**benutzerdefinierte GUI**](./custom-guis).
1.  Gehe in der Menüleiste zu **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Klicke auf **„New GUI“** und gib ihr eine eindeutige Kennung.
3.  Du kannst diesen neuen leeren Bildschirm anschließend öffnen und ein Layout dafür erstellen, indem du beliebige gewünschte Elemente hinzufügst.
4.  Öffne die benutzerdefinierte GUI mit der Aktion [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mein Spiel benötigt nach dem Aktivieren des Vorladens sehr lange zum Laden.

Das ist ein erwartetes Verhalten. Das Vorladen großer Ressourcen wie hochauflösender Animationen oder Sounds während des anfänglichen Starts verlängert zwangsläufig die Ladezeit des Spiels.

### Meine FMA-Animation verbraucht zu viel RAM!

Klassische [FMA-Animationen](./fma) können viel Speicher verbrauchen, wenn sie viele hochauflösende Einzelbilder enthalten. AFMA eignet sich besser für große oder komplexe animierte Texturen. Halte klassische FMA-Animationen kurz und verwende [Video](./video) für die vollständige Videowiedergabe.

### Funktioniert FancyMenu mit OptiFine?

Nein. OptiFine ist **nicht kompatibel** und dafür bekannt, viele Mods einschließlich FancyMenu zu beschädigen. Es wird dringend empfohlen, moderne Alternativen wie Sodium/Embeddium + Iris/Oculus zu verwenden.
Siehe [OptiFine-Alternativen](./optifine-alternatives).

### Mein Spiel stürzt ab. Wie kann ich herausfinden, ob ein Mod-Konflikt vorliegt?

Am besten prüfst du auf einen Mod-Konflikt, indem du **das Spiel nur mit FancyMenu und seinen Abhängigkeiten** (Konkrete, Melody) startest. Wenn der Absturz nicht mehr auftritt, kannst du deine anderen Mods in kleinen Gruppen wieder hinzufügen, bis der Absturz erneut auftritt. So lässt sich der kollidierende Mod identifizieren.

### Eine Schaltfläche eines anderen Mods verschwindet oder funktioniert nicht, wenn ich sie bearbeiten möchte.

Einige Mods fügen Widgets auf eine Weise hinzu, die FancyMenu nicht erkennen oder anpassen kann. Siehe [Vanilla-/Mod-Elemente](./vanilla-elements) und bei listenbasierten Bildschirmen [Anpassung scrollbarer Bildschirme](./customizing-scrollable-screens). Wenn das Widget weiterhin nicht angezeigt wird, muss der Mod, der es hinzufügt, es als unterstütztes Bildschirm-Widget bereitstellen.

### Kann ich FancyMenu-Layouts auf einem Server verwenden?

Layouts und visuelle Anpassungen werden auf dem Client des Spielers gespeichert; ein Server kann sie einem nicht konfigurierten Client nicht aufzwingen. Verteile sie als Teil eines Modpacks. Installiere FancyMenu auf dem Server, wenn du [Serverbefehle](./commands), [FM-Daten](./fm-data), [serverseitigen NBT-Zugriff](./nbt-data-placeholder#server-side-placeholder), Gamerules, Strukturen oder Server-Listener benötigst.

### Was ist der Unterschied zwischen FancyMenu v2 (für ältere MC-Versionen) und v3?

FancyMenu v3 ist eine vollständige Neuentwicklung mit vielen neuen Funktionen, einer stabileren Architektur und besserer Leistung. V2 ist veraltet, wird nicht mehr unterstützt und verfügt über viele Funktionen wie erweiterte Platzhalter und Skripting nicht. Es wird dringend empfohlen, v3 mit einer modernen Minecraft-Version (1.18.2+) zu verwenden. V2-Layouts können beim Laden automatisch in v3 konvertiert werden, möglicherweise sind jedoch einige manuelle Korrekturen erforderlich.

### Wo finde ich vorgefertigte Layouts und Vorlagen?

Die FancyMenu-Community teilt Layouts im Kanal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) des offiziellen Keksuccino's Mods Discord-Servers („Kekscord“).

### Wie kann ich das Spieler-Entity hinter anderen Elementen rendern lassen?

Im Allgemeinen kannst du ein [Spieler-Entity-Element](./elements#player-entity) nicht über das [Layers-Widget](./layers-and-groups) hinter normalen 2D-Elementen erzwingen. Sein Renderer kann die normale GUI-Ebenenreihenfolge ignorieren. Gestalte das Layout unter Berücksichtigung dieser Einschränkung oder verwende ein vorgerendertes Bild, wenn eine strikt eingehaltene Ebenenreihenfolge erforderlich ist.

### Mein Spieler-Entity hat nur ein Bein! Was ist passiert?

Dies ist ein visueller Fehler, der wahrscheinlich durch einen Mod-Konflikt mit einem anderen Mod verursacht wird, der Spieleranimationen oder -modelle verändert. Überprüfe die Pose-Einstellungen des Spieler-Entities, um festzustellen, ob die Beine versehentlich gedreht oder verschoben wurden.

### Wie erstelle ich eine Verzögerung zwischen Aktionen in einem Skript?

Verwende [**Delay**- oder **Execute Later**-Blöcke](./action-scripts#what-are-statements) für verzögerte Aktionslogik. Für sich wiederholende Hintergrundlogik kannst du [Scheduler](./schedulers) verwenden.

### Kann ich Menüs des Create-Mods anpassen?

Nein. Die Anpassung von Create-Bildschirmen ist absichtlich deaktiviert. Siehe [Bildschirme, bei denen die Anpassung absichtlich deaktiviert ist](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Welche Auflösung wird für Hintergrundbilder und Schaltflächen-Texturen empfohlen?

Hintergründe: Ein Standardbild mit 1920 × 1080 (1080p) ist ein guter Ausgangspunkt und lässt sich für die meisten Benutzer gut skalieren.
Schaltflächen: Die meisten Vanilla-Schaltflächen sind etwa 150–200 Pixel breit und 20 Pixel hoch. Benutzerdefinierte Texturen an diese Größe anzupassen, ist eine gute Vorgehensweise für ein einheitliches Erscheinungsbild.

### Gibt es eine Möglichkeit, automatisch ein Menü zu öffnen oder einen Befehl auszuführen, wenn ein Spieler ein Ziel im Spiel (z. B. eine Quest) abschließt?
FancyMenu verfügt über viele [integrierte Listener für Spielereignisse](./listeners), aber keinen allgemeinen Listener für jedes Quest-System eines Drittanbieter-Mods. Wenn der Quest-Mod Befehlsbelohnungen unterstützt, verwende eine solche Belohnung, um [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) oder einen anderen passenden [FancyMenu-Befehl](./commands) auszuführen.

### Wie kann ich eine Schaltfläche inaktiv oder „ausgegraut“ darstellen?

Du kannst den Aktivstatus einer Schaltfläche mithilfe von [Ladeanforderungen](./conditions) steuern.
Klicke im Editor mit der rechten Maustaste auf die Schaltfläche und wähle **Control Active State**.
Füge eine Anforderung hinzu, die erfüllt sein muss, damit die Schaltfläche aktiv ist. Um sie dauerhaft zu deaktivieren, verwende [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number), um zu prüfen, ob 0 gleich 1 ist.
Die Schaltfläche verwendet nun ihre Textur für den „Inactive Background“ und kann nicht angeklickt werden.

### Wie kann ich die Kopf- und Fußzeile (die Balken mit der Erde-Textur) auf scrollbaren Bildschirmen entfernen?

Öffne im Layout-Editor **Layout Properties -> Header/Footer Customizations**. Setze die Texturen auf transparent. Diese Option ist auf einigen modifizierten Bildschirmen möglicherweise nicht verfügbar.

### Ich kann kein Layout „für den aktuellen Bildschirm“ erstellen. Die Schaltfläche ist ausgegraut.

Du musst zuerst über **Menüleiste -> Customization -> Current Screen Customizations -> Enabled** die Anpassungen für diesen Bildschirm aktivieren.

### Ich kann beim Öffnen eines Bildschirms im Editor keine Elemente anpassen. Es wird nur ein leerer Bildschirm angezeigt.

Das könnte bedeuten, dass du ein [universelles Layout](./universal-layouts) statt eines Layouts **für den aktuellen Bildschirm** erstellt hast.

Es könnte sich auch um einen [scrollbaren Bildschirm](./customizing-scrollable-screens) handeln, den FancyMenu standardmäßig nicht anpassen kann.

Die dritte Möglichkeit ist, dass es sich um einen Bildschirm eines Mods handelt, der Elemente auf eine nicht-Vanilla-konforme Weise hinzufügt. Dadurch kann FancyMenu diese Elemente nicht anpassen.

### An meinem Text-Element befinden sich seltsame graue Kästchen.

Diese durchscheinenden Kästchen sind die Scroll-Griffleisten des [Text-Elements](./elements#text) und kein Darstellungsfehler.

Wenn diese Kästchen nicht sichtbar sein sollen, kannst du entweder mit der rechten Maustaste auf das Element klicken und das Scrollen vollständig deaktivieren oder im selben Kontextmenü die Texturen der Griffleisten auf vollständig transparente Texturen setzen, wenn das Element weiterhin scrollbar bleiben soll.

### Wie kann ich das neueste Minecraft-Changelog in meinen Menüs anzeigen?

Es gibt ein großartiges [GitHub-Projekt](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), das Minecrafts Changelogs in mit FancyMenu kompatibles Markdown umwandelt, sodass du das neueste MC-Changelog in deinen Menüs anzeigen kannst! Es wird täglich aktualisiert, um neue Changelogs abzurufen.

Um es in einem [Text-Element](./elements#text) anzuzeigen, setze den **Source Mode** auf **Resource** und dessen Ressourcenquelle auf **Web**. Verwende `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Wie kann ich ein beliebiges Element am einfachsten auf die Bildschirmgröße strecken?

Die meisten Elemente verfügen in ihrem Kontextmenü, das sich per rechter Maustaste öffnet, über eine Option, mit der sie horizontal und vertikal gestreckt werden können. Wenn du diese Option aktivierst, werden sie immer auf die gesamte Breite und/oder Höhe des Bildschirms gestreckt. Das horizontale und vertikale Strecken kann unabhängig voneinander aktiviert werden.

### Ich kann keine Schaltflächen anklicken oder mit Schiebereglern interagieren, wenn sie hinter oder vor einem Text-Element liegen.

Das passiert, weil Text-Elemente standardmäßig interaktiv sind (damit man die Scroll-Griffleiste verwenden oder Markdown-Hyperlinks anklicken kann). Dadurch verbrauchen sie Mausklicks und Scroll-Ereignisse. Am besten verschiebst du Schaltflächen nicht hinter oder vor Text-Elemente. Wenn dies jedoch unvermeidbar ist, kannst du das Text-Element nicht interaktiv machen, indem du **mit der rechten Maustaste darauf klickst** und **Interactable** auf **Disabled** setzt. Beachte, dass das Text-Element dadurch zu statischem, nicht interaktivem Text wird. Du kannst dann nicht mehr darin scrollen oder Hyperlinks anklicken.

### Wie kann ich verhindern, dass Schaltflächen und Schieberegler bei der Navigation mit den Pfeil- und Tab-Tasten ausgewählt oder fokussiert werden?

Damit Schaltflächen und Schieberegler nicht navigierbar sind, musst du **mit der rechten Maustaste darauf klicken** und **Navigable** auf **Disabled** setzen. Die Schaltfläche bzw. der Schieberegler kann weiterhin angeklickt werden, aber du kannst ihn nicht mehr durch die Pfeil-/Tab-Navigation fokussieren.

Dies ist auch nützlich, wenn du Schaltflächen oder Schieberegler zum Chat-Bildschirm hinzufügen möchtest. So kannst du weiterhin die Pfeil-nach-oben-Taste verwenden, um durch ältere Nachrichten zu scrollen, ohne versehentlich Schaltflächen oder Schieberegler auf dem Bildschirm auszuwählen.

### In einem Kontextmenü von FancyMenu fehlt eine Option, die eigentlich vorhanden sein sollte.

Die Kontextmenüs von FancyMenu (die Menüs, die sich öffnen, wenn du irgendwo mit der rechten Maustaste klickst oder mit Menüleisten interagierst) sind SCROLLBAR. Das bedeutet, dass du das Mausrad verwenden kannst, während sich der Mauszeiger über dem Menü befindet, um nach oben oder unten zu scrollen. Dadurch werden weitere Optionen sichtbar, die zuvor nicht angezeigt wurden.

### Ich kann den Titelbildschirm nicht anpassen. Wenn ich den Editor verlasse, wird weiterhin der ursprüngliche angezeigt.

Ein anderer Mod ersetzt den ursprünglichen `title_screen`. Deaktiviere den benutzerdefinierten Titelbildschirm dieses Mods in dessen Einstellungen. Wenn es dafür keine Option gibt, kann FancyMenu das Layout nicht auf den Ersatzbildschirm anwenden.
