---
title: Variables
description: >-
  Cómo guardar textos y listas en variables y usarlos en textos, acciones y
  requisitos.
sourceBlobSha: 2f0d48fd6cc100f976d4fdf1bceb28fe1a540a52
---

# Variables

Las variables son valores que FancyMenu recuerda incluso después de cerrar el juego. Úsalas para contar clics, recordar elecciones, seguir el progreso o guardar listas, como consejos de carga. Los textos, las acciones, los requisitos, los listeners y algunos elementos pueden leerlas y modificarlas.

> [!TIP]
> Las acciones para variables se enumeran en [Scripts de acciones](/action-scripts), los requisitos en [Requisitos](/conditions) y el listener en [Listeners](/listeners#on-variable-updated-fm-variable).

# Variables de texto y de lista

Hay dos tipos de variables:

- Las variables de texto contienen un texto, como `dark`, `5` o `true`.
- Las variables de lista contienen una lista de elementos, como consejos de carga o nombres de servidores. Cada elemento es un texto independiente.

La posición de un elemento en una lista es su índice. El primer elemento tiene el índice `0`, el segundo `1`, y así sucesivamente. Los índices negativos cuentan desde el final, así que `-1` es el último elemento.

Los elementos que solo admiten texto, como `$$name` o **El valor de la variable es (FM Variable)**, reciben una lista como un array JSON con sus elementos, por ejemplo `["Craft a bed before your first night.","Torches keep most mobs away."]`.

# Administrar variables

Abre **barra de menú -> Personalización -> Administrar variables**. La barra de menú solo muestra esta opción fuera del editor de diseños.

<img width="800" alt="Cómo añadir en Administrar variables la variable de texto menu_theme con el valor dark y la variable de lista tips con tres consejos" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_manage.gif?raw=true">

## Añadir variables

1. Haz clic con el botón derecho en la lista y selecciona **Añadir variable de texto** o **Añadir variable de lista**.
2. Escribe un nombre y haz clic en **Listo**.

Los nombres pueden contener letras minúsculas, números, `.`, `_` y `-`. Cada nombre solo puede existir una vez.

## Cambiar variables

Haz clic con el botón derecho en una variable para ver estas opciones:

| Opción | Qué hace |
|---|---|
| **Establecer valor** | Establece el texto de una variable de texto. |
| **Editar lista** | Abre el editor de listas para una variable de lista (consulta más abajo). |
| **Convertir en lista…** | Convierte una variable de texto en una lista. El **Separador** divide el texto en elementos: escribe `\n` para dividirlo en los saltos de línea. **Recortar elementos** elimina los espacios alrededor de cada elemento y **Omitir elementos vacíos** descarta los elementos vacíos. El texto que ya sea un array JSON, como `["a","b"]`, se interpreta como uno (**Leer como array JSON**). |
| **Convertir en texto…** | Convierte una lista en una variable de texto. El **Separador** se coloca entre los elementos, o bien **Conservar texto JSON** mantiene la lista como array JSON. |
| **Vaciar variable al iniciar el juego** | Vacía la variable cada vez que se inicia el juego. Es útil para valores que solo deberían durar una sesión. |
| **Eliminar variable** | Elimina la variable. |
| **Copiar** y **Pegar** | Crea una copia de una variable. |
| **Exportar variable para IA** | Exporta la variable para los [chats de IA](/export-for-ai). |

Los cambios se aplican de inmediato. Deshazlos con `Ctrl + Z` y vuelve a hacerlos con `Ctrl + Y` (`Cmd` en macOS). Empieza a escribir para buscar, pulsa `Enter` para editar la variable seleccionada o `Delete` para eliminarla.

## Editar listas

El editor de listas muestra todos los elementos con sus índices.

- Para añadir elementos, haz clic en **Añadir elemento** debajo de la lista, escribe el elemento y pulsa `Enter`. Se empezará a añadir el siguiente elemento de inmediato. Pulsa `Enter` en un elemento vacío o `Esc` para dejar de añadir.
- Para editar un elemento, haz doble clic en él. `Shift + Enter` lo abre en el editor de texto, donde puede incluir saltos de línea.
- Para cambiar el orden de los elementos, arrástralos o pulsa `Alt + Up` y `Alt + Down`.
- Haz clic con el botón derecho en un elemento para ver **Duplicar elemento** (`Ctrl + D`), **Eliminar elemento** (`Delete`), **Copiar**, **Pegar**, **Subir** y **Bajar**.
- **Editar como texto** permite editar todos los elementos a la vez, uno por línea.

**Listo** guarda la lista. **Cancelar** descarta todos los cambios realizados en el editor de listas.

# Mostrar variables en textos

Escribe `$$` seguido del nombre de una de tus variables para mostrar su valor: una variable llamada `menu_theme` se escribe `$$menu_theme`. Esto funciona en cualquier texto que admita [marcadores de posición](/placeholders), como los [elementos de texto](/text-in-menus), las etiquetas de los botones, la información sobre herramientas y los valores de las acciones y los requisitos. El texto se actualiza automáticamente cuando cambia la variable.

```
Tema actual: $$menu_theme
```

- Si una variable no existe, `$$name` se mantiene tal cual.
- Si varios nombres empiezan igual, como `coins` y `coins_record`, `$$coins_record` siempre hace referencia al nombre más largo.
- Una lista se muestra como un array JSON. Estos marcadores de posición muestran las listas de forma más clara:

| Marcador de posición | Ejemplo | Qué devuelve |
|---|---|---|
| **Obtener valor de variable (FM Variable)** | `{"placeholder":"getvariable","values":{"name":"clicks"}}` | El valor o `0` si la variable está vacía o no existe. Es la opción más adecuada para números. |
| **Obtener elemento de lista (FM Variable)** | `{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}` | El elemento del índice indicado o el valor `fallback` si no hay ninguno. |
| **Tamaño de lista (FM Variable)** | `{"placeholder":"list_size","values":{"name":"tips"}}` | El número de elementos de la lista. |
| **Índice del elemento de lista (FM Variable)** | `{"placeholder":"list_index_of","values":{"name":"tips","value":"Torches keep most mobs away.","ignore_case":"false"}}` | El índice del primer elemento que coincide con todo el `value`, o `-1`. |
| **Unir elementos de lista (FM Variable)** | `{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}` | Todos los elementos en un único texto, separados por `separator` (`, ` si se deja vacío). `\n` es un salto de línea. |

# Cambiar variables con acciones

Los [scripts de acciones](/action-scripts) modifican variables cuando se hace clic en un botón, se ejecuta un temporizador, se activa un listener, etc.

## Variables de texto

[**Establecer valor de variable (FM Variable)**](/action-scripts#set-variable-value-fm-variable) recibe el nombre y el nuevo valor, separados por `:`. Si la variable aún no existe, se crea.

```
menu_theme:dark
```

Solo el primer `:` separa el nombre, por lo que el valor puede contener más, como `last_server:play.example.net:25565`.

Para contar los clics en un botón, suma 1 al valor anterior:

```
clicks:{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

**Obtener valor de variable (FM Variable)** devuelve `0` mientras `clicks` esté vacía, así que el primer clic la establece en `1`.

Establecer valor de variable nunca convierte una lista en texto. Un array JSON se convierte en los elementos de la lista, el texto vacío la vacía y cualquier otro texto pasa a ser su único elemento.

[**Eliminar variable (FM Variable)**](/action-scripts#delete-variable-fm-variable) elimina una variable y [**Vaciar todas las variables (FM Variable)**](/action-scripts#clear-all-variables-fm-variable) las elimina todas.

## Acciones de lista

Cada acción de lista tiene su propia ventana. Todos sus campos admiten marcadores de posición.

| Acción | Qué hace |
|---|---|
| [**Añadir a lista (FM Variable)**](/action-scripts#add-to-list-fm-variable) | Añade un elemento al final o en un índice. **Omitir si ya está en la lista** no lo añade si la lista ya lo contiene. |
| [**Establecer elemento de lista (FM Variable)**](/action-scripts#set-list-entry-fm-variable) | Sustituye el elemento de un índice. |
| [**Eliminar de lista (FM Variable)**](/action-scripts#remove-from-list-fm-variable) | Elimina el **Elemento en el índice**, la **Primera coincidencia** de un valor o **Todas las coincidencias**. |
| [**Vaciar lista (FM Variable)**](/action-scripts#clear-list-fm-variable) | Elimina todos los elementos. La lista sigue existiendo, pero queda vacía. |
| [**Establecer lista (FM Variable)**](/action-scripts#set-list-fm-variable) | Sustituye todos los elementos por las partes de un **Texto dividido** o por los elementos de un **Array JSON**. `$$other_list` como array JSON copia otra lista. |
| [**Ordenar lista (FM Variable)**](/action-scripts#arrange-list-fm-variable) | **Ordenar de A a Z**, **Ordenar de Z a A**, **Números, de menor a mayor**, **Números, de mayor a menor**, **Invertir orden**, **Mezclar** o **Eliminar duplicados**. |

- Las acciones de lista crean la lista si aún no existe y convierten en listas las variables de texto vacías. Nunca modifican una variable de texto que tenga un valor: primero [conviértela](#cambiar-variables).
- Escribe el nombre de la lista sin `$$`. Si incluyes `$$`, la acción utiliza como nombre el valor de esa variable.

Por ejemplo, un elemento de texto muestra el primer elemento de la lista `tips`:

```
{"placeholder":"list_get","values":{"name":"tips","index":"0"}}
```

A continuación, un botón «Siguiente consejo» tiene la acción **Ordenar lista (FM Variable)** con la opción **Mezclar** en su script de acciones:

<img width="800" alt="Cómo añadir Ordenar lista con la lista tips y la opción Mezclar al script de acciones de un botón Siguiente consejo en el editor de diseños" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_script.gif?raw=true">

Cada clic mezcla la lista, por lo que el texto muestra un consejo aleatorio:

<img width="800" alt="Al hacer clic en el botón Siguiente consejo, se muestra un consejo del día diferente" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_result.gif?raw=true">

## Recorrer una lista

El bucle [FOR EACH](/action-scripts#for-each-loop) ejecuta las acciones que contiene una vez por cada elemento de una lista, del primero al último.

1. Haz clic con el botón derecho en el área de scripts del editor de scripts de acciones y selecciona **Añadir bucle FOR EACH**.
2. Escribe el nombre de la variable de lista, sin `$$`, y haz clic en **Listo**.
3. Añade acciones dentro del bucle. En sus valores, `$$list_entry` representa el elemento actual y `$$list_index`, su índice.

Por ejemplo, una lista `starter_commands` con los elementos `/time set day` y `/weather clear`, y una acción [**Enviar mensaje/comando de chat**](/action-scripts#send-chat-messagecommand) dentro del bucle con este valor, ejecutan ambos comandos:

```
$$list_entry
```

- El bucle lee la lista una vez al iniciarse. Las acciones que contiene pueden modificar la lista sin cambiar los elementos que recorre el bucle.
- Si se usa una variable de texto o una lista que no existe, el bucle no se ejecuta.
- Al igual que los bucles WHILE, se detiene tras 3 segundos para evitar que el juego se quede bloqueado.

# Comprobar variables

Los [requisitos](/conditions) muestran elementos o ejecutan partes de scripts de acciones solo cuando una variable tiene un valor determinado.

- [**El valor de la variable es (FM Variable)**](/conditions#is-variable-value-fm-variable) comprueba el valor completo. En las listas, compara el array JSON con todos sus elementos.
- [**La lista contiene el elemento (FM Variable)**](/conditions#list-contains-entry-fm-variable) comprueba si una lista contiene un elemento. Debe coincidir con el elemento completo. **Ignorar mayúsculas y minúsculas** hace que `Apple` coincida con `apple`.
- [**Es un número**](/conditions#is-number) compara números, por ejemplo, si `$$clicks` es mayor que `5`.

Por ejemplo, un botón abre la publicación de noticias más reciente y añade `news_42` a una lista `read_news` con **Añadir a lista (FM Variable)**. Una insignia «¡Nuevo!» junto al botón tiene como requisito **La lista contiene el elemento (FM Variable)** para `news_42`, con el **Modo del requisito** en Opuesto. Así, la insignia se oculta cuando el jugador ha leído la publicación.

# Vincular variables a elementos

- [Campo de entrada de texto](/elements#text-input-field): **Vincular a variable** guarda en la variable lo que escribe el jugador y el campo muestra el valor de la variable. Si se vincula a una lista, el texto escrito sustituye la lista completa.
- [Casilla](/elements#checkbox): activa **Modo de variable** y configura **Vincular a variable**. La casilla guarda `true` o `false` en la variable.
- [Deslizador](/elements#slider) de tipo **Lista de valores**: **Valores de variable de lista** obtiene los valores del deslizador de una lista. Los elementos que se añadan o eliminen de la lista aparecerán de inmediato.

# Reaccionar a los cambios

- El listener [**Al actualizar variable [FM Variable]**](/listeners#on-variable-updated-fm-variable) ejecuta un script de acciones cada vez que se establece una variable.
- El comando [`/fmvariable`](/commands#fmvariable) permite establecer y leer variables desde el chat, bloques de comandos y otros mods.

# Dónde se guardan las variables

FancyMenu guarda las variables de inmediato en `<game-directory>/config/fancymenu/user_variables.db`, para que se conserven tras reiniciar el juego.

- Las variables pertenecen a toda la instancia de Minecraft y a su [perfil](/profiles) activo. No son independientes para cada diseño, mundo, servidor o jugador.
- Los nombres distinguen entre mayúsculas y minúsculas.
- No guardes contraseñas, tokens ni otros secretos en las variables. Cualquier persona con acceso a la carpeta del juego puede leerlos.
