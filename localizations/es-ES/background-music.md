---
title: Música de fondo del menú
description: Personaliza la música que se reproduce en los menús.
---

# Música de fondo del menú

FancyMenu puede desactivar la música del menú de Vanilla, reproducir una lista global de pistas o usar [elementos de Audio](./elements#audio) para música específica de cada diseño.

# Música global del menú

Abre [**Personalizaciones globales**](./global-customizations) desde **Personalización -> Personalizaciones globales** fuera del editor de diseños.

Usa estos ajustes:

- **Reproducir música del menú de Vanilla** activa o desactiva globalmente la música del menú de Vanilla.
- **Pistas personalizadas de música del menú** gestiona la lista global de pistas de sustitución.

> [!IMPORTANT]
> Las pistas personalizadas globales del menú solo se reproducen cuando no hay ningún mundo cargado, como en la pantalla de título. Usa un [elemento de **Audio**](./elements#audio) para audio de menús dentro de un mundo.

Las pistas globales usan el canal de sonido Music. La primera pista empieza tras unos cinco segundos; las siguientes usan un retardo aleatorio de aproximadamente uno a treinta segundos. La selección es aleatoria y evita repetir inmediatamente la pista anterior cuando hay más de una pista configurada.

# Control de música por pantalla

Añade un [elemento **Music Controller**](./elements#music-controller) a un diseño para controlar la música de Vanilla de esa pantalla:

1. Haz clic con el botón derecho en el fondo del editor.
2. Selecciona **Nuevo elemento -> Music Controller**.
3. Configura por separado la música del menú y la música del mundo.

El elemento admite [requisitos de carga](./conditions).

Desactivar la música del menú con un Music Controller también impide que la lista global de pistas personalizadas del menú se reproduzca en esa pantalla.

# Música personalizada con elementos de Audio

Usa un [elemento de **Audio**](./elements#audio) cuando necesites:

- Música diferente en distintas pantallas.
- Música en pantallas dentro de un mundo.
- Requisitos de diseño, listas de reproducción ordenadas, opciones de aleatorio, volumen o control de canal.

Coloca un [elemento de Audio](./elements#audio) en un [Diseño universal](./universal-layouts) para mantener el mismo reproductor activo entre las pantallas compatibles que carguen ese diseño. La personalización de pantalla debe estar activada en cada pantalla normal donde el diseño universal deba aplicarse.
