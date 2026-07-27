---
title: Benutzerdefinierter Cursor
description: Wie Menüs einen benutzerdefinierten Mauszeiger verwenden.
---

# Benutzerdefinierter Mauszeiger

Fügen Sie einem Layout ein [**Cursor**-Element](./elements#cursor) hinzu, um den Systemcursor auf diesem Bildschirm zu ersetzen:

1. Wählen Sie **Neues Element -> Cursor**.
2. Legen Sie eine PNG-Textur mit RGBA-Farben fest.
3. Setzen Sie **Hotspot X** und **Hotspot Y** auf das Textur-Pixel, an dem Klicks ausgelöst werden sollen.
4. Aktivieren Sie die Editor-Vorschau, wenn Sie den Cursor beim Bearbeiten überprüfen möchten.
5. Verwenden Sie ein [Universelles Layout](./universal-layouts), wenn derselbe Cursor auf mehreren unterstützten Bildschirmen angezeigt werden soll.

Empfohlen werden kleine Cursor-Texturen wie `32×32` oder `64×64`. Erscheinungsbild und Verhalten des Cursors können je nach Betriebssystem variieren.
