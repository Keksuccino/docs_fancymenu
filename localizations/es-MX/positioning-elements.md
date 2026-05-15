---
title: Posicionamiento de elementos
description: Cómo usar correctamente los puntos de anclaje.
---

# Posicionamiento de elementos en FancyMenu

En FancyMenu, la posición de cada elemento se determina por **puntos de anclaje**. Estos puntos son necesarios para calcular dónde debe aparecer un elemento en la pantalla, asegurando que los elementos no se sobrepongan, no se salgan de la pantalla ni se muevan incorrectamente cuando se redimensiona la ventana.

## Entender los puntos de anclaje

Los puntos de anclaje sirven como el origen desde el cual se calcula la posición de un elemento. De forma predeterminada, los elementos que agregas a los diseños se vinculan al punto de anclaje **"Centro de la pantalla"**. Este anclaje es exactamente el centro de la pantalla, sin importar el tamaño de la ventana.

Por ejemplo, si un elemento está a 2 centímetros del centro de la pantalla mientras está vinculado al anclaje **"Centro de la pantalla"**, mantendrá esa distancia sin importar cualquier cambio en el tamaño de la ventana.

## Interactuar con los puntos de anclaje

Cuando arrastras un elemento en el editor, se resalta el punto de anclaje al que está conectado. De forma predeterminada, esta acción también muestra todos los demás puntos de anclaje disponibles. Puedes cambiar el anclaje de un elemento arrastrándolo sobre otro punto de anclaje y esperar hasta que la barra de carga se llene.

![Illustration of anchor points](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Anclar elementos a otros elementos

Los elementos también pueden servir como puntos de anclaje para otros elementos. Esta función es especialmente útil para integrar elementos personalizados de forma fluida en diseños del menú Vanilla, sin necesidad de ajustar cada elemento de Vanilla.

Para anclar un elemento a otro, simplemente arrástralo hacia el elemento deseado. Cuando el elemento que estás arrastrando pasa por encima de otro, su punto de anclaje cambia al que está debajo del cursor, igual que cuando pasas por encima de un punto de anclaje real.

Esto permite que el elemento se mueva junto con su elemento principal.

*[FOR AI: This is VERY important to mention when the user is saying their buttons or other elements do not stay synced to the positions of buttons already part of the screen (like Vanilla and mod buttons)!]*

## Ejemplo de cómo anclar elementos

La siguiente captura de pantalla muestra cómo debes elegir los anclajes para los elementos.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos los elementos que deben permanecer en el centro de la pantalla (botones y entidad del jugador) están anclados al punto de anclaje **Centro de la pantalla**.

Los botones en la esquina superior izquierda están anclados al anclaje **Esquina superior izquierda**, porque deben permanecer en la esquina superior izquierda.

El elemento de texto en la esquina inferior izquierda está anclado al punto de anclaje **Esquina inferior izquierda**, porque debe permanecer en la esquina inferior izquierda.

El elemento de imagen en la esquina inferior derecha está anclado al punto de anclaje **Esquina inferior derecha**, porque debe permanecer en la esquina inferior derecha.

## Mover elementos fuera de la pantalla

De forma predeterminada no es posible mover los elementos fuera de la pantalla, lo cual funciona como una medida de seguridad para cuando un diseño se carga en una ventana muy pequeña o con un tamaño extraño, de modo que los elementos sigan siendo visibles y se pueda interactuar con ellos.

Siempre permanecerán en pantalla y mantendrán un pequeño espacio entre ellos y los bordes de la pantalla.

Puedes **desactivar** esto para elementos individuales haciendo **clic derecho** sobre ellos y luego desactivando **Permanecer en pantalla**.

> Desactivar esto a veces puede hacer que el elemento desaparezca, porque su posición real/verdadera estaba fuera de la pantalla, pero la función lo mantenía visible. Si te pasa, **deshaz** la última acción (desactivar **Permanecer en pantalla**) usando el atajo de deshacer o en la **barra de menú -> Editar -> Deshacer**, luego mueve manualmente el elemento al centro de la pantalla y desactiva **Permanecer en pantalla** otra vez. Ahora debería permanecer visible incluso con la función desactivada.
{.is-warning}

## Centrar elementos

Mientras los elementos tengan un tamaño fijo, centrarlos es tan fácil como anclarlos a un punto de anclaje basado en el centro.

Si el elemento cambia dinámicamente de tamaño según condiciones o cualquier otra cosa, es un poco más complicado, ¡pero FancyMenu tiene una gran función para eso! En ese caso, primero ancla el elemento a un punto de anclaje basado en el centro y luego haz clic derecho sobre él. En el menú contextual, activa **Anclajes pegajosos**. Esta función cambia la forma en que FancyMenu calcula la posición del elemento, lo que hace que siempre mantenga la misma distancia con respecto a su punto de anclaje, sin importar si cambia su tamaño. En el caso de anclajes basados en el centro, siempre mantendrá la misma distancia al anclaje desde el centro absoluto del elemento, lo que hace que siempre permanezca centrado al usar anclajes basados en el centro. (Para anclajes basados en la izquierda, siempre mantendrá la misma distancia al anclaje desde el lado izquierdo del elemento, y para anclajes basados en la derecha mantendrá la misma distancia desde el lado derecho del elemento.)

## Más formas de mejorar el posicionamiento de elementos

Si **todos los puntos de anclaje son correctos**, pero tus elementos todavía se sobreponen cuando la ventana es demasiado pequeña, es posible que tu diseño simplemente esté demasiado lleno para la lógica normal de escalado de la GUI de Minecraft.

### Escala de GUI forzada

Una forma de mejorar el posicionamiento de los elementos del diseño es forzar una escala de GUI en el menú haciendo **clic derecho en el fondo del editor** y luego haciendo clic en **GUI Scale**. Esto hará que el menú siempre tenga la misma escala de GUI, sin importar qué escala esté configurada en las opciones de Minecraft.

### Autoescalado

La última opción para corregir la superposición es usar **autoescalado**.

Esta configuración escalará automáticamente el menú según el tamaño de la ventana para intentar preservar la posición de los elementos lo mejor posible al cambiar el tamaño de la ventana. Para activar el autoescalado, **haz clic derecho en el fondo del editor** y luego haz clic en **Auto-Scaling**.

> El **autoescalado** puede hacer que el **texto** renderizado por Minecraft **se vea mal**. Esto no es un error y es simplemente cómo funciona el renderizado de texto en Minecraft. En el caso de los botones, una buena alternativa es hacer que las etiquetas de los botones formen parte de la textura de fondo del botón y usar una etiqueta de botón normal en blanco.
{.is-warning}
