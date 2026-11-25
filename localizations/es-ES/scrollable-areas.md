---
title: Áreas desplazables
description: >-
  Cómo añadir elementos a un área desplazable, organizarlos y cambiar el
  desplazamiento del área.
sourceBlobSha: a424c5e8680ece5f25846de0399fc8e78f375e15
---
# Áreas desplazables

Un **área desplazable** contiene otros elementos y permite que los jugadores se desplacen por ellos. Es ideal para listas largas de botones, selectores de mundos o servidores, exhibiciones de objetos, paneles de noticias y cualquier otra cosa que no quepa en una sola pantalla.

Todo lo que hay en el área se desplaza con ella y queda recortado por sus bordes.

<img width="800" alt="Añadir botones a un área desplazable y apilarlos" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_showcase.gif?raw=true">

> [!NOTE]
> Solo se pueden añadir al área los elementos que hayas agregado al diseño. Los [elementos de Vanilla](/vanilla-elements) no se pueden añadir porque pertenecen al propio menú.

# Añadir un área desplazable

1. Abre un diseño en el editor de diseños.
2. Haz clic derecho en el fondo del editor y selecciona **Nuevo elemento -> Área desplazable**.
3. Arrastra elementos al área.

# Añadir y quitar elementos

- Arrastra un elemento al área para añadirlo. El área se ilumina cuando acepta el elemento. El elemento solo se añade si una parte de él está dentro del área.
- Para arrastrar varios elementos seleccionados a la vez, mantén pulsada la tecla `Ctrl` (`Cmd` en macOS) al empezar a arrastrar.
- Mientras arrastras un elemento cerca del borde del área, esta se desplaza para que puedas acceder a todas sus partes. También puedes desplazarte por ella con la rueda del ratón en el editor.
- Para quitar un elemento, arrástralo fuera del área o haz clic derecho sobre él y selecciona **Sacar del área desplazable**. El elemento se queda donde está en la pantalla.
- También puedes introducir áreas dentro de otras áreas.

## Capas

