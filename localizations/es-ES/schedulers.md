---
title: Tareas programadas
description: >-
  Ejecuta scripts de acción con un temporizador, una vez o repetidamente, en
  cualquier menú y mientras juegas.
sourceBlobSha: 5abcc8450371fa0d23d67618db9cf27c9bd7de97
---

# Tareas programadas

Las tareas programadas ejecutan un [script de acción](/action-scripts) con un temporizador: una vez tras una espera, unas cuantas veces o repetidamente hasta que algo las detenga. Funcionan en cualquier menú y mientras juegas, incluso cuando no hay ningún menú abierto, y no pertenecen a ningún diseño.

Las tareas programadas son la opción recomendada para todo lo que deba suceder más tarde o repetirse. Siempre que sea posible, úsalas en lugar de los [elementos Ticker](/elements#ticker).

<img width="800" alt="Un cuadro de consejos de supervivencia muestra otro consejo cada 4 segundos porque una tarea programada mezcla la lista de consejos" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_tips.gif?raw=true">

> [!CAUTION]
> Una tarea programada puede ejecutar acciones de archivos, red, comandos, portapapeles, paquetes de recursos y enlaces cuando no hay ningún menú abierto. Usa únicamente tareas programadas de perfiles y archivos de personas de confianza.

# Añadir una tarea programada

<img width="800" alt="Se abre Administrar tareas programadas, se hace clic en Añadir tarea programada y se le asigna la acción Organizar lista con Mezclar para la lista tips" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_add.gif?raw=true">

1. Abre **Barra de menús -> Personalización -> Administrar tareas programadas**.
2. Haz clic en **Añadir tarea programada**. Se abrirá el editor de scripts de acción.
3. Añade las acciones que deban ejecutarse cada vez y haz clic en **Listo**. Consulta [Scripts de acción](/action-scripts#making-an-action-script).

<img width="800" alt="Se asigna el nombre random_tip a la nueva tarea programada en Editar ajustes, con un intervalo de 4000 y Activar al iniciar; después se inicia y cambia el consejo del menú" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_start.gif?raw=true">

4. La nueva tarea programada aparece con un ID aleatorio. Haz clic en ella y, después, en **Editar ajustes**.
5. Asígnale un **ID de tarea programada**, como `random_tip`, configura su [temporizador](#settings) y haz clic en **Listo**.
6. Haz clic en **Iniciar ahora** para probarla.

Todo lo que cambies en **Administrar tareas programadas** se guarda de inmediato.

La tarea programada de los GIF ejecuta [**Organizar lista (variable FM)**](/action-scripts#arrange-list-fm-variable) con **Mezclar** en la lista `tips` cada 4 segundos. Un elemento de texto muestra la primera entrada de la lista, por lo que aparece un consejo aleatorio. Más información sobre el funcionamiento de la lista y el texto: [Acciones de lista](/variables#list-actions).

# Ajustes

| Ajuste | Qué hace |
|---|---|
| **ID de tarea programada** | El nombre que utilizan las acciones y los requisitos. Solo puede contener letras minúsculas, números, `.`, `_` y `-`. |
| **Retardo de inicio (ms)** | Cuánto espera desde que se inicia hasta que se ejecuta por primera vez. `0` la ejecuta inmediatamente. |
| **Intervalo (ms)** | El tiempo entre dos ejecuciones. `0` la ejecuta en cada tick, 20 veces por segundo. |
| **Ticks que ejecutar** | Cuántas veces se ejecuta antes de detenerse por sí sola. `0` hace que siga ejecutándose hasta que algo la detenga. |
| **Activar al iniciar** | La inicia cada vez que se inicia el juego. |

Los tiempos se expresan en milisegundos: `1000` es un segundo, `60000` un minuto y `1800000` media hora.

# Iniciar y detener

Una tarea programada solo se ejecuta después de iniciarla:

- Con **Activar al iniciar**, cuando se inicia el juego y después de cambiar de [perfil](/profiles).
- Con **Iniciar ahora** en **Administrar tareas programadas**. Mientras se ejecuta, el botón cambia a **Detener ahora**.
- Con la acción [**Iniciar tarea programada**](/action-scripts#start-scheduler) y el ID de la tarea, por ejemplo, en el script de un botón o de un [escuchador](/listeners).

Se detiene:

- Por sí sola, después de ejecutarse el número de veces indicado en **Ticks que ejecutar**.
- Con **Detener ahora** o con la acción [**Detener tarea programada**](/action-scripts#stop-scheduler) y su ID.
- Si se le cambia el nombre o se elimina, al cambiar de [perfil](/profiles) y al cerrar el juego. Tras reiniciar, solo vuelven a ejecutarse las tareas con **Activar al iniciar**.

Una tarea programada que ya se está ejecutando no puede iniciarse de nuevo: **Iniciar tarea programada** no hace nada hasta que se detiene. Para volver a iniciarla, usa **Detener tarea programada** y, después, **Iniciar tarea programada**.

El requisito [**La tarea programada está en ejecución**](/conditions#scheduler-is-running) comprueba si una tarea programada está ejecutándose; por ejemplo, para mostrar un botón de detención solo mientras lo esté.

## Solo mientras haya una pantalla abierta

Para ejecutar una tarea programada solo mientras una pantalla determinada esté abierta, como la pantalla de título:

1. Abre un diseño de esa pantalla en el editor de diseños.
2. Haz clic con el botón derecho en el fondo del editor, selecciona **Editar script de acción «Abrir pantalla»** y añade **Iniciar tarea programada** con el ID de la tarea.
3. Vuelve a hacer clic con el botón derecho en el fondo, selecciona **Editar script de acción «Cerrar pantalla»** y añade **Detener tarea programada** con el mismo ID.

# Administrar tareas programadas

<img width="800" alt="La ventana Administrar tareas programadas muestra tres tareas; random_tip está seleccionada y a la derecha aparecen sus ajustes y el estado En ejecución" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_manage.png?raw=true">

- Haz clic en una tarea programada para ver sus ajustes, si está ejecutándose y su script de acción en el panel derecho.
- **Editar acciones**, o hacer clic con el botón derecho en una tarea, abre su script de acción.
- Haz doble clic en el ID de una tarea para cambiarle el nombre. `Enter` guarda el nombre y `Esc` cancela. Al cambiarle el nombre, la tarea se detiene y las acciones que usan el ID anterior dejan de encontrarla.
- **Eliminar tarea programada** elimina la tarea seleccionada tras pedirte confirmación.
- **Exportar para IA** copia la tarea seleccionada o todas las tareas para un [chat con IA](/export-for-ai).
- La barra de búsqueda permite buscar tareas por su ID.

Las tareas programadas se guardan en `config/fancymenu/scheduler_instances.txt` (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations)). Cada [perfil](/profiles) tiene sus propias tareas programadas.

# Ejemplo: recordatorio para descansar

Una notificación emergente cada 30 minutos desde que se inicia el juego:

1. Añade una tarea programada con [**Mostrar notificación**](/action-scripts#show-toast). Establece **Título** como `Time for a Break` y **Mensaje** como `Stand up, stretch and drink some water.`
2. En **Editar ajustes**, establece **ID de tarea programada** como `break_reminder`, **Retardo de inicio (ms)** e **Intervalo (ms)** como `1800000`, y **Activar al iniciar** como **Activado**.

Sin **Retardo de inicio (ms)**, la primera notificación aparecería justo al iniciar el juego.

# Información útil

- Mantén **Intervalo (ms)** tan alto como permita la tarea. Con `0`, las acciones se ejecutan 20 veces por segundo, y las acciones lentas pueden hacer que el juego vaya a tirones.
- Si el juego va a tirones, pueden producirse varias ejecuciones seguidas.
- Los cambios en el script de acción se aplican de inmediato, incluso mientras la tarea programada se está ejecutando. Los cambios en sus ajustes se aplican la próxima vez que se inicie.
- Si falla una acción, la tarea programada sigue ejecutándose. El error se registra en el registro del juego, `logs/latest.log`.
- Para una única espera dentro de un script de acción —por ejemplo, «abrir la pantalla 2 segundos después de hacer clic»—, el bloque [Ejecutar más tarde](/action-scripts#execute-later) es más sencillo.
