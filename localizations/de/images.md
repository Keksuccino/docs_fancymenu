---
title: Bilder
description: Alles Wichtige über Bildressourcen in FancyMenu.
---
# Bilder

FancyMenu unterstützt Bildressourcen an vielen Stellen, zum Beispiel als Menü-Hintergründe, Schaltflächen-Texturen und vieles mehr.

Du kannst PNG-, JPEG-, GIF- und APNG-Bilddateien in FancyMenu verwenden. Für statische Bilder wird jedoch empfohlen, nach Möglichkeit PNG zu verwenden. Anstatt GIF und APNG für Animationen zu nutzen, solltest du besser [eine AFMA-Datei](/fma) verwenden. AFMA ist FancyMenus eigener Typ für animierte Bilder, da AFMAs wesentlich stärker optimiert sind als GIF/APNG, weniger RAM benötigen und die Leistung weniger beeinträchtigen.

# Bilder in unterstützte Formate konvertieren

Wenn du Bilder in eines der von FancyMenu unterstützten Formate konvertieren musst oder aus verschiedenen Gründen einfach von einem unterstützten Format in ein anderes konvertieren möchtest, findest du in der folgenden Liste einige Websites, die sich gut für die Online-Konvertierung von Bildern eignen, ohne dass du Software herunterladen musst.

## GIF zu APNG
Um ein GIF-Bild in ein APNG zu konvertieren, verwende diese Website: https://ezgif.com/gif-to-apng.

## APNG zu GIF
Für die Konvertierung eines APNG in ein GIF benötigst du Folgendes: https://ezgif.com/apng-to-gif.

## MP4 zu APNG
Wenn du eine kurze Videosequenz in ein APNG konvertieren musst, probiere diese Website aus: https://ezgif.com/video-to-apng

## PNG zu JPEG
Manchmal können JPEGs die Größe von Ressourcen verringern. In diesem Fall kann es sinnvoll sein, anstelle von PNG JPEG zu verwenden: https://www.freeconvert.com/png-to-jpeg. Beachte, dass JPEGs keine Transparenz unterstützen.

## JPEG zu PNG
Für den häufigen Fall einer JPEG-zu-PNG-Konvertierung kannst du diese Website verwenden: https://jpg2png.com/

## WebP zu PNG
WebP-Dateien werden von FancyMenu nicht unterstützt, daher musst du sie in PNG konvertieren: https://convertio.co/webp-png/

# Einschränkungen animierter Texturen

FancyMenu verwendet für optimierte Animationen sein eigenes [AFMA-Format](/fma). Dadurch können [AFMA-Dateien](/fma) viele Frames in hoher Auflösung enthalten. Bei älteren animierten Dateitypen wie GIF und APNG solltest du dich jedoch an die folgenden empfohlenen Grenzen halten, damit dein RAM nicht zu stark ausgelastet wird und die Leistung deines Spiels nicht zu sehr beeinträchtigt wird:

- Verwende pro Animation maximal **200 Frames**.
- Verwende für deine Frames eine maximale Auflösung von **1080p**.
- Du solltest insgesamt **1000 Frames für ALLE Animationen zusammen** nicht überschreiten. Denn selbst wenn du pro Animation nur 200 Frames verwendest, werden alle Frames in den Speicher geladen. Zu viele Animationen gleichzeitig können daher trotzdem deinen RAM auslasten.

> [!IMPORTANT]
> Diese Grenzen gelten NICHT für [AFMA-Dateien](/fma), da AFMAs nicht alle Frames in den Speicher laden und wesentlich stärker optimiert sind. Daher beeinträchtigen sie die Leistung nicht so stark wie ältere Animationstypen.
