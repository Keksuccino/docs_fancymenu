---
title: Animator de elementos
description: Cómo animar elementos con fotogramas clave usando el Animator de elementos.
---

# Animator de elementos

El **Animator** es un elemento que te permite animar otros elementos. Con este elemento, puedes cambiar de forma fluida el tamaño, la posición y el punto de anclaje de otro elemento a lo largo del tiempo mediante fotogramas clave. Los fotogramas clave son como instantáneas que capturan cómo debe verse el elemento en un momento concreto. Luego, el elemento Animator reproduce estas instantáneas en orden para crear un movimiento fluido.

> El **Animator de elementos** te permite controlar la **posición, el tamaño y el punto de anclaje** de los elementos. **NO** es posible controlar ningún otro ajuste de los elementos, como la opacidad, la visibilidad, la rotación, etc.
{.is-warning}

# Tutorial en vídeo

Como a muchos de vosotros os confundía un poco cómo funciona el animator, he hecho un pequeño vídeo que muestra cómo usarlo.

[FancyMenu | How to Use the Element Editor - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Añadir el elemento Animator

1. **Haz clic derecho sobre el fondo:**  
   En el editor de diseño, haz clic derecho sobre el fondo.

2. **Selecciona Nuevo elemento -> Element Animator:**  
   En el menú que aparece, ve a **Nuevo elemento** y haz clic en **Element Animator**. Esto añade el elemento Animator a tu diseño.

3. **Configúralo:**  
   Después de añadirlo, el elemento Animator aparece con sus ajustes predeterminados. Puedes cambiar opciones como el bucle o el color haciendo clic derecho sobre el Animator y eligiendo una opción del menú.

# Gestión de fotogramas clave

Los fotogramas clave son como marcadores que le indican al Animator cómo debe verse el elemento en un momento determinado.

## Abrir el editor de fotogramas clave

- **Abrir el editor:**  
  Haz clic derecho sobre el elemento Animator y elige **Editar fotogramas clave** (o **Gestionar fotogramas clave**). Esto abre una pantalla en la que puedes añadir, editar o eliminar fotogramas clave.

## Grabar y añadir fotogramas clave

- **Iniciar grabación:**  
  En el editor de fotogramas clave, pulsa la tecla **`R`** para empezar a grabar. Cuando la grabación está activa, el recuadro de vista previa cambia de color para indicarlo.
  
- **Cambiar la vista previa:**  
  Mueve o cambia el tamaño del recuadro de vista previa para establecer el aspecto que quieras. En el modo de desplazamiento, la vista previa permanece centrada en una cruz, de modo que los cambios se muestran como desplazamientos.
  
- **Añadir un fotograma clave:**  
  Pulsa la tecla **`K`** para guardar el aspecto actual como un fotograma clave. Este fotograma guarda la posición, el tamaño y la configuración del ancla de la vista previa.

## Editar fotogramas clave

- **Seleccionar un fotograma clave:**  
  Haz clic en un marcador de fotograma clave de la línea de tiempo. También puedes mantener pulsado **Ctrl** y hacer clic para seleccionar más de uno.
  
- **Mover un fotograma clave:**  
  Arrastra el marcador del fotograma clave hacia la izquierda o la derecha para cambiar su momento temporal. También puedes usar:
  - **Flecha izquierda:** para moverlo 100 ms antes.
  - **Flecha derecha:** para moverlo 100 ms después.
  
- **Ajustar la vista previa con precisión:**  
  Cuando hay un fotograma clave seleccionado, ajusta el recuadro de vista previa moviéndolo o cambiando su tamaño. Usa **Ctrl + Z** para deshacer y **Ctrl + Y** para rehacer los cambios si es necesario.

## Eliminar fotogramas clave

- **Eliminar un fotograma clave:**  
  Selecciona un fotograma clave y pulsa la tecla **Supr** para eliminarlo.
  
- **Eliminar varios fotogramas clave:**  
  Puedes seleccionar varios fotogramas clave (por ejemplo, usando **Ctrl + A** para seleccionarlos todos) y pulsar Supr para eliminarlos todos.

## Suavizado de fotogramas clave

El suavizado de fotogramas clave es una función que te ayuda a espaciar uniformemente tus fotogramas clave. Esto hace que la animación se vea más consistente y fluida.

- **Selecciona varios fotogramas clave:**  
  Primero, selecciona dos o más fotogramas clave que quieras suavizar (usa **Ctrl + clic** o **Ctrl + A**).

- **Haz clic en el botón de suavizado:**  
  En la barra inferior del editor de fotogramas clave, haz clic en el botón etiquetado como **Distance Smoothing**.

- **Introduce una nueva distancia:**  
  Aparecerá un pequeño cuadro de entrada. Escribe un valor (en milisegundos) para establecer el mismo intervalo de tiempo entre cada fotograma clave seleccionado.

- **Aplicar el suavizado:**  
  Pulsa Enter para aplicar el suavizado. Los fotogramas clave se ajustarán para que la diferencia de tiempo entre ellos sea uniforme.

# Previsualizar tu animación

Después de grabar fotogramas clave, puedes ver cómo quedará tu animación:

- **Reproducir la animación:**  
  En el editor de fotogramas clave, pulsa la tecla **`P`** o haz clic en el botón de reproducir. La vista previa comenzará desde el principio y mostrará cómo cambia el recuadro de vista previa con el tiempo.
  
- **Nota sobre el bucle:**  
  Mientras previsualizas en el editor de fotogramas clave, la animación **no** se repetirá en bucle. Esto significa que se reproduce de principio a fin solo una vez. El bucle solo estará activo cuando el elemento Animator se aplique a un elemento objetivo en el diseño final.
  
- **Pausar la vista previa:**  
  Pulsa de nuevo la tecla **`P`** para pausar la animación si quieres detenerte en un punto concreto.
  
- **Arrastrar la barra de progreso:**  
  Si está disponible, puedes arrastrar el marcador de la línea de tiempo para comprobar cómo se ve la animación en un momento específico.

# Elegir elementos objetivo

Después de configurar tus fotogramas clave, debes elegir qué elementos del diseño se animarán:

1. **Abre el gestor de objetivos:**  
   Haz clic derecho sobre el elemento Animator y elige **Gestionar objetivos**.
  
2. **Añadir objetivos:**  
   Haz clic en **Añadir objetivo** para ver una lista de elementos disponibles. Elige los que quieras animar.
  
3. **Eliminar objetivos:**  
   Para eliminar un objetivo, abre el gestor y haz clic en **Eliminar objetivo**.

Cuando la animación se reproduzca en el diseño final, el Animator usará tus fotogramas clave para cambiar el tamaño, la posición y más de los elementos elegidos. Si lo has configurado, aquí se aplicará el bucle.

# Atajos de teclado

Usa estos atajos en el editor de fotogramas clave para trabajar más rápido:

- **Tecla `R`:** Iniciar o detener la grabación.
- **Tecla `T`:** Pausar o reanudar la grabación.
- **Tecla `P`:** Reproducir o pausar la vista previa de la animación.
- **Tecla `K`:** Añadir un nuevo fotograma clave en el momento actual.
- **Teclas de flecha izquierda/derecha:**  
  - **Flecha izquierda:** Mover un fotograma clave 100 ms antes.
  - **Flecha derecha:** Mover un fotograma clave 100 ms después.
- **Tecla Supr:** Eliminar el/los fotograma(s) clave seleccionado(s).
- **Ctrl + A:** Seleccionar todos los fotogramas clave.
- **Ctrl + Z:** Deshacer el último cambio.
- **Ctrl + Y:** Rehacer el cambio que acabas de deshacer.
- **Ctrl + arrastrar fotograma clave**: Arrastrar varios fotogramas clave seleccionados a la vez.

# Ajustes y consejos extra

- **Repetir animación:**  
  Puedes configurar el Animator para que se repita en bucle. Cuando el bucle está activado, la animación se reiniciará después del último fotograma clave, pero ten en cuenta que esto solo ocurre para el elemento objetivo final. En la vista previa del editor de fotogramas clave, el bucle no se produce.
  
- **Ignorar tamaño/posición:**  
  Si no quieres que los fotogramas clave cambien el tamaño o la posición de un elemento, desactiva estas opciones.

- **Desplazamientos de tiempo:**
  FancyMenu 3.9.0 añade desplazamientos de tiempo para los elementos controlados. Puedes desplazar elementos objetivo individuales o usar desplazamientos de tiempo aleatorios dentro de un rango configurado, de modo que una misma animación pueda empezar en momentos ligeramente distintos para cada objetivo.
  
- **Modo de desplazamiento:**  
  En el modo de desplazamiento, las animaciones se aplican como cambios respecto a la posición original del elemento. La vista previa se muestra centrada en una cruz.
  
- **Deshacer y rehacer:**  
  Usa **Ctrl + Z** para deshacer y **Ctrl + Y** para rehacer los cambios.
  
- **Comprueba el orden:**  
  Asegúrate de que tus fotogramas clave estén en el orden temporal correcto. El sistema los ordena por ti, pero si mueves uno, comprueba de nuevo el orden.
  
- **Previsualizar cambios:**  
  Usa el botón de reproducir o la tecla **`P`** para ver tu animación en acción antes de guardarla.

# Conclusión

Siguiendo estos sencillos pasos, puedes añadir un elemento Animator a tu diseño y crear animaciones fluidas. Tanto si grabas cambios en directo con la vista previa, ajustas fotogramas clave con el teclado, eliges qué elementos animar o previsualizas tu animación para ver cómo queda, el elemento Animator te ofrece una forma sencilla de dar vida a tus menús personalizados.

¡Feliz animación!
