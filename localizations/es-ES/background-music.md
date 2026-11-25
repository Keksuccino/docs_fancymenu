---
title: Música de fondo de los menús
description: Personaliza la música de los menús.
sourceBlobSha: 46d219f5573b915991f23082cfbc42e6ed11d132
---

# Música de fondo de los menús

FancyMenu puede desactivar la música de los menús de Vanilla, reproducir una lista global de pistas o usar [elementos de audio](/elements#audio) para reproducir música específica de cada diseño.

# Música global de los menús

Abre [**Personalizaciones globales**](/global-customizations) desde **Personalización -> Personalizaciones globales**, fuera del editor de diseños.

Usa estos ajustes:

- **Reproducir música de los menús de Vanilla** activa o desactiva la música de los menús de Vanilla en todo el juego.
- **Pistas de música personalizadas para los menús** permite administrar la lista global de pistas que sustituye a la música predeterminada.

> [!IMPORTANT]
> Las pistas personalizadas globales solo se reproducen cuando no hay ningún mundo cargado, por ejemplo, en la pantalla de título. Para reproducir audio en los menús dentro del juego, usa un elemento [**Audio**](/elements#audio).

Las pistas globales usan el canal de sonido Música. La primera pista comienza a reproducirse al cabo de unos cinco segundos; las siguientes tienen un retraso aleatorio de entre uno y treinta segundos. La selección es aleatoria y, si hay más de una pista configurada, evita repetir inmediatamente la pista anterior.

# Control de la música por pantalla

Añade un elemento [**Controlador de música**](/elements#music-controller) a un diseño para controlar la música de Vanilla en esa pantalla:

1. Haz clic derecho en el fondo del editor.
2. Selecciona **Elemento nuevo -> Controlador de música**.
3. Configura por separado la música de los menús y la música de los mundos.

El elemento admite [requisitos de carga](/conditions).

Si desactivas la música de los menús con un Controlador de música, también impedirás que se reproduzca la lista global de pistas personalizadas para los menús en esa pantalla.

# Música personalizada con elementos de audio

Usa un elemento [**Audio**](/elements#audio) si necesitas:

- Música distinta en cada pantalla.
- Música en pantallas dentro del juego.
- Requisitos de diseño, listas de reproducción ordenadas, opciones de reproducción aleatoria, control del volumen o del canal.

Coloca un [elemento Audio](/elements#audio) en un [diseño universal](/universal-layouts) para mantener activo el mismo reproductor en las pantallas compatibles que carguen ese diseño. La personalización de pantalla debe estar activada en cada pantalla normal en la que quieras aplicar el diseño universal.
