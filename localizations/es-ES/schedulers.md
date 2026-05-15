---
title: Programadores de tareas
description: >-
  Ejecuta scripts de acciones de FancyMenu con temporizador, incluso en segundo
  plano.
---

# Programadores de tareas

Los programadores de tareas ejecutan un script de acciones con un temporizador.

Son globales (no vinculados a una pantalla específica), por lo que pueden seguir ejecutándose incluso cuando no hay ninguna interfaz gráfica abierta.

Usa programadores de tareas cuando quieras automatización a lo largo del tiempo en lugar de una acción puntual.
Son útiles para tareas repetidas, tareas diferidas y lógica en segundo plano.

Ejemplos habituales:

- Actualizar variables o elementos de texto cada pocos segundos (por ejemplo, un reloj personalizado o una pantalla de estado).
- Ejecutar comprobaciones periódicas y desencadenar acciones cuando se cumplan ciertas condiciones.
- Iniciar efectos de menú, sonidos u otros comportamientos con scripts en un bucle temporizado.
- Retrasar una acción y ejecutarla más tarde sin necesidad de mantener abierta una pantalla.

# Dónde encontrarlos

Abre la **barra de menús** de FancyMenu mientras **no** estés en el editor de diseño y luego ve a **Personalización -> Gestionar programadores de tareas**.

# Inicio rápido

1. Abre **Personalización -> Gestionar programadores de tareas**.
2. Haz clic en **Añadir programador de tareas**.
3. Crea el **script de acciones** del programador (esto es lo que se ejecuta una vez por cada tick del programador).
4. Selecciona el programador y haz clic en **Editar ajustes**.
5. Configura:
   - **ID del programador** (nombre único del programador; se usa en las acciones de iniciar/detener y en los requisitos; permitidos: `a-z`, `0-9`, `.`, `_`, `-`)
   - **Retardo de inicio (ms)** (tiempo de espera antes de que se ejecute el primer tick)
   - **Retardo entre ticks (ms)** (tiempo de espera entre ticks; `0` = cada tick del juego)
   - **Ticks a ejecutar** (cuántos ticks se ejecutarán antes de detenerse automáticamente; `0` = permanente)
   - **Iniciar al arrancar** (inicia automáticamente este programador cuando FancyMenu se carga)
6. Usa **Iniciar ahora** para ejecutarlo de inmediato.
7. Usa **Detener ahora** para detenerlo.

# Controlar y consultar programadores de tareas

Hay acciones y requisitos para controlar los programadores de tareas y comprobar su estado de ejecución.

## Acciones

- **Iniciar programador** toma el ID del programador y lo inicia si todavía no se está ejecutando.
- **Detener programador** también toma el ID del programador y lo detiene.

## Requisito

Para comprobar si un programador de tareas se está ejecutando actualmente, usa el requisito **El programador se está ejecutando**, que toma el ID del programador.

# Consejos

1. Usa IDs claros como `hud_update`, `menu_animation`, `music_fade`.
2. Empieza con un retardo entre ticks más alto (por ejemplo `200`-`1000` ms) y bájalo solo si es necesario, para ahorrar rendimiento.
3. En la lista de programadores, haz clic derecho sobre un programador para editar rápidamente sus acciones.
4. En la lista de programadores, haz doble clic en el ID de un programador para renombrarlo.
