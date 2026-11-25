---
title: Variables
description: >-
  Cómo guardar textos y listas en variables y usarlos en textos, acciones y
  requisitos.
sourceBlobSha: 2f0d48fd6cc100f976d4fdf1bceb28fe1a540a52
---

# Variables

Las variables son valores que FancyMenu recuerda incluso después de cerrar el juego. Úsalas para contar clics, recordar elecciones, llevar un seguimiento del progreso o guardar listas, como consejos de carga. Los textos, las acciones, los requisitos, los listeners y algunos elementos pueden leerlas y modificarlas.

> [!TIP]
> Las acciones para variables están en [Scripts de acciones](/action-scripts), los requisitos en [Requisitos](/conditions) y el listener en [Listeners](/listeners#on-variable-updated-fm-variable).

# Variables de texto y de lista

Hay dos tipos de variables:

- Las variables de texto contienen un solo texto, como `dark`, `5` o `true`.
- Las variables de lista contienen una lista de elementos, como consejos de carga o nombres de servidores. Cada elemento es un texto independiente.

La posición de un elemento en una lista es su índice. El primer elemento tiene el índice `0`, el segundo `1` y así sucesivamente. Los índices negativos cuentan desde el final, por lo que `-1` es el último elemento.

Los elementos que solo reconocen texto, como `$$name` o **El valor de la variable es (FM Variable)**, reciben una lista como un arreglo JSON con sus elementos, por ejemplo, `["Craft a bed before your first night.","Torches keep most mobs away."]`.

# Administrar variables

Abre **barra de menú -> Personalización -> Administrar variables**. Esta opción solo aparece en la barra de menú cuando no estás en el editor de diseños.

<img width="800" alt="Cómo agregar la variable de texto menu_theme con el valor dark y la variable de lista tips con tres consejos en Administrar variables" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_manage.gif?raw=true">

## Agregar variables

1. Haz clic derecho en la lista y selecciona **Agregar variable de texto** o **Agregar variable de lista**.
2. Escribe un nombre y haz clic en **Listo**.

Los nombres pueden contener letras minúsculas, números, `.`, `_` y `-`. Cada nombre solo puede existir una vez.

## Cambiar variables

Haz clic derecho en una variable para ver estas opciones:

| Opción | Qué hace |
|---|---|
| **Establecer valor** | Establece el texto de una variable de texto. |
| **Editar lista** | Abre el editor de listas de una variable de lista (consulta la sección siguiente). |
| **Convertir a lista…** | Convierte una variable de texto en una variable de lista. **Separador** divide el texto en elementos: escribe `\n` para dividirlo en los saltos de línea. **Recortar elementos** elimina los espacios alrededor de cada elemento y **Omitir elementos vacíos** excluye los elementos vacíos. El texto que ya sea un arreglo JSON, como `["a","b"]`, se interpreta como tal (**Leer como arreglo JSON**). |
| **Convertir a texto…** | Convierte una variable de lista en una variable de texto. **Separador** se coloca entre los elementos, o bien **Conservar texto JSON** mantiene la lista como un arreglo JSON. |
| **Vaciar variable al iniciar el juego** | Vacía la variable cada vez que se inicia el juego. Es útil para valores que solo deberían durar una sesión. |
| **Eliminar variable** | Elimina la variable. |
| **Copiar** y **Pegar** | Crea una copia de una variable. |
| **Exportar variable para IA** | Exporta la variable para [chats de IA](/export-for-ai). |

Los cambios se aplican de inmediato. Deshazlos con `Ctrl + Z` y reházalos con `Ctrl + Y` (`Cmd` en macOS). Empieza a escribir para buscar, presiona `Enter` para editar la variable seleccionada o `Delete` para eliminarla.

## Editar listas

El editor de listas muestra cada elemento junto con su índice.

- Para agregar elementos, haz clic en **Agregar elemento** debajo de la lista, escribe el elemento y presiona `Enter`. Se empezará a agregar el siguiente elemento de inmediato. Presiona `Enter` en un elemento vacío o `Esc` para dejar de agregar.
- Para editar un elemento, haz doble clic en él. `Shift + Enter` lo abre en el editor de texto, donde puede tener saltos de línea.
- Para cambiar el orden de los elementos, arrástralos o presiona `Alt + Up` y `Alt + Down`.
- Haz clic derecho en un elemento para ver las opciones **Duplicar elemento** (`Ctrl + D`), **Eliminar elemento** (`Delete`), **Copiar**, **Pegar**, **Mover arriba** y **Mover abajo**.
- **Editar como texto** permite editar todos los elementos a la vez, uno por línea.

**Listo** guarda la lista. **Cancelar** descarta todos los cambios que hiciste en el editor de listas.

# Mostrar variables en el texto

Escribe `$$` seguido del nombre de una variable para mostrar su valor: una variable llamada `menu_theme` se escribe como `$$menu_theme`. Esto funciona en cualquier texto que admita [marcadores de posición](/placeholders), como los [elementos de texto](/text-in-menus), las etiquetas de botones, la información sobre herramientas y los valores de las acciones y los requisitos. El texto se actualiza automáticamente cuando cambia la variable.

```
Tema actual: $$menu_theme
```

- `$$name` se mantiene sin cambios si la variable no existe.
- Si varios nombres empiezan igual, como `coins` y `coins_record`, `$$coins_record` siempre se refiere al nombre más largo.
- Una lista se muestra como un arreglo JSON. Estos marcadores de posición muestran las listas de forma más clara:

| Marcador de posición | Ejemplo | Resultado |
|---|---|---|
| **Obtener valor de variable (FM Variable)** | `{"placeholder":"getvariable","values":{"name":"clicks"}}` | El valor o `0` si la variable está vacía o no existe. Es ideal para números. |
| **Obtener elemento de lista (FM Variable)** | `{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}` | El elemento en el índice indicado o el valor de `fallback` si no hay ninguno. |
| **Tamaño de lista (FM Variable)** | `{"placeholder":"list_size","values":{"name":"tips"}}` | La cantidad de elementos de la lista. |
| **Índice del elemento de lista (FM Variable)** | `{"placeholder":"list_index_of","values":{"name":"tips","value":"Torches keep most mobs away.","ignore_case":"false"}}` | El índice del primer elemento que coincide con todo el `value` o `-1`. |
| **Unir elementos de lista (FM Variable)** | `{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}` | Todos los elementos en un solo texto, separados por `separator` (`, ` si se omite). `\n` representa un salto de línea. |

# Cambiar variables con acciones

Los [scripts de acciones](/action-scripts) cambian variables cuando se hace clic en un botón, se ejecuta un ticker, se activa un listener, entre otras situaciones.

## Variables de texto

[**Establecer valor de variable (FM Variable)**](/action-scripts#set-variable-value-fm-variable) recibe el nombre y el nuevo valor, separados por `:`. Si la variable aún no existe, se crea.

```
menu_theme:dark
```

Solo los primeros `:` separan el nombre, así que el valor puede contener más, como en `last_server:play.example.net:25565`.

Para contar los clics en un botón, suma 1 al valor anterior:

```
clicks:{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

**Obtener valor de variable (FM Variable)** devuelve `0` mientras `clicks` esté vacío, por lo que el primer clic establece su valor en `1`.

Establecer valor de variable nunca convierte una lista en texto. Un arreglo JSON se convierte en los elementos de la lista, un texto vacío la vacía y cualquier otro texto se convierte en su único elemento.

[**Eliminar variable (FM Variable)**](/action-scripts#delete-variable-fm-variable) elimina una variable y [**Borrar todas las variables (FM Variable)**](/action-scripts#clear-all-variables-fm-variable) las elimina todas.

## Acciones para listas

Cada acción para listas tiene su propia ventana. Todos sus campos admiten marcadores de posición.

| Acción | Qué hace |
|---|---|
| [**Agregar a la lista (FM Variable)**](/action-scripts#add-to-list-fm-variable) | Agrega un elemento al final o en un índice. **Omitir si ya está en la lista** no agrega nada si el elemento ya está en ella. |
| [**Establecer elemento de lista (FM Variable)**](/action-scripts#set-list-entry-fm-variable) | Reemplaza el elemento en un índice. |
| [**Eliminar de la lista (FM Variable)**](/action-scripts#remove-from-list-fm-variable) | Elimina el **Elemento en el índice**, la **Primera coincidencia** de un valor o **Todas las coincidencias**. |
| [**Borrar lista (FM Variable)**](/action-scripts#clear-list-fm-variable) | Elimina todos los elementos. La lista se conserva, pero queda vacía. |
| [**Establecer lista (FM Variable)**](/action-scripts#set-list-fm-variable) | Reemplaza todos los elementos con las partes de un **Texto dividido** o con los elementos de un **Arreglo JSON**. `$$other_list` como arreglo JSON copia otra lista. |
| [**Ordenar lista (FM Variable)**](/action-scripts#arrange-list-fm-variable) | **Ordenar de A a Z**, **Ordenar de Z a A**, **Números de menor a mayor**, **Números de mayor a menor**, **Orden inverso**, **Orden aleatorio** o **Eliminar duplicados**. |

- Las acciones para listas crean una lista si no existe y convierten en listas las variables de texto vacías. Nunca modifican una variable de texto que tenga un valor: primero [conviértela](#cambiar-variables).
- Escribe el nombre de la lista sin `$$`. Si usas `$$`, la acción emplea como nombre el valor de esa variable.

Por ejemplo, un elemento de texto muestra el primer elemento de la lista `tips`:

```
{"placeholder":"list_get","values":{"name":"tips","index":"0"}}
```

El botón Siguiente consejo que aparece debajo usa **Ordenar lista (FM Variable)** con **Orden aleatorio** en su script de acciones:

<img width="800" alt="Cómo agregar Ordenar lista con la lista tips y Orden aleatorio al script de acciones de un botón Siguiente consejo en el editor de diseños" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_script.gif?raw=true">

Cada clic cambia el orden de la lista, así que el texto muestra un consejo aleatorio:

<img width="800" alt="Al hacer clic en el botón Siguiente consejo, se muestra un consejo del día diferente" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_result.gif?raw=true">

## Recorrer una lista

El [bucle FOR EACH](/action-scripts#for-each-loop) ejecuta las acciones que contiene una vez por cada elemento de una lista, desde el primero hasta el último.

1. Haz clic derecho en el área de scripts del editor de scripts de acciones y selecciona **Agregar bucle FOR EACH**.
2. Escribe el nombre de la variable de lista, sin `$$`, y haz clic en **Listo**.
3. Agrega acciones dentro del bucle. En sus valores, `$$list_entry` representa el elemento actual y `$$list_index`, su índice.

Por ejemplo, una lista `starter_commands` con los elementos `/time set day` y `/weather clear`, y una acción [**Enviar mensaje/comando de chat**](/action-scripts#send-chat-messagecommand) dentro del bucle con este valor, ejecuta ambos comandos:

```
$$list_entry
```

- El bucle lee la lista una sola vez al iniciar. Las acciones que contiene pueden modificarla sin cambiar los elementos que recorrerá.
- Si se usa una variable de texto o una lista que no existe, el bucle se ejecuta cero veces.
- Al igual que los bucles WHILE, se detiene después de 3 segundos para evitar que el juego se congele.

# Comprobar variables

Los [requisitos](/conditions) muestran elementos o ejecutan partes de scripts de acciones solo cuando una variable tiene determinado valor.

- [**El valor de la variable es (FM Variable)**](/conditions#is-variable-value-fm-variable) comprueba el valor completo. En el caso de las listas, compara el arreglo JSON de todos sus elementos.
- [**La lista contiene el elemento (FM Variable)**](/conditions#list-contains-entry-fm-variable) comprueba si una lista contiene un elemento. Debe coincidir con el elemento completo. **Ignorar mayúsculas y minúsculas** permite que `Apple` coincida con `apple`.
- [**Es un número**](/conditions#is-number) compara números, por ejemplo, si `$$clicks` es mayor que `5`.

Por ejemplo, un botón abre la publicación de noticias más reciente y agrega `news_42` a una lista `read_news` con **Agregar a la lista (FM Variable)**. Una insignia «¡Nuevo!» junto al botón tiene el requisito **La lista contiene el elemento (FM Variable)** para `news_42`, con **Modo del requisito** en **Opuesto**. Así, la insignia se oculta cuando el jugador ya leyó la publicación.

# Vincular variables a elementos

- [Campo de texto](/elements#text-input-field): **Vincular a variable** guarda en la variable lo que escribe el jugador y el campo muestra el valor de la variable. Si se vincula a una lista, el texto escrito reemplaza la lista completa.
- [Casilla](/elements#checkbox): activa **Modo de variable** y configura **Vincular a variable**. La casilla escribe `true` o `false` en la variable.
- [Deslizador](/elements#slider) de tipo **Lista de valores**: **Valores de la variable de lista** obtiene los valores del deslizador de una lista. Los elementos que se agreguen o eliminen de la lista aparecen de inmediato.

# Reaccionar a los cambios

- El listener [**Al actualizarse una variable [FM Variable]**](/listeners#on-variable-updated-fm-variable) ejecuta un script de acciones cada vez que se establece una variable.
- El comando [`/fmvariable`](/commands#fmvariable) permite establecer y leer variables desde el chat, bloques de comandos y otros mods.

# Dónde se guardan las variables

FancyMenu guarda las variables de inmediato en `<game-directory>/config/fancymenu/user_variables.db`, para que se conserven después de reiniciar el juego.

- Las variables pertenecen a toda la instancia de Minecraft y a su [perfil](/profiles) activo. No son independientes para cada diseño, mundo, servidor o jugador.
- Los nombres distinguen entre mayúsculas y minúsculas.
- No guardes contraseñas, tokens ni otros datos secretos en las variables. Cualquier persona con acceso a la carpeta del juego puede leerlos.
