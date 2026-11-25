---
title: Posicionamiento de elementos
description: Cómo usar correctamente los puntos de anclaje.
sourceBlobSha: c6c6b53374ed720fcdc32a3a0fbc1784f202cc5a
---

# Posicionamiento de elementos en FancyMenu

En FancyMenu, la posición de cada elemento se determina mediante **puntos de anclaje**. Estos puntos permiten calcular dónde debe aparecer un elemento en la pantalla y garantizan que los elementos no se superpongan, no queden fuera de la pantalla ni se muevan de forma incorrecta al cambiar el tamaño de la ventana.

## Cómo funcionan los puntos de anclaje

Los puntos de anclaje sirven como origen desde el que se calcula la posición de un elemento. De forma predeterminada, los elementos que añades a los diseños están vinculados al punto de anclaje **«Centro de la pantalla»**. Este anclaje corresponde al centro exacto de la pantalla, independientemente del tamaño de la ventana.

Por ejemplo, si un elemento está a 2 centímetros del centro de la pantalla y está vinculado al anclaje **«Centro de la pantalla»**, mantendrá esa distancia aunque cambie el tamaño de la ventana.

## Interacción con los puntos de anclaje

Al arrastrar un elemento en el editor, se resalta el punto de anclaje al que está conectado. De forma predeterminada, también se muestran todos los demás puntos de anclaje disponibles. Puedes cambiar el anclaje de un elemento arrastrándolo sobre otro punto de anclaje y esperando a que se complete la barra de carga.

