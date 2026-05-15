---
title: Diseños universales
description: Cómo crear y usar diseños universales.
---

# ¿Qué son los diseños universales?

Los diseños universales son una función muy potente de FancyMenu que te permite crear diseños que pueden aplicarse a **varias pantallas** en lugar de solo a una pantalla concreta. Esto los hace increíblemente útiles para crear عناصر de interfaz coherentes que aparecen en todo el juego.

Piensa en los diseños universales como diseños "globales" que pueden aparecer en cualquier parte de tu juego.

# ¿Por qué usar diseños universales?

Los diseños universales son muy útiles cuando quieres:

- Añadir el mismo fondo a todas las pantallas
- Crear un logotipo o texto que aparezca en muchas pantallas
- Hacer que los elementos de audio sigan reproduciéndose entre varias pantallas
- Mantener un aspecto visual coherente en todo el juego

# Cómo funcionan los diseños universales

Cuando creas un diseño universal, se carga con **cada pantalla** del juego de forma predeterminada. Esto significa que cualquier elemento que añadas a un diseño universal (como botones, imágenes o texto) aparecerá en todas las pantallas.

¡Pero no te preocupes! También es posible hacer que el diseño universal solo se cargue en pantallas concretas. Para ello, desplázate hacia abajo hasta las secciones de **lista negra** y **lista blanca**.

# Crear un diseño universal

1. Abre cualquier pantalla del juego
2. Pulsa **Ctrl+Alt+C** para mostrar el menú de personalización
3. Ve a **Diseños → Nuevo → Para todas las pantallas [Universal]**
4. Diseña tu disposición con elementos como imágenes, texto o botones
5. Guarda tu diseño con un nombre descriptivo

# Gestionar en qué pantallas se aplica tu diseño universal

## Usar la lista negra

La lista negra te permite especificar las pantallas en las que NO quieres que aparezca tu diseño universal:

1. En el editor de diseños, haz clic derecho sobre el fondo
2. Selecciona **Configuración del diseño → Opciones de diseño universal**
3. Haz clic en **Añadir pantalla a la lista negra**
4. Introduce el identificador de la pantalla (por ejemplo, `title_screen` para la pantalla de título)

Ahora tu diseño universal se mostrará en todas las pantallas EXCEPTO en las que hayas añadido a la lista negra.

## Usar la lista blanca

La lista blanca es lo contrario: SOLO muestra tu diseño universal en pantallas concretas:

1. En el editor de diseños, haz clic derecho sobre el fondo
2. Selecciona **Configuración del diseño → Opciones de diseño universal**
3. Haz clic en **Añadir pantalla a la lista blanca**
4. Introduce el identificador de cada pantalla en la que quieras que aparezca el diseño

Al usar una lista blanca, tu diseño universal SOLO se mostrará en las pantallas que hayas indicado.

# Encontrar identificadores de pantalla

Para añadir pantallas a la lista blanca o a la lista negra, necesitas conocer sus identificadores:

1. Ve a la pantalla que quieras identificar
2. Pulsa **Ctrl+Alt+C** para abrir el menú de personalización
3. Haz clic en **Personalización → Copiar identificador de la pantalla actual**
4. El identificador se copiará al portapapeles

Puedes pegar este identificador en la lista blanca o en la lista negra.

# Habilitar la personalización para todas las pantallas

No es posible habilitar la personalización para todas las pantallas a la vez.
Esto es intencionado y evita que la gente rompa accidentalmente su juego al habilitar la personalización para una pantalla modificada que no es compatible.

# Consejos avanzados

## Gestionar el orden de carga

Cuando tienes tanto diseños universales como diseños específicos de pantalla, los diseños universales se cargan PRIMERO. Esto significa que los diseños específicos de pantalla pueden sobrescribir elementos de los diseños universales.

## Requisitos de carga

Puedes añadir requisitos de carga a tu diseño universal para que solo se cargue en ciertas condiciones:

1. Haz clic derecho en el editor
2. Elige **Configuración del diseño → Requisitos de todo el diseño**
3. Añade condiciones como la hora del día, el sistema operativo u otros requisitos
