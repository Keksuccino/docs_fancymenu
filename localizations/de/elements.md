---
title: Elemente
description: 'Alles, was du über die Elementtypen von FancyMenu wissen musst.'
---
# Elemente

Elemente sind die Bausteine deiner benutzerdefinierten Layouts in FancyMenu. Du kannst sie zu jedem Layout hinzufügen, um Informationen anzuzeigen, Interaktivität hinzuzufügen oder beeindruckende visuelle Effekte zu erzeugen.

# Elemente zu einem Layout hinzufügen

Du kannst im **Layout-Editor** ein neues Element zu deinem Layout hinzufügen.

1.  **Rechtsklicke** auf den Hintergrund des Editors, um das Kontextmenü zu öffnen.
2.  Bewege den Mauszeiger über **Neues Element**.
3.  Es erscheint eine Liste aller verfügbaren Elementtypen. Klicke auf den gewünschten Typ.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Sobald ein Element hinzugefügt wurde, kannst du es verschieben, in der Größe ändern und anpassen, indem du es **rechtsklickst**, um sein spezielles Kontextmenü zu öffnen. Mehr dazu, wie du Elemente anordnest, findest du unter [Elemente positionieren](./positioning-elements) und [Element-Identifikatoren](./element-identifiers).

# Elemente im Detail

Dieser Abschnitt listet die in FancyMenu enthaltenen Elemente auf. Verwende [Ebenen und Gruppen](./layers-and-groups), um ihre Render-Reihenfolge zu organisieren.

## Button
Ein anklickbarer Button, der eine Vielzahl von Aktionen ausführen kann. Dies ist eines der leistungsstärksten und vielseitigsten Elemente zum Erstellen interaktiver Menüs.

*   **Anwendungsfälle:**
    *   Einen "Discord beitreten"- oder "Website besuchen"-Button erstellen.
    *   Einen Schnellbeitritts-Button für einen bestimmten Server hinzufügen.
    *   Benutzerdefinierte Navigation zwischen verschiedenen Menüs erstellen.
    *   Buttons erstellen, die andere Layouts ein- oder ausschalten.