![Ilustración de los puntos de anclaje](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Anclaje de elementos a otros elementos

Un elemento puede usar otro elemento como anclaje. De este modo, se mueve junto con él y mantiene la distancia con respecto a la esquina superior izquierda del otro elemento. Esto resulta útil para paneles compuestos por varios elementos, para una etiqueta situada junto a un botón vanilla y para los [arrastradores](/dragger).

Hay dos formas de hacerlo. En ambos casos, el elemento permanece en su sitio.

### Arrastrando

1. Arrastra el elemento y mantén el puntero sobre el otro elemento.
2. Espera a que la barra se complete y suelta el elemento.

Si el puntero ya está sobre el otro elemento cuando empiezas a arrastrar, sácalo de encima una vez y vuelve a colocarlo sobre él. Los elementos que ya están bajo el puntero al empezar no cuentan.

Para ello, las opciones **Mantener el puntero sobre el área de anclaje** y **Mantener el puntero sobre el elemento de anclaje** del menú **Ventana** deben estar activadas; ambas lo están de forma predeterminada. La primera activa y desactiva el anclaje al mantener el puntero sobre un elemento, y la segunda añade otros elementos a los puntos de anclaje. La opción **Tiempo de carga al mantener el puntero sobre el área/elemento de anclaje (segundos)**, en el mismo menú, determina cuánto tiempo tienes que mantenerlo encima. El valor predeterminado es de 2 segundos.

### Mediante ID

1. Haz clic con el botón derecho en el otro elemento y selecciona **Copiar ID del elemento**.
2. Haz clic con el botón derecho en el elemento y selecciona **Punto de anclaje -> Otro elemento**.
3. Pega el ID en **ID del elemento** y haz clic en **Listo**.

Si hay varios elementos seleccionados, los pasos 2 y 3 los anclan todos a la vez. Consulta [Identificadores de elementos](/element-identifiers) para obtener más información sobre los ID.

## Anclajes en áreas desplazables

Los elementos de un [área desplazable](/scrollable-areas) también tienen anclajes, pero estos pertenecen al contenido del área, no a la pantalla:

- **Esquina superior izquierda** corresponde a la esquina superior izquierda del contenido; **Centro de la pantalla**, a su centro, y los anclajes inferiores se fijan al final del contenido. Así, un elemento puede situarse al final de una lista larga y permanecer allí aunque la lista crezca.
- Los elementos de un área solo pueden usar como anclaje otros elementos de esa misma área.
- Al mover un elemento hacia dentro o fuera de un área, los elementos que estaban anclados a través de su borde pasan a tener el anclaje **Esquina superior izquierda** y permanecen en el mismo sitio.

Esto funciona en el modo **Anclajes** del área. En los demás modos, el área coloca los elementos por sí misma. Consulta [Áreas desplazables](/scrollable-areas#anchors-mode).

## Ejemplo de anclaje de elementos

La siguiente captura de pantalla muestra cómo elegir los anclajes de los elementos.

<br>
<img width="571" alt="Captura de pantalla_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos los elementos que deben permanecer en el centro de la pantalla (los botones y la entidad del jugador) están anclados al punto de anclaje **Centro de la pantalla**.

Los botones de la esquina superior izquierda están anclados al punto **Esquina superior izquierda**, ya que deben permanecer en esa esquina.

El elemento de texto de la esquina inferior izquierda está anclado al punto **Esquina inferior izquierda**, ya que debe permanecer en esa esquina.

El elemento de imagen de la esquina inferior derecha está anclado al punto **Esquina inferior derecha**, ya que debe permanecer en esa esquina.

## Sacar elementos de la pantalla

De forma predeterminada, no es posible sacar elementos de la pantalla. Esto sirve de protección si se carga un diseño en una ventana muy pequeña o con un tamaño inusual, para que los elementos sigan visibles y se pueda interactuar con ellos.

Los elementos siempre permanecerán en pantalla y conservarán una pequeña separación con respecto a los bordes.

Puedes **desactivar** esta opción para elementos concretos haciendo **clic con el botón derecho** sobre ellos y desactivando **Mantener en pantalla**.

> [!WARNING]
> Desactivar esta opción puede hacer que el elemento desaparezca, porque su posición real estaba fuera de la pantalla, pero esta función lo mantenía visible. Si te ocurre, **deshaz** la última acción (desactivar **Mantener en pantalla**) con el atajo para deshacer o desde **barra de menú -> Editar -> Deshacer**. Después, mueve manualmente el elemento al centro de la pantalla y vuelve a desactivar **Mantener en pantalla**. Ahora debería permanecer visible aunque la opción esté desactivada.

## Centrar elementos

Si los elementos tienen un tamaño fijo, centrarlos es tan sencillo como anclarlos a un punto de anclaje centrado.

Si el tamaño del elemento cambia dinámicamente según ciertas condiciones u otros factores, resulta un poco más complicado. ¡Pero FancyMenu tiene una función muy útil para ello! En ese caso, primero ancla el elemento a un punto de anclaje centrado y luego haz clic con el botón derecho sobre él. En el menú contextual, activa **Anclaje fijo**. Esta función cambia la forma en que FancyMenu calcula la posición del elemento, de modo que siempre mantiene la misma distancia con respecto a su punto de anclaje, aunque cambie de tamaño. En los anclajes centrados, siempre mantiene la misma distancia con respecto al anclaje desde el centro absoluto del elemento, lo que hace que permanezca centrado. (Con los anclajes a la izquierda, mantiene siempre la misma distancia con respecto al anclaje desde el lado izquierdo del elemento; con los anclajes a la derecha, desde el lado derecho.)

## Otras formas de mejorar el posicionamiento de los elementos

Si **todos los puntos de anclaje son correctos**, pero los elementos siguen superponiéndose cuando la ventana es demasiado pequeña, es posible que el diseño simplemente tenga demasiados elementos para el sistema de escalado normal de la interfaz de Minecraft.

### Escala de interfaz forzada

Una forma de mejorar el posicionamiento de los elementos del diseño es forzar una escala de interfaz para el menú. Para ello, **haz clic con el botón derecho en el fondo del editor** y selecciona **Forzar escala de interfaz**. Así, el menú siempre tendrá la misma escala de interfaz, independientemente de la escala configurada en las opciones de Minecraft.

### Escalado automático

La última opción para evitar las superposiciones es usar el **escalado automático**.
Esta opción ajusta automáticamente la escala del menú según el tamaño de la ventana para intentar conservar lo mejor posible la posición de los elementos al cambiarla. Para activar el escalado automático, **haz clic con el botón derecho en el fondo del editor** y selecciona **Escalado automático**.

> [!WARNING]
> El **escalado automático** puede hacer que el **texto** que renderiza Minecraft **se vea mal**. No es un error, sino el resultado de cómo funciona el renderizado de texto de Minecraft. En el caso de los botones, una buena solución es incluir las etiquetas de los botones en la textura de fondo y dejar en blanco la etiqueta normal del botón.
