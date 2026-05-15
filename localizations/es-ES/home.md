---
title: Primeros pasos
description: ¡El mundo de FancyMenu te espera! ¡Este es el comienzo de algo precioso!
---

# Para desarrolladores

Si eres desarrollador y quieres crear un addon para FancyMenu o integrar FancyMenu en tu mod, deberías echar un vistazo a la [documentación para desarrolladores](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki).

# Primeros pasos

La primera vez que usas FancyMenu puede resultar un poco abrumadora, pero no te preocupes: ¡la mayor parte se entiende bastante bien en cuanto empiezas a trabajar con ello!

> Por favor, **ten en cuenta** que esta página solo sirve para introducirte en FancyMenu y ayudarte con tus **primeros pasos**.
Asegúrate también de consultar el resto de la documentación para obtener información más detallada sobre las funciones de FancyMenu.
{.is-info}

# La barra de menú

Una de las primeras cosas que notarás al iniciar el juego es la **barra de menú** en la parte superior de cada menú.

La **barra de menú** es tu punto de entrada a prácticamente todas las funciones de FancyMenu, como **crear diseños** para **personalizar menús**, cambiar el **título y el icono de la ventana** y mucho más.

> Si has pulsado accidentalmente algunas teclas y la **barra de menú ha desaparecido**, puedes recuperarla pulsando **CTRL + ALT + C**.
{.is-warning}

<img width="650" alt="menu_bar" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/menu_bar.png?raw=true">

# Tu primer diseño

Como probablemente quieras personalizar los menús de Minecraft, ¡déjame contarte algo sobre los **diseños**!

Los diseños son como capas de personalización para los menús y te permiten añadir nuevos elementos y personalizar los existentes.

Para crear un nuevo diseño para un **menú específico**:
1. Abre el menú para el que quieras crear un diseño (por ejemplo, la pantalla de título)
2. Abre la pestaña **Personalización** de la **barra de menú**

Las personalizaciones están desactivadas por defecto para todos los menús y tienes que activarlas para cada menú que quieras personalizar, así que primero hagamos clic en la entrada **"Personalización de la pantalla actual: desactivada"**, que cambiará el interruptor a **Activada**.

<img width="475" alt="toggle_customizations" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/toggle_customizations.png?raw=true">

Después de hacerlo, haz clic en **Diseños -> Nuevo -> Para la pantalla actual**.

Esto abrirá el **editor de diseños**, donde podrás añadir elementos al diseño y personalizar elementos de Vanilla y de mods (como los botones).

<img width="550" alt="new_layout_current" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/new_layout_current.png?raw=true">

## Editar el diseño

A la mayoría de las opciones de personalización se puede acceder haciendo **clic derecho en el fondo del editor**.

Al hacerlo, se abrirá un menú contextual con muchas opciones, como personalizar el **fondo del menú** o **añadir elementos** al diseño.

<br>
<img width="350" alt="context_menu" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/context_menu.png?raw=true">

## Añadir elementos a los diseños

Para añadir un nuevo elemento a tu diseño, haz **clic derecho** sobre el fondo del editor.

En el menú contextual que se abre, haz clic en **Nuevo elemento** y elige uno de los muchos tipos de elementos.

<img width="525" alt="add_element" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/add_element.png?raw=true">

## Personalizar elementos

Para personalizar un elemento, haz **clic derecho** sobre él, lo que abrirá un menú contextual con todo lo que puedes personalizar para ese tipo de elemento.

Además de los elementos que hayas añadido, también puedes personalizar elementos de Vanilla (aunque a veces hay menos opciones para ellos)

<img width="525" alt="element_customization" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/element_customization.png?raw=true">

> [!IMPORTANT]
> ¡Algunos menús contextuales como este son **desplazables**!

## Posicionar elementos

Cada elemento en FancyMenu está conectado a un **punto de anclaje**.

Los puntos de anclaje son necesarios para calcular la posición de un elemento y, si se usan correctamente, evitan que los elementos se solapen entre sí, se salgan de la pantalla o se muevan al lugar equivocado al cambiar el tamaño de la ventana.

Son el punto de origen desde el que se calcula la posición del elemento.

Por defecto, los elementos están conectados al punto de anclaje **"Centro de la pantalla"**, que básicamente es el centro exacto de la pantalla, sin importar el tamaño de la ventana.
Así que, por ejemplo, si un elemento está a 2 centímetros del centro de la pantalla y está conectado al anclaje **"Centro de la pantalla"**, ese elemento estará **siempre** a 2 centímetros del centro de la pantalla, sin importar el tamaño de la ventana.

Puedes ver el punto de anclaje al que está conectado un elemento cuando lo arrastras. Esto también mostrará, por defecto, todos los demás puntos de anclaje. Puedes pasar el cursor por encima de un punto de anclaje mientras arrastras un elemento para cambiar el anclaje del elemento al punto sobre el que estás pasando el cursor.

¡Incluso puedes usar un elemento como punto de anclaje para otros elementos! Solo tienes que pasar el cursor por encima de un elemento mientras arrastras otro y el punto de anclaje del elemento arrastrado cambiará al elemento sobre el que estás pasando el cursor.

**[Aprende más sobre cómo posicionar tus elementos.](/positioning-elements)**

<img width="650" alt="anchor_points" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/anchor_points.png?raw=true">

## Guardar tu trabajo

¡No olvides guardar tu obra maestra!

Verás un indicador de "Cambios sin guardar" en la esquina superior derecha del editor si necesitas guardar tus cambios antes de cerrar.

¡Guarda tu trabajo haciendo clic en **Diseño -> Guardar**!

<img width="375" alt="save_your_work" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/save_your_work.png?raw=true">

> [!TIP]
> También puedes guardar tu trabajo usando el atajo de teclado **CTRL + S**

*¡Enhorabuena! ¡Ahora puedes hacer que los menús de Minecraft se vean mucho más bonitos!*
