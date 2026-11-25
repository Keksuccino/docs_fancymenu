---
title: Posicionamiento de elementos
description: Cómo usar correctamente los puntos de anclaje.
sourceBlobSha: c6c6b53374ed720fcdc32a3a0fbc1784f202cc5a
---

# Posicionar elementos en FancyMenu

En FancyMenu, la posición de cada elemento se determina mediante **puntos de anclaje**. Estos puntos sirven para calcular dónde debe aparecer un elemento en la pantalla y evitar que los elementos se encimen, se salgan de la pantalla o se muevan de forma incorrecta al cambiar el tamaño de la ventana.

## Cómo funcionan los puntos de anclaje

Los puntos de anclaje sirven como origen para calcular la posición de un elemento. De forma predeterminada, los elementos que agregas a los diseños están vinculados al punto de anclaje **"Centro de la pantalla"**. Este punto corresponde al centro exacto de la pantalla, sin importar el tamaño de la ventana.

Por ejemplo, si un elemento está a 2 centímetros del centro de la pantalla y está vinculado al punto de anclaje **"Centro de la pantalla"**, mantendrá esa distancia sin importar los cambios en el tamaño de la ventana.

## Interactuar con los puntos de anclaje

Al arrastrar un elemento en el editor, se resalta el punto de anclaje al que está conectado. De forma predeterminada, también se muestran todos los demás puntos de anclaje disponibles. Puedes cambiar el punto de anclaje de un elemento arrastrándolo sobre otro punto y esperando a que se complete la barra de carga.