*   **Wichtige Funktionen:**
    *   **Aktionen:** Kann eine Reihe von [Aktionen](./action-scripts) ausführen, z. B. eine URL öffnen, einem Server beitreten, einen Chat-Befehl senden, die Funktion eines anderen Buttons nachahmen oder Variablen steuern.
    *   **Benutzerdefiniertes Aussehen:** Vollständig anpassbare Texturen für normale, hover- und inaktive Zustände. Unterstützt transparente Hintergründe, Nine-Slicing, benutzerdefinierte Label-Farben, Hover-Label-Farben, Label-Skalierung, Schatten-Umschalter für Labels und Button-Icon-Texturen.
    *   **Sounds:** Benutzerdefinierte Klick-, Hover- und Unhover-Sounds.
    *   **Vorlagenmodus:** Kann sein Aussehen und seine Eigenschaften auf andere Vanilla- oder modifizierte Buttons im Menü anwenden. Siehe [Button- & Slider-Vorlagen](./button-slider-templates).
    *   **Automatisierte Klicks auf Vanilla-/Mod-Widgets:** Vorhandene Vanilla- und Mod-Widgets haben die Eigenschaft **Automatisierte Klicks**, mit der ihr ursprüngliches Klickverhalten beim Laden des Bildschirms eine festgelegte Anzahl von Malen ausgelöst werden kann. Siehe [Vanilla-Elemente](./vanilla-elements#automated-clicks) für Details.

## Slider
Ein Schieberegler, den Benutzer ziehen können, um einen Wert aus einer Liste oder einem Bereich auszuwählen. Er kann Aktionen ausführen, sobald sich sein Wert ändert.

*   **Anwendungsfälle:**
    *   Eine benutzerdefinierte Lautstärkeregelung erstellen.
    *   Ein Slider zum Wechseln zwischen verschiedenen Themes oder Hintergrundbildern (mit dem Typ "Liste").
    *   Eine bestimmte Minecraft-Option anpassen, z. B. Helligkeit oder Renderdistanz.
*   **Wichtige Funktionen:**
    *   **Typen:** Kann eine `Werteliste` (z. B. "Einfach", "Normal", "Schwer"), ein `Ganzzahlbereich` (z. B. 1–100) oder ein `Dezimalbereich` (z. B. 0,0–1,0) sein.
    *   **Dynamische Aktionen:** Führt Aktionen aus, wenn sich sein Wert ändert. Der aktuelle Wert kann mit [Variablen](./variables) verwendet werden.
    *   **Anpassung:** Das Label des Sliders kann seinen aktuellen Wert dynamisch anzeigen. Der Griff und die Hintergrundtexturen sind vollständig anpassbar, einschließlich transparenter Hintergründe, Optionen für Label-Farbe/-Skalierung, Umschalter für Textschatten sowie benutzerdefinierte Klick-/Unhover-Sounds.

## Checkbox
Eine Standard-Checkbox, die ein- oder ausgeschaltet werden kann. Sie kann beim Umschalten Aktionen ausführen.

*   **Anwendungsfälle:**
    *   Eine Checkbox "Ich stimme den Regeln zu".
    *   Eine Einstellung zum Aktivieren oder Deaktivieren einer bestimmten Funktion in deinem benutzerdefinierten Menü.
    *   Ein Layout oder eine Variable ein-/ausschalten.
*   **Wichtige Funktionen:**
    *   **Aktionen beim Umschalten:** Führt [Action Scripts](./action-scripts) aus, wenn sich ihr Zustand ändert. Der aktuelle Zustand (`true` oder `false`) steht den Aktionen zur Verfügung.
    *   **Variablenmodus:** Kann direkt mit einer FancyMenu-Variable verknüpft werden, sodass der Zustand der Checkbox aus dieser Variable gelesen und in sie geschrieben wird.
    *   **Persistenter Zustand:** Wenn der Variablenmodus deaktiviert ist, speichert die Checkbox ihren Zustand automatisch anhand ihrer Element-ID und stellt ihn nach einem Neustart des Spiels wieder her. Diese Zustände werden in `<game-directory>/checkbox_states.json` gespeichert. Im Variablenmodus ist stattdessen die verknüpfte FancyMenu-Variable die Zustandsquelle der Checkbox.
    *   **Benutzerdefiniertes Aussehen:** Unterstützt benutzerdefinierte Texturen für den Hintergrund (in normalen, Hover- und inaktiven Zuständen) sowie für das Häkchen selbst.

## Text Input Field
Ein Feld, in das Benutzer Text eingeben können. Sein Inhalt kann mit einer FancyMenu-Variable verknüpft werden, sodass du Benutzereingaben erfassen und verwenden kannst.

*   **Anwendungsfälle:**
    *   Ein "Server-IP"-Eingabefeld, das mit einem "Server beitreten"-Button funktioniert.
    *   Ein Feld zur Eingabe des Spielernamens für eine benutzerdefinierte Skin-Vorschau.
    *   Eine einfache login-ähnliche Oberfläche erstellen.
*   **Wichtige Funktionen:**
    *   **Variablenverknüpfung:** Speichert den eingegebenen Text in einer angegebenen [Variable](./variables).
    *   **Eingabevalidierung:** Kann so konfiguriert werden, dass nur bestimmte Zeichentypen akzeptiert werden, z. B. Zahlen, URLs oder Klartext.
    *   **Maximale Länge:** Du kannst ein maximales Zeichenlimit für die Eingabe festlegen.
    *   **Aussehen und Sounds:** Unterstützt benutzerdefinierte Hintergrundfarbe, Rahmenfarben, Rahmenrundung, Textfarbe, Hinweis-/Platzhaltertext, Hinweisfarbe, Hover-Sounds, Unhover-Sounds und Klick-Sounds.

## Tooltip
Eine Textbox, die an einer festen Position erscheinen oder dem Mauszeiger folgen kann. Ihre Sichtbarkeit wird normalerweise über [Ladeanforderungen](./conditions) gesteuert.

*   **Anwendungsfälle:**
    *   Detaillierte Informationen anzeigen, wenn ein Benutzer über einen Button oder ein Bild fährt.
    *   Kontextabhängige Hilfetipps erstellen, die unter bestimmten Bedingungen erscheinen.
    *   Dynamische Informationen (z. B. Serverstatus) neben dem Mauszeiger anzeigen.
*   **Wichtige Funktionen:**
    *   **Mausverfolgung:** Kann so eingestellt werden, dass es dem Mauszeiger folgt.
    *   **Markdown-Unterstützung:** Der Tooltip-Inhalt unterstützt vollständige Markdown-Formatierung.
    *   **Benutzerdefinierter Hintergrund:** Der Hintergrund kann eine Vollfarbe oder eine benutzerdefinierte Nine-Sliced-Textur für ein vollständig abgestimmtes Erscheinungsbild sein.

## Item
Zeigt ein einzelnes Minecraft-Item an, entweder aus Vanilla oder aus einem Mod.

*   **Anwendungsfälle:**
    *   Items als Symbole für Buttons oder Menüauswahlen verwenden.
    *   Eine GUI zur Auswahl von Shop- oder Kit-Inhalten erstellen.
    *   Das gehaltene Item oder die Rüstung eines Spielers anzeigen.
*   **Wichtige Funktionen:**
    *   **Benutzerdefinierte Daten:** Unterstützt einen benutzerdefinierten Namen, Lore, Anzahl, Verzauberungsglanz und NBT-Daten. Siehe den [NBT-Daten-Platzhalter](./nbt-data-placeholder).
    *   **Tooltip-Anzeige:** Kann so konfiguriert werden, dass der Standard-Tooltip des Items beim Überfahren angezeigt wird.

## Block/Item JSON Model
Rendert ein Block- oder Item-JSON-Modell aus Minecraft-Ressourcen oder externen Quellen.

*   **Anwendungsfälle:**
    *   Ein 3D-Ressourcenpaket-Modell in einem Menü anzeigen.
    *   Item-/Block-Vorschauen mit benutzerdefinierten Texturen anzeigen.
    *   Modellbasierte dekorative UI-Elemente erstellen.
*   **Wichtige Funktionen:**
    *   **Modellquelle:** Kann Modell-JSON aus Minecraft-Ressourcen oder externen Quellen laden.
    *   **Texturüberschreibungen:** Unterstützt das Festlegen einer benutzerdefinierten Textur.
    *   **Render-Steuerung:** Modellversatz, Skalierung, Rotation um drei Achsen, transparente Darstellung und die GUI-Transformation des Modells.
    *   **Beleuchtung:** Zwei konfigurierbare Lichter mit unabhängigen Farbton- und Rotationssteuerungen.

## Image
Zeigt ein statisches Bild aus einer lokalen Datei, einer Web-URL oder einer Minecraft-Ressourcenadresse an.

*   **Anwendungsfälle:**
    *   Ein Server-Logo oder eine Modpack-Marke hinzufügen.
    *   Dekorative Rahmen oder UI-Rahmen erstellen.
    *   Bilder als Teil eines komplexeren UI-Designs verwenden.
*   **Wichtige Funktionen:**
    *   **Nine-Slicing:** Skaliert Ränder oder Panels, ohne die Ecken zu verzerren. Siehe [Nine-Slicing & Tiling](./nine-slicing-and-tiling).
    *   **Textur-Wiederholung:** Das Bild kann gekachelt werden, um die Fläche des Elements zu füllen.
    *   **Einfärbung:** Du kannst dem Bild eine Farbtönung hinzufügen.
    *   **Abgerundete Ecken:** Nicht-nine-slicete und nicht wiederholte Bilder können abgerundete Ecken haben.
    *   **Parallax-Effekt:** Bewegt sich mit der Maus, um visuelle Tiefe zu erzeugen. Siehe [Parallax-Effekt](./parallax).

## Text
Ein äußerst vielseitiges Element zur Anzeige von Text. Es kann für alles verwendet werden, von einzeiligen Beschriftungen bis hin zu mehrseitigen, scrollbareren Dokumenten.

*   **Anwendungsfälle:**
    *   Serverregeln, Patchnotes oder Willkommensnachrichten anzeigen.
    *   Dynamische Infofelder mit [Platzhaltern](./placeholders) erstellen, z. B. `Welcome, {"placeholder":"playername"}!`.
    *   Beschriftungen und Beschreibungen zu deiner UI hinzufügen.
*   **Wichtige Funktionen:**
    *   **Inhaltsquellen:** Text kann direkt eingegeben, aus einer lokalen Datei geladen oder von einer Web-URL abgerufen werden.
    *   **Markdown-Unterstützung:** Unterstützt Überschriften, Listen, Codeblöcke, Tabellen und andere Markdown-Formatierungen. Siehe [Textformatierung](./text-formatting).
    *   **Scrollen:** Wird automatisch scrollbar, wenn der Inhalt größer ist als die Fläche des Elements. Scrollleisten können angepasst oder deaktiviert werden.
    *   **Formatierung:** Volle Kontrolle über Textfarbe, Skalierung, Ausrichtung, Schatten und Zeilenabstand.

## Video
Spielt eine Videodatei ab. Das ist perfekt für filmische Intros oder dekorative Loop-Hintergründe.

> [!WARNING]
> Das native Video-Element erfordert **Watermedia V3** und **Watermedia Binaries V3**. Das alte Element **Video [Rinku]** ist veraltet.

*   **Anwendungsfälle:**
    *   Ein animierter Modpack- oder Server-Trailer.
    *   Ein sich wiederholendes, atmosphärisches Video, um dein Menü lebendiger zu machen.
    *   Ein Tutorial-Video im Spiel.
*   **Wichtige Funktionen:**
    *   **Quellen:** Unterstützt lokale Videodateien und Web-URLs. Siehe [Videos](./video).
    *   **Wiedergabesteuerung:** Kann so eingestellt werden, dass es automatisch in einer Schleife läuft. Lautstärke, Soundkanal und das Verhalten zur Beibehaltung des Seitenverhältnisses sind anpassbar.
    *   **Interaktive Steuerung:** Wiedergabe, Suchposition und Lautstärke des Videos können über Button-Aktionen gesteuert werden.

## GLSL Shader
Rendert einen benutzerdefinierten GLSL-Shader innerhalb eines Elements.

*   **Anwendungsfälle:**
    *   Animierte Shader-Panels.
    *   Prozedurale visuelle Effekte.
    *   Shadertoy-ähnliche Menüeffekte, auf ein Element-Rechteck zugeschnitten.
*   **Wichtige Funktionen:**
    *   **Shader-Laufzeit:** Unterstützt Single-Pass- und Multipass-Shader.
    *   **Shadertoy-Unterstützung:** Kann Shadertoy-ähnliche `mainImage`-Shader verwenden.
    *   **Uniforms:** Stellt FancyMenu- und Eingabe-Uniforms bereit. Siehe die [GLSL-Shader-API](./glsl-shader-api).

## Slideshow
Zeigt eine Abfolge von Bildern an. Die Bilder und die Konfigurationsdatei `properties.txt` befinden sich im eigenen Unterverzeichnis der Slideshow unter `<game-directory>/config/fancymenu/slideshows/`.

*   **Anwendungsfälle:**
    *   Eine rotierende Galerie von Screenshots aus dem Spiel.
    *   Wichtige Funktionen eines Modpacks präsentieren.
    *   Einen dynamischen Hintergrund, der zwischen verschiedenen Szenen wechselt.
*   **Wichtige Funktionen:**
    *   Lädt vorkonfigurierte [Slideshows](./slideshows).
    *   Kann so eingestellt werden, dass das Seitenverhältnis der Bilder beibehalten wird.

## Rectangle Shape
Ein einfaches, einfarbiges Rechteck.

*   **Anwendungsfälle:**
    *   Einen halbtransparenten Hintergrund hinter Text erstellen, um die Lesbarkeit zu verbessern.
    *   Einfache UI-Panels und Trennlinien gestalten.
    *   Als farbiger Platzhalter während des Layout-Designs.
*   **Wichtige Funktionen:**
    *   Unterstützt HEX-RGBA-Farben, abgerundete Ecken und optionalen Blur, sodass die Form als einfaches Panel, Tönung oder Unschärfe-Hintergrund verwendet werden kann.

## Circle Shape
Eine einfache, einfarbige Kreis-/Ellipsenform.

*   **Anwendungsfälle:**
    *   Runde Akzente, Anzeigen oder weiche UI-Bereiche erstellen.
    *   Thematische UI-Dekorationen ohne Texturdatei bauen.
*   **Wichtige Funktionen:**
    *   Unterstützt Farbe, Blur und einen konfigurierbaren Rundheits-/Exponentenwert.

## Splash Text
Eine Nachbildung von Minecrafts ikonischem gelbem, hüpfendem Splash-Text auf dem Titelbildschirm.

*   **Anwendungsfälle:**
    *   Den Vanilla-Splash-Text durch eigene benutzerdefinierte Nachrichten ersetzen.
    *   Eine auffällige, animierte Nachricht zu jedem Menü hinzufügen.
*   **Wichtige Funktionen:**
    *   **Inhaltsquellen:** Kann die standardmäßigen Vanilla-Splashes, eine Liste benutzerdefinierter direkt eingegebener Texte oder Text aus einer lokalen Datei verwenden.
    *   **Anpassung:** Du kannst den Hüpf-Effekt umschalten und Farbe, Skalierung, Rotation und Schatten des Textes anpassen.

## Player Entity
Rendert ein Spielermodell im Menü.

*   **Anwendungsfälle:**
    *   Den aktuellen Spielercharakter im Hauptmenü anzeigen.
    *   Einen Team-Auswahl- oder Klassen-Vorschaubildschirm erstellen.
    *   Einen "Profil"-Bereich, der Skin und Namen des Spielers zeigt.
*   **Wichtige Funktionen:**
    *   **Dynamisches Aussehen:** Kann den Skin, Umhang und Namen des aktuellen Spielers übernehmen. Siehe [Player Heads](./player-heads).
    *   **Benutzerdefinierte Posen:** Bietet feingranulare Steuerung über die Rotation von Kopf, Körper, Armen und Beinen. Kopf und Körper können außerdem so eingestellt werden, dass sie dem Mauszeiger folgen.
    *   **Eigenschaften:** Kann als Baby, geduckt oder mit einem Slim-Modell angezeigt werden.

## Browser
Ein Element, das eine Live-Webseite innerhalb des Spiels rendert.

Dieses Element erfordert, dass das **[Rinku](https://modrinth.com/mod/rinku)**-Mod installiert und funktionsfähig ist!

Du kannst Rinku von den offiziellen Projektseiten auf [CurseForge](https://www.curseforge.com/minecraft/mc-mods/rinku) und [Modrinth](https://modrinth.com/mod/rinku) herunterladen.

*   **Anwendungsfälle:**
    *   Eine Live-Dynmap eines Servers anzeigen.
    *   Einen YouTube-Videoplayer einbetten.
    *   Ein Wiki oder eine Dokumentationsseite direkt im Spiel anzeigen.
*   **Wichtige Funktionen:**
    *   **Interaktivität:** Kann vollständig interaktiv gemacht werden, sodass Benutzer Links anklicken, scrollen und tippen können.
    *   **Mediensteuerung:** Bietet Optionen zum Stummschalten von Medien, zum Wiederholen von Videos und zum Ausblenden von Videosteuerungen auf der geladenen Seite.

### Lokale HTML-Dateien laden
Das Browser-Element kann lokale HTML-Dokumente aus `<game-directory>/config/fancymenu/assets/` laden.

Um eine lokale HTML-Datei zu laden, beginne deine URL mit `file:///`, gefolgt vom SHORT-Dateipfad, zum Beispiel `/config/fancymenu/assets/cool_changelog.html`, wodurch sie so aussieht: `file:///config/fancymenu/assets/cool_changelog.html`.

Unter **Linux** verwende den Platzhalter [**Absolute File/Folder Path**](./placeholders#absolute-filefolder-path-absolute_path) anstelle eines hart kodierten instanzspezifischen absoluten Pfads: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Der Linux-Short-Pfad muss, wie im Beispiel gezeigt, mit `/` beginnen.

## Element Animator
Ein leistungsstarkes Werkzeug zum Erstellen komplexer Animationen auf Basis von Keyframes. Es kann die Position, Größe und den Ankerpunkt eines oder mehrerer anderer Elemente animieren.

*   **Anwendungsfälle:**
    *   Elemente ins Bild hinein- oder aus dem Bild herausgleiten lassen.
    *   Panels oder Benachrichtigungen in der Größe ändern.
    *   Positionsversätze und Ankerübergänge animieren.
*   **Wichtige Funktionen:**
    *   **Keyframe-Editor:** Ein eigener Editor zum Hinzufügen, Bearbeiten und Sequenzieren von Keyframes auf einer Zeitleiste.
    *   **Mehrfachziel:** Ein einzelner Animator kann mehrere "Ziel"-Elemente gleichzeitig steuern.
    *   **Steuerung:** Animationen können auf Wiederholung eingestellt werden. Du kannst außerdem wählen, nur Position oder Größe zu animieren.
    *   **Zeitversätze:** Ziel-Elemente können individuelle oder zufällige Start-Zeitversätze verwenden.
    *   Siehe [Element Animator](./element-animator) für Einrichtung und Keyframe-Bearbeitung.

## Ticker
Ein unsichtbares Element, das in regelmäßigen Abständen (bei jedem "Tick") eine Liste von Aktionen ausführt.

> [!NOTE]
> Für Hintergrundautomatisierung solltest du [Scheduler](./schedulers) in Betracht ziehen. Scheduler sind global und können unabhängig von einem bestimmten Bildschirm laufen.

*   **Anwendungsfälle:**
    *   Regelmäßig den Online-Status eines Servers prüfen und ein Textelement aktualisieren.
    *   Einen Countdown-Timer erstellen, der ein Textlabel aktualisiert.
    *   Ein Skript wiederholt ausführen, um benutzerdefinierte Verhaltensweisen zu erzeugen.
*   **Wichtige Funktionen:**
    *   **Zeitsteuerung:** Du kannst die Verzögerung zwischen Ticks in Millisekunden festlegen.
    *   **Tick-Modi:** Kann so eingestellt werden, dass es fortlaufend tickt, nur einmal pro Spielsitzung oder einmal jedes Mal, wenn das Menü geladen wird.
    *   **Asynchron:** Kann seine [Aktionen](./action-scripts) getrennt ausführen, obwohl einige Aktionen bei aktivierter Option nicht ausgeführt werden können.

## Audio
Ein unsichtbares Element, das Audiodateien abspielt. Es kann eine Playlist von Titeln verwalten und bietet verschiedene Wiedergabesteuerungen.

*   **Anwendungsfälle:**
    *   Benutzerdefinierte Hintergrundmusik zu einem Menü hinzufügen.
    *   Einen Musikplayer erstellen, mit Buttons zur Steuerung der Wiedergabe (nächster/vorheriger Titel, Lautstärke).
    *   Atmosphärische Klanglandschaften abspielen.
*   **Wichtige Funktionen:**
    *   **Playlist:** Kann mehrere Audiospuren verwalten.
    *   **Wiedergabemodi:** Kann Titel der Reihe nach abspielen oder mischen (mit Unterstützung für Titelgewichtung, damit manche Titel häufiger vorkommen als andere).
    *   **Steuerung:** Unterstützt Wiederholung, Lautstärkeregelung und Auswahl des Soundkanals. Siehe [Menü-Hintergrundmusik](./background-music).

## Music Controller
Ein unsichtbares Element, das verwendet wird, um die standardmäßige Minecraft-Musikwiedergabe innerhalb eines bestimmten Menüs zu steuern.

*   **Anwendungsfälle:**
    *   Die standardmäßige Menümusik auf einem Bildschirm deaktivieren, auf dem du deine eigene benutzerdefinierte Musik über ein [**Audio**-Element](#audio) abspielen möchtest.
    *   Verhindern, dass Musik aus der Spielwelt weiter abgespielt wird, wenn im Spiel ein Menü geöffnet wird.
*   **Wichtige Funktionen:**
    *   Separate Umschalter zur Steuerung von Vanilla-"Menümusik" und "Weltmusik".

## Progress Bar
Eine anpassbare Leiste, die einen numerischen Wert visuell darstellt.

*   **Anwendungsfälle:**
    *   Eine Ladeleiste, die den Weltladefortschritt mit `{"placeholder":"world_load_progress"}` verfolgt.
    *   Visuelle Lebens-, Hunger- oder Erfahrungsbalken für ein In-Game-HUD.
    *   Eine Lautstärkeanzeige, die von einem [**Slider**-Element](#slider) gesteuert wird.
*   **Wichtige Funktionen:**
    *   **Dynamischer Wert:** Der Fortschrittswert (0–100 oder 0,0–1,0) wird über ein Textfeld gesetzt, das [Platzhalter](./placeholders) unterstützt.
    *   **Aussehen:** Richtung der Leiste (oben, unten, links, rechts), Farben, Texturen und Nine-Slicing für Balken-/Hintergrundtexturen sind alle anpassbar.
    *   **Animation:** Bietet eine sanfte Füllanimation, damit Fortschrittsänderungen weniger abrupt wirken.
    *   **Fortschrittsbasierter Element-Anker:** Wenn ein anderes Element die Fortschrittsleiste als seinen **Element**-Anker verwendet, aktiviere **Progress für Element-Anker verwenden**, um diesen Anker an die aktuelle Kante des gefüllten Bereichs zu verschieben. Verankerte Elemente bewegen sich dann mit dem Fortschritt der Leiste statt an ihren statischen Grenzen zu bleiben.

## Dragger
Ein unsichtbares Element, auf das der Benutzer klicken und das er ziehen kann, um es zu verschieben. Andere Elemente können daran verankert werden, um verschiebbare Widgets zu erstellen.

*   **Anwendungsfälle:**
    *   Eine verschiebbare Uhr oder ein Informationspanel erstellen.
    *   Benutzern erlauben, die Position von UI-Elementen nach ihren Vorlieben anzupassen.
*   **Wichtige Funktionen:**
    *   **Optionale Persistenz:** Aktiviere **Benutzer-Drag-Versatz speichern**, um die vom Benutzer gezogene Position über das Öffnen des Bildschirms und Spielneustarts hinweg beizubehalten. Deaktiviere es, um den Versatz zurückzusetzen.
    *   **Ankerpunkt:** Dient als beweglicher Anker für andere Elemente, was ein wichtiger Teil von [Elemente positionieren](./positioning-elements) ist.

## Cursor
Ein unsichtbares Element, das den standardmäßigen Systemcursor durch ein benutzerdefiniertes Bild ersetzt, wenn ein Layout aktiv ist.

*   **Anwendungsfälle:**
    *   Eine vollständig thematisierte UI erstellen, die zur Ästhetik deines Modpacks passt.
*   **Wichtige Funktionen:**
    *   **Benutzerdefinierte Textur:** Verwende jedes beliebige Bild für deinen Cursor.
    *   **Hotspot:** Legt den exakten Bildpixel fest, der als Klickpunkt verwendet wird. Siehe [Benutzerdefinierter Cursor](./custom-cursor).
