---
title: Aleatorizar diseños
description: Cómo aleatorizar diseños completos o partes de ellos.
---

# Aleatorización

FancyMenu tiene muchas funciones que te ayudan a aleatorizar diseños o partes de ellos.

Esto puede ser útil, por ejemplo, si quieres que los usuarios vean fondos de pantalla diferentes cada vez que abran una pantalla o consejos aleatorios en la pantalla de carga.

# Aleatorizar diseños

Hay una función en FancyMenu que te permite crear un grupo de diseños y el sistema elegirá automáticamente un diseño aleatorio de ese grupo. De este modo, básicamente puedes mostrar un diseño de menú completamente distinto y aleatorio cada vez que el usuario inicia el juego o abre una pantalla, pero también se puede usar para cambiar solo partes de la pantalla, por ejemplo, el fondo.

## Modo aleatorio

Para aleatorizar diseños, debes habilitar el **Modo aleatorio** en cada diseño que deba poder seleccionarse aleatoriamente. Para hacerlo, haz **clic derecho** sobre el **fondo del editor** y busca la opción **Modo aleatorio**.

<br>

<img width="351" alt="Captura_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/ef0f22d5-2f48-47cd-b526-d12415d8e099">

## Identificador de grupo aleatorio

Después de habilitar el modo aleatorio, debes establecer su **Identificador de grupo aleatorio**.
Este número debe ser **el mismo** para todos los diseños que deban pertenecer al **mismo grupo**.

<br>

<img width="301" alt="Captura_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/dde0c94e-9729-4251-9aca-32a55c3dfd02">

<br>

<img width="377" alt="Captura_8" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/25e7777c-0503-4e54-b866-e85647241eee">

## Comportamiento de la aleatorización

Si solo quieres que el sistema elija un diseño aleatorio del grupo **una vez por sesión de juego**, activa **Aleatorizar solo la primera vez**. Esto hará que elija un diseño la primera vez que se abra la pantalla y luego use siempre el diseño que eligió la primera vez. Si esta opción está desactivada, elegirá un diseño aleatorio cada vez que se abra la pantalla.

<br>

<img width="305" alt="Captura_9" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/355e49eb-73b0-4646-aeb2-c6f113f6ce3b">

# Escenario de ejemplo 1: Fondo

Supongamos que quieres aleatorizar el fondo de la pantalla de título.

Para hacerlo, necesitas crear **un diseño por cada fondo** y _**SOLO**_ cambiar el fondo en estos diseños, además de habilitar el modo aleatorio con el identificador de grupo aleatorio correcto.

En este ejemplo usamos el identificador de grupo aleatorio **10**. Este identificador debe configurarse en todos los diseños de este grupo de diseños aleatorios.

La forma más sencilla de hacerlo es preparar un diseño con el identificador de grupo aleatorio correcto y luego usar **Guardar como**. Cambia el fondo cada vez que guardes el diseño con un nombre nuevo; así acabarás con varios diseños con fondos distintos y uno de esos diseños se elegirá cada vez que abras la pantalla o una vez por sesión de juego.

# Escenario de ejemplo 2: Elemento

Otro caso de uso habitual es aleatorizar un elemento de texto o de imagen.

Igual que con el fondo, crea un diseño por cada versión del elemento que quieras elegir aleatoriamente. Añade solo el elemento a los diseños y nada más. No personalices nada ni añadas otros elementos.

Después, guarda todos los diseños con el mismo identificador de grupo aleatorio y se elegirá un diseño del grupo al abrir la pantalla o iniciar el juego.
