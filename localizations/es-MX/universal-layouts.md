---
title: Diseños universales
description: Cómo crear y usar diseños universales.
---

# ¿Qué son los diseños universales?

Los diseños universales son una función poderosa de FancyMenu que te permite crear diseños que pueden aplicarse a **varias pantallas** en lugar de solo a una pantalla específica. Esto los hace increíblemente útiles para crear elementos de interfaz consistentes que aparecen en todo tu juego.

Piensa en los diseños universales como diseños "globales" que pueden aparecer en cualquier parte de tu juego.

# ¿Por qué usar diseños universales?

Los diseños universales son muy útiles cuando quieres:

- Agregar el mismo fondo a todas las pantallas
- Crear un logo o texto que aparezca en muchas pantallas
- Hacer que los elementos de audio sigan reproduciéndose entre varias pantallas
- Lograr una apariencia uniforme en todo tu juego

# Cómo funcionan los diseños universales

Cuando creas un diseño universal, se carga con **cada pantalla** del juego de forma predeterminada. Esto significa que cualquier elemento que agregues a un diseño universal (como botones, imágenes o texto) aparecerá en todas las pantallas.

¡Pero no te preocupes! También es posible hacer que el diseño universal solo se cargue en pantallas específicas. Para eso, desplázate hacia abajo a las secciones de **lista negra** y **lista blanca**.

# Crear un diseño universal

1. Abre cualquier pantalla del juego
2. Presiona **Ctrl+Alt+C** para mostrar el menú de personalización
3. Ve a **Layouts → New → For All Screens [Universal]**
4. Diseña tu layout con elementos como imágenes, texto o botones
5. Guarda tu layout con un nombre descriptivo

# Administrar en qué pantallas aparece tu diseño universal

## Usar la lista negra

La lista negra te permite especificar en qué pantallas NO quieres que aparezca tu diseño universal:

1. En el Editor de Layouts, haz clic derecho sobre el fondo
2. Selecciona **Layout Settings → Universal Layout Options**
3. Haz clic en **Add Screen To Blacklist**
4. Escribe el identificador de la pantalla (como `title_screen` para la pantalla de título)

Ahora tu diseño universal se mostrará en todas las pantallas EXCEPTO en las que agregaste a la lista negra.

## Usar la lista blanca

La lista blanca es lo contrario: SOLO muestra tu diseño universal en pantallas específicas:

1. En el Editor de Layouts, haz clic derecho sobre el fondo
2. Selecciona **Layout Settings → Universal Layout Options**
3. Haz clic en **Add Screen To Whitelist**
4. Escribe el identificador de cada pantalla en la que quieras que aparezca el diseño

Al usar una lista blanca, tu diseño universal SOLO se mostrará en las pantallas que hayas indicado.

# Encontrar identificadores de pantalla

Para agregar pantallas a la lista blanca o negra, necesitas conocer sus identificadores:

1. Ve a la pantalla que quieres identificar
2. Presiona **Ctrl+Alt+C** para abrir el menú de personalización
3. Haz clic en **Customization → Copy Identifier of Current Screen**
4. El identificador ahora se copió a tu portapapeles

Puedes pegar este identificador en la lista blanca o negra.

# Habilitar la personalización para todas las pantallas

No es posible habilitar la personalización para todas las pantallas al mismo tiempo.
Esto está diseñado así y evita que la gente descomponga accidentalmente su juego al habilitar la personalización para una pantalla modificada que no es compatible.

# Consejos avanzados

## Administrar el orden de carga

Cuando tienes tanto diseños universales como diseños específicos de una pantalla, los diseños universales se cargan PRIMERO. Esto significa que los diseños específicos de una pantalla pueden sobrescribir elementos de los diseños universales.

## Requisitos de carga

Puedes agregar requisitos de carga a tu diseño universal para que solo se cargue bajo ciertas condiciones:

1. Haz clic derecho en el editor
2. Elige **Layout Settings → Layout-Wide Requirements**
3. Agrega condiciones como la hora del día, el sistema operativo u otros requisitos
