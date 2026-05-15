---
title: FAQ
description: Häufig gestellte Fragen.
---

# FAQ

### Ich brauche Hilfe bei einem Problem. Welche Informationen sollte ich bereitstellen?
Um die bestmögliche Hilfe zu erhalten, gib bitte so viel Kontext wie möglich an:
1.  **Eine klare Beschreibung des Problems:** Was hast du erwartet, und was ist tatsächlich passiert?
2.  **Deine `latest.log`-Datei:** Das ist die wichtigste Datei für die Fehlersuche. Du findest sie im `/logs/`-Ordner deiner Instanz. **Sende keinen Crash-Log**, außer du wirst ausdrücklich darum gebeten; die `latest.log` ist viel nützlicher. Nutze zum Teilen am besten eine Seite wie https://gist.github.com.
3.  **Deine Minecraft-Version:** (z. B. 1.20.1)
4.  **Dein Mod-Loader und seine Version:** (z. B. Forge 47.2.0, Fabric 0.15.7)
5.  **Deine FancyMenu-Version:** (z. B. 3.5.2)
6.  **Screenshots oder Videos** des Problems können ebenfalls sehr hilfreich sein.

### Wie ändere ich die Ebenenreihenfolge von Elementen (etwas in den Vordergrund oder Hintergrund bringen)?
*   **Custom vs. Custom:** Um die Render-Reihenfolge deiner eigenen benutzerdefinierten Elemente zu ändern, verwende das **Layers-Widget**. Du kannst es über die Menüleiste öffnen: **Fenster -> Widgets -> Layers**. Dort kannst du Elemente in der Hierarchie nach oben oder unten ziehen. Du kannst auch mit der rechten Maustaste auf ein Element klicken und „Eine Ebene nach oben/unten verschieben“ verwenden.
*   **Custom vs. Vanilla:** Um alle benutzerdefinierten Elemente hinter allen Vanilla-Elementen zu rendern (z. B. um ein Hintergrundbild hinter die Standard-Buttons zu setzen), **klicke mit der rechten Maustaste auf den Editor-Hintergrund** und aktiviere die Option **„Render Custom Elements Behind Vanilla“**.

### Kann ich bestimmte Buttons von einer universellen Button-Vorlage ausschließen?
**Nein. Wenn ein Vorlagen-Button benutzerdefinierte Texturen hat, werden diese Texturen immer mit allen betroffenen Elementen geteilt. Du kannst einzelne Buttons nicht ausschließen.**

