---
title: Daten-Speicherorte
description: >-
  Wo FancyMenu Layouts, Ressourcen, Konfiguration und persistenten
  Laufzeitstatus speichert.
---

# Daten-Speicherorte

`<game-directory>` bezeichnet den aktiven Minecraft-Instanzordner, der sich von `.minecraft` unterscheiden kann.

Verzeichnisse und Dateien werden in der Regel erst erstellt, nachdem die zugehörige Funktion initialisiert oder verwendet wurde. Schließe Minecraft, bevor du generierte Statusdateien manuell bearbeitest, und sichere deine Daten vor dem Migrieren oder Zurücksetzen.

# Layouts, Ressourcen und Konfiguration

Einige Einträge sind erstellte Konfigurationen oder Assets; andere sind Zustände, die FancyMenu zur Laufzeit aktualisiert.

| System / Funktion | Datei oder Verzeichnis |
| --- | --- |
| Anpassbare Bildschirme | `<game-directory>/config/fancymenu/customizablemenus.txt` |
| [Benutzerdefinierte GUIs](./custom-guis) und Regeln für Bildschirm-Überschreibungen | `<game-directory>/config/fancymenu/custom_gui_screens.txt` |
| Layouts | `<game-directory>/config/fancymenu/customization/` |
| [Lokale Assets](./resources#local-resources) | `<game-directory>/config/fancymenu/assets/` |
| [Benutzerdefinierte Lokalisierungsdateien](./localization#fancymenu-custom-localization-files) | `<game-directory>/config/fancymenu/custom_locals/` |
| [Panoramen](./panoramas) | `<game-directory>/config/fancymenu/panoramas/` |
| [Diashows](./slideshows) | `<game-directory>/config/fancymenu/slideshows/` |
| [FancyMenu-Variablen](./variables) | `<game-directory>/config/fancymenu/user_variables.db` |
| Metadaten des Controllers für das [Video-Element](./elements#video) | `<game-directory>/config/fancymenu/video_element_controller_metas.json` |
| Metadaten des Controllers für das [Audio-Element](./elements#audio) | `<game-directory>/config/fancymenu/audio_element_controller_metas.json` |
| Server-Listener für [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_server_listeners.json` |
| Begrüßungsdaten für [FM Data](./fm-data) | `<game-directory>/config/fancymenu/fmdata_welcome_data.json` |
| [Listener](./listeners)-Instanzen und Aktionsskripte | `<game-directory>/config/fancymenu/listener_instances.txt` |
| [Scheduler](./schedulers) | `<game-directory>/config/fancymenu/scheduler_instances.txt` |

`customizablemenus.txt` wird von der Umschaltoption **Aktuelle Bildschirm-Anpassung** verwaltet und speichert konkrete Bildschirm-Klassen-IDs. Füge keine [Universal Layout](./universal-layouts)-IDs hinzu; FancyMenu ignoriert sie beim Laden der Datei.

Auf einem dedizierten Server liegen die beiden FM-Data-Dateien relativ zum Spielstammverzeichnis dieses Servers. Andere clientseitige Konfigurationen und Ressourcen gehören in die jeweilige Instanz jedes Spielers.

# Persistenter Laufzeitstatus

FancyMenu speichert zusätzliche generierte instanzbezogene Zustände außerhalb von `config/fancymenu/`. Nimm diese Pfade nur dann in ein Backup auf, wenn du den zugehörigen Benutzer-/Laufzeitstatus behalten möchtest; sie sind keine Layout-Definitionen oder Quell-Assets.

| System / Funktion | Datei oder Verzeichnis |
| --- | --- |
| Nicht-Variable Zustände von [Checkboxen](./elements#checkbox) | `<game-directory>/checkbox_states.json` |
| Positionen/Metadaten von [Dragger](./dragger)-Elementen | `<game-directory>/fancymenu_data/dragger_metas.json` |
| Letzter Weltstatus | `<game-directory>/fancymenu_data/last_world.fmdata` |
| Status von [Nahtlosem Weltladen](./seamless-world-loading) | `<game-directory>/fancymenu_data/seamless_world_loading/` |
| Speicherstände von Buddy-Pet und Leveling | `<game-directory>/fancymenu_data/buddy/` |
| Widget-Positionen und Sichtbarkeit des Layout-Editors | `<game-directory>/config/fancymenu/layout_editor/widgets/` |
| Marker zur Initialisierung der Standard-GUI-Skalierung | `<game-directory>/fancymenu_data/default_scale_set.fm` |

Buddy speichert den Haustier-Status sowie den Leveling-/Erfolgsstatus in separaten JSON-Dateien innerhalb seines Verzeichnisses. Jede Buddy-Overlay-Instanz verwendet ihr eigenes Dateipaar.

Die Widget-Dateien des Layout-Editors speichern die Position, Größe, Sichtbarkeit, den aufgeklappten Zustand und die Andockseite jedes Widgets. Wenn du `default_scale_set.fm` löschst, behandelt FancyMenu die konfigurierte Standard-GUI-Skalierung beim nächsten Start so, als wäre sie noch nicht angewendet worden.
