---
title: FAQ
description: Häufig gestellte Fragen.
sourceBlobSha: 4ae872e8e4a54fc6a89de7c87c8a137a89292455
---
# FAQ

### Ich brauche Hilfe bei einem Problem. Welche Informationen sollte ich bereitstellen?

Damit wir dir bestmöglich helfen können, gib bitte so viel Kontext wie möglich an:
1.  **Eine klare Beschreibung des Problems:** Was hast du erwartet und was ist tatsächlich passiert?
2.  **Deine `latest.log`-Datei:** Du findest sie unter `<game-directory>/logs/latest.log`. **Sende kein Crash-Log**, es sei denn, wir bitten dich ausdrücklich darum. Die `latest.log` enthält normalerweise alle erforderlichen Informationen. Nutze zum Teilen eine Website wie https://gist.github.com.
3.  **Deine Minecraft-Version:** (z. B. 1.20.1)
4.  **Deinen Mod-Loader und dessen Version:** (z. B. Forge 47.2.0, Fabric 0.15.7)
5.  **Deine FancyMenu-Version:** (z. B. 3.5.2)
6.  **Screenshots oder Videos** des Problems können ebenfalls sehr hilfreich sein.

> [!TIP]
> Fragst du Alice oder eine andere KI um Hilfe? Füge einen [Export für KI](/export-for-ai) des Problems hinzu. Er zeigt der KI genau, wie alles eingerichtet ist, und enthält bereits deine Minecraft-, Mod-Loader- und FancyMenu-Versionen.

### Wie ändere ich die Ebenenreihenfolge von Elementen (etwas vor oder hinter ein anderes verschieben)?

