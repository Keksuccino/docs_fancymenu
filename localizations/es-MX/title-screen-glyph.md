---
title: Glifo de pantalla de título
description: >-
  Cómo ocultar o quitar el pequeño ícono en forma de diamante o esmeralda (verde
  o azul) en la pantalla de título.
---

# Ícono de esmeralda/diamante en la pantalla de título

Si te cuesta ocultar el pequeño ícono que sigue apareciendo en tu pantalla de título y que parece un pequeño diamante o una esmeralda (un pequeño ícono verde o azul), normalmente se trata de la notificación de actualización del mod Mod Menu (mod de Fabric) o de Forge (función integrada del cargador de mods).

En algunos casos, también puede formar parte del botón de Realms de Minecraft Vanilla (para mostrar notificaciones).

# Ocultar el ícono de Mod Menu

Para ocultar el glifo de Mod Menu, necesitas desactivar el "indicador de actualización" en sus ajustes.

Haz clic en el botón **Mods** -> Pasa el cursor sobre el ícono del mod Mod Menu en la lista de mods -> Haz clic en él -> Establece "Update Indicator" en "Hidden".

# Ocultar el ícono de Forge

Forge usa un verificador de versiones integrado para mostrar ese ícono de esmeralda cuando los mods están desactualizados. Puedes desactivarlo:

1. Abre tu archivo `config/fml.toml`.
2. Busca la opción `versionCheck`.
3. Cámbiala a `false`: `versionCheck = false`
4. Guarda y reinicia Minecraft.

Esto desactiva por completo la verificación de versión, lo que también oculta el glifo de esmeralda al iniciar.

Otra forma de ocultar el ícono es simplemente ocultando por completo el botón de Mods con FancyMenu. Al ocultar el botón también se ocultará el glifo.

# Ocultar los íconos de Vanilla Realms

Si no es el glifo de Mod Menu ni el de Forge, probablemente sean los íconos de notificación de Realms de Minecraft. Estos íconos aparecen aproximadamente en la posición del botón de Realms y se pueden ocultar con FancyMenu en el editor de diseño. Necesitas crear un diseño "para la pantalla actual" (la pantalla de título en este caso) y entonces verás los íconos de Realms como un elemento independiente en el editor. Para ocultarlos, solo haz **clic derecho** sobre ellos y luego clic en **Delete**.

Los íconos de Realms pueden ser un ícono de periódico, un glifo de diamante y otros, como un círculo rojo con un contador de notificaciones.
