---
title: Música de fondo en los menús
description: Personaliza la música que se reproduce en los menús.
sourceBlobSha: 46d219f5573b915991f23082cfbc42e6ed11d132
---

# Música de fondo en los menús

FancyMenu puede desactivar la música de los menús de Vanilla, reproducir una lista global de pistas o usar [elementos de audio](/elements#audio) para asignar música específica a cada diseño.

# Música global de los menús

Fuera del editor de diseños, abre [**Personalizaciones globales**](/global-customizations) desde **Personalización -> Personalizaciones globales**.

Usa estos ajustes:

- **Reproducir música de los menús de Vanilla** activa o desactiva globalmente la música de los menús de Vanilla.
- **Pistas personalizadas para los menús** administra la lista global de pistas que reemplazará la música original.

> [!IMPORTANT]
> Las pistas personalizadas globales solo se reproducen cuando no hay ningún mundo cargado, por ejemplo, en la pantalla de título. Usa un elemento [**Audio**](/elements#audio) para reproducir audio en los menús dentro del mundo.

Las pistas globales usan el canal de sonido Music. La primera pista comienza después de unos cinco segundos; las siguientes se reproducen tras un intervalo aleatorio de entre uno y treinta segundos. La selección es aleatoria y, si hay más de una pista configurada, evita repetir inmediatamente la pista anterior.

# Control de música por pantalla

Agrega un elemento [**Controlador de música**](/elements#music-controller) a un diseño para controlar la música de Vanilla en esa pantalla:

1. Haz clic derecho en el fondo del editor.
2. Selecciona **Nuevo elemento -> Controlador de música**.
3. Configura por separado la música de los menús y la música del mundo.

El elemento admite [requisitos de carga](/conditions).

Si desactivas la música de los menús con un Controlador de música, también evitarás que se reproduzca la lista global de pistas personalizadas en esa pantalla.

# Música personalizada con elementos de audio

Usa un elemento [**Audio**](/elements#audio) cuando necesites:

- Música distinta en cada pantalla.
- Música en pantallas dentro del mundo.
- Requisitos del diseño, listas de reproducción ordenadas, opciones de reproducción aleatoria, control de volumen o del canal.

Coloca un [elemento Audio](/elements#audio) en un [diseño universal](/universal-layouts) para mantener activo el mismo reproductor en las pantallas compatibles que carguen ese diseño. La personalización de pantalla debe estar habilitada en cada pantalla normal donde quieras aplicar el diseño universal.
