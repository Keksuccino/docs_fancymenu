---
title: FAQ
description: Häufig gestellte Fragen.
---
# FAQ

### Ich brauche Hilfe bei einem Problem. Welche Informationen sollte ich angeben?

Damit du die bestmögliche Hilfe bekommst, gib bitte so viel Kontext wie möglich an:
1.  **Eine klare Beschreibung des Problems:** Was hast du erwartet, und was ist stattdessen passiert?
2.  **Deine `latest.log`-Datei:** Du findest sie unter `<game-directory>/logs/latest.log`. **Sende kein Crash-Log**, außer es wird ausdrücklich angefordert; `latest.log` enthält normalerweise den nötigen Kontext. Nutze beim Teilen zum Beispiel eine Seite wie https://gist.github.com.
3.  **Deine Minecraft-Version:** (z. B. 1.20.1)
4.  **Deinen Mod-Loader und dessen Version:** (z. B. Forge 47.2.0, Fabric 0.15.7)
5.  **Deine FancyMenu-Version:** (z. B. 3.5.2)
6.  **Screenshots oder Videos** des Problems können ebenfalls sehr hilfreich sein.

### Wie ändere ich die Ebenenreihenfolge von Elementen (etwas vor oder hinter etwas anderem platzieren)?

*   **Custom vs. Custom:** Öffne **Fenster -> Editor-Widgets -> Ebenen** und ziehe Elemente in der Hierarchie. Du kannst außerdem mit der rechten Maustaste auf ein Element klicken und **Eine Ebene nach oben/unten verschieben** verwenden. Siehe [Ebenen und Gruppen](./layers-and-groups).
*   **Custom vs. Vanilla:** Um alle eigenen Elemente hinter allen Vanilla-Elementen zu rendern (z. B. um ein Hintergrundbild hinter die Standard-Buttons zu legen), **klicke mit der rechten Maustaste auf den Editor-Hintergrund** und aktiviere die Option **„Eigene Elemente hinter Vanilla rendern“**.

### Kann ich bestimmte Buttons von einer universellen Button-Vorlage ausschließen?

**Nein. Wenn ein Vorlagen-Button eigene Texturen festgelegt hat, werden diese Texturen immer mit allen betroffenen Elementen gemeinsam verwendet. Einzelne Buttons lassen sich nicht ausschließen.**

### Wie kann ich einen Button dazu bringen, bei einem Klick etwas auszuführen?

