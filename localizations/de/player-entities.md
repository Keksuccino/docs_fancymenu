---
title: Spieler-Entitäten
description: >-
  Wie das FancyMenu-Element „Player Entity“ funktioniert und wie man es korrekt
  verwendet.
---
# Spieler-Entitäten

FancyMenu ermöglicht es dir, Spieler-Entitäten auf Bildschirmen hinzuzufügen, sodass du den Client-Spieler oder andere Spieler anzeigen kannst – einschließlich benutzerdefinierter Entitäten, die überhaupt keinen echten Spieler darstellen, mit einem eigenen Skin, Namen, Cape und so weiter.

# Client-Spieler

Um einen „Spiegel“ des Client-Spielers anzuzeigen, klicke einfach mit der rechten Maustaste auf das Player-Entity-Element und aktiviere **Copy Client Player**. Dadurch werden Skin, Cape und Name des Client-Spielers übernommen.

# Andere Spieler

Wenn du einen anderen vorhandenen Spieler anzeigen möchtest, klicke einfach mit der rechten Maustaste auf das Element und setze den **Player Name** auf den Namen eines vorhandenen Spielers. Dadurch werden automatisch Skin, Cape und Name dieses Spielers angezeigt, solange du keinen benutzerdefinierten Skin oder Cape gesetzt hast und **Copy Client Player** **deaktiviert** ist.

# Benutzerdefinierte Spieler-Entitäten

Wenn du überhaupt keinen echten Spieler anzeigen möchtest und stattdessen das Aussehen der Entität mit Skin, Cape und Name vollständig anpassen willst, kannst du das Element per Rechtsklick öffnen. Dort gibt es Optionen zum Setzen einer benutzerdefinierten Skin- und Cape-Textur. Wenn ein benutzerdefinierter Skin und ein benutzerdefiniertes Cape aktiv sind, kannst du auch einen beliebigen Spielernamen festlegen, ohne dass dessen Skin übernommen wird, falls der Spieler existiert.

# Entitäten-Pose

Das Player-Entity-Element unterstützt die Anpassung seiner Pose vollständig, das heißt, du kannst alle Gliedmaßen, Körperteile usw. frei bewegen.

Dazu klicke mit der rechten Maustaste auf das Element und dann auf **Player Pose**. Dadurch öffnet sich ein Bildschirm mit Schiebereglern, mit denen du die X/Y/Z-Rotation aller Körperteile konfigurieren kannst.

Die Pose-Einstellungen des Spielers haben einen normalen Modus, in dem du die Rotationen mit Schiebereglern anpassen kannst. Es gibt außerdem einen erweiterten Modus, der eine Texteingabe für alle Rotationen mit voller Platzhalterunterstützung ermöglicht, wodurch es sogar möglich ist, die Entität mit einem Ticker-Element zu animieren, das Rotationsvariablen setzt!

# Größe der Entität ändern

In Minecraft 1.20.1+ kannst du einfach die normalen Größenänderungs-Griffe des Elements verwenden, um die Entität zu skalieren.

Für ältere Versionen (1.19.2 und älter) unterstützen Player-Entity-Elemente keine direkte Größenänderung über die Größenänderungs-Griffe. Stattdessen musst du das Element per Rechtsklick öffnen und auf **Scale** klicken. Damit kannst du eine Skalierung für das Element festlegen. Der Standardwert sollte `30` sein; wenn du ihn beispielsweise auf `60` setzt, ist der Spieler doppelt so groß wie normal, bei `15` wird er in halber Größe angezeigt und so weiter.

# Abhängigkeit: Fancy Entity Renderer (FER)

Für **Minecraft 1.20.1+** wird ein **zusätzliches Mod** benötigt, damit Player-Entity-Elemente funktionieren. Das Mod heißt **Fancy Entity Renderer** und ist auf [CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer) und [Modrinth](https://modrinth.com/mod/fancy-entity-renderer) verfügbar.

Falls für die von dir verwendete Minecraft-Version noch kein Build verfügbar ist, wird er höchstwahrscheinlich zu einem späteren Zeitpunkt veröffentlicht.

Bitte beachte, dass FER nicht von Keksuccino entwickelt wird und er daher keinen Einfluss darauf hat, wann Builds veröffentlicht werden.
