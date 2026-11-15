---
title: Variables
description: Cómo crear y utilizar variables.
sourceBlobSha: dcd1512bc7f20f3ab535205f24a67c6489231e11
---

# Variables en FancyMenu

Las variables almacenan valores de texto que pueden reutilizar los diseños, las acciones, los placeholders, los requisitos, los listeners, los programadores y las interfaces gráficas personalizadas.

## Crear variables

Para crear una variable en FancyMenu:

1. Asegúrate de no estar actualmente en el editor de diseños. 
2. Haz clic en la barra de menús situada en la parte superior de la pantalla.
3. Ve a **Personalización -> Variables -> Gestionar variables**.
4. En la pantalla «Gestionar variables» que aparece, haz clic en el botón **Añadir variable**.
5. Escribe un nombre para la nueva variable y haz clic en **Aceptar**.

¡Eso es todo! Tu variable ya está lista para utilizarse. Puedes verla en la lista de la pantalla «Gestionar variables».

La ventana «Gestionar variables» admite un menú contextual al hacer clic derecho, navegación mediante el teclado, copiar y pegar, deshacer y rehacer, búsqueda al escribir, **Supr** para eliminar y **Ctrl/Comando + S** para guardar.

## Establecer valores de variables

Una variable vacía no resulta muy útil por sí sola. Para que las variables te sean útiles, debes introducir datos en ellas. En FancyMenu, esto se denomina «establecer el valor de la variable». 

Hay dos formas principales de establecer el valor de una variable:

1. En la pantalla «Gestionar variables», busca la variable en la lista, haz clic en ella y, después, haz clic en **Establecer valor**. Escribe los datos que quieras almacenar.

2. Mientras personalizas el menú, utiliza la [acción **Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable) en un elemento [Botón](./elements#button), [Control deslizante](./elements#slider) o [Ticker](./elements#ticker).

Por ejemplo, crea una variable llamada `clicks` y añade la [acción **Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable) a un botón:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Así es como funciona:
1. El [placeholder **Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable) recupera el valor actual de la variable `clicks`.
2. El placeholder [**Calculadora**](./placeholders#calculator-calc) toma ese valor y le suma 1.
3. El resultado se vuelve a guardar en `clicks` mediante la [acción **Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable).

Por lo tanto, cada vez que se hace clic en el botón, la variable `clicks` aumenta en 1, contando así el número total de clics.

## Utilizar variables

Ahora que tienes variables que contienen datos, puedes utilizar esos datos en distintas partes de la personalización del menú:

* [**Requisitos de carga**](./conditions): Comprueba el valor de una variable para controlar cuándo aparecen los elementos. Por ejemplo, muestra un elemento cuando `clicks` sea mayor que 5 combinando [**Es un número**](./conditions#is-number-fancymenu_visibility_requirement_is_number) con el placeholder [**Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable).

* **Placeholders**: Inserta una variable en un texto con el placeholder [**Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable), por ejemplo `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Placeholders anidados**: Puedes utilizar el placeholder [**Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable) dentro del placeholder [**Calculadora**](./placeholders#calculator-calc).

* **Acciones**: Las variables pueden crear comportamientos dinámicos:
  - Utiliza una instrucción **IF** en un [script de acciones](./action-scripts#what-are-statements) con [**Es un número**](./conditions#is-number-fancymenu_visibility_requirement_is_number) y el placeholder [**Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Combina el placeholder [**Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable) con [**Copiar texto al portapapeles**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Utiliza variables en [**Abrir pantalla o interfaz gráfica personalizada**](./action-scripts#open-screen-or-custom-gui-opengui) para seleccionar una pantalla a partir del progreso o las preferencias almacenadas.

## Ejemplos de variables

Aquí tienes algunos ejemplos para inspirarte a la hora de utilizar tus propias variables:

1. **Puntuación máxima**: Crea una variable `highscore` y un botón que la establezca en la puntuación actual del jugador si esta es superior al valor existente. Muéstrala con el placeholder [**Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Selector de dificultad**: Crea variables para los distintos niveles de dificultad del juego, como `easy`, `medium` y `hard`. Utiliza botones para establecer la variable de dificultad y muestra u oculta elementos según la dificultad seleccionada.

3. **Progreso del tutorial**: Añade variables para seguir el progreso del jugador en un tutorial, como `tutorial_step`. Incrementa la variable cuando complete cada paso y utiliza requisitos de carga para mostrar gradualmente más elementos del menú.

## Persistencia, ámbito y almacenamiento

Las variables se comparten en la instancia actual de Minecraft. No se separan por diseño, mundo, servidor o jugador.

Los valores se guardan inmediatamente en `<game-directory>/config/fancymenu/user_variables.db` y se conservan tras reiniciar el juego.

- **Restablecer al iniciar** vacía esa variable la próxima vez que se inicie el juego.
- [**Borrar todas las variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) elimina todos los valores de variables almacenados.
- Los nombres distinguen entre mayúsculas y minúsculas. Utiliza nombres sencillos y únicos, como `tutorial_step`.

El placeholder [**Obtener variable almacenada**](./placeholders#get-variable-value-fm-variable-getvariable) devuelve `0` cuando la variable indicada no existe o cuando su valor almacenado está vacío. Este valor alternativo es importante en las comparaciones y las expresiones de la calculadora.

La acción [**Establecer valor de variable**](./action-scripts#set-variable-value-fm-variable-set_variable) utiliza `variable_name:variable_value` y divide el texto en el primer signo de dos puntos, por lo que el valor puede contener más signos de dos puntos.

No almacenes contraseñas, tokens ni otros secretos en las variables de FancyMenu. Son datos de configuración legibles.
