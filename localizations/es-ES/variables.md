---
title: Variables
description: Cómo crear y usar variables.
---

# Variables en FancyMenu

Las variables son una función muy potente de FancyMenu que te permite almacenar y reutilizar información en todas tus personalizaciones del menú. Funcionan como contenedores en los que puedes guardar distintos tipos de datos, dar a cada contenedor un nombre y luego acceder a esos datos más adelante usando el nombre de la variable. Las variables abren un mundo de posibilidades para crear menús dinámicos que cambian en función de las condiciones que definas.

## Crear variables

Para crear una variable en FancyMenu:

1. Asegúrate de que no estás actualmente en el Editor de diseño. 
2. Haz clic en la barra de menú de la parte superior de la pantalla.
3. Ve a **Customization -> Variables -> Manage Variables**.
4. En la pantalla "Manage Variables" que aparece, haz clic en el botón **Add Variable**.
5. Escribe un nombre para tu nueva variable y haz clic en **OK**.

¡Eso es todo! Tu variable ya está lista para usarse. Puedes verla en la lista de la pantalla "Manage Variables".

FancyMenu 3.9.0 rediseña la ventana Manage Variables. Las acciones importantes están disponibles mediante un menú contextual al hacer clic derecho, la lista admite navegación con el teclado, las variables se pueden copiar y pegar, los cambios se pueden deshacer/rehacer, al escribir se inicia una búsqueda, **DEL** elimina la variable seleccionada y **CTRL + S** confirma la ventana.

## Establecer valores de variables

Una variable vacía por sí sola no es muy útil. Para que las variables te sirvan, necesitas introducir datos en ellas. En FancyMenu, esto se llama "establecer el valor de la variable". 

Hay dos formas principales de establecer el valor de una variable:

1. En la pantalla "Manage Variables", busca la variable en la lista, haz clic en ella y luego haz clic en **Set Value**. Escribe los datos que quieres almacenar.

2. Mientras personalizas tu menú, usa la acción **Set Variable** en un elemento de botón, deslizador o ticker. Con esta acción, especificas el nombre de la variable y el valor que se almacenará en ella. Cuando alguien, por ejemplo, hace clic en un botón con esta acción, la variable se actualizará con el nuevo valor.

Por ejemplo, supongamos que creas una variable llamada `clicks` para contar cuántas veces se pulsa un botón. Añadirías la acción **Set Variable** al botón y usarías un marcador de posición en el valor de la acción para incrementar el contador de clics cada vez, así:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Así es como funciona esto:
1. El marcador de posición **Get Stored Variable** recupera el valor actual de la variable `clicks`.
2. El marcador de posición **Calculator** toma ese valor y le suma 1.
3. El resultado se vuelve a almacenar en la variable `clicks` usando la acción **Set Variable**.

Así, cada vez que se haga clic en el botón, la variable `clicks` aumentará en 1, contando de forma efectiva el total de clics.

## Usar variables

Ahora que tienes variables que almacenan datos, puedes usar esos datos en distintas partes de la personalización de tu menú:

* **Requisitos de carga**: Puedes comprobar el valor de una variable en un requisito de carga para controlar cuándo aparecen ciertos elementos del menú. Por ejemplo, podrías hacer que un elemento solo se muestre si la variable `clicks` es mayor que 5 usando una combinación del requisito **Is Number** y el marcador de posición **Get Stored Variable**.

* **Marcadores de posición**: Las variables se pueden insertar en texto usando el marcador de posición **Get Stored Variable**. Si tienes un elemento de texto, podrías usar `{"placeholder":"getvariable","values":{"name":"clicks"}}` para mostrar el valor actual de la variable "clicks".

* **Marcadores de posición anidados**: ¡Incluso puedes usar variables dentro de otros marcadores de posición! El ejemplo de conteo de clics anterior lo demostró usando el marcador de posición **Get Stored Variable** dentro del marcador de posición **Calculator**.

* **Acciones**: Las variables se pueden usar en acciones para crear comportamientos dinámicos basados en los valores de las variables. Aquí tienes algunos ejemplos:
    - Usa una instrucción **IF** en un script de acción para comprobar el valor de una variable usando una combinación del requisito de carga **Is Number** y la acción **Get Stored Variable**, y realizar distintas acciones según el resultado. Por ejemplo, podrías tener un botón que diga "¡Me has pulsado X veces!" y usar un bloque IF para mostrar un mensaje especial si el número de clics es superior a 10.
    - Combina el marcador de posición **Get Stored Variable** con la acción **Copy to Clipboard** para permitir que los usuarios copien el valor de una variable al portapapeles.
    - Usa variables en la acción **Open GUI** para cargar distintas pantallas según el progreso o las preferencias del usuario, que tú controlas con variables.

## Ejemplos de variables

Aquí tienes algunos ejemplos para inspirarte en el uso de variables:

1. **Puntuación más alta**: Crea una variable `highscore` y un botón que la establezca con la puntuación actual del jugador si es superior al valor existente. Muestra la puntuación más alta en el menú usando el marcador de posición **Get Stored Variable**.

2. **Selector de dificultad**: Crea variables para distintas dificultades del juego, como `easy`, `medium` y `hard`. Usa botones para establecer la variable de dificultad, y muestra u oculta elementos según la dificultad seleccionada.

3. **Progreso del tutorial**: Añade variables para hacer seguimiento del progreso del jugador en un tutorial, como `tutorial_step`. Incrementa la variable a medida que completan cada paso y usa requisitos de carga para revelar gradualmente más partes del menú.

Las variables, combinadas con otras funciones de FancyMenu, te dan una flexibilidad increíble para crear menús adaptados a las acciones y preferencias de cada jugador. ¡Experimenta con distintas configuraciones de variables para desbloquear todo el potencial de tus personalizaciones de menú!
