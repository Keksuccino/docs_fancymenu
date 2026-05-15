---
title: Música de fondo del menú
description: Cómo personalizar la música que se reproduce en los menús.
---

# Música de fondo del menú

Es posible reemplazar la música de fondo predeterminada de los menús de Minecraft con pistas personalizadas o simplemente desactivar la música normal de Vanilla que se reproduce en los menús.

# Desactivar la música de Vanilla

FancyMenu tiene varias formas de desactivar la música de los menús de Vanilla. Esto puede ser útil si planeas reproducir otras pistas de audio en las pantallas o si simplemente no quieres que suene música en algunas pantallas.

## Globalmente

Si no quieres música en los menús en absoluto, esta es la forma más sencilla de hacerlo.

Para desactivar o reemplazar globalmente la música de los menús de Vanilla en FancyMenu 3.9.0+, ve a la barra de menú de FancyMenu en la parte superior de las pantallas y haz clic en **Personalización -> Personalizaciones globales**. Las Personalizaciones globales pueden reemplazar la música del menú sin necesidad de un paquete de recursos y sin habilitar personalizaciones para cada pantalla.

<br>
<img width="600" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/d829a35e-f23f-42a9-ad79-193de73b499b">

> Desactivar la música predeterminada de Minecraft la desactivará en todas las pantallas, no solo en la actual.
{.is-info}

## Por pantalla

Si quieres más control sobre en qué menús de Vanilla debe reproducirse la música, deberías usar el elemento **Music Controller**. Este elemento se agrega a los diseños como cualquier otro elemento haciendo **clic derecho en el fondo del editor** y luego clic en **Nuevo elemento -> Music Controller**.

Al **hacer clic derecho** en el elemento, puedes personalizar qué tipos de música que se reproducen en los menús deben desactivarse (la música normal del menú y la música del mundo que sigue reproduciéndose en pantallas que no pausan el juego, como la pantalla del Inventario).

> Este elemento admite **requisitos de carga**, ¡así que tienes aún más control sobre cuándo debe reproducirse la música de Vanilla!
{.is-info}


# Agregar música personalizada

Ahora podemos agregar la música de fondo personalizada como tal.

Si quieres reproducir la misma música personalizada en todas las pantallas y necesitas control a nivel de diseño, deberías usar un **diseño universal**, que se carga en todas las pantallas que tienen las personalizaciones habilitadas. Para un reemplazo simple y global de la música de menú, usa [Personalizaciones globales](/global-customizations) en su lugar.

Al usar un diseño universal, la música **seguirá reproduciéndose** al pasar de un menú con ese diseño habilitado a otro con el mismo diseño habilitado.

Si quieres reproducir música diferente por pantalla, usa diseños normales.

En este ejemplo usaremos **diseños universales**.

Agrega un nuevo elemento **Audio** al diseño universal, que funcionará como nuestro reproductor de música de fondo.

<br>
<img width="400" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/bddf8f46-47c5-4a00-a6f7-b5ca1df8ae67">

Ahora agrega las pistas de música que deben reproducirse en segundo plano.

<br>
<img width="300" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/824dcb90-3bd5-4c0b-96d0-e581a7c2f9f7">

Básicamente, eso ya es todo.
También puedes configurar el elemento Audio en modo aleatorio y cambiar su canal de sonido si es necesario.

Guarda el diseño y sal del editor.

# Habilitar las personalizaciones para todos los menús

Usamos un **diseño universal** en este ejemplo, porque queremos que nuestra música de fondo se reproduzca en varias pantallas.

Como los diseños solo se cargan en las pantallas que tienen las **personalizaciones habilitadas**, ahora necesitamos activarlas para cada pantalla en la que queramos que suene nuestra música.

Para hacerlo, haz clic en **Personalización** y habilita **Personalización de la pantalla actual**.

<br>
<img width="320" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/2f6527b7-ae14-4e82-abc6-3572cc6490b2">

Repite esto para cada pantalla en la que quieras que se reproduzca tu música de fondo personalizada.

¡Y listo! ¡Ahora tienes música de fondo personalizada en tus menús de Minecraft!