- **Deine eigenen Elemente:** Ziehe ihre Ebenen im Ebenen-Widget des Layout-Editors an die gewünschte Stelle oder klicke mit der rechten Maustaste auf ein Element und wähle **Eine Ebene nach oben verschieben** oder **Eine Ebene nach unten verschieben**. Siehe [Ebenen und Gruppen](/layout-editor#layers-and-groups).
- **Deine Elemente und Vanilla-Elemente:** Die Reihenfolge der Vanilla-Elemente lässt sich nicht ändern. Um alle deine Elemente dahinter zu platzieren, etwa ein Hintergrundbild hinter den Standard-Schaltflächen, klicke mit der rechten Maustaste auf den Editor-Hintergrund und setze **Benutzerdefinierte Elemente hinter Vanilla** auf **Aktiviert**.

### Kann ich bestimmte Schaltflächen von einer universellen Schaltflächenvorlage ausschließen?

**Nein. Wenn für eine Vorlagen-Schaltfläche eigene Texturen festgelegt sind, werden diese immer mit allen betroffenen Elementen geteilt. Einzelne Schaltflächen können nicht ausgeschlossen werden.**

### Wie lege ich fest, dass beim Klicken auf eine Schaltfläche etwas passiert?

Verwende ein [**Aktionsskript**](/action-scripts).
1.  Klicke im Editor mit der rechten Maustaste auf die Schaltfläche.
2.  Wähle **Aktionsskript bearbeiten**.
3. Klicke auf **Aktion hinzufügen** und wähle eine Aktion aus, zum Beispiel [**Bildschirm oder benutzerdefinierte GUI öffnen**](/action-scripts#open-screen-or-custom-gui), [**Server beitreten**](/action-scripts#join-server) oder [**Variablenwert festlegen**](/action-scripts#set-variable-value-fm-variable).

### Kann ich einen komplett neuen Menübildschirm von Grund auf erstellen?

Ja, mit einer [benutzerdefinierten GUI](/custom-guis):

1. Öffne **Menüleiste -> Anpassung -> Benutzerdefinierte GUIs -> Benutzerdefinierte GUIs verwalten** und klicke auf **Neue GUI**.
2. Gib ihr eine Kennung, zum Beispiel `modpack_info`, und klicke auf **Fertig**.
3. Öffne sie über **GUI öffnen** und erstelle ein Layout dafür, wie für jedes andere Menü.
4. Öffne sie über eine Schaltfläche mit der Aktion [**Bildschirm oder benutzerdefinierte GUI öffnen**](/action-scripts#open-screen-or-custom-gui) und ihrer Kennung.

### Mein Spiel braucht nach dem Aktivieren des Vorladens sehr lange zum Laden.

Das ist erwartetes Verhalten. Wenn große Ressourcen wie hochauflösende Animationen oder Sounds beim ersten Start vorgeladen werden, verlängert sich die Ladezeit des Spiels ganz natürlich.

### Meine Animation verbraucht viel RAM oder lässt das Spiel ruckeln!

Große Einzelbilder und hohe Bildraten kosten Speicher und Leistung. Passe die Größe der Einzelbilder ungefähr an die Größe an, in der sie auf dem Bildschirm angezeigt werden, und verwende weniger Bilder pro Sekunde. Siehe [Animationen](/animations#performance). Für lange Clips mit Ton solltest du stattdessen ein [Video](/video) verwenden.

### Funktioniert FancyMenu mit OptiFine?

Nein. OptiFine ist **nicht kompatibel** und dafür bekannt, viele Mods zu beeinträchtigen, darunter auch FancyMenu. Es wird dringend empfohlen, moderne Alternativen wie Sodium/Embeddium + Iris/Oculus zu verwenden.
Siehe [OptiFine-Alternativen](/optifine-alternatives).

### Mein Spiel stürzt ab. Wie finde ich heraus, ob ein Mod-Konflikt vorliegt?

Am besten prüfst du auf einen Mod-Konflikt, indem du **das Spiel nur mit FancyMenu und seinen Abhängigkeiten** (Konkrete, Melody) startest. Tritt der Absturz dann nicht mehr auf, kannst du deine anderen Mods nach und nach in kleinen Gruppen wieder hinzufügen, bis der Absturz erneut auftritt. So findest du den konfliktverursachenden Mod.

### Eine Schaltfläche eines anderen Mods verschwindet oder funktioniert nicht, wenn ich sie bearbeiten möchte.

Manche Mods fügen Widgets auf eine Weise hinzu, die FancyMenu nicht erkennen oder anpassen kann. Sieh dir [Vanilla-/Mod-Elemente](/vanilla-elements) und bei listenbasierten Bildschirmen [Scrollbare Bildschirme anpassen](/customizing-scrollable-screens) an. Wird das Widget weiterhin nicht angezeigt, muss der Mod, der es hinzufügt, es als unterstütztes Bildschirm-Widget bereitstellen.

### Kann ich FancyMenu-Layouts auf einem Server verwenden?

Layouts und visuelle Anpassungen werden auf dem Client des Spielers gespeichert. Ein Server kann sie einem nicht entsprechend eingerichteten Client nicht aufzwingen. Verteile sie als Teil eines Modpacks. Installiere FancyMenu auf dem Server, wenn du [Serverbefehle](/commands), [FM-Daten](/fm-data), [serverseitigen NBT-Zugriff](/nbt-data-placeholder#server-side-placeholder), Spielregeln, Strukturen oder Server-Listener benötigst.

### Was ist der Unterschied zwischen FancyMenu v2 (für ältere MC-Versionen) und v3?

FancyMenu v3 ist eine vollständige Neuentwicklung mit vielen neuen Funktionen, einer stabileren Architektur und besserer Leistung. V2 ist veraltet, wird nicht mehr unterstützt und bietet viele Funktionen wie erweiterte Platzhalter und Skripting nicht. Es wird dringend empfohlen, v3 mit einer modernen Minecraft-Version (1.18.2+) zu verwenden. V2-Layouts können beim Laden automatisch in v3 konvertiert werden, möglicherweise sind jedoch einige manuelle Anpassungen erforderlich.

### Wo finde ich vorgefertigte Layouts und Vorlagen?

Die FancyMenu-Community teilt vollständige Konfigurationen im Kanal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) des offiziellen Discord-Servers („Kekscord“). Installiere sie als eigenes Profil; siehe [Layout-Vorlagen](/profiles#layout-templates).

### Wie kann ich die Spielerkörper-Entität hinter anderen Elementen anzeigen lassen?

In der Regel kannst du ein [Spielerkörper-Entität-Element](/elements#player-entity) nicht über das [Ebenen-Widget](/layout-editor#layers-and-groups) hinter normale 2D-Elemente zwingen. Der Renderer kann die normale GUI-Ebenenreihenfolge ignorieren. Gestalte dein Layout so, dass es diese Einschränkung berücksichtigt, oder verwende ein vorgerendertes Bild, wenn eine feste Ebenenreihenfolge erforderlich ist.

### Meine Spielerkörper-Entität hat nur ein Bein! Was ist passiert?

Das ist ein Grafikfehler, der wahrscheinlich durch einen Mod-Konflikt mit einem anderen Mod verursacht wird, der Spielermodelle oder -animationen verändert. Prüfe die Pose-Einstellungen der Spielerkörper-Entität, um festzustellen, ob die Beine versehentlich gedreht oder verschoben wurden.

### Wie füge ich in einem Skript eine Verzögerung zwischen Aktionen ein?

Klicke mit der rechten Maustaste auf den Skriptbereich des Aktionsskript-Editors, klicke auf **EXECUTE LATER-Block hinzufügen** und füge die Aktionen ein, die warten sollen. Sie werden nach der angegebenen Zeit in Millisekunden einmal ausgeführt. Der Rest des Skripts wird sofort fortgesetzt. Siehe [Später ausführen](/action-scripts#execute-later).

Für Aktionen, die sich wiederholen sollen, verwende [Scheduler](/schedulers).

### Kann ich Menüs des Create-Mods anpassen?

Nein. Die Anpassung von Create-Bildschirmen ist absichtlich deaktiviert. Siehe [Bildschirme, für die die Anpassung absichtlich deaktiviert ist](/incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Welche Auflösung wird für Hintergrundbilder und Schaltflächentexturen empfohlen?

Hintergründe: Ein Standardbild mit 1920 × 1080 Pixeln (1080p) ist ein guter Ausgangspunkt und lässt sich für die meisten Nutzer gut skalieren.
Schaltflächen: Die meisten Vanilla-Schaltflächen sind etwa 150–200 Pixel breit und 20 Pixel hoch. Benutzerdefinierte Texturen in ähnlicher Größe sorgen für ein einheitliches Erscheinungsbild.

### Kann ein Menü automatisch geöffnet oder ein Befehl ausgeführt werden, wenn ein Spieler ein Spielziel (wie eine Quest) abschließt?
FancyMenu verfügt über viele [integrierte Spielereignis-Listener](/listeners), aber keinen allgemeinen Listener für jedes Quest-System eines Drittanbieters. Wenn der Quest-Mod Befehlsbelohnungen unterstützt, kannst du damit [`/openguiscreen`](/commands#openguiscreen), [`/fmvariable`](/commands#fmvariable) oder einen anderen passenden [FancyMenu-Befehl](/commands) ausführen.

### Wie mache ich eine Schaltfläche inaktiv oder „ausgegraut“?

Du kannst den Aktivierungszustand einer Schaltfläche mithilfe von [Bedingungen](/conditions) steuern.
Klicke im Editor mit der rechten Maustaste auf die Schaltfläche und wähle **Aktivierungszustand steuern**.
Füge eine Bedingung hinzu, die erfüllt sein muss, damit die Schaltfläche aktiv ist. Um sie dauerhaft zu deaktivieren, verwende [**Ist Zahl**](/conditions#is-number), um zu prüfen, ob 0 gleich 1 ist.
Die Schaltfläche verwendet dann ihre Textur für den „Inaktiven Hintergrund“ und kann nicht angeklickt werden.

### Wie entferne ich Kopf- und Fußzeile (die Balken mit der Erdtextur) auf scrollbaren Bildschirmen?

Öffne im Layout-Editor **Layouteigenschaften -> Kopf-/Fußzeilen-Anpassungen**. Stelle die Texturen auf transparent. Bei manchen modifizierten Bildschirmen ist diese Option möglicherweise nicht verfügbar.

### Ich kann kein Layout „für den aktuellen Bildschirm“ erstellen. Die Schaltfläche ist ausgegraut.

Aktiviere zuerst die Anpassungen für diesen Bildschirm: Klicke auf **Menüleiste -> Anpassung -> Anpassung des aktuellen Bildschirms**, sodass **Aktiviert** angezeigt wird.

### Ich kann im Editor keine Elemente eines Bildschirms anpassen. Beim Öffnen ist der Bildschirm einfach leer.

Möglicherweise hast du ein [universelles Layout](/universal-layouts) statt eines Layouts **für den aktuellen Bildschirm** erstellt.

Es könnte sich auch um einen [scrollbaren Bildschirm](/customizing-scrollable-screens) handeln, den FancyMenu standardmäßig nicht anpassen kann.

Eine dritte Möglichkeit ist, dass es sich um einen Bildschirm eines Mods handelt, der Elemente auf eine nicht mit Vanilla übereinstimmende Weise hinzufügt. Dadurch kann FancyMenu diese Elemente nicht anpassen.

### Neben meinem Textelement werden seltsame graue Kästchen angezeigt.

Das sind die Bildlaufleisten des [Textelements](/elements#text). Sie erscheinen, wenn der Text nicht in das Element passt, damit Spieler darin scrollen können.

- Vergrößere das Element oder kürze den Text, dann verschwinden sie.
- Klicke mit der rechten Maustaste auf das Element und öffne **Bildlaufleisten**. Unter **Anzeigen** legst du fest, wann sie erscheinen: **Immer**, nur **Beim Scrollen** oder **Nie**. Bei **Nie** funktioniert das Scrollen mit dem Mausrad weiterhin.
- Im selben Menü kannst du unter **Stil des Bildlaufleisten-Griffs**, **Texturen des Bildlaufleisten-Griffs** und **Farbe des Bildlaufleisten-Griffs [HEX]** das Aussehen ändern.

Alle Einstellungen für Bildlaufleisten findest du unter [Text in Menüs](/text-in-menus#scroll-bars).

### Wie kann ich das aktuelle Minecraft-Änderungsprotokoll in meinen Menüs anzeigen?

Es gibt ein tolles [GitHub-Projekt](https://github.com/ClaytonTDM/minecraft-changelogs-markdown), das die Minecraft-Änderungsprotokolle in FancyMenu-kompatibles Markdown umwandelt. So kannst du das aktuelle MC-Änderungsprotokoll in deinen Menüs anzeigen! Das Projekt wird täglich aktualisiert, um neue Änderungsprotokolle abzurufen.

Um es in einem [Textelement](/elements#text) anzuzeigen, stelle **Quellmodus** auf **Ressource** und die Ressourcenquelle auf **Web**. Verwende `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Wie kann ich ein beliebiges Element am einfachsten auf Bildschirmgröße strecken?

Bei den meisten Elementen kannst du im Kontextmenü, das sich per Rechtsklick öffnet, festlegen, dass sie horizontal und vertikal gestreckt werden. Wenn du diese Option aktivierst, werden sie immer auf die volle Bildschirmbreite und/oder -höhe gestreckt. Die horizontale und vertikale Streckung lassen sich unabhängig voneinander aktivieren.

### Ich kann keine Schaltflächen anklicken oder Regler bedienen, wenn sie hinter oder vor einem Textelement liegen.

Das liegt daran, dass Textelemente standardmäßig interaktiv sind (damit man den Bildlaufleisten-Griff bewegen oder auf Markdown-Links klicken kann). Daher fangen sie Mausklicks und Scroll-Ereignisse ab. Am besten platzierst du Schaltflächen nicht hinter oder vor Textelementen. Wenn sich das nicht vermeiden lässt, kannst du das Textelement **mit der rechten Maustaste anklicken** und **Interaktiv** auf **Deaktiviert** setzen. Beachte, dass das Textelement dadurch statisch und nicht mehr interaktiv ist: Du kannst dann weder darin scrollen noch auf Links klicken.

### Wie verhindere ich, dass Schaltflächen und Regler bei der Navigation mit den Pfeiltasten und der Tabulatortaste ausgewählt oder fokussiert werden?

Damit Schaltflächen und Regler nicht über die Tastatur angesteuert werden können, klicke mit der rechten Maustaste darauf und setze **Navigierbar** auf **Deaktiviert**. Die Schaltfläche bzw. der Regler kann weiterhin angeklickt werden, lässt sich aber nicht mehr mit den Pfeiltasten oder der Tabulatortaste fokussieren.

Das ist auch nützlich, wenn du Schaltflächen oder Regler zum Chat-Bildschirm hinzufügst. So kannst du weiterhin mit der Pfeiltaste nach oben durch ältere Nachrichten blättern, ohne versehentlich Schaltflächen oder Regler auf dem Bildschirm auszuwählen.

### In einem Kontextmenü von FancyMenu fehlt eine Option, die dort eigentlich sein sollte.

Die Kontextmenüs von FancyMenu (Menüs, die sich öffnen, wenn du irgendwo mit der rechten Maustaste klickst oder mit Menüleisten interagierst) sind SCROLLBAR. Du kannst das Mausrad bewegen, während sich der Mauszeiger über dem Menü befindet, um nach oben oder unten zu scrollen und weitere Optionen anzuzeigen, die vorher nicht sichtbar waren.

### Ich kann den Titelbildschirm nicht anpassen. Wenn ich den Editor verlasse, wird immer wieder der ursprüngliche Bildschirm angezeigt.

Ein anderer Mod ersetzt den ursprünglichen `title_screen`. Deaktiviere den benutzerdefinierten Titelbildschirm dieses Mods in dessen Einstellungen. Gibt es keine solche Option, kann FancyMenu das Layout nicht auf den Ersatzbildschirm anwenden.

### Wenn ich den Inventarbildschirm anpassen möchte, kann ich den Inventarcontainer nicht bearbeiten.

Das ist so vorgesehen. FancyMenu unterstützt nicht die Bearbeitung des eigentlichen Containers eines Inventarbildschirms (Spielerinventar, Truhe, Werkbank usw.), da die Implementierung dieser Unterstützung sehr aufwendig wäre.

Du kannst diesen Bildschirmen weiterhin neue Elemente hinzufügen, aber die Container selbst nicht bearbeiten.

Übrigens hilft SpiffyHUD dabei ebenfalls nicht, da es zum Bearbeiten des HUDs gedacht ist (zum Beispiel der Gegenstandsleiste), aber keine Bildschirme wie Inventarbildschirme bearbeiten kann.
