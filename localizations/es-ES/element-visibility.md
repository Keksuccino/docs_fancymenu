---
title: Visibilidad de los elementos
description: >-
  Cómo mostrar y ocultar elementos con requisitos, retrasos, fundidos y
  opacidad, y cómo alternar su visibilidad con un botón.
sourceBlobSha: 819fbc2639734fc8658f6fb65e9df6b1234e9cc5
---

# Visibilidad de los elementos

Los elementos no tienen que mostrarse todo el tiempo. Pueden aparecer solo en determinadas situaciones, mostrarse un poco más tarde, aparecer y desaparecer gradualmente o activarse y desactivarse con un botón.

<img width="800" alt="Un texto de bienvenida aparece gradualmente unos segundos después de abrirse la pantalla; después, un botón de normas del servidor muestra y oculta gradualmente un panel de normas" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_visibility_toggle.gif?raw=true">

En el editor de diseño, los elementos siempre se muestran para que puedas seguir editándolos. Todo lo que se explica en esta página funciona fuera del editor.

> [!TIP]
> Consulta todos los requisitos en [Requisitos](/conditions).

# Mostrar elementos solo a veces

Haz clic con el botón derecho en un elemento y selecciona **Requisitos de carga**. El elemento solo se muestra mientras se cumplan todos sus [requisitos](/conditions), como «el cursor está sobre este botón», «es diciembre» o «una variable tiene este valor». FancyMenu los comprueba constantemente, así que el elemento aparece y desaparece al momento.

- **Modo de requisito**: la opción Invertido invierte un requisito, como «NO es diciembre».
- Los grupos permiten expresar «esto O aquello».
- Los elementos de Minecraft también tienen **Requisitos de carga**. Para eliminar uno por completo, consulta [Elementos de Minecraft eliminados](/deleted-vanilla-elements).

