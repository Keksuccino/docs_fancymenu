---
title: Elemente
description: 'Alles, was du über die Elementtypen von FancyMenu wissen musst.'
---

# Elemente

Elemente sind die Bausteine deiner benutzerdefinierten Layouts in FancyMenu. Du kannst sie zu jedem Layout hinzufügen, um Informationen anzuzeigen, Interaktivität einzubauen oder beeindruckende visuelle Effekte zu erzeugen.

# Elemente zu einem Layout hinzufügen

Du kannst im **Layout-Editor** ein neues Element zu deinem Layout hinzufügen.

1.  **Rechtsklicke** auf den Hintergrund des Editors, um das Kontextmenü zu öffnen.
2.  Fahre mit der Maus über **Neues Element**.
3.  Es erscheint eine Liste aller verfügbaren Elementtypen. Klicke auf den Typ, den du hinzufügen möchtest.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Sobald ein Element hinzugefügt wurde, kannst du es verschieben, in der Größe ändern und anpassen, indem du es **rechtsklickst**, um sein spezielles Kontextmenü zu öffnen. Mehr darüber, wie man Elemente anordnet, findest du unter [Elemente positionieren](./positioning-elements) und [Element-IDs](./element-identifiers).

# Elemente im Detail

Dieser Abschnitt listet die eingebauten Elemente von FancyMenu auf. Verwende [Ebenen und Gruppen](./layers-and-groups), um ihre Render-Reihenfolge zu organisieren.

## Schaltfläche
Eine anklickbare Schaltfläche, die eine Vielzahl von Aktionen ausführen kann. Dies ist eines der leistungsstärksten und vielseitigsten Elemente zum Erstellen interaktiver Menüs.

*   **Anwendungsfälle:**
    *   Eine Schaltfläche für „Discord beitreten“ oder „Website besuchen“ erstellen.
    *   Eine Schnellbeitritts-Schaltfläche für einen bestimmten Server hinzufügen.
    *   Benutzerdefinierte Navigation zwischen verschiedenen Menüs erstellen.
    *   Schaltflächen erstellen, die andere Layouts ein- oder ausschalten.
