---
title: Programadores
description: >-
  Ejecuta scripts de acciones de FancyMenu en un temporizador, incluso en
  segundo plano.
---

# Programadores

Los programadores ejecutan un script de acciones en un temporizador.

Son globales (no están ligados a una pantalla específica), así que pueden seguir ejecutándose incluso cuando no hay ninguna GUI abierta.

Usa programadores cuando quieras automatización a lo largo del tiempo en lugar de una acción única.
Son útiles para tareas repetidas, tareas con retraso y lógica en segundo plano.

Ejemplos comunes:

- Actualizar variables o elementos de texto cada pocos segundos (por ejemplo, una pantalla personalizada de reloj/estado).
- Ejecutar verificaciones periódicas y disparar acciones cuando se cumplan condiciones.
- Iniciar efectos de menú, sonidos u otro comportamiento con script en un ciclo temporizado.
- Retrasar una acción y ejecutarla después sin necesidad de dejar una pantalla abierta.

# Dónde encontrarlos

Abre la **barra de menú** de FancyMenu mientras **no** estés en el editor de diseño, luego **Personalización -> Administrar Programadores**.

# Inicio rápido

1. Abre **Personalización -> Administrar Programadores**.
2. Haz clic en **Agregar Programador**.
3. Construye el **Script de Acciones** del programador (esto es lo que se ejecuta una vez por cada tick del programador).
4. Selecciona el programador y haz clic en **Editar ajustes**.
5. Configura:
   - **ID del programador** (nombre único del programador; se usa en las acciones Iniciar/Detener y en los requisitos; permitido: `a-z`, `0-9`, `.`, `_`, `-`)
   - **Retraso de inicio (ms)** (tiempo de espera antes de que se ejecute el primer tick)
   - **Retraso entre ticks (ms)** (tiempo de espera entre ticks; `0` = cada tick del juego)
   - **Ticks a ejecutar** (cuántos ticks ejecutar antes de detenerse automáticamente; `0` = permanente)
   - **Iniciar al arrancar** (inicia automáticamente este programador cuando FancyMenu se cargue)
6. Usa **Iniciar ahora** para ejecutarlo inmediatamente.
7. Usa **Detener ahora** para detenerlo.

# Controlar y observar programadores

Hay acciones y requisitos para controlar programadores y comprobar su estado de ejecución.

## Acciones

- **Iniciar programador** toma el ID del programador y lo inicia si todavía no está ejecutándose.
- **Detener programador** también toma el ID del programador y lo detiene.

## Requisito

Para comprobar si un programador se está ejecutando actualmente, usa el requisito **El programador está en ejecución**, que toma el ID del programador.

# Consejos

1. Usa IDs claros como `hud_update`, `menu_animation`, `music_fade`.
2. Empieza con un retraso entre ticks más alto (por ejemplo `200`-`1000` ms), y luego bájalo solo si es necesario, para ahorrar rendimiento.
3. En la lista de programadores, haz clic derecho sobre un programador para editar rápidamente sus acciones.
4. En la lista de programadores, haz doble clic en el ID de un programador para cambiarle el nombre.