Consulta cómo añadir y combinar requisitos en [Requisitos](/conditions#adding-a-requirement).

## Cargar una vez por sesión

Haz clic con el botón derecho en un elemento y activa **Cargar una vez por sesión**. El elemento se muestra la primera vez que se abre su pantalla. Cuando el jugador pasa a otra pantalla, permanece oculto hasta que se reinicia el juego.

Es útil para mostrar una sola vez por inicio del juego indicaciones como «Pulsa F1 para ver los controles». Para usar la misma idea en scripts de acción, puedes utilizar el requisito [**Solo una vez por sesión**](/conditions#only-once-per-session).

# Retrasar elementos

## Retrasar la aparición

Haz clic con el botón derecho en un elemento y selecciona **Retrasar aparición**:

- **Retraso**:
  - **Sin retraso**: aparece de inmediato.
  - **La primera vez**: espera solo la primera vez que aparece el elemento después de iniciar el juego.
  - **Cada vez**: espera cada vez que se abre la pantalla y cada vez que vuelven a cumplirse sus requisitos.
- **Retraso en segundos**: cuánto tiempo espera, por ejemplo, `1.5`.

Cambiar el tamaño de la ventana no vuelve a iniciar el retraso.

## Retrasar la desaparición

Haz clic con el botón derecho en un elemento y selecciona **Retrasar desaparición**. Cuando dejan de cumplirse sus requisitos, el elemento permanece durante el tiempo indicado en **Retraso en segundos** antes de desaparecer. **Retraso** ofrece las mismas opciones que en el apartado anterior.

Por ejemplo, un cuadro informativo con el requisito [**El cursor está sobre el elemento**](/conditions#is-element-hovered) para un botón permanece durante 1 segundo después de que el cursor deja de estar sobre el botón.

# Aparición y desaparición gradual

Haz clic con el botón derecho en un elemento y selecciona **Aparición/desaparición gradual**:

- **Aparición gradual** y **Desaparición gradual**:
  - **Sin fundido**: aparece o desaparece de inmediato.
  - **Solo una vez**: el fundido se aplica solo la primera vez después de iniciar el juego.
  - **Cada vez**: el fundido se aplica cada vez.
- **Velocidad de aparición gradual** y **Velocidad de desaparición gradual**: con el valor `1`, el fundido dura 2,5 segundos. `2` es el doble de rápido.

Los elementos aparecen gradualmente cuando se abre la pantalla y cuando se cumplen sus requisitos. Si se usa **Retrasar aparición**, el fundido empieza después del retraso.

La desaparición gradual solo se aplica cuando los requisitos ocultan el elemento, no cuando se cierra la pantalla.

# Opacidad

Haz clic con el botón derecho en un elemento y selecciona **Opacidad**: `1.0` significa que es totalmente visible, `0.5` que es semitransparente y `0.0` que es invisible. La mayoría de los elementos tienen esta opción.

La opacidad admite [marcadores de posición](/placeholders) y [variables](/variables), como `$$panel_opacity`. Los fundidos de aparición se detienen al alcanzar la opacidad del elemento.

# Alternar elementos con un botón

Un botón puede mostrar y ocultar elementos, como el panel de normas del GIF anterior. Una [variable](/variables) recuerda si se muestra el panel.

1. Haz clic con el botón derecho en el panel y selecciona **Requisitos de carga**. Añade [**El valor de la variable es (variable FM)**](/conditions#is-variable-value-fm-variable) con la variable `show_rules` y el valor `true`.
2. Haz clic con el botón derecho en el botón y selecciona **Editar script de acción**.
3. Haz clic con el botón derecho en el área del script y selecciona **Añadir instrucción IF**. Añádele el mismo requisito que al panel.
4. Añade [**Establecer valor de variable (variable FM)**](/action-scripts#set-variable-value-fm-variable) dentro de IF, con este valor:

   ```
   show_rules:false
   ```

5. Haz clic con el botón derecho en IF y selecciona **Añadir instrucción ELSE**. Añade **Establecer valor de variable (variable FM)** dentro de ELSE, con este valor:

   ```
   show_rules:true
   ```

Así, cada clic invierte el valor de la variable: los paneles visibles se ocultan y los paneles ocultos se muestran. Todos los elementos con el mismo requisito aparecen y desaparecen a la vez. Para conseguir una transición fluida, configura **Aparición gradual** y **Desaparición gradual** del panel en **Cada vez**.

Encontrarás más información sobre IF y ELSE en [Scripts de acción](/action-scripts#if-else-if-and-else).

> [!NOTE]
> Las variables se conservan al cerrar el juego, así que el panel seguirá abierto la próxima vez que lo inicies. Para que se cierre cada vez que inicies el juego, haz clic con el botón derecho en la variable dentro de **Administrar variables** y activa **Borrar variable al iniciar el juego**.

## Alternar entre varias versiones

Un botón también puede alternar entre más de dos versiones, por ejemplo, entre tres fondos:

1. En **barra de menús -> Personalización -> Administrar variables**, añade la variable de texto `background` con el valor `0`.
2. Añade a los tres [elementos de imagen](/elements#image) el requisito **El valor de la variable es (variable FM)** para `background`, con los valores `0`, `1` y `2`.
3. Añade al botón **Establecer valor de variable (variable FM)** con este valor. Va contando `0`, `1`, `2` y vuelve a empezar en `0`:

   ```
   background:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"getvariable","values":{"name":"background"}} + 1) % 3"}}
   ```

Para añadir más versiones, cambia el `3` del final. Consulta [**Calculadora**](/placeholders#calculator) para saber cómo funcionan los cálculos.

# Activar y desactivar diseños

Para mostrar u ocultar un diseño completo:

- **Requisitos de carga [para todo el diseño]** en el menú contextual del fondo del editor funciona igual que los requisitos de los elementos. Consulta [Requisitos para todo el diseño](/conditions#layout-wide-requirements).
- Las acciones [**Alternar diseño**](/action-scripts#toggle-layout), [**Activar diseño**](/action-scripts#enable-layout) y [**Desactivar diseño**](/action-scripts#disable-layout) permiten activar y desactivar un diseño por su nombre.

Coloca el botón en un diseño distinto del que desactiva. De lo contrario, el botón desaparecerá con el diseño y no habrá forma de volver a activarlo.
