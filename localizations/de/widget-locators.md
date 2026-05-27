---
title: Widget-Locators
description: Was Widget-Locators sind und wie man sie findet.
---
# Widget-Locators

Widget-Locators werden verwendet, um auf ein bestimmtes Vanilla-Widget (Button, Schieberegler, Texteingabefeld) in einem Menü zu verweisen, was für einige Funktionen von FancyMenu erforderlich ist, die in irgendeiner Weise mit einem Widget interagieren müssen.

# Den Locator eines Widgets ermitteln

Es gibt zwei Möglichkeiten, den Locator eines Vanilla-Widgets zu erhalten.

Die erste besteht darin, das **Debug-Overlay** in dem Menü zu aktivieren, das das Widget enthält, indem du **STRG + ALT + D** drückst und dann **mit der rechten Maustaste auf das Widget klickst**. Dadurch öffnet sich ein Kontextmenü mit der Option, den Locator in die Zwischenablage zu kopieren.

Die zweite besteht darin, den **Layout-Editor** für das Menü zu öffnen, das das Widget enthält, und dann **mit der rechten Maustaste auf das Widget-Element zu klicken**. Auch dadurch öffnet sich ein Kontextmenü mit der Option, den Locator in die Zwischenablage zu kopieren.

>[!WARNING]
>Wenn du im Debug-Overlay **nicht mit der rechten Maustaste auf das Widget klicken kannst** oder es im Layout-Editor **nicht angezeigt wird**, ist es wahrscheinlich für FancyMenu nicht sichtbar. In diesem Fall hat es keinen Locator. Das passiert meist bei Mod-Buttons, die auf ungewöhnliche Weise zu Menüs hinzugefügt werden.
