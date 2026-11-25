---
title: Programadores
description: >-
  Ejecuta scripts de acciones con un temporizador: una vez o repetidamente, en
  cualquier menú y durante el juego.
sourceBlobSha: 5abcc8450371fa0d23d67618db9cf27c9bd7de97
---

# Programadores

Los programadores ejecutan un [script de acciones](/action-scripts) con un temporizador: una vez después de esperar, unas cuantas veces o repetidamente hasta que algo los detenga. Funcionan en cualquier menú y durante el juego, incluso cuando no hay ningún menú abierto, y no pertenecen a ningún diseño.

Los programadores son la opción recomendada para todo lo que deba ocurrir más tarde o repetidamente. Siempre que sea posible, úsalos en lugar de los [elementos Ticker](/elements#ticker).

<img width="800" alt="Un cuadro de Consejo de supervivencia muestra otro consejo cada 4 segundos porque un programador mezcla la lista de consejos" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_tips.gif?raw=true">

> [!CAUTION]
> Un programador puede ejecutar acciones de archivos, red, comandos, portapapeles, paquetes de recursos y enlaces cuando no hay ningún menú abierto. Usa únicamente programadores de perfiles y archivos de personas en quienes confíes.

# Agregar un programador

<img width="800" alt="Abrir Administrar programadores, hacer clic en Agregar programador y asignarle la acción Organizar lista con Mezclar para la lista tips" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_add.gif?raw=true">

1. Abre **barra de menú -> Personalización -> Administrar programadores**.
2. Haz clic en **Agregar programador**. Se abrirá el editor de scripts de acciones.
3. Agrega las acciones que deben ejecutarse cada vez y haz clic en **Listo**. Consulta [Scripts de acciones](/action-scripts#making-an-action-script).

<img width="800" alt="Asignar el nombre random_tip al nuevo programador en Editar configuración, con un Retraso de tick de 4000 y la opción Iniciar al iniciar activada; después, iniciarlo y ver cómo cambia el consejo del menú" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_start.gif?raw=true">

4. El nuevo programador aparecerá con un ID aleatorio. Haz clic en él y luego en **Editar configuración**.
5. Asígnale un **ID de programador**, como `random_tip`, configura su [temporizador](#settings) y haz clic en **Listo**.
6. Haz clic en **Iniciar ahora** para probarlo.

Todo lo que cambies en **Administrar programadores** se guarda de inmediato.

El programador de los GIF ejecuta [**Organizar lista (variable de FM)**](/action-scripts#arrange-list-fm-variable) con la opción **Mezclar** para la lista `tips` cada 4 segundos. Un elemento de texto muestra la primera entrada de la lista, así que aparece un consejo aleatorio. Consulta cómo funcionan la lista y el texto en [Acciones de listas](/variables#list-actions).

# Configuración

| Configuración | Qué hace |
|---|---|
| **ID de programador** | El nombre que usan las acciones y los requisitos. Solo puede contener letras minúsculas, números, `.`, `_` y `-`. |
| **Retraso inicial (ms)** | Cuánto espera después de iniciarse antes de ejecutarse por primera vez. `0` lo ejecuta de inmediato. |
| **Retraso de tick (ms)** | El tiempo entre dos ejecuciones. `0` lo ejecuta en cada tick, 20 veces por segundo. |
| **Ticks que se ejecutará** | Cuántas veces se ejecuta antes de detenerse por sí solo. `0` hace que siga ejecutándose hasta que algo lo detenga. |
| **Iniciar al iniciar** | Lo inicia cada vez que se inicia el juego. |

Los tiempos se indican en milisegundos: `1000` es un segundo, `60000` es un minuto y `1800000` es media hora.

# Iniciar y detener

Un programador solo se ejecuta después de iniciarlo:

- Con **Iniciar al iniciar**, cuando se inicia el juego y después de cambiar de [perfil](/profiles).
- Con **Iniciar ahora** en **Administrar programadores**. Mientras el programador se ejecuta, el botón cambia a **Detener ahora**.
- Con la acción [**Iniciar programador**](/action-scripts#start-scheduler) y el ID del programador, por ejemplo, en el script de un botón o de un [escuchador](/listeners).

Se detiene:

- Por sí solo, después de ejecutarse la cantidad de veces indicada en **Ticks que se ejecutará**.
- Con **Detener ahora** o con la acción [**Detener programador**](/action-scripts#stop-scheduler) y su ID.
- Cuando se le cambia el nombre o se elimina, al cambiar de [perfil](/profiles) y al cerrar el juego. Después de reiniciar, solo vuelven a ejecutarse los programadores que tengan activada la opción **Iniciar al iniciar**.

Un programador que ya se está ejecutando no puede iniciarse por segunda vez: **Iniciar programador** no hace nada hasta que se detenga. Para iniciarlo de nuevo, usa **Detener programador** y luego **Iniciar programador**.

El requisito [**El programador está en ejecución**](/conditions#scheduler-is-running) comprueba si un programador se está ejecutando; por ejemplo, sirve para mostrar un botón de detener solo mientras esté en ejecución.

## Solo mientras una pantalla está abierta

Para ejecutar un programador únicamente mientras haya una pantalla determinada abierta, como la pantalla de título:

1. Abre en el editor de diseños un diseño de esa pantalla.
2. Haz clic derecho en el fondo del editor, selecciona **Editar script de acciones de «Abrir pantalla»** y agrega **Iniciar programador** con el ID del programador.
3. Vuelve a hacer clic derecho en el fondo, selecciona **Editar script de acciones de «Cerrar pantalla»** y agrega **Detener programador** con el mismo ID.

# Administrar programadores

<img width="800" alt="La ventana Administrar programadores con tres programadores, random_tip seleccionado y su configuración y estado En ejecución a la derecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/schedulers_manage.png?raw=true">

- Haz clic en un programador para ver a la derecha su configuración, si está en ejecución y su script de acciones.
- **Editar acciones** o hacer clic derecho en un programador abre su script de acciones.
- Haz doble clic en el ID de un programador para cambiarle el nombre. `Enter` guarda el nombre y `Esc` cancela. Cambiarle el nombre detiene el programador, y las acciones que usan el ID anterior ya no lo encontrarán.
- **Eliminar programador** elimina el programador seleccionado después de pedirte confirmación.
- **Exportar para IA** copia el programador seleccionado o todos los programadores para un [chat de IA](/export-for-ai).
- La barra de búsqueda encuentra programadores por su ID.

Los programadores se guardan en `config/fancymenu/scheduler_instances.txt` (consulta [Ubicaciones de almacenamiento de datos](/data-storage-locations)). Cada [perfil](/profiles) tiene sus propios programadores.

# Ejemplo: Recordatorio para descansar

Un aviso cada 30 minutos desde que se inicia el juego:

1. Agrega un programador con [**Mostrar aviso**](/action-scripts#show-toast). Establece **Título** en `Time for a Break` y **Mensaje** en `Stand up, stretch and drink some water.`
2. En **Editar configuración**, establece **ID de programador** en `break_reminder`, **Retraso inicial (ms)** y **Retraso de tick (ms)** en `1800000`, y cambia **Iniciar al iniciar** a **Activado**.

Sin **Retraso inicial (ms)**, el primer aviso aparecería justo cuando se inicia el juego.

# Información útil

- Mantén **Retraso de tick (ms)** tan alto como lo permita la tarea. Con el valor `0`, las acciones se ejecutan 20 veces por segundo, y las acciones lentas pueden hacer que el juego se vuelva lento.
- Si el juego se pone lento, pueden ocurrir varias ejecuciones seguidas.
- Los cambios en el script de acciones se aplican de inmediato, incluso mientras el programador está en ejecución. Los cambios en su configuración se aplican la próxima vez que se inicie.
- Si una acción falla, el programador sigue ejecutándose. El error se registra en el archivo de registro del juego, `logs/latest.log`.
- Para esperar una sola vez dentro de un script de acciones, por ejemplo, «abrir la pantalla 2 segundos después de hacer clic», es más sencillo usar el bloque [Ejecutar más tarde](/action-scripts#execute-later).
