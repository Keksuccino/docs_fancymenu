---
title: Glifo de la pantalla de título
description: >-
  Cómo ocultar o quitar el pequeño diamante o esmeralda (glifo/icono verde o
  azul) en la pantalla de título.
---
# Icono de esmeralda/diamante en la pantalla de título

Si te cuesta ocultar el pequeño icono que sigue apareciendo en tu pantalla de título y que parece un pequeño diamante o una esmeralda (un icono pequeño verde o azul), normalmente se trata de la notificación de actualización del mod Mod Menu (mod de Fabric) o de Forge (función integrada del cargador de mods).

En algunos casos, también puede formar parte del botón de Realms de Minecraft vanilla (para mostrar notificaciones).

# Ocultar el icono de Mod Menu

Para ocultar el glifo de Mod Menu, tienes que desactivar el "indicador de actualización" en sus ajustes.

Haz clic en el botón **Mods** -> Pasa el cursor por encima del icono del mod Mod Menu en la lista de mods -> Haz clic en él -> Establece "Update Indicator" en "Hidden".

# Ocultar el icono de Forge

Forge usa un comprobador de versiones integrado para mostrar ese icono de esmeralda cuando los mods están desactualizados. Puedes desactivarlo:

1. Abre tu archivo `/config/fml.toml`.
2. Busca la opción `versionCheck`.
3. Cámbiala a `false`: `versionCheck = false`
4. Guarda y reinicia Minecraft.

Esto desactiva por completo la comprobación de versiones, lo que también oculta el glifo de esmeralda al iniciar.

Otra forma de ocultar el icono es simplemente ocultar todo el botón de Mods mediante FancyMenu. Al ocultar el botón, también se ocultará el glifo.

# Ocultar el icono de NeoForge

En NeoForge funciona exactamente igual que en Forge clásico.

1. Abre tu archivo `/config/fml.toml`.
2. Busca la opción `versionCheck`.
3. Cámbiala a `false`: `versionCheck = false`
4. Guarda y reinicia Minecraft.

# Ocultar los iconos de Realms de vanilla

Si no es ni el glifo de Mod Menu ni el de Forge, probablemente sean los iconos de notificación de Realms de Minecraft. Estos iconos aparecen aproximadamente en la posición del botón de Realms y se pueden ocultar con FancyMenu en el editor de diseño. Necesitas crear un diseño "para la pantalla actual" (en este caso, la pantalla de título) y entonces verás los iconos de Realms como un elemento independiente en el editor. Para ocultarlos, simplemente haz **clic derecho** sobre ellos y luego haz clic en **Delete**.

Los iconos de Realms pueden ser un icono de periódico, un glifo de diamante y otros, como un círculo rojo con un contador de notificaciones.
