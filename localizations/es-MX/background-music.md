---
title: Música de fondo del menú
description: Personaliza la música que se reproduce en los menús.
---

# Música de fondo del menú

FancyMenu puede desactivar la música del menú de Vanilla, reproducir una lista global de pistas o usar [elementos de Audio](./elements#audio) para música específica según el diseño.

# Música global del menú

Abre [**Personalizaciones globales**](./global-customizations) desde **Customization -> Global Customizations** fuera del editor de diseños.

Usa estos ajustes:

- **Play Vanilla Menu Music** habilita o deshabilita globalmente la música del menú de Vanilla.
- **Custom Menu Music Tracks** administra la lista global de pistas de reemplazo.

> [!IMPORTANT]
> Las pistas globales de música personalizada solo se reproducen cuando no hay ningún mundo cargado, como en la pantalla de título. Usa un elemento [**Audio**](./elements#audio) para audio de menú dentro del mundo.

Las pistas globales usan el canal de sonido Music. La primera pista comienza después de unos cinco segundos; las pistas posteriores usan un retraso aleatorio de entre uno y treinta segundos aproximadamente. La selección es aleatoria y evita repetir inmediatamente la pista anterior cuando hay más de una configurada.

# Control de música por pantalla

Agrega un elemento [**Music Controller**](./elements#music-controller) a un diseño para controlar la música de Vanilla para esa pantalla:

1. Haz clic derecho en el fondo del editor.
2. Selecciona **New Element -> Music Controller**.
3. Configura por separado Menu Music y World Music.

El elemento admite [requisitos de carga](./conditions).

Desactivar la música del menú con un Music Controller también evita que la lista global de pistas personalizadas del menú se reproduzca en esa pantalla.

# Música personalizada con elementos de Audio

Usa un elemento [**Audio**](./elements#audio) cuando necesites:

- Música diferente en distintas pantallas.
- Música en pantallas dentro del mundo.
- Requisitos de diseño, listas de reproducción ordenadas, ajustes de mezcla aleatoria, volumen o control de canal.

Coloca un elemento [Audio](./elements#audio) en un [Universal Layout](./universal-layouts) para mantener activo el mismo reproductor en las pantallas compatibles que carguen ese diseño. La personalización de pantalla debe estar habilitada en cada pantalla normal donde deba aplicarse el diseño universal.
