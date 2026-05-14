---
title: Elemente
description: 'Alles, was du über die Elementtypen von FancyMenu wissen musst.'
---

# Elemente

Elemente sind die Bausteine deiner benutzerdefinierten Layouts in FancyMenu. Du kannst sie jedem beliebigen Layout hinzufügen, um Informationen anzuzeigen, Interaktivität hinzuzufügen oder beeindruckende visuelle Effekte zu erstellen.

# Elemente zu einem Layout hinzufügen

Du kannst im **Layout-Editor** ein neues Element zu deinem Layout hinzufügen.

1.  **Rechtsklicke** auf den Hintergrund des Editors, um das Kontextmenü zu öffnen.
2.  Fahre mit der Maus über **Neues Element**.
3.  Eine Liste aller verfügbaren Elementtypen erscheint. Klicke auf den Typ, den du hinzufügen möchtest.

![add_element](https://github.com/Keksuccino/FancyMenu/assets/35544624/865a66c5-76a6-404d-b746-d57802b1c12f)

Sobald ein Element hinzugefügt wurde, kannst du es verschieben, in der Größe anpassen und bearbeiten, indem du **rechtsklickst**, um sein spezielles Kontextmenü zu öffnen. Weitere Informationen zum Anordnen von Elementen findest du auf den Seiten [Elemente positionieren](https://docs.fancymenu.net/en/positioning-elements) und [Element-Identifikatoren](https://docs.fancymenu.net/en/element-identifiers).

# Elemente im Detail

Die folgende Liste enthält die meisten, wenn nicht sogar alle, in FancyMenu verfügbaren Elemente. Die Liste kann aufgrund von FancyMenu-Updates manchmal etwas veraltet sein.

## Button
Ein anklickbarer Button, der eine Vielzahl von Aktionen ausführen kann. Dies ist eines der leistungsstärksten und vielseitigsten Elemente zum Erstellen interaktiver Menüs.

*   **Anwendungsfälle:**
    *   Einen „Discord beitreten“- oder „Website besuchen“-Button erstellen.
    *   Einen Quick-Join-Button für einen bestimmten Server hinzufügen.
    *   Benutzerdefinierte Navigation zwischen verschiedenen Menüs aufbauen.
    *   Buttons erstellen, die andere Layouts ein- oder ausschalten.
*   **Hauptfunktionen:**
    *   **Aktionen:** Kann eine Folge von Aktionen ausführen, z. B. eine URL öffnen, einem Server beitreten, einen Chatbefehl senden, die Funktion eines anderen Buttons nachahmen, Variablen steuern und vieles mehr. Mehr dazu in der Dokumentation zu [Action Scripts](https://docs.fancymenu.net/en/action-scripts).
    *   **Benutzerdefiniertes Aussehen:** Vollständig anpassbare Texturen für normale, Hover- und inaktive Zustände. Unterstützt transparente Hintergründe, Nine-Slicing, benutzerdefinierte Label-Farben, Hover-Label-Farben, Label-Skalierung, Schattentoggles für Labels und Button-Icon-Texturen.
    *   **Sounds:** Benutzerdefinierte Klick-, Hover- und Unhover-Sounds.
    *   **Vorlagenmodus:** Kann als Vorlage dienen, um sein Aussehen und seine Eigenschaften auf alle anderen Vanilla- oder modifizierten Buttons im Menü anzuwenden und so ein einheitliches Design zu gewährleisten. Mehr dazu auf der Seite [Button- & Slider-Vorlagen](https://docs.fancymenu.net/en/button-slider-templates).

## Slider
Ein Schieberegler, den Benutzer ziehen können, um einen Wert aus einer Liste oder einem Bereich auszuwählen. Er kann Aktionen ausführen, sobald sich sein Wert ändert.

*   **Anwendungsfälle:**
    *   Eine benutzerdefinierte Lautstärkeregelung erstellen.
    *   Einen Slider verwenden, um zwischen verschiedenen Themes oder Hintergrundbildern zu wechseln (mit dem Typ „Liste“).
    *   Eine bestimmte Minecraft-Option anpassen, z. B. Helligkeit oder Renderdistanz.
*   **Hauptfunktionen:**
    *   **Typen:** Kann eine `Werteliste` sein (z. B. „Leicht“, „Normal“, „Schwer“), ein `Ganzzahlbereich` (z. B. 1–100) oder ein `Dezimalbereich` (z. B. 0.0–1.0).
    *   **Dynamische Aktionen:** Führt Aktionen bei Wertänderungen aus. Der aktuelle Wert des Sliders kann innerhalb seiner Aktionen verwendet werden, um dynamische Aufgaben auszuführen, die mit [Variablen](https://docs.fancymenu.net/en/variables) genutzt werden können.
    *   **Anpassung:** Das Label des Sliders kann seinen aktuellen Wert dynamisch anzeigen. Der Griff und die Hintergrundtexturen sind vollständig anpassbar, einschließlich transparenter Hintergründe, Optionen für Label-Farbe/-Skalierung, Schattentoggles für Text und benutzerdefinierte Klick-/Unhover-Sounds.

## Checkbox
Eine Standard-Checkbox, die ein- oder ausgeschaltet werden kann. Sie kann Aktionen ausführen, wenn ihr Zustand geändert wird.

*   **Anwendungsfälle:**
    *   Eine Checkbox „Ich stimme den Regeln zu“.
    *   Eine Einstellung, um eine bestimmte Funktion in deinem benutzerdefinierten Menü zu aktivieren oder zu deaktivieren.
    *   Ein Layout oder eine Variable ein- oder ausschalten.
*   **Hauptfunktionen:**
    *   **Aktionen beim Umschalten:** Führt [Action Scripts](https://docs.fancymenu.net/en/action-scripts) aus, wenn sich ihr Zustand ändert. Der aktuelle Zustand (`true` oder `false`) kann innerhalb ihrer Aktionen verwendet werden.
    *   **Variablenmodus:** Kann direkt mit einer FancyMenu-Variable verknüpft werden, sodass der Checkbox-Zustand aus dieser Variable gelesen und in sie geschrieben wird.
    *   **Benutzerdefiniertes Aussehen:** Unterstützt benutzerdefinierte Texturen für den Hintergrund (im normalen, Hover- und inaktiven Zustand) sowie das Häkchen selbst.

## Text-Eingabefeld
Ein Feld, in das Benutzer Text eingeben können. Sein Inhalt kann mit einer FancyMenu-Variable verknüpft werden, sodass du Benutzereingaben erfassen und verwenden kannst.

*   **Anwendungsfälle:**
    *   Ein Eingabefeld für die „Server-IP“, das mit einem „Server beitreten“-Button funktioniert.
    *   Ein Feld zur Eingabe des Spielernamens für eine benutzerdefinierte Skin-Vorschau.
    *   Eine einfache Login-ähnliche Oberfläche erstellen.
*   **Hauptfunktionen:**
    *   **Variablenverknüpfung:** Der vom Benutzer eingegebene Text wird in einer angegebenen [Variable](https://docs.fancymenu.net/en/variables) gespeichert.
    *   **Eingabevalidierung:** Kann so konfiguriert werden, dass nur bestimmte Zeichentypen akzeptiert werden, z. B. Zahlen, URLs oder reiner Text.
    *   **Maximale Länge:** Du kannst eine maximale Zeichenanzahl für die Eingabe festlegen.
    *   **Aussehen und Sounds:** Unterstützt benutzerdefinierte Hintergrundfarbe, Rahmenfarben, Rahmenrundung, Textfarbe, Hinweis-/Platzhaltertext, Hinweisfarbe, Hover-Sounds, Unhover-Sounds und Klick-Sounds.

## Tooltip
Ein Textfeld, das so konfiguriert werden kann, dass es an einer bestimmten Position erscheint oder dem Mauszeiger folgt. Seine Sichtbarkeit wird typischerweise durch [Bedingungen (Ladeanforderungen)](https://docs.fancymenu.net/en/conditions) gesteuert.

*   **Anwendungsfälle:**
    *   Detaillierte Informationen anzeigen, wenn ein Benutzer über einen Button oder ein Bild fährt.
    *   Kontextabhängige Hilfetipps erstellen, die unter bestimmten Bedingungen erscheinen.
    *   Dynamische Informationen (z. B. Serverstatus) neben dem Cursor anzeigen.
*   **Hauptfunktionen:**
    *   **Mausverfolgung:** Kann so eingestellt werden, dass es dem Mauszeiger folgt.
    *   **Markdown-Unterstützung:** Der Tooltip-Inhalt unterstützt vollständige Markdown-Formatierung.
    *   **Benutzerdefinierter Hintergrund:** Der Hintergrund kann eine Volltonfarbe oder eine benutzerdefinierte, nine-geslicte Textur für ein vollständig thematisiertes Aussehen sein.

## Item
Zeigt ein einzelnes Minecraft-Item an, entweder aus Vanilla oder aus einem Mod.

*   **Anwendungsfälle:**
    *   Items als Symbole für Buttons oder Menüauswahlen verwenden.
    *   Eine GUI zur Shop- oder Kit-Auswahl erstellen.
    *   Das gehaltene Item oder die Rüstung eines Spielers anzeigen.
*   **Hauptfunktionen:**
    *   **Benutzerdefinierte Daten:** Du kannst den Namen, die Lore, die Anzahl, den Verzauberungsglanz und sogar benutzerdefinierte NBT-Daten des Items festlegen. Mehr zur Verwendung von NBT findest du in der Dokumentation zum [NBT-Daten-Platzhalter](https://docs.fancymenu.net/en/nbt-data-placeholder).
    *   **Tooltip-Anzeige:** Kann so konfiguriert werden, dass der Standard-Tooltip des Items beim Darüberfahren angezeigt wird.

## Block-/Item-JSON-Modell
Rendert ein Block- oder Item-JSON-Modell aus Minecraft-Ressourcen oder externen Quellen.

*   **Anwendungsfälle:**
    *   Ein 3D-Resourcepack-Modell in einem Menü anzeigen.
    *   Item-/Block-Vorschauen mit benutzerdefinierten Texturen zeigen.
    *   Modellbasierte dekorative UI-Elemente erstellen.
*   **Hauptfunktionen:**
    *   **Modellquelle:** Kann Modell-JSON aus Minecraft-Ressourcen oder externen Quellen laden.
    *   **Texturüberschreibungen:** Unterstützt das Festlegen einer benutzerdefinierten Textur.
    *   **Rendering-Steuerung:** Enthält Rotations- und Lichtsteuerungen.

## Bild
Zeigt ein statisches Bild aus einer lokalen Datei, einer Web-URL oder einer Minecraft-Ressourcenadresse an.

*   **Anwendungsfälle:**
    *   Ein Serverlogo oder Modpack-Branding hinzufügen.
    *   Dekorative Ränder oder UI-Rahmen erstellen.
    *   Bilder als Teil eines komplexeren UI-Designs verwenden.
*   **Hauptfunktionen:**
    *   **Nine-Slicing:** Ermöglicht die Verwendung des Bildes als skalierbaren Rahmen oder Panel, ohne die Ecken zu verzerren. Mehr dazu auf der Seite [Nine-Slicing & Tiling](https://docs.fancymenu.net/en/nine-slicing-and-tiling).
    *   **Textur-Wiederholung:** Das Bild kann gekachelt werden, um den Bereich des Elements auszufüllen.
    *   **Einfärbung:** Du kannst dem Bild eine Farbtönung hinzufügen.
    *   **Abgerundete Ecken:** Bilder ohne Nine-Slicing und ohne Wiederholung können abgerundete Ecken haben.
    *   **Parallax-Effekt:** Kann so konfiguriert werden, dass es sich mit der Maus leicht bewegt und so einen 3D-Effekt erzeugt. Siehe die Seite [Parallax-Effekt](https://docs.fancymenu.net/en/parallax) für mehr Informationen.

## Text
Ein äußerst vielseitiges Element zur Anzeige von Text. Es kann für alles verwendet werden, von einzeiligen Beschriftungen bis hin zu mehrseitigen, scrollbareren Dokumenten.

*   **Anwendungsfälle:**
    *   Serverregeln, Patch Notes oder Willkommensnachrichten anzeigen.
    *   Dynamische Info-Panel mit [Platzhaltern](https://docs.fancymenu.net/en/placeholders) erstellen, z. B. „Willkommen, `{"placeholder":"playername"}`!“.
    *   Beschriftungen und Beschreibungen für deine UI hinzufügen.
*   **Hauptfunktionen:**
    *   **Inhaltsquellen:** Text kann direkt eingegeben, aus einer lokalen Datei geladen oder von einer Web-URL abgerufen werden.
    *   **Markdown-Unterstützung:** Unterstützt eine große Auswahl an Markdown für reichhaltige Textformatierung, einschließlich Überschriften, Listen, Codeblöcken und Tabellen. Das Aussehen von Markdown-Elementen ist vollständig anpassbar. Weitere Informationen findest du auf der Seite [Textformatierung](https://docs.fancymenu.net/en/text-formatting).
    *   **Scrollen:** Wird automatisch scrollbar, wenn der Inhalt größer ist als der Bereich des Elements. Scrollleisten können angepasst oder deaktiviert werden.
    *   **Gestaltung:** Volle Kontrolle über Textfarbe, Skalierung, Ausrichtung, Schatten und Zeilenabstand.

## Video
Spielt eine Videodatei ab. Das ist perfekt für cineastische Intros oder dekorative, sich wiederholende Hintergründe.

> Das neue native Video-Element in FancyMenu 3.9.0 erfordert **Watermedia V3** und **Watermedia Binaries V3**. Das alte Element **Video [MCEF]** ist veraltet.
{.is-warning}

*   **Anwendungsfälle:**
    *   Ein animierter Modpack- oder Server-Trailer.
    *   Ein sich wiederholendes, atmosphärisches Video, das deinem Menü Leben einhaucht.
    *   Ein Tutorial-Video im Spiel.
*   **Hauptfunktionen:**
    *   **Quellen:** Unterstützt sowohl lokale Videodateien als auch Web-URLs. Siehe die Seite [Videos (MP4)](https://docs.fancymenu.net/en/video) für Details.
    *   **Wiedergabesteuerung:** Kann so eingestellt werden, dass es automatisch in einer Schleife läuft. Lautstärke, Soundkanal und das Verhalten zur Beibehaltung des Seitenverhältnisses sind anpassbar.
    *   **Interaktive Steuerung:** Wiedergabe, Suchposition und Lautstärke des Videos können über Button-Aktionen gesteuert werden.

## GLSL-Shader
Rendert einen benutzerdefinierten GLSL-Shader innerhalb eines Elements.

*   **Anwendungsfälle:**
    *   Animierte Shader-Panels.
    *   Prozedurale visuelle Effekte.
    *   Shadertoy-ähnliche Menüeﬀekte, die auf ein Element-Rechteck zugeschnitten sind.
*   **Hauptfunktionen:**
    *   **Shader-Laufzeit:** Unterstützt Single-Pass- und Multi-Pass-Shader.
    *   **Shadertoy-Unterstützung:** Kann Shadertoy-ähnliche `mainImage`-Shader verwenden.
    *   **Uniforms:** Stellt FancyMenu- und Eingabe-Uniforms bereit. Siehe die Seite [GLSL-Shader-API](https://docs.fancymenu.net/en/glsl-shader-api) für Details.

## Slideshow
Zeigt eine Abfolge von Bildern an. Die Konfiguration der Slideshow (Bilder, Timing, Übergänge) erfolgt in einer separaten `.properties`-Datei im Verzeichnis `/config/fancymenu/assets/slideshows/`.

*   **Anwendungsfälle:**
    *   Eine rotierende Galerie von In-Game-Screenshots.
    *   Wichtige Funktionen eines Modpacks präsentieren.
    *   Ein dynamischer Hintergrund, der zwischen verschiedenen Szenen wechselt.
*   **Hauptfunktionen:**
    *   Lädt vorkonfigurierte Slideshows. Siehe die Dokumentation zu [Slideshows](https://docs.fancymenu.net/en/slideshows) für Einrichtungsanweisungen.
    *   Kann so eingestellt werden, dass das Seitenverhältnis der Bilder beibehalten wird.

## Rechteckform
Ein einfaches, einfarbiges Rechteck.

*   **Anwendungsfälle:**
    *   Einen halbtransparenten Hintergrund hinter Text erstellen, um die Lesbarkeit zu verbessern.
    *   Einfache UI-Panels und Trennlinien entwerfen.
    *   Als farbiger Platzhalter während des Layout-Designs.
*   **Hauptfunktionen:**
    *   Unterstützt HEX-RGBA-Farben, abgerundete Ecken und optionalen Blur, sodass die Form als einfaches Panel, Tönung oder verschwommener Hintergrund dienen kann.

## Kreisform
Eine einfache, einfarbige Kreis-/Ellipse-Form.

*   **Anwendungsfälle:**
    *   Runde Akzente, Anzeigen oder weiche UI-Bereiche erstellen.
    *   Themenbezogene UI-Dekorationen ohne Texturdatei aufbauen.
*   **Hauptfunktionen:**
    *   Funktioniert ähnlich wie das Element Rechteckform und unterstützt visuelle Anpassungen im Stil von Farbe/Blur.

## Splash-Text
Eine Nachbildung von Minecrafts ikonischem gelbem, springendem Splash-Text auf dem Titelbildschirm.

*   **Anwendungsfälle:**
    *   Den Vanilla-Splash-Text durch eigene benutzerdefinierte Nachrichten ersetzen.
    *   Eine auffällige, animierte Nachricht zu jedem Menü hinzufügen.
*   **Hauptfunktionen:**
    *   **Inhaltsquellen:** Kann die standardmäßigen Vanilla-Splashes, eine Liste direkt eingegebener benutzerdefinierter Texte oder Text aus einer lokalen Datei verwenden.
    *   **Anpassung:** Du kannst den Springeffekt ein- oder ausschalten und Farbe, Skalierung, Rotation und Schatten des Textes anpassen.

## Spieler-Entität
Rendert ein Spielermodell im Menü.

*   **Anwendungsfälle:**
    *   Den aktuellen Charakter des Spielers im Hauptmenü anzeigen.
    *   Einen Team-Auswahl- oder Klassen-Vorschau-Bildschirm erstellen.
    *   Einen Bereich „Profil“, der Skin und Namen des Spielers zeigt.
*   **Hauptfunktionen:**
    *   **Dynamisches Aussehen:** Kann so konfiguriert werden, dass Skin, Cape und Name des aktuellen Spielers automatisch übernommen werden. Mehr dazu im Leitfaden [Spielerköpfe](https://docs.fancymenu.net/en/player-heads).
    *   **Benutzerdefinierte Posen:** Bietet feingranulare Kontrolle über die Rotation von Kopf, Körper, Armen und Beinen. Kopf und Körper können außerdem dem Mauszeiger folgen.
    *   **Attribute:** Kann als Baby, in geduckter Haltung oder mit einem schlanken Modell dargestellt werden.

## Browser
Ein Element, das eine Live-Webseite innerhalb des Spiels rendert.

Dieses Element erfordert, dass das Mod **MCEF (Minecraft Chromium Embedded Framework)** installiert ist und funktioniert!

Du kannst MCEF von den offiziellen Projektseiten auf [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mcef) und [Modrinth](https://modrinth.com/mod/mcef) herunterladen.

Für neuere Minecraft-Versionen (1.21.5+) bieten die offiziellen MCEF-Projekte keine Builds an, aber es gibt einen Fork mit Builds für die neuesten Minecraft-Versionen, den du [hier](https://www.curseforge.com/minecraft/mc-mods/mcef-keksuccino) (CurseForge) und [hier](https://modrinth.com/mod/mcef-keksuccino) (Modrinth) findest. Dieser Fork wird von Keksuccino gepflegt, um Builds für die neuesten Minecraft-Versionen so schnell wie möglich bereitzustellen.

*   **Anwendungsfälle:**
    *   Einen live Dynmap-Server anzeigen.
    *   Einen YouTube-Videoplayer einbetten.
    *   Eine Wiki- oder Dokumentationsseite direkt im Spiel anzeigen.
*   **Hauptfunktionen:**
    *   **Interaktivität:** Kann vollständig interaktiv gemacht werden, sodass Benutzer Links anklicken, scrollen und tippen können.
    *   **Mediensteuerung:** Bietet Optionen zum Stummschalten von Medien, zum Wiederholen von Videos und zum Ausblenden von Videosteuerungen auf der geladenen Seite.

### Lokale HTML-Dateien laden
Mit dem Browser-Element kannst du lokale HTML-Dokumente in `/config/fancymenu/assets/` laden! Das bedeutet, dass du lokal gerenderten Browser-Inhalt für schick aussehende Changelogs und mehr anzeigen kannst.

Um eine lokale HTML-Datei zu laden, beginne deine URL mit `file:///`, gefolgt vom KURZEN Dateipfad, zum Beispiel `/config/fancymenu/assets/cool_changelog.html`, sodass es so aussieht: `file:///config/fancymenu/assets/cool_changelog.html`.

Unter **Linux** musst du den absoluten Dateipfad angeben. Da ein fest codierter absoluter Pfad jedoch dein Layout zerstören würde, musst du einen Platzhalter den kurzen Pfad dynamisch in einen absoluten umwandeln lassen: `file:///{"placeholder":"absolute_path","values":{"short_path":"/config/fancymenu/assets/cool_changelog.html"}}`.

Es ist SUPER WICHTIG, dass du den kurzen Pfad unter Linux mit `/` beginnst, wie im obigen Beispiel. Ohne das funktioniert es nicht.

## Element-Animator
Ein leistungsstarkes Werkzeug zum Erstellen komplexer Animationen auf Basis von Keyframes. Es kann die Position, Größe und den Ankerpunkt eines oder mehrerer anderer Elemente animieren.

*   **Anwendungsfälle:**
    *   Eine ausgefeilte Intro-Animation erstellen, bei der Menüe­lemente hinein- oder herausgleiten.
    *   Dekorative Elemente pulsieren, rotieren oder sich entlang eines Pfads bewegen lassen.
    *   Eine Benachrichtigung animieren, die auftaucht und dann wieder verschwindet.
*   **Hauptfunktionen:**
    *   **Keyframe-Editor:** Ein spezieller Editor zum Hinzufügen, Bearbeiten und Anordnen von Keyframes auf einer Timeline.
    *   **Multi-Ziel:** Ein einzelner Animator kann mehrere „Ziel“-Elemente gleichzeitig steuern.
    *   **Steuerung:** Animationen können in einer Schleife abgespielt werden. Du kannst außerdem wählen, ob nur Position oder nur Größe animiert werden soll.
    *   **Zeitversätze:** Ziel-Elemente können individuelle oder zufällige Start-Zeitversätze verwenden.
    *   **[Mehr über den Element-Animator erfahren.](https://docs.fancymenu.net/en/element-animator)**

## Ticker
Ein unsichtbares Element, das in regelmäßigen Abständen (bei jedem „Tick“) eine Liste von Aktionen ausführt.

> Für neue Hintergrundautomatisierung in FancyMenu 3.9.0+ solltest du [Scheduler](https://docs.fancymenu.net/en/schedulers) in Betracht ziehen. Scheduler sind global, einfacher zu organisieren und können unabhängig von einem bestimmten Bildschirm weiterlaufen.
{.is-info}

*   **Anwendungsfälle:**
    *   Regelmäßig den Online-Status eines Servers prüfen und ein Textelement aktualisieren.
    *   Einen Countdown-Timer erstellen, der eine Textbeschriftung aktualisiert.
    *   Ein Skript wiederholt ausführen, um benutzerdefinierte Verhaltensweisen zu erzeugen.
*   **Hauptfunktionen:**
    *   **Zeitsteuerung:** Du kannst die Verzögerung zwischen den Ticks in Millisekunden festlegen.
    *   **Tick-Modi:** Kann so eingestellt werden, dass es fortlaufend tickt, nur einmal pro Spielsitzung oder jedes Mal, wenn das Menü geladen wird.
    *   **Asynchron:** Kann seine [Aktionen](https://docs.fancymenu.net/en/action-scripts) in einem separaten Thread ausführen, um die Spielleistung nicht zu beeinträchtigen, auch wenn einige Aktionen auf diese Weise nicht ausgeführt werden können.

## Audio
Ein unsichtbares Element, das Audiodateien abspielt. Es kann eine Playlist von Titeln verwalten und bietet verschiedene Wiedergabesteuerungen.

*   **Anwendungsfälle:**
    *   Benutzerdefinierte Hintergrundmusik zu einem Menü hinzufügen.
    *   Einen Musikplayer mit Buttons zur Steuerung der Wiedergabe erstellen (nächster/vorheriger Titel, Lautstärke).
    *   Atmosphärische Klanglandschaften abspielen.
*   **Hauptfunktionen:**
    *   **Playlist:** Kann mehrere Audiotitel verwalten.
    *   **Wiedergabemodi:** Kann Titel in Reihenfolge abspielen oder zufällig mischen (mit Unterstützung für Gewichtung, sodass manche Titel häufiger vorkommen als andere).
    *   **Steuerung:** Unterstützt Wiederholung, Lautstärkeanpassung und kann einem bestimmten Soundkanal zugewiesen werden (z. B. Master, Musik). Weitere Informationen findest du auf der Seite [Menü-Hintergrundmusik](https://docs.fancymenu.net/en/background-music).

## Musik-Controller
Ein unsichtbares Element, mit dem sich die standardmäßige Minecraft-Musikwiedergabe innerhalb eines bestimmten Menüs steuern lässt.

*   **Anwendungsfälle:**
    *   Die standardmäßige Menümusik auf einem Bildschirm deaktivieren, auf dem du deine eigene Musik über ein **Audio**-Element abspielen möchtest.
    *   Verhindern, dass In-World-Musik weiterläuft, wenn im Spiel ein Menü geöffnet wird.
*   **Hauptfunktionen:**
    *   Separate Schalter zur Steuerung der Vanilla-„Menümusik“ und der „Weltenmusik“.

## Fortschrittsbalken
Ein anpassbarer Balken, der einen numerischen Wert visuell darstellt.

*   **Anwendungsfälle:**
    *   Eine Ladeanzeige, die den Ladefortschritt der Welt mit `{"placeholder":"world_load_progress"}` verfolgt.
    *   Visuelle Lebens-, Hunger- oder Erfahrungsbalken für ein In-Game-HUD.
    *   Eine Lautstärkeanzeige, die von einem **Slider**-Element gesteuert wird.
*   **Hauptfunktionen:**
    *   **Dynamischer Wert:** Der Fortschrittswert (0–100 oder 0.0–1.0) wird über ein Textfeld festgelegt, das [Platzhalter](https://docs.fancymenu.net/en/placeholders) unterstützt.
    *   **Aussehen:** Richtung des Balkens (oben, unten, links, rechts), Farben, Texturen und Nine-Slicing für Balken-/Hintergrundtexturen sind vollständig anpassbar.
    *   **Animation:** Bietet eine sanfte Füllanimation, damit Fortschrittsänderungen weniger abrupt wirken.

## Dragger
Ein unsichtbares Element, das der Benutzer anklicken und ziehen kann, um es zu bewegen. Andere Elemente können daran verankert werden, um verschiebbare Widgets zu erstellen.

*   **Anwendungsfälle:**
    *   Eine verschiebbare Uhr oder ein Informationspanel erstellen.
    *   Benutzern erlauben, die Position von UI-Elementen nach ihren Vorlieben anzupassen.
*   **Hauptfunktionen:**
    *   **Persistente Position:** Der gezogene Versatz wird gespeichert, sodass das Element dort bleibt, wo der Benutzer es zuletzt abgelegt hat, auch nach einem Neustart des Spiels.
    *   **Ankerpunkt:** Dient als beweglicher Anker für andere Elemente, was ein wichtiger Teil von [Elemente positionieren](https://docs.fancymenu.net/en/positioning-elements) ist.

## Cursor
Ein unsichtbares Element, das den standardmäßigen Systemcursor durch ein benutzerdefiniertes Bild ersetzt, wenn ein Layout aktiv ist.

*   **Anwendungsfälle:**
    *   Eine vollständig thematisierte UI erstellen, die zur Ästhetik deines Modpacks passt.
*   **Hauptfunktionen:**
    *   **Benutzerdefinierte Textur:** Verwende jedes beliebige Bild für deinen Cursor.
    *   **Hotspot:** Du kannst den exakten Pixel im Bild festlegen, der als „Klickpunkt“ dient. Mehr dazu im Leitfaden [Benutzerdefinierter Cursor](https://docs.fancymenu.net/en/custom-cursor).
