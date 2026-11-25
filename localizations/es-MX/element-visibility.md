---
title: Visibilidad de los elementos
description: >-
  Cómo mostrar y ocultar elementos con requisitos, retrasos, desvanecimientos y
  opacidad, y cómo alternar su visibilidad con un botón.
sourceBlobSha: 819fbc2639734fc8658f6fb65e9df6b1234e9cc5
---

# Visibilidad de los elementos

Los elementos no tienen que mostrarse todo el tiempo. Pueden mostrarse solo en ciertas situaciones, aparecer un poco después, desvanecerse al aparecer y desaparecer, o activarse y desactivarse con un botón.

<img width="800" alt="Un texto de bienvenida aparece gradualmente unos segundos después de abrir la pantalla; luego, un botón de Reglas del servidor hace aparecer y desaparecer gradualmente un panel de reglas" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_visibility_toggle.gif?raw=true">

En el editor de diseños, los elementos siempre se muestran para que puedas editarlos. Todo lo que se explica en esta página funciona fuera del editor.

> [!TIP]
> Todos los requisitos están en [Requisitos](/conditions).

# Mostrar elementos solo a veces

Haz clic derecho en un elemento y selecciona **Requisitos de carga**. El elemento solo se muestra mientras se cumplan todos sus [requisitos](/conditions), como «el cursor está sobre este botón», «es diciembre» o «una variable tiene este valor». FancyMenu los comprueba constantemente, así que el elemento aparece y se oculta de inmediato.

- **Modo de requisito** Invertido cambia un requisito por su opuesto, como «NO es diciembre».
- Los grupos permiten crear condiciones de «esto O aquello».
- Los elementos de Minecraft también tienen **Requisitos de carga**. Para quitar uno por completo, consulta [Elementos de Minecraft eliminados](/deleted-vanilla-elements).

