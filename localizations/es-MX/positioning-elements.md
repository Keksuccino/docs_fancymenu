---
title: Posicionamiento de elementos
description: Cómo usar correctamente los puntos de anclaje.
---

# Posicionamiento de elementos en FancyMenu

En FancyMenu, la posición de cada elemento se determina mediante **puntos de anclaje**. Estos puntos se usan para calcular dónde debe aparecer un elemento en la pantalla, asegurando que los elementos no se sobrepongan, no se salgan de la pantalla ni se muevan incorrectamente cuando se cambia el tamaño de la ventana.

## Entendiendo los puntos de anclaje

Los puntos de anclaje sirven como el origen desde el cual se calcula la posición de un elemento. De forma predeterminada, los elementos que agregas a los diseños están vinculados al punto de anclaje **"Centro de la pantalla"**. Este ancla es el centro exacto de la pantalla, sin importar el tamaño de la ventana.

Por ejemplo, si un elemento está a 2 centímetros del centro de la pantalla mientras está vinculado al ancla **"Centro de la pantalla"**, mantendrá esa distancia sin importar los cambios en el tamaño de la ventana.

## Interacción con los puntos de anclaje

Cuando arrastras un elemento en el editor, se resalta el punto de anclaje al que está conectado. De forma predeterminada, esta acción también muestra todos los demás puntos de anclaje disponibles. Puedes cambiar el ancla de un elemento arrastrándolo sobre otro punto de anclaje y esperar hasta que la barra de carga se llene.

![Ilustración de puntos de anclaje](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Anclar elementos a otros elementos

Los elementos también pueden servir como puntos de anclaje para otros elementos. Esta función es especialmente útil para integrar elementos personalizados sin problemas en los diseños del menú vanilla, sin necesidad de ajustar cada elemento vanilla.

Para anclar un elemento a otro, simplemente arrástralo hacia el elemento deseado. Cuando el elemento que estás arrastrando pasa sobre otro, su punto de anclaje cambia al que está debajo del cursor, igual que cuando pasas sobre un punto de anclaje real.

Esto permite que el elemento se mueva junto con su elemento padre.

## Ejemplo de cómo anclar elementos

La siguiente captura muestra cómo debes elegir los anclas para los elementos.

<br>
<img width="571" alt="Captura de pantalla_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos los elementos que deben permanecer en el centro de la pantalla (botones y entidad del jugador) están anclados al punto de anclaje **Centro de la pantalla**.

Los botones de la esquina superior izquierda están anclados al ancla **Esquina superior izquierda**, porque deben permanecer en la esquina superior izquierda.

El elemento de texto de la esquina inferior izquierda está anclado al punto de anclaje **Esquina inferior izquierda**, porque debe permanecer en la esquina inferior izquierda.

El elemento de imagen de la esquina inferior derecha está anclado al punto de anclaje **Esquina inferior derecha**, porque debe permanecer en la esquina inferior derecha.

## Mover elementos fuera de la pantalla

De forma predeterminada no es posible mover elementos fuera de la pantalla, lo cual funciona como una medida de seguridad cuando un diseño se carga en una ventana muy pequeña o con un tamaño extraño, para que los elementos sigan visibles y se pueda interactuar con ellos.

Siempre permanecerán en pantalla y mantendrán un pequeño espacio entre ellos y los bordes de la pantalla.

Puedes **desactivar** esto para elementos individuales haciendo **clic derecho** sobre ellos y luego desactivando **Permanecer en pantalla**.

> [!WARNING]
> Desactivar esto a veces puede hacer que el elemento desaparezca, porque su posición real estaba fuera de la pantalla, pero la función lo mantenía visible. Si te pasa eso, **deshaz** la última acción (desactivar **Permanecer en pantalla**) con el atajo de deshacer o en la **barra de menú -> Editar -> Deshacer**, luego mueve manualmente el elemento al centro de la pantalla y vuelve a desactivar **Permanecer en pantalla**. Ahora debería seguir visible incluso con la función desactivada.

## Centrar elementos

Mientras los elementos tengan un tamaño fijo, centrarlo es tan fácil como anclarlos a un punto de anclaje basado en el centro.

Si el elemento cambia dinámicamente de tamaño según condiciones o cualquier otra cosa, es un poco más complicado, ¡pero FancyMenu tiene una gran función para eso! En ese caso, primero ancla el elemento a un punto de anclaje basado en el centro y luego haz clic derecho sobre él. En el menú contextual, activa **Anclas adhesivas**. Esta función cambia la forma en que FancyMenu calcula la posición del elemento, lo que hace que siempre mantenga la misma distancia respecto a su punto de anclaje, sin importar si cambia de tamaño. Para anclas basadas en el centro, siempre mantendrá la misma distancia al ancla desde el centro absoluto del elemento, lo que hace que siempre permanezca centrado al usar anclas basadas en el centro. (Para anclas basadas en la izquierda, siempre mantendrá la misma distancia al ancla desde el lado izquierdo del elemento y para anclas basadas en la derecha, mantendrá la misma distancia desde el lado derecho del elemento.)

## Más formas de mejorar el posicionamiento de elementos

Si **todos los puntos de anclaje son correctos**, pero tus elementos siguen superponiéndose cuando la ventana es demasiado pequeña, es posible que tu diseño simplemente tenga demasiados elementos para la lógica normal de escalado de la interfaz de Minecraft.

### Escala forzada de la interfaz

Una forma de mejorar el posicionamiento de los elementos del diseño es forzar una escala de interfaz en el menú haciendo **clic derecho sobre el fondo del editor** y seleccionando **Forzar escala de interfaz**. Esto hará que el menú siempre tenga la misma escala de interfaz, sin importar la escala configurada en las opciones de Minecraft.

### Autoescalado

La última opción para corregir la superposición es usar **autoescalado**.
Esta configuración escalará automáticamente el menú según el tamaño de la ventana para tratar de conservar la posición de los elementos lo mejor posible al cambiar el tamaño de la ventana. Para activar el autoescalado, **haz clic derecho sobre el fondo del editor** y luego haz clic en **Autoescalado**.

> [!WARNING]
> El **autoescalado** puede hacer que el **texto** renderizado por Minecraft se **vea mal**. Esto no es un error; simplemente así funciona el renderizado de texto de Minecraft. En el caso de los botones, una buena solución es hacer que las etiquetas de los botones formen parte de la textura de fondo del botón y dejar una etiqueta normal en blanco.
