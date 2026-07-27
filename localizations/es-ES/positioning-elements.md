---
title: Posicionamiento de elementos
description: Cómo usar correctamente los puntos de anclaje.
---

# Posicionamiento de elementos en FancyMenu

En FancyMenu, la posición de cada elemento se determina mediante **puntos de anclaje**. Estos puntos son necesarios para calcular dónde debe aparecer un elemento en pantalla, garantizando que los elementos no se solapen, no se salgan de la pantalla ni se muevan incorrectamente cuando se redimensiona la ventana.

## Entender los puntos de anclaje

Los puntos de anclaje sirven como origen a partir del cual se calcula la posición de un elemento. De forma predeterminada, los elementos que añades a los diseños están vinculados al punto de anclaje **"Centro de la pantalla"**. Este anclaje es exactamente el centro de la pantalla, independientemente del tamaño de la ventana.

Por ejemplo, si un elemento está a 2 centímetros del centro de la pantalla mientras está vinculado al anclaje **"Centro de la pantalla"**, mantendrá esa distancia sin importar los cambios en el tamaño de la ventana.

## Interactuar con los puntos de anclaje

Cuando arrastras un elemento en el editor, se resalta el punto de anclaje al que está conectado. De forma predeterminada, esta acción también muestra todos los demás puntos de anclaje disponibles. Puedes cambiar el anclaje de un elemento arrastrándolo sobre otro punto de anclaje y esperando hasta que la barra de carga se llene.

![Illustration of anchor points](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Anclar elementos a otros elementos

Los elementos también pueden servir como puntos de anclaje para otros elementos. Esta función es especialmente útil para integrar elementos personalizados de forma fluida en diseños de menú de Vanilla sin necesidad de ajustar cada elemento de Vanilla.

Para anclar un elemento a otro, simplemente arrástralo hacia el elemento deseado. Cuando el elemento que estás arrastrando pasa por encima de otro, su punto de anclaje cambia al elemento sobre el que se ha pasado, igual que cuando pasas por encima de un punto de anclaje real.

Esto permite que el elemento se mueva junto con su elemento padre.

## Ejemplo de cómo anclar elementos

La siguiente captura de pantalla muestra cómo deberías elegir los anclajes para los elementos.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos los elementos que deben permanecer en el centro de la pantalla (botones y la entidad del jugador) están anclados al punto de anclaje **Centro de la pantalla**.

Los botones de la esquina superior izquierda están anclados al anclaje **Esquina superior izquierda**, porque deben permanecer en la esquina superior izquierda.

El elemento de texto de la esquina inferior izquierda está anclado al punto de anclaje **Esquina inferior izquierda**, porque debe permanecer en la esquina inferior izquierda.

El elemento de imagen de la esquina inferior derecha está anclado al punto de anclaje **Esquina inferior derecha**, porque debe permanecer en la esquina inferior derecha.

## Mover elementos fuera de la pantalla

De forma predeterminada no es posible mover los elementos fuera de la pantalla, lo cual funciona como un mecanismo de seguridad para cuando se carga un diseño en una ventana muy pequeña o extraña, de modo que los elementos sigan siendo visibles y se pueda interactuar con ellos.

Siempre permanecerán en pantalla y mantendrán un pequeño espacio entre ellos y los bordes de la pantalla.

Puedes **desactivar** esto para elementos individuales **haciendo clic derecho** sobre ellos y desactivando **Permanecer en pantalla**.

> [!WARNING]
> Desactivar esto a veces puede hacer que el elemento desaparezca, porque su posición real estaba fuera de la pantalla, pero la función hacía que siguiera visible. Si te ocurre, **deshaz** la última acción (desactivar **Permanecer en pantalla**) mediante el atajo de deshacer o en la **barra de menús -> Editar -> Deshacer**, y luego mueve manualmente el elemento al centro de la pantalla y desactiva **Permanecer en pantalla** otra vez. Ahora debería seguir siendo visible incluso con la función desactivada.

## Centrar elementos

Mientras los elementos tengan un tamaño fijo, centrarlos es tan fácil como anclarlos a un punto de anclaje basado en el centro.

Si el elemento cambia dinámicamente de tamaño en función de condiciones o de cualquier otra cosa, es un poco más complicado, ¡pero FancyMenu tiene una gran función para eso! En ese caso, primero ancla el elemento a un punto de anclaje basado en el centro y luego haz clic derecho sobre él. En el menú contextual, activa **Anclajes adhesivos**. Esta función cambia la forma en que FancyMenu calcula la posición del elemento, haciendo que siempre mantenga la misma distancia respecto a su punto de anclaje, sin importar si cambia de tamaño. En el caso de los anclajes basados en el centro, siempre mantendrá la misma distancia al anclaje desde el centro absoluto del elemento, lo que hace que permanezca siempre centrado al usar anclajes basados en el centro. (Para anclajes basados en la izquierda, siempre mantendrá la misma distancia al anclaje desde el lado izquierdo del elemento y, para anclajes basados en la derecha, mantendrá la misma distancia desde el lado derecho del elemento.)

## Más formas de mejorar el posicionamiento de los elementos

Si **todos los puntos de anclaje son correctos**, pero tus elementos siguen solapándose cuando la ventana es demasiado pequeña, es posible que tu diseño simplemente esté demasiado cargado para la lógica normal de escalado de la interfaz de Minecraft.

### Forzar escala de la interfaz

Una forma de mejorar el posicionamiento de los elementos del diseño es forzar una escala de interfaz en el menú haciendo **clic derecho en el fondo del editor** y seleccionando **Forzar escala de la interfaz**. Esto hará que el menú tenga siempre la misma escala de interfaz, independientemente de la escala configurada en las opciones de Minecraft.

### Autoescalado

La última opción para solucionar los solapamientos es usar el **autoescalado**.
Esta opción ajustará automáticamente la escala del menú en función del tamaño de la ventana para intentar conservar la posición de los elementos lo mejor posible al redimensionar la ventana. Para activar el autoescalado, **haz clic derecho en el fondo del editor** y luego pulsa en **Autoescalado**.

> [!WARNING]
> El **autoescalado** puede hacer que el **texto** renderizado por Minecraft **se vea mal**. Esto no es un error y es simplemente así como funciona el renderizado del texto en Minecraft. En el caso de los botones, una buena solución alternativa para esto es hacer que las etiquetas de los botones formen parte de la textura de fondo del botón y establecer una etiqueta de botón vacía por defecto.
