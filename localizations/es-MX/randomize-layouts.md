---
title: Aleatorizar diseños
description: Cómo aleatorizar diseños completos o partes de ellos.
---

# Aleatorización

FancyMenu tiene muchas funciones que te ayudan a aleatorizar diseños o partes de ellos.

Esto puede ser útil, por ejemplo, si quieres que los usuarios vean diferentes fondos de pantalla cada vez que abren una pantalla o consejos aleatorios en la pantalla de carga.

# Aleatorizar diseños

Hay una función en FancyMenu que te permite crear un grupo de diseños y el sistema elegirá automáticamente un diseño aleatorio de ese grupo. Al hacer eso, básicamente puedes mostrar un menú completamente distinto y aleatorio cada vez que el usuario inicia el juego o abre una pantalla, pero también se puede usar para cambiar solo partes de la pantalla, por ejemplo, el fondo.

## Modo aleatorio

Para aleatorizar diseños, necesitas habilitar el **Modo aleatorio** en cada diseño que deba ser una opción posible para la aleatorización. Para hacerlo, haz **clic derecho** en el **fondo del editor** y busca la opción **Modo aleatorio**.

<br>

<img width="351" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/ef0f22d5-2f48-47cd-b526-d12415d8e099">

## Identificador de grupo aleatorio

Después de habilitar el modo aleatorio, necesitas establecer su **Identificador de grupo aleatorio**.
Este número necesita ser **el mismo** para todos los diseños que deban estar en el **mismo grupo**.

<br>

<img width="301" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/dde0c94e-9729-4251-9aca-32a55c3dfd02">

<br>

<img width="377" alt="Screenshot_8" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/25e7777c-0503-4e54-b866-e85647241eee">

## Comportamiento de la aleatorización

Si solo quieres que el sistema elija un diseño aleatorio del grupo **una sola vez por sesión de juego**, habilita **Aleatorizar solo la primera vez**. Esto hará que elija un diseño la primera vez que se abra la pantalla y después siempre use el diseño que eligió la primera vez. Si esto está deshabilitado, elegirá un diseño aleatorio cada vez que se abra la pantalla.

<br>

<img width="305" alt="Screenshot_9" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/355e49eb-73b0-4646-aeb2-c6f113f6ce3b">

# Escenario de ejemplo 1: Fondo

Digamos que quieres aleatorizar el fondo de la pantalla de título.

Para hacerlo, necesitas crear **un diseño por cada fondo** y _**SOLO**_ cambiar el fondo en esos diseños y habilitar el modo aleatorio con el identificador de grupo aleatorio correcto.

En este ejemplo usamos el identificador de grupo aleatorio **10**. Este identificador debe configurarse en cada diseño de este grupo de diseños aleatorios.

La forma más fácil de hacerlo es preparar un diseño con el identificador de grupo aleatorio correcto y luego usar **Guardar como**. Cambia el fondo cada vez que guardes el diseño con un nombre nuevo; así terminarás con varios diseños con fondos diferentes y uno de esos diseños se elegirá cada vez que abras la pantalla o una vez por sesión de juego.

# Escenario de ejemplo 2: Elemento

Otro caso de uso común es aleatorizar un elemento de texto o imagen.

Igual que con el fondo, crea un diseño por cada versión del elemento que quieras elegir aleatoriamente. Solo agrega el elemento a los diseños y nada más. No personalices nada ni agregues otros elementos.

Después, simplemente guarda todos los diseños con el mismo identificador de grupo aleatorio y se elegirá un diseño del grupo cuando abras la pantalla o inicies el juego.