Cómo agregar requisitos y combinarlos: [Requisitos](/conditions#adding-a-requirement).

## Cargar una vez por sesión

Haz clic derecho en un elemento y activa **Cargar una vez por sesión**. El elemento se muestra la primera vez que se abre su pantalla. Cuando el jugador pasa a otra pantalla, permanece oculto hasta que se reinicie el juego.

Es útil para mostrar indicaciones una sola vez por inicio del juego, como «Presiona F1 para ver los controles». Para usar la misma idea en scripts de acciones, existe el requisito [**Solo una vez por sesión**](/conditions#only-once-per-session).

# Retrasar elementos

## Retrasar la aparición

Haz clic derecho en un elemento y selecciona **Retrasar aparición**:

- **Retraso**:
  - **Sin retraso**: se muestra de inmediato.
  - **La primera vez**: espera solo la primera vez que aparece el elemento después de iniciar el juego.
  - **Cada vez**: espera cada vez que se abre la pantalla y cada vez que vuelven a cumplirse sus requisitos.
- **Retraso en segundos**: cuánto tiempo espera, por ejemplo, `1.5`.

Cambiar el tamaño de la ventana no vuelve a iniciar el retraso.

## Retrasar la desaparición

Haz clic derecho en un elemento y selecciona **Retrasar desaparición**. Cuando sus requisitos dejan de cumplirse, el elemento permanece durante el tiempo indicado en **Retraso en segundos** antes de desaparecer. **Retraso** tiene las mismas opciones que arriba.

Por ejemplo, un cuadro de información con el requisito [**El cursor está sobre el elemento**](/conditions#is-element-hovered) para un botón permanece durante 1 segundo después de que el cursor sale del botón.

# Desvanecer al aparecer y desaparecer

Haz clic derecho en un elemento y selecciona **Desvanecimiento de entrada y salida**:

- **Desvanecimiento de entrada** y **Desvanecimiento de salida**:
  - **Sin desvanecimiento**: aparece o se oculta de inmediato.
  - **Solo una vez**: se desvanece solo la primera vez después de iniciar el juego.
  - **Cada vez**: se desvanece cada vez.
- **Velocidad de desvanecimiento de entrada** y **Velocidad de desvanecimiento de salida**: con el valor `1`, el desvanecimiento tarda 2.5 segundos. `2` es el doble de rápido.

Los elementos se desvanecen al abrirse la pantalla y cuando se cumplen sus requisitos. Si usas **Retrasar aparición**, el desvanecimiento comienza después del retraso.

El desvanecimiento de salida solo ocurre cuando los requisitos ocultan el elemento, no cuando se cierra la pantalla.

# Opacidad

Haz clic derecho en un elemento y selecciona **Opacidad**: `1.0` significa que es completamente visible, `0.5` que es semitransparente y `0.0` que es invisible. La mayoría de los elementos tiene esta opción.

La opacidad admite [marcadores de posición](/placeholders) y [variables](/variables), como `$$panel_opacity`. Los desvanecimientos de entrada se detienen al llegar a la opacidad del elemento.

# Alternar elementos con un botón

Un botón puede mostrar y ocultar elementos, como el panel de reglas del GIF de arriba. Una [variable](/variables) recuerda si el panel está visible.

1. Haz clic derecho en el panel y selecciona **Requisitos de carga**. Agrega [**El valor de la variable es (variable de FM)**](/conditions#is-variable-value-fm-variable) con la variable `show_rules` y el valor `true`.
2. Haz clic derecho en el botón y selecciona **Editar script de acciones**.
3. Haz clic derecho en el área del script y selecciona **Agregar instrucción IF**. Asígnale el mismo requisito que al panel.
4. Dentro de IF, agrega [**Establecer el valor de la variable (variable de FM)**](/action-scripts#set-variable-value-fm-variable) con este valor:

   ```
   show_rules:false
   ```

5. Haz clic derecho en IF y selecciona **Agregar instrucción ELSE**. Dentro de ELSE, agrega **Establecer el valor de la variable (variable de FM)** con este valor:

   ```
   show_rules:true
   ```

Así, cada clic invierte el valor de la variable: los paneles visibles se ocultan y los paneles ocultos se muestran. Todos los elementos que tengan el mismo requisito aparecen y se ocultan juntos. Para que el efecto se vea más fluido, configura **Desvanecimiento de entrada** y **Desvanecimiento de salida** del panel en **Cada vez**.

Más información sobre IF y ELSE en [Scripts de acciones](/action-scripts#if-else-if-and-else).

> [!NOTE]
> Las variables se conservan al cerrar el juego, así que el panel seguirá abierto la próxima vez que inicies el juego. Para cerrarlo cada vez que inicies, haz clic derecho en la variable en **Administrar variables** y activa **Borrar variable al iniciar el juego**.

## Alternar entre varias versiones

Un botón también puede alternar entre más de dos versiones, como tres fondos:

1. En **barra de menú -> Personalización -> Administrar variables**, agrega la variable de texto `background` con el valor `0`.
2. Asigna a los tres [elementos de imagen](/elements#image) el requisito **El valor de la variable es (variable de FM)** para `background`, con los valores `0`, `1` y `2`.
3. Asigna al botón **Establecer el valor de la variable (variable de FM)** con este valor. Cuenta `0`, `1`, `2` y vuelve a empezar en `0`:

   ```
   background:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"getvariable","values":{"name":"background"}} + 1) % 3"}}
   ```

Para agregar más versiones, cambia el `3` del final. Consulta [**Calculadora**](/placeholders#calculator) para ver cómo funcionan las operaciones matemáticas.

# Activar y desactivar diseños

Para mostrar u ocultar un diseño completo:

- **Requisitos de carga [para todo el diseño]** en el menú que aparece al hacer clic derecho en el fondo del editor funciona igual que los requisitos de los elementos. Consulta [Requisitos para todo el diseño](/conditions#layout-wide-requirements).
- Las acciones [**Alternar diseño**](/action-scripts#toggle-layout), [**Activar diseño**](/action-scripts#enable-layout) y [**Desactivar diseño**](/action-scripts#disable-layout) activan y desactivan un diseño por su nombre.

Coloca el botón en un diseño distinto del que desactiva. De lo contrario, el botón desaparecerá junto con él y no habrá forma de volver a activar el diseño.
