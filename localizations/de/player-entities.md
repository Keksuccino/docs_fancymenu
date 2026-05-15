---
title: Spieler-Entitäten
description: >-
  Wie das FancyMenu-Element „Player Entity“ funktioniert und wie man es korrekt
  verwendet.
---

# Spieler-Entitäten

FancyMenu ermöglicht es dir, Spieler-Entitäten zu Bildschirmen hinzuzufügen, sodass du den Client-Spieler oder andere Spieler anzeigen kannst. Dazu gehören auch benutzerdefinierte Entitäten, die überhaupt keinen echten Spieler darstellen, mit eigenem Skin, Namen, Umhang und so weiter.

# Client-Spieler

Um einen „Spiegel“ des Client-Spielers anzuzeigen, klicke einfach mit der rechten Maustaste auf das Player-Entity-Element und aktiviere **Copy Client Player**. Dadurch werden der Skin, der Umhang und der Name des Client-Spielers übernommen.

# Andere Spieler

Wenn du einen anderen vorhandenen Spieler anzeigen möchtest, klicke einfach mit der rechten Maustaste auf das Element und setze den **Player Name** auf den Namen eines bestehenden Spielers. Dadurch werden automatisch der Skin, der Umhang und der Name dieses Spielers angezeigt, solange du keinen benutzerdefinierten Skin oder Umhang festgelegt hast und **Copy Client Player** **deaktiviert** ist.

# Benutzerdefinierte Spieler-Entitäten

Wenn du überhaupt keinen echten Spieler anzeigen möchtest und stattdessen Skin, Umhang und Name der Entität vollständig anpassen willst, kannst du das Element per Rechtsklick bearbeiten. Es gibt Optionen, um eine benutzerdefinierte Skin- und Umhang-Textur festzulegen. Wenn ein benutzerdefinierter Skin und Umhang aktiv sind, kannst du auch jeden beliebigen Spielernamen festlegen, ohne dass der Skin des Spielers übernommen wird, falls der Spieler existiert.

# Entitätenpose

Das Player-Entity-Element unterstützt das Anpassen seiner Pose vollständig. Mit anderen Worten: Du kannst alle Gliedmaßen, Körperteile usw. frei bewegen.

Dazu klickst du mit der rechten Maustaste auf das Element und dann auf **Player Pose**. Dadurch öffnet sich ein Bildschirm mit Schiebereglern, mit denen du die X/Y/Z-Rotation aller Körperteile konfigurieren kannst.

Die Pose-Einstellungen haben einen normalen Modus, in dem du die Rotationen mit Schiebereglern anpassen kannst, und es gibt außerdem einen erweiterten Modus, der eine Texteingabe für alle Rotationen mit vollständiger Platzhalterunterstützung bietet. Damit ist es sogar möglich, die Entität mit einem Ticker-Element zu animieren, das Rotationsvariablen setzt!

# Größe der Entität ändern

In Minecraft 1.21.1+ kannst du einfach die normalen Größen-Anfasser des Elements verwenden, um die Entität zu skalieren.

In älteren Versionen (1.21.0 und älter) unterstützen Player-Entity-Elemente keine direkte Größenänderung über die Größen-Anfasser. Stattdessen musst du mit der rechten Maustaste auf das Element klicken und dann auf **Scale**. Dadurch kannst du eine Skalierung für das Element festlegen. Der Standardwert sollte `30` sein. Wenn du ihn beispielsweise auf `60` setzt, ist der Spieler doppelt so groß wie normal, mit `15` wird er in halber Größe angezeigt und so weiter.

# Abhängigkeit: Fancy Entity Renderer (FER)

Für Minecraft 1.21.1+ wird ein zusätzliches Mod benötigt, damit Player-Entity-Elemente funktionieren. Das Mod heißt „Fancy Entity Renderer“ und ist auf CurseForge und Modrinth verfügbar.

Wenn für die von dir verwendete Minecraft-Version noch kein Build verfügbar ist, wird es sehr wahrscheinlich zu einem späteren Zeitpunkt veröffentlicht.

Bitte beachte, dass FER nicht von Keksuccino entwickelt wird. Daher hat er keinen Einfluss darauf, wann Builds veröffentlicht werden.