Verwende ein [**Action Script**](./action-scripts).
1.  Klicke im Editor mit der rechten Maustaste auf den Button.
2.  Wähle **Action Script bearbeiten**.
3. Klicke auf **Aktion hinzufügen** und wähle eine Aktion aus, z. B. [**Bildschirm oder Custom GUI öffnen**](./action-scripts#open-screen-or-custom-gui-opengui), [**Server beitreten**](./action-scripts#join-server-joinserver) oder [**Variablenwert setzen**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Kann ich einen komplett neuen Menübildschirm von Grund auf erstellen?

Verwende eine [**Custom GUI**](./custom-guis).
1.  Gehe in der Menüleiste zu **Anpassung -> Custom GUIs -> Custom GUIs verwalten**.
2.  Klicke auf **„Neue GUI“** und gib ihr eine eindeutige Kennung.
3.  Du kannst diesen neuen leeren Bildschirm dann öffnen und ein Layout dafür erstellen, dem du beliebige Elemente hinzufügen kannst.
4. Öffne die Custom GUI mit der [**Aktion „Bildschirm oder Custom GUI öffnen“**](./action-scripts#open-screen-or-custom-gui-opengui).

### Mein Spiel lädt nach dem Aktivieren von Vorladen sehr lange.

Das ist erwartetes Verhalten. Das Vorladen großer Ressourcen wie hochauflösender Animationen oder Sounds während des ersten Starts erhöht die Ladezeit des Spiels natürlich.

### Meine FMA-Animation verbraucht viel zu viel RAM!

Klassische [FMA-Animationen](./fma) können viel Speicher verbrauchen, wenn sie viele hochauflösende Frames enthalten. AFMA eignet sich besser für große oder komplexe animierte Texturen. Halte klassische FMA-Animationen kurz; verwende [Video](./video) für vollständige Videowiedergabe.

### Funktioniert FancyMenu mit OptiFine?

Nein. OptiFine ist **nicht kompatibel** und dafür bekannt, viele Mods zu stören, darunter auch FancyMenu. Es wird dringend empfohlen, moderne Alternativen wie Sodium/Embeddium + Iris/Oculus zu verwenden.
Siehe [OptiFine-Alternativen](./optifine-alternatives).

### Mein Spiel stürzt ab. Wie finde ich heraus, ob es ein Mod-Konflikt ist?

Der beste Weg, einen Mod-Konflikt zu prüfen, ist, **das Spiel nur mit FancyMenu und seinen Abhängigkeiten** (Konkrete, Melody) zu starten. Wenn der Absturz dann nicht mehr auftritt, kannst du deine anderen Mods schrittweise in kleinen Gruppen wieder hinzufügen, bis der Absturz erneut auftritt, um den konfliktverursachenden Mod zu identifizieren.

### Ein Button von einem anderen Mod verschwindet oder funktioniert nicht, wenn ich versuche, ihn zu bearbeiten.

Einige Mods fügen Widgets auf eine Weise hinzu, die FancyMenu nicht erkennen oder anpassen kann. Prüfe [Vanilla/Mod-Elemente](./vanilla-elements) und bei listenbasierten Bildschirmen [Scrollable Screens anpassen](./customizing-scrollable-screens). Wenn das Widget weiterhin nicht angezeigt wird, muss der Mod, der es hinzufügt, es als unterstütztes Bildschirm-Widget bereitstellen.

### Kann ich FancyMenu-Layouts auf einem Server verwenden?

Layouts und visuelle Anpassungen werden auf dem Client des Spielers gespeichert; ein Server kann sie nicht auf einen nicht konfigurierten Client erzwingen. Verteile sie als Teil eines Modpacks. Installiere FancyMenu auf dem Server, wenn du [Server-Befehle](./commands), [FM Data](./fm-data), [serverseitigen NBT-Zugriff](./nbt-data-placeholder#server-side-placeholder), Gamerules, Strukturen oder Server-Listener benötigst.

### Was ist der Unterschied zwischen FancyMenu v2 (für ältere MC-Versionen) und v3?

FancyMenu v3 ist eine vollständige Neuentwicklung mit vielen neuen Funktionen, einer stabileren Architektur und besserer Leistung. V2 ist veraltet, wird nicht mehr unterstützt und es fehlen viele Funktionen wie erweiterte Platzhalter und Skripting. Es wird dringend empfohlen, v3 auf einer modernen Minecraft-Version (1.18.2+) zu verwenden. V2-Layouts können beim Laden automatisch in v3 konvertiert werden, aber möglicherweise sind einige manuelle Anpassungen nötig.

### Wo finde ich vorgefertigte Layouts und Vorlagen?

Die FancyMenu-Community teilt Layouts im Kanal `#layout-templates` auf dem offiziellen Discord-Server für Keksuccino's Mods („Kekscord“).

### Wie kann ich die Spieler-Entität hinter anderen Elementen rendern lassen?

Im Allgemeinen kannst du ein [Player Entity-Element](./elements#player-entity) nicht über das [Ebenen-Widget](./layers-and-groups) hinter normale 2D-Elemente zwingen. Sein Renderer kann die normale GUI-Ebenenreihenfolge ignorieren. Gestalte das Layout unter dieser Einschränkung oder verwende ein vorgerendertes Bild, wenn eine strikte Ebenenreihenfolge erforderlich ist.

### Meine Spieler-Entität hat nur ein Bein! Was ist passiert?

Das ist ein visueller Fehler, vermutlich verursacht durch einen Mod-Konflikt mit einem anderen Mod, der Spieleranimationen oder Modelle verändert. Prüfe die Pose-Einstellungen der Spieler-Entität, um zu sehen, ob die Beine versehentlich rotiert oder verschoben wurden.

### Wie erstelle ich eine Verzögerung zwischen Aktionen in einem Skript?

Verwende [**Delay**- oder **Execute Later**-Blöcke](./action-scripts#what-are-statements) für verzögerte Aktionslogik. Für wiederkehrende Hintergrundlogik verwende [Scheduler](./schedulers).

### Kann ich Menüs aus dem Create-Mod anpassen?

Nein. Die Anpassung ist für Create-Bildschirme absichtlich deaktiviert. Siehe [Bildschirme, bei denen Anpassung absichtlich deaktiviert ist](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Welche Auflösung ist für Hintergrundbilder und Button-Texturen empfohlen?

Hintergründe: Ein Standardbild mit 1920x1080 (1080p) ist ein guter Ausgangspunkt und skaliert für die meisten Nutzer gut.
Buttons: Die meisten Vanilla-Buttons sind etwa 150–200 Pixel breit und 20 Pixel hoch. Diese Größe für eigene Texturen zu übernehmen, ist eine gute Praxis für Konsistenz.

### Gibt es eine Möglichkeit, automatisch ein Menü zu öffnen oder einen Befehl auszuführen, wenn ein Spieler ein In-Game-Ziel abgeschlossen hat (z. B. eine Quest)?
FancyMenu hat viele [eingebaute Spielereignis-Listener](./listeners), aber keinen generischen Listener für jedes Quest-System von Drittanbietern. Wenn der Quest-Mod Kommando-Belohnungen unterstützt, verwende eine davon, um [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) oder einen anderen passenden [FancyMenu-Befehl](./commands) auszuführen.

### Wie mache ich einen Button inaktiv oder „ausgegraut“?

Du kannst den aktiven Zustand eines Buttons über [Ladebedingungen](./conditions) steuern.
Klicke im Editor mit der rechten Maustaste auf den Button und wähle **Aktiven Zustand steuern**.
Füge eine Bedingung hinzu, die erfüllt sein muss, damit der Button aktiv ist. Um ihn dauerhaft zu deaktivieren, verwende [**Ist Zahl**](./conditions#is-number-fancymenu_visibility_requirement_is_number), um zu prüfen, ob 0 gleich 1 ist.
Der Button verwendet dann seine Textur „Inaktiver Hintergrund“ und ist nicht anklickbar.

### Wie kann ich den Header und Footer (die Schmutztextur-Leisten) auf scrollbaren Bildschirmen entfernen?

Öffne im Layout-Editor **Layout-Eigenschaften -> Header/Footer-Anpassungen**. Setze die Texturen auf transparent. Diese Option ist auf einigen modded Bildschirmen möglicherweise nicht verfügbar.

### Ich kann kein Layout „für den aktuellen Bildschirm“ erstellen. Der Button ist ausgegraut.

Du musst die Anpassungen für diesen Bildschirm zuerst über **Menüleiste -> Anpassung -> Aktuelle Bildschirm-Anpassungen -> Aktiviert** einschalten.

### Ich kann keine Elemente eines Bildschirms anpassen, wenn ich ihn im Editor öffne. Dann ist es nur ein leerer Bildschirm.

Das könnte bedeuten, dass du ein [Universelles Layout](./universal-layouts) statt eines Layouts **für den aktuellen Bildschirm** erstellt hast.

Es könnte auch ein [scrollbarer Bildschirm](./customizing-scrollable-screens) sein, den FancyMenu standardmäßig nicht anpassen kann.

Die dritte Möglichkeit ist, dass es sich um einen Bildschirm von einem Mod handelt, der Elemente nicht auf Vanilla-Art hinzufügt, wodurch FancyMenu diese Elemente nicht anpassen kann.

### Bei meinem Text-Element sind seltsame graue Kästen zu sehen.

Diese durchscheinenden Kästen sind die Scroll-Griffe des [Text-Elements](./elements#text) und kein Renderfehler.

Wenn du diese Kästen nicht sehen möchtest, kannst du entweder mit der rechten Maustaste auf das Element klicken und das Scrollen vollständig deaktivieren ODER du kannst im selben Rechtsklick-Menü auch die Griff-Texturen auf vollständig transparente Texturen setzen, wenn das Element weiterhin scrollbar bleiben soll.

### Wie kann ich das neueste Minecraft-Changelog in meinen Menüs anzeigen?

Es gibt ein großartiges [GitHub-Projekt](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), das Minecrafts Changelogs in FancyMenu-kompatibles Markdown umwandelt, sodass du das neueste Minecraft-Changelog in deinen Menüs anzeigen kannst! Es aktualisiert sich täglich, um neue Changelogs abzurufen.

Um es in einem [Text-Element](./elements#text) anzuzeigen, setze den **Quellenmodus** auf **Ressource** und die Ressourcenquelle auf **Web**. Verwende `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Was ist der einfachste Weg, jedes Element auf die Größe des Bildschirms zu strecken?

Die meisten Elemente haben in ihren Rechtsklick-Kontextmenüs eine Option, sie horizontal und vertikal zu strecken. Wenn du diese aktivierst, werden sie immer auf die volle Breite und/oder Höhe des Bildschirms gestreckt. Horizontales und vertikales Strecken können unabhängig voneinander umgeschaltet werden.

### Ich kann keine Buttons oder Schieberegler anklicken bzw. mit ihnen interagieren, wenn sie hinter oder vor einem Text-Element liegen.

Das liegt daran, dass Text-Elemente standardmäßig interaktiv sind (damit du den Scroll-Griff greifen oder Markdown-Links anklicken kannst), wodurch sie Mausklicks und Scroll-Ereignisse abfangen. Am besten wäre es, Buttons nicht vor/hinter Text-Elemente zu verschieben, aber wenn es nicht anders geht, kannst du das Text-Element per **Rechtsklick** nicht interaktiv machen und dann **Interaktiv** auf **Deaktiviert** setzen. Beachte, dass das Text-Element dadurch statisch und nicht interaktiv wird, sodass du es nicht mehr scrollen oder auf Hyperlinks klicken kannst.

### Wie kann ich verhindern, dass Buttons und Schieberegler beim Navigieren mit den Pfeiltasten und der Tab-Taste in Bildschirmen ausgewählt/fokussiert werden?

Damit Buttons und Schieberegler nicht navigierbar sind, musst du **mit der rechten Maustaste** darauf klicken und **Navigierbar** auf **Deaktiviert** setzen. Der Button/Schieberegler ist dann zwar weiterhin anklickbar, aber du kannst ihn nicht mehr per Pfeil-/Tab-Navigation fokussieren.

Das ist auch nützlich, wenn du Buttons/Schieberegler zum Chat-Bildschirm hinzufügen möchtest, damit du weiterhin mit der Pfeil-nach-oben-Taste durch ältere Nachrichten scrollen kannst, ohne versehentlich Buttons/Schieberegler auf dem Bildschirm auszuwählen.

### Ein Kontextmenü von FancyMenu hat eine Option nicht, die dort eigentlich sein sollte.

Die Kontextmenüs von FancyMenu (die Menüs, die sich öffnen, wenn du irgendwo mit der rechten Maustaste klickst oder mit Menüleisten interagierst) sind SCROLLBAR. Das bedeutet, dass du dein Mausrad benutzen kannst, während sich der Mauszeiger über dem Menü befindet, um nach oben oder unten zu scrollen und so mehr Optionen zu sehen, die vorher nicht sichtbar waren.

### Ich kann den Titelbildschirm nicht anpassen, er zeigt nach dem Verlassen des Editors immer noch den ursprünglichen Bildschirm.

Ein anderes Mod ersetzt den ursprünglichen `title_screen`. Deaktiviere den benutzerdefinierten Titelbildschirm dieses Mods in dessen Einstellungen. Wenn es keine solche Option gibt, kann FancyMenu das Layout nicht auf den ersetzten Bildschirm anwenden.
