---
title: Spieler-Entities
description: >-
  Zeige Spieler in deinen Menüs mit dem Element „Spieler-Entity“ – mit Skin,
  Name, Pose, Rüstung und mehr.
sourceBlobSha: b8f8d4340ca3a87e1c55c86f95f36786ab840644
---

# Spieler-Entities

Das Element „Spieler-Entity“ zeigt einen Spieler in 3D an – wie den eigenen Charakter des Spielers neben den Schaltflächen auf dem Titelbildschirm. Es kann die spielende Person darstellen, einen beliebigen anderen Spieler anzeigen oder als eigene Figur mit eigenem Skin, Umhang und Namen dienen.

<img width="800" alt="Fünf Spieler-Entities: ein echter Spieler mit Skin und Umhang, einer in verzauberter Diamantrüstung mit Schwert und Schild, einer in geduckter Haltung, einer winkend und ein Baby" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_showcase.png?raw=true">

> [!IMPORTANT]
> Für Minecraft 1.20.1 und neuer benötigen Spieler-Entities die Mod Fancy Entity Renderer ([CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer), [Modrinth](https://modrinth.com/mod/fancy-entity-renderer)). Ohne sie werden sie als roter Kasten angezeigt. Gibt es noch keinen Build für deine Minecraft-Version, können Spieler-Entities dort nicht angezeigt werden.

# Eine Spieler-Entity hinzufügen

Klicke mit der rechten Maustaste auf den Hintergrund des Editors und wähle **Neues Element -> Spieler-Entity**. Ziehe an den Griffen, um die Größe zu ändern. Die Größe des Spielers richtet sich nach der Höhe des Elements.

Alle folgenden Einstellungen findest du im Rechtsklickmenü des Elements.

# Wen sie anzeigt

- **Client-Spieler kopieren** zeigt die spielende Person mit ihrem Namen, Skin und Umhang an. Solange diese Option aktiviert ist, sind die Einstellungen für Name, Skin und Umhang gesperrt.
- **Spielername** kann ein beliebiger Name sein und muss keinem echten Spieler gehören. Die Einstellung unterstützt [Platzhalter](/placeholders).
- **Spielernamen anzeigen** zeigt das Namensschild über dem Kopf an. Ist **Namensschild-Rotation** deaktiviert, dreht sich das Namensschild nicht mit dem Spieler.

## Skin und Umhang

- **Skin automatisch laden** und **Umhang automatisch laden** laden den Skin und Umhang des Spielers mit dem eingestellten **Spielernamen**. Dafür ist eine Internetverbindung erforderlich.
- **Skin-Textur** und **Umhang-Textur** verwenden eigene Skin- und Umhangdateien, zum Beispiel einen Skin aus deinen [Ressourcen](/resources). Skins sind die üblichen Skin-Dateien von Minecraft.
- **Schmaler Skin** ist für Skins mit dünnen Armen gedacht, wie etwa Alex. **Skin automatisch laden** und **Client-Spieler kopieren** erkennen dies selbstständig.

# Pose und Bewegung

<img width="800" alt="Zwei Spieler-Entities blicken auf den Mauszeiger, während er sich bewegt: Die linke dreht nur den Kopf, die rechte dreht Kopf und Körper" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_follow_mouse.gif?raw=true">

- **Kopf folgt der Maus** und **Körper folgt der Maus** lassen den Spieler auf den Mauszeiger blicken. Bei neuen Spieler-Entities sind beide Optionen aktiviert.
- **Pose** legt die Körperhaltung fest: **Stehend**, **Duckend**, **Schlafend**, **Schwimmend**, **Sterbend** oder **Drehangriff**.
- **Körperbewegung** animiert die Pose.

## Entity-Pose

Über **Entity-Pose** öffnest du ein Fenster mit den X-, Y- und Z-Rotationswerten für **Kopf**, **Körper**, **linken Arm**, **rechten Arm**, **linkes Bein** und **rechtes Bein**. Die Werte reichen von `-180` bis `180`.

<img width="800" alt="Das Fenster „Entity-Pose“ mit Rotationsreglern für Kopf und Körper des Spielers" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/player_entities_pose_window.png?raw=true">

Über **Erweiterter Modus** neben einem Regler wird daraus ein Textfeld, das [Platzhalter](/placeholders) unterstützt. Verwendest du darin eine [Variable](/variables), zum Beispiel `$$arm_angle`, kann ein [Scheduler](/schedulers) den Spieler animieren, indem er den Variablenwert ändert.

# Rüstung, Gegenstände und mehr

- **Rüstung und Werkzeuge** stattet den Spieler mit Gegenständen aus: **Kopfrüstung**, **Brustrüstung**, **Beinrüstung**, **Fußrüstung**, **Gegenstand in der linken Hand** und **Gegenstand in der rechten Hand**. Gib dafür eine Gegenstands-ID an, zum Beispiel `minecraft:diamond_sword`. Gegenstands-IDs unterstützen Platzhalter. **Kopfrüstung verzaubern** und die anderen Verzauberungs-Schalter fügen den Verzauberungsschimmer hinzu.
- **Ist ein Baby** macht den Spieler klein, wie ein Baby.
- **Papagei** setzt einen Papagei auf die rechte Schulter. Mit **Papagei auf linker Schulter** sitzt er stattdessen auf der linken.

# Gut zu wissen

- Spieler-Entities können nicht gedreht, geneigt, ausgeblendet oder durchsichtig gemacht werden.
- Um nur den Kopf eines Spielers anzuzeigen, siehe [Spielerköpfe](/player-heads).
- Unter Minecraft 1.19.2 benötigen Spieler-Entities Fancy Entity Renderer nicht, bieten aber weniger Einstellungen: **Duckend** statt **Pose** sowie keine **Namensschild-Rotation**, **Körperbewegung** oder **Rüstung und Werkzeuge**. Ihre Größe wird über **Entity-Skalierung** festgelegt (standardmäßig `30`, also ist `60` doppelt so groß), nicht über die Größe des Elements.
