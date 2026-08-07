---
title: Variables
description: Cómo crear y usar variables.
---
# Variables en FancyMenu

Las variables almacenan valores de texto que los diseños, acciones, marcadores de posición, requisitos, escuchas, programadores y GUI personalizados pueden reutilizar.

## Crear variables

Para crear una variable en FancyMenu:

1. Asegúrate de que no estés actualmente en el Editor de diseño.
2. Haz clic en la barra de menú en la parte superior de la pantalla.
3. Ve a **Customization -> Variables -> Manage Variables**.
4. En la pantalla "Manage Variables" que aparece, haz clic en el botón **Add Variable**.
5. Escribe un nombre para tu nueva variable y haz clic en **OK**.

¡Eso es todo! Tu variable ya está lista para usarse. Puedes verla listada en la pantalla "Manage Variables".

La ventana Manage Variables admite un menú contextual al hacer clic derecho, navegación con teclado, copiar/pegar, deshacer/rehacer, búsqueda mientras escribes, **Delete** para eliminar y **Ctrl/Command + S** para guardar.

## Establecer valores de variables

Una variable vacía no es muy útil por sí sola. Para que las variables trabajen para ti, necesitas poner datos en ellas. En FancyMenu, esto se llama "establecer el valor de la variable".

Hay dos formas principales de establecer el valor de una variable:

1. En la pantalla "Manage Variables", busca la variable en la lista, haz clic en ella y luego haz clic en **Set Value**. Escribe los datos que quieres almacenar.

2. Mientras personalizas tu menú, usa la [acción **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) en un elemento [Button](./elements#button), [Slider](./elements#slider) o [Ticker](./elements#ticker).

Por ejemplo, crea una variable llamada `clicks` y agrega la [acción **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) a un botón:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Así funciona esto:
1. El [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) recupera el valor actual de la variable `clicks`.
2. El [marcador de posición **Calculator**](./placeholders#calculator-calc) toma ese valor y le suma 1.
3. El resultado se vuelve a guardar en `clicks` usando la [acción **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

Entonces, cada vez que se haga clic en el botón, la variable `clicks` se incrementará en 1, contando efectivamente el total de clics.

## Usar variables

Ahora que tienes variables con datos, puedes usar esos datos en distintas partes de la personalización de tu menú:

* [**Loading Requirements**](./conditions): Verifica el valor de una variable para controlar cuándo aparecen los elementos. Por ejemplo, muestra un elemento cuando `clicks` sea mayor que 5 combinando [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) con el [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

* **Placeholders**: Inserta una variable en texto con el [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable), por ejemplo `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Nested Placeholders**: Puedes usar el [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) dentro del [marcador de posición **Calculator**](./placeholders#calculator-calc).

* **Actions**: Las variables pueden crear comportamiento dinámico:
  - Usa una declaración **IF** en un [script de acción](./action-scripts#what-are-statements) con [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) y el [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Combina el [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) con [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Usa variables en [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) para seleccionar una pantalla a partir del progreso o las preferencias almacenadas.

## Ejemplos de variables

Aquí hay algunos ejemplos para inspirar tu propio uso de variables:

1. **High Score**: Crea una variable `highscore` y un botón que la establezca al puntaje actual del jugador si es mayor que el valor existente. Muéstrala con el [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Difficulty Selector**: Crea variables para diferentes dificultades del juego, como `easy`, `medium` y `hard`. Usa botones para establecer la variable de dificultad y mostrar/ocultar elementos según la dificultad seleccionada.

3. **Tutorial Progress**: Agrega variables para rastrear el progreso del jugador en un tutorial, como `tutorial_step`. Incrementa la variable a medida que completan cada paso y usa requisitos de carga para revelar gradualmente más del menú.

## Persistencia, alcance y almacenamiento

Las variables se comparten en toda la instancia actual de Minecraft. No están separadas por diseño, mundo, servidor o jugador.

Los valores se guardan de inmediato en `<game-directory>/config/fancymenu/user_variables.db` y persisten tras reiniciar.

- **Reset on Launch** vacía esa variable la próxima vez que se inicia el juego.
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) elimina todos los valores de variables almacenados.
- Los nombres distinguen entre mayúsculas y minúsculas. Usa nombres simples y únicos como `tutorial_step`.

El [marcador de posición **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) devuelve `0` cuando la variable con ese nombre no existe o cuando su valor almacenado está vacío. Este valor alternativo importa en comparaciones y expresiones de calculadora.

La [acción **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) usa `variable_name:variable_value` y divide en el primer dos puntos, así que el valor puede contener más dos puntos.

No almacenes contraseñas, tokens ni otros secretos en variables de FancyMenu. Son datos de configuración legibles.
