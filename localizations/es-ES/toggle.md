---
title: Alternar partes de los diseños
description: Cómo alternar partes de los diseños según la entrada del usuario.
---

# Alternar partes de los diseños

A veces viene bien tener donde elegir. Quizá a algunos de tus usuarios no les guste oír constantemente a Rick Astley como música del menú, o quieran otra chica anime mona como fondo del menú.

¡No pasa nada! Puedes hacer que tus usuarios activen o desactiven partes de tus diseños, o que vayan alternando entre varias versiones de esas partes.

# Activar y desactivar

Para alternar, por ejemplo, la visibilidad de un elemento al hacer clic en un botón, solo necesitas usar una variable que se establezca al pulsar el botón, y el elemento que quieres alternar debe comprobar en sus requisitos de carga si esa variable tiene el valor correcto.

## La variable

Lo primero es crear la variable que usarás para guardar el estado de visibilidad del elemento que quieres alternar.

Para añadir una nueva variable, ve a la pestaña **Customization** en la barra de menús y haz clic en **Variables -> Manage Variables**; después, añade una nueva variable con un nombre **único**. Asegúrate de usar un nombre realmente **único** que no se esté usando ya.

Tras crear la variable, establece su valor en `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## El elemento

El siguiente paso es añadir el elemento que quieres activar o desactivar.

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

Ahora haz clic derecho sobre el elemento y selecciona **Loading Requirements**.
Esto abrirá la pantalla de gestión de requisitos. Haz clic en **Add Requirement**.

Busca el requisito **Is Variable Value**, selecciónalo y haz clic en **Edit Requirement Value**.

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

Ahora introduce el nombre de la variable que creaste antes y haz que el requisito compruebe `true` como valor.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Eso es todo para esta parte. Ahora tu elemento será visible cuando el valor de la variable sea `true`.

## El botón

Ahora tenemos que añadir un nuevo elemento Button.

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

Después de añadirlo, haz clic derecho y selecciona **Edit Action Script**.
Esto abrirá la pantalla de gestión del script de acción del botón.

Haz clic en **Add IF Statement**, añade el requisito **Is Variable Value** y establece el modo del requisito en **OPPOSITE**.

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

Ahora haz clic en **Edit Requirement Value**, igual que hiciste antes con el elemento, e introduce exactamente el mismo nombre de variable y el mismo valor que comprobar.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Como hemos establecido el modo del requisito en **OPPOSITE**, ahora comprobará si el valor de la variable NO es `true`, que es exactamente lo que queremos.

De vuelta en la pantalla Edit Action Script, ahora verás la instrucción IF que acabamos de añadir.

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

Ahora haz clic en **Add Action**, busca la acción **Set Variable Value**, selecciónala y luego haz clic en **Edit Action Value**.

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

Como valor de la acción, introduce primero el nombre de tu variable y después el valor al que quieres asignarla. Separa el nombre y el valor con `:`.
En este caso queremos establecer nuestro valor en `true`, porque esta acción se ejecutará más adelante cuando el valor NO sea `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

Ahora añade la acción a la instrucción IF arrastrándola y colocándola sobre la instrucción IF, para que solo se ejecute cuando el valor de nuestra variable NO sea `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

Después de hacerlo, selecciona la instrucción IF y haz clic en **Append ELSE Statement**.

Ahora añade otra acción **Set Variable Value**, pero en lugar de establecer el valor de la variable en `true`, establécelo en `false`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

Ahora añade la segunda acción a la instrucción ELSE, para que se ejecute si el valor de la variable SÍ es `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

¡Y eso es todo! La primera vez parece que son muchos pasos, pero en realidad es algo bastante fácil y rápido de hacer una vez te acostumbras.

Ahora puedes guardar tu diseño, salir del editor y pulsar el botón para ver si funciona.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

Si quieres, puedes usar la misma variable para otros elementos, de modo que **alternes varios elementos a la vez** al pulsar el botón.

Incluso puedes alternar diseños completos usando los **Layout-Wide Loading Requirements**. Para configurar requisitos de ámbito global del diseño, haz clic derecho en el fondo del editor. Solo asegúrate de añadir el botón a otro diseño, no al que quieres alternar.

# Recorrer valores

A diferencia de alternar entre dos valores, recorrer valores requiere que el script de acción pueda ir pasando entre más de dos valores.

La lógica del script de acción es muy similar a la que se usa para alternar, así que aquí lo dejaré bastante breve. Asegúrate de leer también la parte sobre alternar.

Añadí 3 imágenes. La primera imagen es visible cuando el valor de la variable es `1`, la segunda cuando el valor es `2` y la tercera cuando el valor es `3`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

Después de eso añadí el botón de recorrido y lo hice cambiar el valor de la variable de `1` a `2` a `3` y de vuelta a `1`.

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

Y eso es todo. Ahora guarda el diseño, sal del editor y comprueba si el botón de recorrido funciona correctamente.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
