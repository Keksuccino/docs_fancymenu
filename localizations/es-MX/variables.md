---
title: Variables
description: Cómo crear y usar variables.
---

# Variables en FancyMenu

Las variables son una función muy poderosa en FancyMenu que te permite guardar y reutilizar información en todas tus personalizaciones de menú. Funcionan como contenedores en los que puedes poner distintos tipos de datos, asignarle un nombre a cada contenedor y luego acceder a esos datos más tarde usando el nombre de la variable. Las variables abren un mundo de posibilidades para crear menús dinámicos que cambian según las condiciones que definas.

## Crear variables

Para crear una variable en FancyMenu:

1. Asegúrate de no estar actualmente en el Editor de diseño. 
2. Haz clic en la barra de menú en la parte superior de la pantalla.
3. Ve a **Customization -> Variables -> Manage Variables**.
4. En la pantalla "Manage Variables" que aparece, haz clic en el botón **Add Variable**.
5. Escribe un nombre para tu nueva variable y haz clic en **OK**.

¡Y listo! Tu variable ya está lista para usarse. Puedes verla en la lista de la pantalla "Manage Variables".

FancyMenu 3.9.0 rediseña la ventana de Manage Variables. Las acciones importantes están disponibles mediante un menú contextual con clic derecho, la lista admite navegación por teclado, las variables se pueden copiar y pegar, los cambios se pueden deshacer o rehacer, al escribir se inicia una búsqueda, **DEL** elimina la variable seleccionada y **CTRL + S** confirma la ventana.

## Asignar valores a variables

Una variable vacía no es muy útil por sí sola. Para que las variables te sirvan, necesitas ponerles datos. En FancyMenu, esto se llama "asignar el valor de la variable". 

Hay dos formas principales de asignar el valor de una variable:

1. En la pantalla "Manage Variables", busca la variable en la lista, selecciónala y luego haz clic en **Set Value**. Escribe los datos que quieres guardar.

2. Mientras personalizas tu menú, usa la acción **Set Variable** en un elemento Button, Slider o Ticker. Con esta acción, especificas el nombre de la variable y el valor que se guardará en ella. Cuando alguien, por ejemplo, hace clic en un botón con esta acción, la variable se actualizará con el nuevo valor.

Por ejemplo, supongamos que creas una variable llamada `clicks` para contar cuántas veces se presiona un botón. Agregarías la acción **Set Variable** al botón y usarías un marcador de posición en el valor de la acción para incrementar el contador de clics cada vez, así:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Así funciona esto:
1. El marcador de posición **Get Stored Variable** obtiene el valor actual de la variable `clicks`.
2. El marcador de posición **Calculator** toma ese valor y le suma 1.
3. El resultado luego se guarda de nuevo en la variable `clicks` usando la acción **Set Variable**.

Así, cada vez que se hace clic en el botón, la variable `clicks` se incrementa en 1, contando efectivamente el total de clics.

## Usar variables

Ahora que tienes variables con datos, puedes usar esa información en distintas partes de la personalización de tu menú:

* **Requisitos de carga**: Puedes revisar el valor de una variable en un requisito de carga para controlar cuándo aparecen ciertos elementos del menú. Por ejemplo, podrías hacer que un elemento solo se muestre si la variable `clicks` es mayor que 5 usando una combinación del requisito **Is Number** y el marcador de posición **Get Stored Variable**.

* **Marcadores de posición**: Las variables pueden insertarse en texto usando el marcador de posición **Get Stored Variable**. Si tienes un elemento de texto, podrías usar `{"placeholder":"getvariable","values":{"name":"clicks"}}` para mostrar el valor actual de la variable "clicks".

* **Marcadores de posición anidados**: ¡Incluso puedes usar variables dentro de otros marcadores de posición! El ejemplo de conteo de clics anterior lo demostró usando el marcador de posición **Get Stored Variable** dentro del marcador de posición **Calculator**.

* **Acciones**: Las variables pueden usarse en acciones para crear comportamientos dinámicos según sus valores. Aquí tienes algunos ejemplos:
    - Usa una instrucción **IF** en un script de acción para revisar el valor de una variable usando una combinación del requisito de carga **Is Number** y la acción **Get Stored Variable**, y realiza diferentes acciones según el resultado. Por ejemplo, podrías tener un botón que diga "¡Me has hecho clic X veces!" y usar un bloque IF para mostrar un mensaje especial si el número de clics es mayor que 10.
    - Combina el marcador de posición **Get Stored Variable** con la acción **Copy to Clipboard** para permitir que los usuarios copien el valor de una variable en su portapapeles.
    - Usa variables en la acción **Open GUI** para cargar diferentes pantallas según el progreso o las preferencias del usuario, que tú rastreas con variables.

## Ejemplos de variables

Aquí tienes algunos ejemplos para inspirar tu propio uso de variables:

1. **Puntuación más alta**: Crea una variable `highscore` y un botón que la establezca con la puntuación actual del jugador si es mayor que el valor existente. Muestra la puntuación más alta en el menú usando el marcador de posición **Get Stored Variable**.

2. **Selector de dificultad**: Crea variables para distintas dificultades del juego, como `easy`, `medium` y `hard`. Usa botones para establecer la variable de dificultad, y muestra u oculta elementos según la dificultad seleccionada.

3. **Progreso del tutorial**: Agrega variables para rastrear el progreso del jugador en un tutorial, como `tutorial_step`. Incrementa la variable a medida que completa cada paso y usa requisitos de carga para revelar gradualmente más del menú.

Las variables, combinadas con otras funciones de FancyMenu, te dan una flexibilidad increíble para crear menús adaptados a las acciones y preferencias de cada jugador. ¡Experimenta con diferentes configuraciones de variables para desbloquear todo el potencial de tus personalizaciones de menú!
