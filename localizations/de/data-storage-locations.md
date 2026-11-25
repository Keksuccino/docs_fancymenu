---
title: Datenspeicherorte
description: >-
  Wo FancyMenu Layouts, Ressourcen, Einstellungen und alles Weitere speichert
  und welche Dateien zu Profilen gehören.
sourceBlobSha: 30dd81ed90e08184e3063892870e3325d7d7c5cb
---

# Datenspeicherorte

FancyMenu speichert alles in zwei Ordnern in deinem Spielverzeichnis. Das ist der Instanzordner deines Launchers, der sich vom Ordner `.minecraft` unterscheiden kann.

- `config/fancymenu/` enthält deine Konfiguration: Layouts, Ressourcen, Variablen, Einstellungen und mehr. Das ist das geladene [Profil](/profiles), deshalb wird dieser Ordner mit Modpacks ausgeliefert.
- `fancymenu_data/` enthält Daten dieser Spielinstanz, zum Beispiel Dragger-Positionen und Downloads. Dieser Ordner bleibt für alle Profile gleich.

**Menüleiste -> Werkzeuge -> FancyMenu-Verzeichnis öffnen** öffnet `config/fancymenu/`.

Die meisten Dateien und Ordner werden erst angezeigt, wenn du die jeweilige Funktion verwendest. Beende das Spiel, bevor du Dateien darin änderst oder löschst.

> [!TIP]
> Um diese Ordner für mehrere Instanzen gemeinsam zu verwenden, kannst du sie an einen anderen Ort verschieben und an ihrer Stelle einen symbolischen Link (unter Windows eine Verzeichnisverknüpfung) erstellen.

# Deine Konfiguration

Alles in `<game-directory>/config/fancymenu/`. Der gesamte Inhalt gehört zum geladenen [Profil](/profiles).

| Was | Wo |
| --- | --- |
| Layouts als `.txt`-Dateien, auch in Unterordnern | `customization/` |
| [Lokale Ressourcen](/resources#local-resources), etwa Bilder und Sounds | `assets/` |
| FancyMenus Einstellungen | `options.txt` |
| Bildschirme, für die **Aktuelle Bildschirm-Anpassung** aktiviert ist | `customizablemenus.txt` |
| [Benutzerdefinierte GUIs](/custom-guis) und die Bildschirme, die sie ersetzen | `custom_gui_screens.txt` |
| [Variablen](/variables) | `user_variables.db` |
| [Listener](/listeners) | `listener_instances.txt` |
| [Scheduler](/schedulers) | `scheduler_instances.txt` |
| [Panoramen](/panoramas) | `panoramas/` |
| [Diashows](/slideshows) | `slideshows/` |
| [Benutzerdefinierte lokale Übersetzungen](/localization#fancymenu-custom-localization-files) | `custom_locals/` |
| Themes für FancyMenus eigene Benutzeroberfläche (**Menüleiste -> Anpassung -> Einstellungen -> FancyMenus Benutzeroberfläche -> UI-Theme**) | `ui_themes/` |
| Zustände von [Checkbox-Elementen](/elements#checkbox), die keine Variable verwenden | `checkbox_states.json` |
| Lautstärke und Pausenzustand, die Aktionen für [Videoelemente](/video) festgelegt haben | `video_element_controller_metas.json` |
| Lautstärke, die Aktionen für [Audioelemente](/elements#audio) festgelegt haben | `audio_element_controller_metas.json` |
| Ein- und Aus-Zustand, den Aktionen für [Element-Animatoren](/element-animator) festgelegt haben | `animation_controller_states.json` |
| Bildschirme, für die **Inhalt des Scrollbereichs des aktuellen Bildschirms verfügbar machen** aktiviert ist (siehe [Anpassung scrollbarer Bildschirme](/customizing-scrollable-screens)) | `normalized_scroll_screens.json` |
| [FM-Data](/fm-data)-Server-Listener | `fmdata_server_listeners.json` |
| [FM-Data](/fm-data)-Begrüßungsdaten | `fmdata_welcome_data.json` |
| Position, Größe und Sichtbarkeit der Widgets im Layout-Editor | `layout_editor/widgets/` |
| Name, Symbol und Details des geladenen Profils | `profile.json` und `profile_icon.png` |
| Alle anderen [Profile](/profiles#where-profiles-are-stored) | `profiles/` |
| Welche Aktualisierungen älterer Dateien FancyMenu bereits durchgeführt hat | `legacy_checklist.txt` |

`customizablemenus.txt` führt Bildschirme anhand ihres Java-Klassennamens auf. Kurze [Bildschirmkennungen](/screen-identifiers) wie `title_screen` werden darin ausgelassen.

Auf einem dedizierten Server verwendet FancyMenu nur die beiden [FM-Data](/fm-data)-Dateien im Ordner `config/fancymenu/` des Servers.

# Instanzdaten

Alles in `<game-directory>/fancymenu_data/`. Dieser Ordner ist nicht Teil der Profile und bleibt deshalb beim Wechsel zwischen ihnen erhalten.

| Was | Wo |
| --- | --- |
| Positionen von [Dragger-Elementen](/dragger) | `dragger_metas.json` |
| Die zuletzt verwendete Welt oder der zuletzt verwendete Server für die Aktion **Letzte Welt/letzten Server betreten** und den Platzhalter **Letzte Welt oder letzter Server** | `last_world.fmdata` |
| Screenshots von [Nahtlosem Weltladen](/seamless-world-loading) | `seamless_world_loading/` |
| Speicherstände von [Buddy](/decoration-overlays#buddy), zwei Dateien pro Buddy-Overlay | `buddy/` |
| Dateien für [KI-Export](/export-for-ai) | `ai_exports/` |
| Deine bevorzugten Aktionen in der Aktionsauswahl | `action_favorites.json` |
| Lautstärke der Audio- und Videovorschauen in Dateiauswahldialogen | `browser_audio_settings.json` und `browser_video_settings.json` |
| Das Einzelbild, das ein [Videohintergrund](/video) während der Pause anzeigt | `video_thumbnails/` |
| FFmpeg, das FancyMenu für den [AFMA Creator](/animations#fma-and-afma) herunterlädt | `ffmpeg_cache/` |
| Ein Hinweis darauf, dass FancyMenu die [**Standard-GUI-Skalierung**](/global-customizations) bereits festgelegt hat | `default_scale_set.fm` |
| Temporäre Dateien, die bei jedem Spielstart gelöscht werden | `fancymenu_temp/` |

- FancyMenu legt die **Standard-GUI-Skalierung** nur einmal fest. Lösche `default_scale_set.fm`, damit die Skalierung beim nächsten Start erneut festgelegt wird.
- Screenshots für Nahtloses Weltladen zeigen alles, was in der Welt auf dem Bildschirm zu sehen war. Lösche sie bei geschlossenem Spiel, wenn du sie nicht behalten möchtest.

# Dateien älterer Versionen

Ältere FancyMenu-Versionen speicherten einige Dateien an anderen Orten. FancyMenu übernimmt sie beim nächsten Spielstart:

- `checkbox_states.json` und `normalized_scroll_screens.json` werden aus dem Spielverzeichnis selbst nach `config/fancymenu/` verschoben.
- `dragger_metas.json` wird aus `config/fancymenu/` nach `fancymenu_data/` verschoben.