![Ilustración de los puntos de anclaje](https://github.com/Keksuccino/FancyMenu/assets/35544624/25bff930-0b52-4d76-b0e9-3e1cbcf3c20e)

## Anclar elementos a otros elementos

Puedes usar otro elemento como punto de anclaje. Así, el elemento se moverá junto con el otro y mantendrá su distancia respecto a la esquina superior izquierda de este. Esto resulta práctico para paneles formados por varios elementos, para colocar una etiqueta junto a un botón vanilla y para los [elementos arrastrables](/dragger).

Hay dos formas de hacerlo. En ambos casos, el elemento conserva su posición.

### Arrastrando

1. Arrastra el elemento y mantén el puntero sobre el otro elemento.
2. Espera a que se complete la barra y suelta el elemento.

Si el puntero ya está sobre el otro elemento cuando empiezas a arrastrar, sácalo del elemento y vuelve a colocarlo encima. Los elementos que ya están debajo del puntero al comenzar no cuentan.

Para esto, las opciones **Mantener el puntero sobre el área de anclaje** y **Mantener el puntero sobre el elemento de anclaje** del menú **Ventana** deben estar activadas; ambas lo están de forma predeterminada. La primera activa o desactiva la función de anclar al mantener el puntero encima, y la segunda agrega otros elementos a los puntos de anclaje. La opción **Tiempo de espera sobre el área/elemento de anclaje (segundos)** del mismo menú determina cuánto tiempo debes mantener el puntero encima; el valor predeterminado es 2 segundos.

### Por ID

1. Haz clic derecho en el otro elemento y selecciona **Copiar ID del elemento**.
2. Haz clic derecho en el elemento y selecciona **Punto de anclaje -> Otro elemento**.
3. Pega el ID en **ID del elemento** y haz clic en **Listo**.

Si seleccionas varios elementos, los pasos 2 y 3 los anclarán todos a la vez. Consulta [Identificadores de elementos](/element-identifiers) para obtener más información sobre los ID.

## Anclajes en áreas desplazables

Los elementos de un [área desplazable](/scrollable-areas) también tienen puntos de anclaje, pero estos corresponden al contenido del área, no a la pantalla:

- La **Esquina superior izquierda** corresponde a la esquina superior izquierda del contenido; el **Centro de la pantalla**, a su centro; y los anclajes inferiores se ajustan al final del contenido. Así, un elemento puede colocarse al final de una lista larga y permanecer ahí aunque la lista crezca.
- Los elementos de un área solo pueden usar como anclaje otros elementos de esa misma área.
- Al mover un elemento hacia dentro o fuera de un área, los elementos que estaban anclados a través de su borde reciben el anclaje **Esquina superior izquierda** y conservan su posición.

Esto funciona en el modo **Anclajes** del área. En los demás modos, el área posiciona los elementos por sí misma. Consulta [Áreas desplazables](/scrollable-areas#anchors-mode).

## Ejemplo de cómo anclar elementos

La siguiente captura de pantalla muestra cómo elegir los puntos de anclaje de los elementos.

<br>
<img width="571" alt="Screenshot_2" src="https://gist.github.com/user-attachments/assets/159073e1-ab78-4086-9add-e660a1e4c93f">

Todos los elementos que deben permanecer en el centro de la pantalla (los botones y la entidad del jugador) están anclados al punto **Centro de la pantalla**.

Los botones de la esquina superior izquierda están anclados al punto **Esquina superior izquierda**, porque deben permanecer en esa esquina.

El elemento de texto de la esquina inferior izquierda está anclado al punto **Esquina inferior izquierda**, porque debe permanecer en esa esquina.

El elemento de imagen de la esquina inferior derecha está anclado al punto **Esquina inferior derecha**, porque debe permanecer en esa esquina.

## Mover elementos fuera de la pantalla

De forma predeterminada, no es posible mover elementos fuera de la pantalla. Esto funciona como una medida de seguridad cuando se carga un diseño en una ventana muy pequeña o de tamaño poco común, para que los elementos sigan visibles y se pueda interactuar con ellos.

Los elementos siempre permanecerán en pantalla y conservarán una pequeña separación respecto a sus bordes.

Puedes **desactivar** esta opción para elementos individuales. Para hacerlo, haz **clic derecho** en ellos y desactiva **Mantener en pantalla**.

> [!WARNING]
> Desactivar esta opción puede hacer que el elemento desaparezca, ya que su posición real estaba fuera de la pantalla, pero esta función lo mantenía visible. Si esto te sucede, **deshaz** la última acción (desactivar **Mantener en pantalla**) con el atajo para deshacer o desde **Barra de menús -> Editar -> Deshacer**. Después, mueve manualmente el elemento al centro de la pantalla y vuelve a desactivar **Mantener en pantalla**. Ahora debería seguir visible aunque la opción esté desactivada.

## Centrar elementos

Mientras los elementos tengan un tamaño fijo, centrarlos es tan sencillo como anclarlos a un punto de anclaje basado en el centro.

Si el tamaño del elemento cambia dinámicamente según ciertas condiciones u otros factores, es un poco más complicado, ¡pero FancyMenu tiene una función excelente para eso! En ese caso, primero ancla el elemento a un punto de anclaje basado en el centro y luego haz clic derecho sobre él. En el menú contextual, activa **Anclaje fijo**. Esta función cambia la forma en que FancyMenu calcula la posición del elemento para que siempre conserve la misma distancia respecto a su punto de anclaje, sin importar si cambia de tamaño. Con los puntos de anclaje basados en el centro, el elemento siempre conservará la misma distancia respecto al anclaje desde su centro exacto, por lo que permanecerá centrado. (Con los puntos de anclaje basados en la izquierda, conservará la misma distancia respecto al anclaje desde su lado izquierdo; y con los basados en la derecha, desde su lado derecho).

## Otras formas de mejorar el posicionamiento de los elementos

Si **todos los puntos de anclaje son correctos**, pero los elementos aún se enciman cuando la ventana es demasiado pequeña, es posible que el diseño simplemente tenga demasiados elementos para la lógica de escalado de la interfaz normal de Minecraft.

### Escala de interfaz forzada

Una forma de mejorar el posicionamiento de los elementos del diseño es forzar una escala de interfaz para el menú. Para hacerlo, **haz clic derecho en el fondo del editor** y selecciona **Forzar escala de interfaz**. Así, el menú siempre tendrá la misma escala de interfaz, sin importar la escala establecida en las opciones de Minecraft.

### Escalado automático

La última opción para corregir los elementos encimados es usar el **escalado automático**.
Esta opción ajusta automáticamente la escala del menú según el tamaño de la ventana para intentar conservar lo mejor posible la posición de los elementos al cambiar el tamaño de la ventana. Para activar el escalado automático, **haz clic derecho en el fondo del editor** y selecciona **Escalado automático**.

> [!WARNING]
> El **escalado automático** puede hacer que el **texto** de Minecraft **se vea mal**. No es un error; así funciona el renderizado de texto de Minecraft. Para los botones, una buena solución es incluir las etiquetas de los botones en la textura de fondo del botón y dejar vacía la etiqueta normal.