*   **Hauptfunktionen:**
    *   **Aktionen:** Kann eine Abfolge von [Aktionen](./action-scripts) ausführen, z. B. eine URL öffnen, einem Server beitreten, einen Chat-Befehl senden, die Funktion einer anderen Schaltfläche nachahmen oder Variablen steuern.
    *   **Benutzerdefiniertes Aussehen:** Vollständig anpassbare Texturen für normale, hervorgehobene und inaktive Zustände. Unterstützt transparente Hintergründe, Nine-Slicing, benutzerdefinierte Textfarben, Textfarben beim Hovern, Textskalierung, Ein-/Ausschalten des Textschattens und Schaltflächen-Icon-Texturen.
    *   **Sounds:** Benutzerdefinierte Klick-, Hover- und Unhover-Sounds.
    *   **Vorlagenmodus:** Kann sein Aussehen und seine Eigenschaften auf andere Vanilla- oder modifizierte Schaltflächen im Menü anwenden. Siehe [Schaltflächen- & Slider-Vorlagen](./button-slider-templates).
    *   **Automatisierte Vanilla-/Mod-Widget-Klicks:** Vorhandene Vanilla- und Mod-Widgets haben die Eigenschaft **Automatisierte Klicks**, mit der ihr ursprüngliches Klickverhalten beim Laden des Bildschirms eine festgelegte Anzahl von Malen ausgelöst werden kann. Details findest du unter [Vanilla-Elemente](./vanilla-elements#automated-clicks).

## Slider
Ein Schieberegler, den Benutzer ziehen können, um einen Wert aus einer Liste oder einem Bereich auszuwählen. Er kann Aktionen ausführen, wann immer sich sein Wert ändert.

*   **Anwendungsfälle:**
    *   Eine benutzerdefinierte Lautstärkeregelung erstellen.
    *   Ein Slider, um zwischen verschiedenen Themes oder Hintergrundbildern zu wechseln (mit dem Typ „Liste“).
    *   Eine bestimmte Minecraft-Option anpassen, etwa Helligkeit oder Renderdistanz.
*   **Hauptfunktionen:**
    *   **Typen:** Kann eine `Werteliste` sein (z. B. „Einfach“, „Normal“, „Schwer“), ein `Ganzzahlbereich` (z. B. 1–100) oder ein `Dezimalbereich` (z. B. 0,0–1,0).
    *   **Dynamische Aktionen:** Führt Aktionen aus, wenn sich sein Wert ändert. Der aktuelle Wert kann mit [Variablen](./variables) verwendet werden.
    *   **Anpassung:** Das Label des Sliders kann seinen aktuellen Wert dynamisch anzeigen. Griff und Hintergrundtexturen sind vollständig anpassbar, einschließlich transparenter Hintergründe, Optionen für Label-Farbe/-Skalierung, Textschatten-Umschalter und benutzerdefinierte Klick-/Unhover-Sounds.

## Kontrollkästchen
Ein normales Kontrollkästchen, das ein- oder ausgeschaltet werden kann. Es kann beim Umschalten Aktionen ausführen.

*   **Anwendungsfälle:**
    *   Ein Kontrollkästchen „Ich stimme den Regeln zu“.
    *   Eine Einstellung, um eine bestimmte Funktion in deinem benutzerdefinierten Menü zu aktivieren oder zu deaktivieren.
    *   Ein Layout oder eine Variable ein- bzw. ausschalten.
*   **Hauptfunktionen:**
    *   **Aktionen beim Umschalten:** Führt [Action Scripts](./action-scripts) aus, wenn sich sein Zustand ändert. Der aktuelle Zustand (`true` oder `false`) steht den Aktionen zur Verfügung.
    *   **Variablenmodus:** Kann direkt mit einer FancyMenu-Variable verknüpft werden, sodass der Zustand des Kontrollkästchens aus dieser Variable gelesen und in sie geschrieben wird.
    *   **Persistenter Zustand:** Wenn der Variablenmodus deaktiviert ist, speichert das Kontrollkästchen seinen Zustand automatisch anhand der Element-ID und stellt ihn nach einem Spielneustart wieder her. Diese Zustände werden in `<game-directory>/checkbox_states.json` gespeichert. Im Variablenmodus ist stattdessen die verknüpfte FancyMenu-Variable die Zustandsquelle des Kontrollkästchens.
    *   **Benutzerdefiniertes Aussehen:** Unterstützt benutzerdefinierte Texturen für den Hintergrund (im normalen, Hover- und inaktiven Zustand) sowie für das Häkchen selbst.

## Texteingabefeld
Ein Feld, in das Benutzer Text eingeben können. Sein Inhalt kann mit einer FancyMenu-Variable verknüpft werden, sodass du Benutzereingaben erfassen und verwenden kannst.

*   **Anwendungsfälle:**
    *   Ein Eingabefeld für „Server-IP“, das mit einer Schaltfläche „Server beitreten“ funktioniert.
    *   Ein Feld zur Eingabe des Spielernamens für eine benutzerdefinierte Skin-Vorschau.
    *   Eine einfache loginähnliche Oberfläche erstellen.
*   **Hauptfunktionen:**
    *   **Verknüpfung mit Variablen:** Speichert den eingegebenen Text in einer angegebenen [Variable](./variables).
    *   **Eingabevalidierung:** Kann so konfiguriert werden, dass nur bestimmte Zeichentypen akzeptiert werden, z. B. Zahlen, URLs oder einfacher Text.
    *   **Maximale Länge:** Du kannst eine maximale Zeichenzahl für die Eingabe festlegen.
    *   **Aussehen und Sounds:** Unterstützt benutzerdefinierte Hintergrundfarbe, Rahmenfarben, Rahmenrundung, Textfarbe, Hinweis-/Platzhaltertext, Hinweisfarbe, Hover-Sounds, Unhover-Sounds und Klick-Sounds.

## Tooltip
Ein Textfeld, das an einer festen Position erscheinen oder dem Mauszeiger folgen kann. Seine Sichtbarkeit wird normalerweise über [Ladebedingungen](./conditions) gesteuert.

*   **Anwendungsfälle:**
    *   Detaillierte Informationen anzeigen, wenn ein Benutzer über eine Schaltfläche oder ein Bild hovert.
    *   Kontextbezogene Hilfetipps erstellen, die unter bestimmten Bedingungen erscheinen.
    *   Dynamische Informationen (z. B. Serverstatus) neben dem Cursor anzeigen.
*   **Hauptfunktionen:**
    *   **Folgt der Maus:** Kann so eingestellt werden, dass es dem Mauszeiger folgt.
    *   **Markdown-Unterstützung:** Der Tooltip-Inhalt unterstützt vollständige Markdown-Formatierung.
    *   **Benutzerdefinierter Hintergrund:** Der Hintergrund kann eine einfarbige Farbe oder eine benutzerdefinierte, neunfach geslicte Textur sein, für ein vollständig thematisches Erscheinungsbild.

## Item
Zeigt ein einzelnes Minecraft-Item an, entweder aus Vanilla oder aus einem Mod.

*   **Anwendungsfälle:**
    *   Items als Symbole für Schaltflächen oder Menüauswahlen verwenden.
    *   Eine GUI für Shop- oder Kit-Auswahl erstellen.
    *   Das aktuell gehaltene Item oder die Rüstung eines Spielers anzeigen.
*   **Hauptfunktionen:**
    *   **Benutzerdefinierte Daten:** Unterstützt einen benutzerdefinierten Namen, Lore, Anzahl, Verzauberungsglanz und NBT-Daten. Siehe den [NBT-Daten-Platzhalter](./nbt-data-placeholder).
    *   **Tooltip-Anzeige:** Kann so konfiguriert werden, dass der Standard-Tooltip des Items beim Hover angezeigt wird.

## Block-/Item-JSON-Modell
Rendert ein Block- oder Item-JSON-Modell aus Minecraft-Ressourcen oder externen Quellen.

*   **Anwendungsfälle:**
    *   Ein 3D-Modell aus einem Resource Pack in einem Menü anzeigen.
    *   Item-/Block-Vorschauen mit benutzerdefinierten Texturen anzeigen.
    *   Modellbasierte dekorative UI-Elemente erstellen.
*   **Hauptfunktionen:**
    *   **Modellquelle:** Kann Modell-JSON aus Minecraft-Ressourcen oder externen Quellen laden.
    *   **Texturüberschreibungen:** Unterstützt das Festlegen einer benutzerdefinierten Textur.
    *   **Render-Steuerung:** Modellversatz, Skalierung, Rotation um drei Achsen, transparente Darstellung und die GUI-Transformation des Modells.
    *   **Beleuchtung:** Zwei konfigurierbare Lichter mit unabhängiger Farbton- und Rotationssteuerung.

## Bild
Zeigt ein statisches Bild aus einer lokalen Datei, einer Web-URL oder einer Minecraft-Ressourcenadresse an.

*   **Anwendungsfälle:**
    *   Ein Serverlogo oder Modpack-Branding hinzufügen.
    *   Dekorative Ränder oder UI-Rahmen erstellen.
    *   Bilder als Teil eines komplexeren UI-Designs verwenden.
*   **Hauptfunktionen:**
    *   **Nine-Slicing:** Skaliert Ränder oder Panels, ohne ihre Ecken zu verzerren. Siehe [Nine-Slicing & Kachelung](./nine-slicing-and-tiling).
    *   **Textur-Wiederholung:** Das Bild kann gekachelt werden, um die Fläche des Elements zu füllen.
    *   **Einfärbung:** Du kannst dem Bild einen Farbstich hinzufügen.
    *   **Abgerundete Ecken:** Nicht-nine-geslicte und nicht wiederholte Bilder können abgerundete Ecken haben.
    *   **Parallax-Effekt:** Bewegt sich mit der Maus, um visuelle Tiefe zu erzeugen. Siehe [Parallax-Effekt](./parallax).

## Text
Ein äußerst vielseitiges Element zum Anzeigen von Text. Es kann für alles verwendet werden, von einzeiligen Beschriftungen bis hin zu mehrseitigen, scrollbaren Dokumenten.

*   **Anwendungsfälle:**
    *   Serverregeln, Patch Notes oder Willkommensnachrichten anzeigen.
    *   Dynamische Informationsfelder mit [Platzhaltern](./placeholders) erstellen, zum Beispiel `Willkommen, {"placeholder":"playername"}!`.
    *   Beschriftungen und Beschreibungen zu deiner UI hinzufügen.
*   **Hauptfunktionen:**
    *   **Inhaltsquellen:** Text kann direkt eingegeben, aus einer lokalen Datei geladen oder von einer Web-URL abgerufen werden.
    *   **Markdown-Unterstützung:** Unterstützt Überschriften, Listen, Codeblöcke, Tabellen und andere Markdown-Formatierungen. Siehe [Textformatierung](./text-formatting).
    *   **Scrollen:** Wird automatisch scrollbar, wenn der Inhalt größer als die Fläche des Elements ist. Scrollleisten können angepasst oder deaktiviert werden.
    *   **Gestaltung:** Vollständige Kontrolle über Textfarbe, Skalierung, Ausrichtung, Schatten und Zeilenabstand.

## Video
Spielt eine Videodatei ab. Das ist perfekt für cineastische Intros oder dekorative, sich wiederholende Hintergründe.

> [!WARNING]
> Das native Video-Element erfordert **Watermedia V3** und **Watermedia Binaries V3**. Das alte Element **Video [MCEF]** ist veraltet.

*   **Anwendungsfälle:**
    *   Ein animierter Trailer für ein Modpack oder einen Server.
    *   Ein sich wiederholendes, stimmungsvolles Video, um dein Menü lebendiger zu machen.
    *   Ein In-Game-Tutorialvideo.
*   **Hauptfunktionen:**
    *   **Quellen:** Unterstützt lokale Videodateien und Web-URLs. Siehe [Videos](./video).
    *   **Wiedergabesteuerung:** Kann so eingestellt werden, dass es automatisch in Schleife läuft. Lautstärke, Soundkanal und das Verhalten zur Beibehaltung des Seitenverhältnisses sind anpassbar.
    *   **Interaktive Steuerung:** Wiedergabe, Suchzeit und Lautstärke des Videos können über Schaltflächenaktionen gesteuert werden.

## GLSL-Shader
Rendert einen benutzerdefinierten GLSL-Shader innerhalb eines Elements.

*   **Anwendungsfälle:**
    *   Animierte Shader-Panels.
    *   Prozedurale visuelle Effekte.
    *   Shadertoy-ähnliche Menüeffekte, die auf ein Element-Rechteck zugeschnitten sind.
*   **Hauptfunktionen:**
    *   **Shader-Laufzeit:** Unterstützt Single-Pass- und Multi-Pass-Shader.
    *   **Shadertoy-Unterstützung:** Kann Shadertoy-ähnliche `mainImage`-Shader verwenden.
    *   **Uniforms:** Stellt FancyMenu- und Eingabe-Uniforms bereit. Siehe die [GLSL-Shader-API](./glsl-shader-api).

## Diashow
Zeigt eine Abfolge von Bildern an. Die Bilder und die Konfigurationsdatei `properties.txt` befinden sich im eigenen Unterverzeichnis der Diashow unter `<game-directory>/config/fancymenu/slideshows/`.

*   **Anwendungsfälle:**
    *   Eine rotierende Galerie von In-Game-Screenshots.
    *   Die wichtigsten Funktionen eines Modpacks präsentieren.
    *   Ein dynamischer Hintergrund, der zwischen verschiedenen Szenen wechselt.
*   **Hauptfunktionen:**
    *   Lädt vorkonfigurierte [Diashows](./slideshows).
    *   Kann so eingestellt werden, dass das Seitenverhältnis der Bilder beibehalten wird.

## Rechteckform
Ein einfaches, einfarbiges Rechteck.

*   **Anwendungsfälle:**
    *   Einen halbtransparenten Hintergrund hinter Text erstellen, um die Lesbarkeit zu verbessern.
    *   Einfache UI-Panels und Trennlinien gestalten.
    *   Als farbiger Platzhalter während des Layout-Designs.
*   **Hauptfunktionen:**
    *   Unterstützt HEX-RGBA-Farben, abgerundete Ecken und optionalen Unschärfeeffekt, sodass die Form als einfaches Panel, Tönung oder unscharfer Hintergrund verwendet werden kann.

## Kreisform
Eine einfache, einfarbige Kreis-/Ellipseform.

*   **Anwendungsfälle:**
    *   Runde Akzente, Anzeigen oder weiche UI-Bereiche erstellen.
    *   Thematische UI-Dekorationen ohne Texturdatei bauen.
*   **Hauptfunktionen:**
    *   Unterstützt Farbe, Unschärfe und einen konfigurierbaren Rundungs-/Exponentenwert.

## Splash-Text
Eine Nachbildung von Minecrafts ikonischem gelbem, hüpfendem Splash-Text vom Titelbildschirm.

*   **Anwendungsfälle:**
    *   Den Vanilla-Splash-Text durch eigene Nachrichten ersetzen.
    *   Eine auffällige, animierte Nachricht zu jedem Menü hinzufügen.
*   **Hauptfunktionen:**
    *   **Inhaltsquellen:** Kann die standardmäßigen Vanilla-Splashes, eine Liste direkt eingegebener benutzerdefinierter Texte oder Text aus einer lokalen Datei verwenden.
    *   **Anpassung:** Du kannst den Hüpf-Effekt ein- oder ausschalten und die Farbe, Skalierung, Drehung und den Schatten des Textes anpassen.

## Spieler-Entity
Rendert ein Spielermodell im Menü.

*   **Anwendungsfälle:**
    *   Den aktuellen Charakter des Spielers im Hauptmenü anzeigen.
    *   Einen Teamauswahl- oder Klassen-Vorschaubildschirm erstellen.
    *   Einen Bereich „Profil“ erstellen, der Skin und Namen des Spielers zeigt.
*   **Hauptfunktionen:**
    *   **Dynamisches Aussehen:** Kann Skin, Umhang und Namen des aktuellen Spielers übernehmen. Siehe [Spielerköpfe](./player-heads).
    *   **Benutzerdefinierte Posen:** Bietet feinkörnige Kontrolle über die Rotation von Kopf, Körper, Armen und Beinen. Kopf und Körper können außerdem dem Mauszeiger folgen.
    *   **Attribute:** Kann als Baby, geduckt oder mit schlankem Modell dargestellt werden.

## Browser
Ein Element, das eine Live-Webseite innerhalb des Spiels rendert.

Für dieses Element muss das Mod **MCEF (Minecraft Chromium Embedded Framework)** installiert und funktionsfähig sein!

Du kannst MCEF von den offiziellen Projektseiten auf [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) und [Modrinth](https://modrinth.com/mod/mcef) herunterladen.

Für neuere Minecraft-Versionen (1.21.5+) stellen die offiziellen MCEF-Projekte keine Builds bereit, es gibt jedoch einen Fork mit Builds für die neuesten Minecraft-Versionen, den du [hier](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) und [hier](https://modrinth.com/mod/mcef-keksuccino) (Modrinth) findest. Dieser Fork wird von Keksuccino gepflegt, damit Builds für die neuesten Minecraft-Versionen so schnell wie möglich verfügbar sind.

*   **Anwendungsfälle:**
    *   Eine Live-Dynmap eines Servers anzeigen.
    *   Einen YouTube-Videoplayer einbetten.
    *   Ein Wiki oder eine Dokumentationsseite direkt im Spiel anzeigen.
*   **Hauptfunktionen:**
    *   **Interaktivität:** Kann vollständig interaktiv gemacht werden, sodass Benutzer Links anklicken, scrollen und tippen können.
    *   **Mediensteuerung:** Bietet Optionen zum Stummschalten von Medien, zum Wiederholen von Videos und zum Ausblenden von Videosteuerungen auf der geladenen Seite.

### Lokale HTML-Dateien laden
Das Browser-Element kann lokale HTML-Dokumente aus `<game-directory>/config/fancymenu/assets/` laden.

Um eine lokale HTML-Datei zu laden, beginne deine URL mit `file:///`, gefolgt vom KURZEN Dateipfad, zum Beispiel `/config/fancymenu/assets/cool_changelog.html`, wodurch es so aussieht: `file:///config/fancymenu/assets/cool_changelog.html`.

Unter **Linux** verwende den Platzhalter [**Absoluter Datei-/Ordnerpfad**](./placeholders#absolute-filefolder-path-absolute_path) anstelle eines instance-spezifischen absoluten Pfads: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Der kurze Linux-Pfad muss, wie im Beispiel gezeigt, mit `/` beginnen.

## Element-Animator
Ein leistungsstarkes Werkzeug zum Erstellen komplexer Animationen auf Basis von Keyframes. Es kann Position, Größe und Ankerpunkt eines oder mehrerer anderer Elemente animieren.

*   **Anwendungsfälle:**
    *   Elemente ins Bild hinein- oder herausgleiten lassen.
    *   Panels oder Benachrichtigungen in der Größe ändern.
    *   Positionsversätze und Ankerübergänge animieren.
*   **Hauptfunktionen:**
    *   **Keyframe-Editor:** Ein eigener Editor zum Hinzufügen, Bearbeiten und Anordnen von Keyframes auf einer Zeitleiste.
    *   **Mehrfachziel:** Ein einzelner Animator kann mehrere „Ziel“-Elemente gleichzeitig steuern.
    *   **Steuerung:** Animationen können in Schleife laufen. Du kannst außerdem wählen, nur Position oder Größe zu animieren.
    *   **Timing-Offsets:** Ziel-Elemente können individuelle oder zufällige Start-Timing-Offsets verwenden.
    *   Siehe [Element-Animator](./element-animator) für Einrichtung und Keyframe-Bearbeitung.

## Ticker
Ein unsichtbares Element, das in regelmäßigen Abständen (bei jedem „Tick“) eine Liste von Aktionen ausführt.

> [!NOTE]
> Für Hintergrundautomatisierung solltest du [Scheduler](./schedulers) in Betracht ziehen. Scheduler sind global und können unabhängig von einem bestimmten Bildschirm ausgeführt werden.

*   **Anwendungsfälle:**
    *   Regelmäßig den Online-Status eines Servers prüfen und ein Textelement aktualisieren.
    *   Einen Countdown-Timer erstellen, der ein Textlabel aktualisiert.
    *   Ein Skript wiederholt ausführen, um benutzerdefinierte Verhaltensweisen zu erzeugen.
*   **Hauptfunktionen:**
    *   **Zeitsteuerung:** Du kannst die Verzögerung zwischen Ticks in Millisekunden festlegen.
    *   **Tick-Modi:** Kann so eingestellt werden, dass es kontinuierlich tickt, nur einmal pro Spielsitzung oder jedes Mal, wenn das Menü geladen wird.
    *   **Asynchron:** Kann seine [Aktionen](./action-scripts) getrennt ausführen, wobei einige Aktionen nicht ausgeführt werden können, solange diese Option aktiviert ist.

## Audio
Ein unsichtbares Element, das Audiodateien abspielt. Es kann eine Playlist mit Titeln verwalten und bietet verschiedene Wiedergabesteuerungen.

*   **Anwendungsfälle:**
    *   Benutzerdefinierte Hintergrundmusik zu einem Menü hinzufügen.
    *   Einen Musikplayer mit Schaltflächen zur Steuerung der Wiedergabe erstellen (nächster/vorheriger Titel, Lautstärke).
    *   Atmosphärische Soundlandschaften abspielen.
*   **Hauptfunktionen:**
    *   **Playlist:** Kann mehrere Audiospuren verwalten.
    *   **Wiedergabemodi:** Kann Titel in Reihenfolge abspielen oder zufällig mischen (mit Unterstützung für Titelgewichtung, damit manche Titel häufiger vorkommen als andere).
    *   **Steuerung:** Unterstützt Schleifen, Lautstärkeanpassung und Auswahl des Soundkanals. Siehe [Menü-Hintergrundmusik](./background-music).

## Musiksteuerung
Ein unsichtbares Element, mit dem die standardmäßige Minecraft-Musikwiedergabe in einem bestimmten Menü gesteuert wird.

*   **Anwendungsfälle:**
    *   Die standardmäßige Menümusik auf einem Bildschirm deaktivieren, auf dem du deine eigene Musik über ein [**Audio**-Element](#audio) abspielen möchtest.
    *   Verhindern, dass Musik aus der Spielwelt weiterläuft, wenn im Spiel ein Menü geöffnet wird.
*   **Hauptfunktionen:**
    *   Separate Umschalter zur Steuerung von vanilla „Menümusik“ und „Weltmusik“.

## Fortschrittsbalken
Ein anpassbarer Balken, der einen numerischen Wert visuell darstellt.

*   **Anwendungsfälle:**
    *   Ein Ladebalken, der den Ladefortschritt der Welt mit `{"placeholder":"world_load_progress"}` verfolgt.
    *   Visuelle Balken für Gesundheit, Hunger oder Erfahrung in einem In-Game-HUD.
    *   Eine Lautstärkeanzeige, die von einem [**Slider**-Element](#slider) gesteuert wird.
*   **Hauptfunktionen:**
    *   **Dynamischer Wert:** Der Fortschrittswert (0–100 oder 0,0–1,0) wird über ein Textfeld gesetzt, das [Platzhalter](./placeholders) unterstützt.
    *   **Aussehen:** Richtung des Balkens (hoch, runter, links, rechts), Farben, Texturen und Nine-Slicing für Balken-/Hintergrundtexturen sind alle anpassbar.
    *   **Animation:** Verfügt über eine sanfte Füllanimation, damit Fortschrittsänderungen weniger sprunghaft wirken.
    *   **Fortschrittsbasierter Element-Anker:** Wenn ein anderes Element den Fortschrittsbalken als seinen **Element**-Anker verwendet, aktiviere **Fortschritt für Element-Anker verwenden**, um diesen Anker an die aktuelle Kante des gefüllten Bereichs zu verschieben. Verankerte Elemente bewegen sich dann mit dem Fortschritt des Balkens mit, anstatt an den statischen Begrenzungen des Fortschrittsbalkens zu bleiben.

## Zieher
Ein unsichtbares Element, das der Benutzer anklicken und ziehen kann, um es zu bewegen. Andere Elemente können daran verankert werden, um verschiebbare Widgets zu erstellen.

*   **Anwendungsfälle:**
    *   Eine verschiebbare Uhr oder ein Informationsfeld erstellen.
    *   Benutzern erlauben, die Position von UI-Elementen nach ihren Vorlieben anzupassen.
*   **Hauptfunktionen:**
    *   **Optionale Persistenz:** Aktiviere **Benutzer-Drag-Versatz speichern**, um die gezogene Position des Benutzers über das erneute Öffnen des Bildschirms und Spielneustarts hinweg beizubehalten. Deaktiviere die Option, um den Versatz zurückzusetzen.
    *   **Ankerpunkt:** Dient als beweglicher Anker für andere Elemente und ist ein wichtiger Bestandteil von [Elemente positionieren](./positioning-elements).

## Cursor
Ein unsichtbares Element, das den standardmäßigen Systemcursor durch ein benutzerdefiniertes Bild ersetzt, wenn ein Layout aktiv ist.

*   **Anwendungsfälle:**
    *   Eine vollständig thematisierte Benutzeroberfläche erstellen, die zur Ästhetik deines Modpacks passt.
*   **Hauptfunktionen:**
    *   **Benutzerdefinierte Textur:** Verwende jedes beliebige Bild für deinen Cursor.
    *   **Hotspot:** Legt den exakten Bildpixel fest, der als Klickpunkt verwendet wird. Siehe [Benutzerdefinierter Cursor](./custom-cursor).