### Wie mache ich, dass ein Button bei einem Klick etwas ausführt?
Verwende ein **Action Script**.
1.  Klicke im Editor mit der rechten Maustaste auf den Button.
2.  Wähle **Edit Action Script**.
3.  Klicke auf **Add Action** und wähle aus der Liste aus (z. B. `Open Screen or Custom GUI`, `Join Server`, `Set Variable Value`).
*   Mehr Infos: [Action Scripts](https://docs.fancymenu.net/en/action-scripts)

### Kann ich einen komplett neuen Menübildschirm von Grund auf erstellen?
Ja, das geschieht über **Custom GUIs**.
1.  Gehe in der Menüleiste zu **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Klicke auf **„New GUI“** und gib ihm eine eindeutige Kennung.
3.  Danach kannst du diesen neuen leeren Bildschirm öffnen und ein Layout dafür erstellen, indem du beliebige Elemente hinzufügst.
4.  Diese Custom GUI kann dann über eine Button-Aktion geöffnet werden.
*   Mehr Infos: [Custom GUIs](https://docs.fancymenu.net/en/custom-guis)

### Mein Spiel braucht nach dem Aktivieren des Vorladens sehr lange zum Laden.
Das ist erwartetes Verhalten. Das Vorladen großer Ressourcen wie hochauflösender Animationen oder Sounds während des initialen Starts erhöht die Ladezeit des Spiels naturgemäß.

### Meine FMA-Animation verbraucht zu viel RAM!
Klassische FMA-Dateien können sehr viel Speicher verbrauchen, wenn sie viele hochauflösende Frames enthalten. FancyMenu 3.9.0 fügt AFMA hinzu, was für große oder komplexe animierte Texturen deutlich besser geeignet ist. Bei klassischen FMA-Dateien solltest du Animationen kurz halten und sehr große Frame-Anzahlen/Auflösungen vermeiden. Animationen sind für kurze, dekorative Schleifen gedacht, nicht dafür, ganze Videos abzuspielen.

### Funktioniert FancyMenu mit OptiFine?
Nein. OptiFine ist **nicht kompatibel** und ist dafür bekannt, viele Mods zu beschädigen, einschließlich FancyMenu. Es wird dringend empfohlen, moderne Alternativen wie Sodium/Embeddium + Iris/Oculus zu verwenden.
*   Mehr Infos: [OptiFine-Alternativen](https://docs.fancymenu.net/en/optifine-alternatives)

### Mein Spiel stürzt ab. Wie finde ich heraus, ob es ein Mod-Konflikt ist?
Der beste Weg, um einen Mod-Konflikt zu überprüfen, ist, **das Spiel nur mit FancyMenu und seinen Abhängigkeiten** (Konkrete, Melody) zu starten. Tritt der Absturz dann nicht mehr auf, kannst du deine anderen Mods in kleinen Gruppen wieder hinzufügen, bis der Absturz erneut auftritt, um den konfliktverursachenden Mod zu identifizieren.

### Ein Button aus einem anderen Mod verschwindet oder funktioniert nicht, wenn ich versuche, ihn zu bearbeiten.
Das bedeutet normalerweise, dass der andere Mod seine Buttons auf eine nicht standardmäßige Weise hinzufügt, mit der FancyMenu nicht interagieren kann. Das ist ein Problem, das der Entwickler des anderen Mods auf seiner Seite beheben müsste. FancyMenu kann Elemente nicht anpassen, die es nicht „sehen“ kann.

### Kann ich FancyMenu-Layouts auf einem Server verwenden?
FancyMenu ist ein Client-seitiger Mod. Alle Layouts und Anpassungen befinden sich auf dem Client des Spielers. Du kannst keine Layouts auf einem Server platzieren, um Spieler dazu zu zwingen, sie zu sehen. Du kannst jedoch deinen `config/fancymenu`-Ordner als Teil eines Modpacks verteilen. Wenn du vom Server aus Befehle wie `/fmvariable` oder `/openguiscreen` verwenden möchtest, muss FancyMenu (oder sein Spigot-Plugin) auf dem Server installiert sein.

### Was ist der Unterschied zwischen FancyMenu v2 (für ältere MC-Versionen) und v3?
FancyMenu v3 ist eine vollständige Neuentwicklung mit vielen neuen Funktionen, einer stabileren Architektur und besserer Leistung. V2 ist veraltet, wird nicht mehr unterstützt und es fehlen viele Funktionen wie erweiterte Platzhalter und Skripting. Es wird dringend empfohlen, v3 auf einer modernen Minecraft-Version (1.18.2+) zu verwenden. V2-Layouts können beim Laden automatisch in v3 umgewandelt werden, aber möglicherweise sind einige manuelle Nacharbeiten nötig.

### Wo finde ich vorgefertigte Layouts und Vorlagen?
Die FancyMenu-Community teilt Layouts im Kanal `#layout-templates` auf dem offiziellen Discord-Server von Keksuccino's Mods.

### Wie kann ich die Player Entity hinter anderen Elementen rendern lassen?
Das geht nicht. Aufgrund der Art und Weise, wie Minecraft Entitäten rendert, wird das Player-Entity-Element fast immer vor anderen 2D-Elementen gerendert, unabhängig von den Ebeneneinstellungen.

### Meine Player Entity hat nur ein Bein! Was ist passiert?
Das ist ein visueller Fehler, vermutlich verursacht durch einen Mod-Konflikt mit einem anderen Mod, der Spieleranimationen oder -modelle verändert. Prüfe die Pose-Einstellungen der Player Entity, um zu sehen, ob die Beine versehentlich gedreht oder verschoben wurden.

### Wie erstelle ich eine Verzögerung zwischen Aktionen in einem Skript?
FancyMenu 3.9.0 fügt **Delay**- und **Execute Later**-Blöcke zu Action Scripts hinzu. Verwende diese für die meisten verzögerten Aktionslogiken. Für wiederkehrende Hintergrundlogik verwende [Schedulers](https://docs.fancymenu.net/en/schedulers).

### Kann ich Menüs aus dem Create-Mod anpassen?
Nein. FancyMenu hat bekannte Inkompatibilitäten mit den komplexen GUIs von Create. Die Anpassung für Create-Bildschirme wurde absichtlich deaktiviert, um Abstürze zu verhindern.

### Warum verschwinden Buttons aus Mod X im Editor?
Das bedeutet, dass der Mod seine Buttons auf eine benutzerdefinierte, nicht-Vanilla-Art hinzufügt. FancyMenu kann diese Elemente nicht „sehen“ oder mit ihnen interagieren und sie daher nicht anpassen. Der Entwickler des anderen Mods müsste ändern, wie er seine Buttons hinzufügt, damit sie kompatibel werden.

### Welche Auflösung wird für Hintergrundbilder und Button-Texturen empfohlen?
Hintergründe: Ein Standardbild mit 1920x1080 (1080p) ist ein sehr guter Ausgangspunkt und skaliert für die meisten Benutzer gut.
Buttons: Die meisten Vanilla-Buttons sind etwa 150–200 Pixel breit und 20 Pixel hoch. Diese Größe für benutzerdefinierte Texturen nachzubilden, ist eine gute Praxis für Konsistenz.

### Gibt es eine Möglichkeit, automatisch ein Menü zu öffnen oder einen Befehl auszuführen, wenn ein Spieler ein In-Game-Ziel (z. B. eine Quest) abschließt?
FancyMenu selbst kann solche In-Game-Ereignisse nicht erkennen. Du kannst es jedoch mit einem Quest-Mod wie FTB Quests integrieren. Die meisten Quest-Mods erlauben es, einen Befehl als Quest-Belohnung auszuführen. Du würdest die Belohnung so einrichten, dass der Befehl `/openguiscreen` oder `/fmvariable` ausgeführt wird, um mit deinen Menüs zu interagieren.

### Wie mache ich einen Button inaktiv oder „ausgegraut“?
Du kannst den aktiven Zustand eines Buttons mit Loading Requirements steuern.
Klicke im Editor mit der rechten Maustaste auf den Button und wähle „Active State“.
Füge eine Voraussetzung hinzu, die erfüllt sein muss, damit der Button aktiv ist. Um zum Beispiel einen Button dauerhaft zu deaktivieren, könntest du eine Is Number-Voraussetzung hinzufügen, die prüft, ob 0 gleich 1 ist (was immer falsch ist).
Der Button verwendet dann seine Textur „Inactive Background“ und ist nicht anklickbar.

### Wie kann ich den Header und Footer (die Dirt-Textur-Leisten) auf scrollbaren Bildschirmen entfernen?
In FancyMenu v3 kannst du diese anpassen. Klicke im Layout-Editor mit der rechten Maustaste auf den Editor-Hintergrund und suche nach Optionen wie „Customize Header/Footer“. Du kannst ihre Texturen vollständig transparent setzen, um sie optisch effektiv zu entfernen. Beachte, dass dies nicht auf allen Bildschirmen funktioniert, besonders nicht auf älteren oder stark modifizierten.

### Ich kann kein Layout „für den aktuellen Bildschirm“ erstellen. Der Button ist ausgegraut.
Du musst die Anpassungen für diesen Bildschirm zuerst über **Menüleiste -> Customization -> Current Screen Customizations -> auf Enabled umschalten** aktivieren.

### Ich kann beim Öffnen eines Bildschirms im Editor keine Elemente anpassen. Dann ist er einfach leer.

Das könnte bedeuten, dass du versehentlich ein universelles Layout statt eines Layouts **für den aktuellen Bildschirm** erstellt hast.

Es könnte auch bedeuten, dass der Bildschirm, den du anpasst, ein scrollbarer Bildschirm ist, und solche Bildschirme kann FancyMenu standardmäßig nicht anpassen.

Die dritte Möglichkeit ist, dass es sich um einen Bildschirm aus einem Mod handelt, der Elemente auf eine nicht-Vanilla-Art hinzufügt, wodurch FancyMenu diese Elemente nicht anpassen kann.

### Bei meinem Text-Element sind seltsame graue Kästen zu sehen.

Diese durchscheinenden Kästen/Rechtecke mit geringer Deckkraft können am rechten oder unteren Rand deines Text-Elements erscheinen und sind kein Bug. Es handelt sich dabei um die Scroll-Griffe des Text-Elements, da das Element scrollbar ist.

Wenn du nicht möchtest, dass diese Kästen sichtbar sind, kannst du entweder mit der rechten Maustaste auf das Element klicken und das Scrollen komplett deaktivieren ODER du kannst im selben Rechtsklick-Menü die Griff-Texturen auf vollständig transparente Texturen setzen, wenn das Element weiterhin scrollbar sein soll.

### Wie kann ich das neueste Minecraft-Changelog in meinen Menüs anzeigen?

Es gibt ein großartiges [GitHub-Projekt](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), das Minecraft-Changelogs in FancyMenu-kompatibles Markdown umwandelt, damit du das neueste MC-Changelog in deinen Menüs anzeigen kannst! Es aktualisiert sich täglich, um neue Changelogs abzurufen.

Um zum Beispiel das neueste Minecraft-Changelog in einem Text-Element anzuzeigen, setze den **Source Mode** auf **Resource** und die Ressourcenquelle auf **Web**. Verwende dann diese URL als Quelle: `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`

### Was ist der einfachste Weg, um ein beliebiges Element auf die Größe des Bildschirms zu strecken?

Die meisten Elemente haben in ihren Kontextmenüs per Rechtsklick eine Option, sie horizontal und vertikal zu strecken. Wenn du dies aktivierst, werden sie immer auf die volle Breite und/oder Höhe des Bildschirms gestreckt. Horizontales und vertikales Strecken können unabhängig voneinander umgeschaltet werden.

### Ich kann keine Buttons anklicken oder mit Schiebereglern interagieren, wenn sie sich hinter oder vor einem Text-Element befinden.

Das passiert, weil Text-Elemente standardmäßig interaktiv sind (damit man den Scroll-Griff greifen oder Markdown-Hyperlinks anklicken kann), wodurch sie Mausklicks und Scroll-Ereignisse verbrauchen. Am besten wäre es, Buttons einfach nicht hinter/vor Text-Elementen zu platzieren, aber wenn es nicht anders geht, kannst du das Text-Element nicht interaktiv machen, indem du **mit der rechten Maustaste darauf klickst** und dann **Interactable** auf **Disabled** setzt. Beachte, dass das Text-Element dadurch zu einem statischen, nicht interaktiven Text wird, sodass du es nicht mehr scrollen oder auf Hyperlinks klicken kannst.

### Wie kann ich verhindern, dass Buttons und Schieberegler beim Navigieren in Bildschirmen mit den Pfeil- und Tabulator-Tasten ausgewählt/fokussiert werden?

Damit Buttons und Schieberegler nicht per Tastatur navigierbar sind, musst du sie **mit der rechten Maustaste anklicken** und **Navigable** auf **Disabled** setzen. Der Button/Schieberegler bleibt weiterhin anklickbar, aber du kannst ihn nicht mehr mit der Pfeil-/Tab-Navigation fokussieren.

Das ist auch nützlich, wenn du Buttons/Schieberegler zum Chat-Bildschirm hinzufügen möchtest, damit du weiterhin mit der Pfeil-nach-oben-Taste durch ältere Nachrichten scrollen kannst, ohne versehentlich Buttons/Schieberegler im Bildschirm auszuwählen.

### In einem Kontextmenü von FancyMenu fehlt eine Option, die dort sein sollte.

Die Kontextmenüs von FancyMenu (die Menüs, die sich öffnen, wenn du irgendwo mit der rechten Maustaste klickst oder mit Menüleisten interagierst), sind SCROLLBAR. Das bedeutet, du kannst dein Mausrad verwenden, während sich der Mauszeiger über dem Menü befindet, um nach oben oder unten zu scrollen, wodurch du mehr Optionen sehen kannst, die vorher nicht sichtbar waren.