En el [widget Capas](/layout-editor#scrollable-areas), los elementos de un área aparecen debajo de ella. Arrastra capas hasta allí para añadirlas a un área o sacarlas de ella, o para cambiar su orden. El botón de contraer de la capa de un área oculta sus elementos en la lista.

## Copiar y eliminar

- Al copiar un área, también se copia todo lo que contiene.
- Si eliminas un área que aún contiene elementos, se te preguntará qué quieres hacer con ellos: **Eliminar elementos** también los elimina; **Conservar elementos** los mantiene donde están en la pantalla.

# Organizar elementos

Haz clic derecho en el área y abre **Organización**. **Modo** define cómo coloca el área sus elementos:

- **Anclas**: colocas los elementos tú mismo, como en el resto del diseño. Las áreas nuevas usan este modo.
- **Pila**: los elementos se colocan uno tras otro.
- **Cuadrícula**: los elementos se colocan en celdas del mismo tamaño.
- **Flujo**: los elementos se colocan uno al lado del otro y empiezan una nueva línea cuando la anterior está llena.

<img width="800" alt="Áreas desplazables en los modos Pila, Cuadrícula y Flujo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_modes.png?raw=true">

## Modo Anclas

Los elementos de un área tienen sus propias anclas, que hacen referencia al contenido del área en vez de a la pantalla. Por ejemplo, el ancla **Esquina superior izquierda** corresponde a la esquina superior izquierda del contenido, y las anclas inferiores se ajustan al final del contenido. Consulta [Colocar elementos](/positioning-elements) para saber cómo funcionan las anclas.

- **Estirar horizontalmente** y **Estirar verticalmente** hacen que el elemento tenga la misma anchura o altura que el contenido.
- Los elementos solo se pueden anclar a otros elementos de la misma área. Al mover un elemento dentro o fuera de un área, los elementos que estaban anclados al otro lado del borde del área pasan a tener el ancla **Esquina superior izquierda** y se quedan donde están.

### Tamaño del contenido

En el modo Anclas, decides el tamaño del contenido y, por tanto, cuánto se desplaza el área.

Selecciona el área y arrastra el controlador del extremo de su contenido. Arrástralo más allá del borde para seguir avanzando; el área se desplazará a la vez.

<img width="698" alt="Controlador del contenido de un área desplazable seleccionada" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/scroll_area_content_handle.png?raw=true">

También puedes hacer clic derecho en el área y abrir **Tamaño del contenido**:

- **Anchura del contenido** y **Altura del contenido** establecen el tamaño mediante un valor numérico. Admiten [marcadores de posición](/placeholders). Si se usa un marcador de posición, no se puede arrastrar el controlador.
- **Ajustar al contenido** hace que el contenido termine justo donde termina el último elemento que contiene. Los elementos anclados al centro o al final del contenido se desplazan con él, por lo que no se tienen en cuenta.

El contenido nunca es más pequeño que el área y solo aumenta en las direcciones en las que se desplaza el área.

## Pila, Cuadrícula y Flujo

- El área coloca los elementos por ti y el contenido aumenta automáticamente con ellos.
- Arrastra un elemento para cambiarlo de orden. Una línea indica dónde se colocará.
- Al cambiar de Anclas a uno de estos modos, se conserva el orden que tenían los elementos en la pantalla. Al volver a Anclas, cada elemento se queda donde estaba.
- Los elementos que ocultan sus [requisitos](/conditions) no dejan huecos.
- El estiramiento no funciona en estos modos.
- Estos modos solo se desplazan en una dirección. Un área configurada como **Ambas** se desplaza verticalmente.

Abre **Organización** para ajustar estos modos:

| Ajuste | Función |
|---|---|
| **Alineación** | Dónde se sitúan los elementos en el eje perpendicular a la dirección en la que se alinean: **Inicio**, **Centro**, **Final** o **Rellenar**. Con **Rellenar**, ocupan toda la anchura disponible (o toda la altura, en las áreas con desplazamiento horizontal). Flujo no incluye la opción **Rellenar**. |
| **Espaciado** | Espacio entre los elementos. |
| **Relleno** | Espacio entre los elementos y los bordes del contenido. |
| **Elementos por línea** | Solo para Cuadrícula. Número de elementos por línea. |
| **Ajustar tantos como sea posible** | Solo para Cuadrícula. Coloca tantos elementos como quepan en una línea, en lugar de usar un número fijo. **Tamaño mínimo de celda** determina cuántos caben. |

# Desplazamiento

Los jugadores se desplazan por el área con la rueda del ratón. Mantén pulsada la tecla `Shift` para desplazarte horizontalmente.

- **Dirección de desplazamiento** determina si el área se desplaza en vertical (**Vertical**), en horizontal (**Horizontal**) o en ambas direcciones (**Ambas**). En las direcciones en las que no se desplaza, el contenido tiene exactamente el mismo tamaño que el área.
- Los elementos de texto de un área se desplazan primero. Cuando llegan al final, el área sigue desplazándose.
- Cuando los jugadores pasan de un botón a otro con `Tab`, el área se desplaza hasta el botón seleccionado.

Los menús **Desplazamiento**, **Desplazamiento automático** y **Barras de desplazamiento** incluyen los mismos ajustes que los elementos de texto. Consulta [Texto en los menús](/text-in-menus#scrolling-settings) para verlos todos. Estas son las diferencias:

- Con **Ajuste**, el contenido puede ajustarse **A los elementos**, de modo que un elemento quede siempre al principio del área, o **A las páginas**.
- Los botones y todos los demás elementos del área siguen funcionando aunque la opción **Arrastrar para desplazarse** esté activada.
- Los controladores de desplazamiento son controles de píxeles, a menos que les asignes tus propias **Texturas de los controladores de desplazamiento** o un **Color de los controladores de desplazamiento [HEX]**.

# Fondo

Las áreas dibujan un panel detrás de su contenido. Abre **Fondo** para cambiarlo. Funciona como el [fondo de los elementos de texto](/text-in-menus#background): desactívalo con **Mostrar fondo**, usa una textura propia con [división en nueve partes](/nine-slicing-and-tiling) o repetición, y cambia hasta dónde llega con **Relleno**.

# Desplazamiento con acciones

También puedes controlar y consultar las áreas desde otras partes de FancyMenu:

- La [acción](/action-scripts) **Desplazar un elemento** desplaza un área hasta el principio, el final, una posición o uno de los elementos que contiene.
- Los [marcadores de posición](/placeholders) **Posición de desplazamiento del elemento**, **Porcentaje de desplazamiento del elemento** y **Tamaño del contenido desplazable del elemento** indican cuánto se ha desplazado el área y el tamaño de su contenido.
- El [requisito](/conditions) **El elemento está desplazado hasta el final** comprueba si el área ha llegado al final de su desplazamiento.
- Los [eventos](/listeners) **Al desplazarse el elemento**, **Al desplazarse el elemento hasta el principio** y **Al desplazarse el elemento hasta el final** ejecutan acciones mientras el área se desplaza.

Todo esto necesita el [identificador del elemento](/element-identifiers) del área. Por ejemplo, esto muestra cuánto se ha desplazado un área, de 0 a 100:

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"3f2a9c1e-7b4d-4e8a-9c2f-1d5e6a7b8c9d-1763950000000","axis":"vertical"}}
```

# Información útil

- Al ocultar un área, se oculta todo lo que contiene. La opacidad del área también se aplica a todos sus elementos.
- Las áreas no se pueden rotar ni inclinar, y el paralaje no funciona ni en las áreas ni en los elementos que contienen.
- Los elementos de información emergente de un área quedan recortados por sus bordes, salvo que sigan al ratón.
