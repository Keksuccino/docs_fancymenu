---
title: Animador de elementos
description: Cómo animar elementos con fotogramas clave usando el Animador de elementos.
---

# Animador de elementos

El **Animador** es un elemento que te permite animar otros elementos. Con este elemento, puedes cambiar suavemente el tamaño, la posición y el punto de anclaje de otro elemento a lo largo del tiempo usando fotogramas clave. Los fotogramas clave son como instantáneas que capturan cómo debe verse el elemento en un momento concreto. Después, el elemento Animador reproduce estas instantáneas en orden para crear un movimiento fluido.

> [!WARNING]
> El **Animador de elementos** te permite controlar la **posición, el tamaño y el punto de anclaje** de los elementos. **NO** es posible controlar ningún otro ajuste de los elementos, como la opacidad, la visibilidad, la rotación, etc.!

# Tutorial en vídeo

Como a muchos os confundía un poco cómo funciona el animador, hice un pequeño vídeo que muestra cómo usarlo.

[FancyMenu | Cómo usar el editor de elementos - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Añadir el elemento Animador

1. **Haz clic derecho en el fondo:**  
   En el editor de diseño, haz clic derecho sobre el fondo.

2. **Selecciona Nuevo elemento -> Animador de elementos:**  
   En el menú que aparece, ve a **Nuevo elemento** y haz clic en **Animador de elementos**. Esto añade el elemento Animador a tu diseño.

3. **Configúralo:**  
   Después de añadirlo, el elemento Animador aparece con su configuración predeterminada. Puedes cambiar opciones como el bucle o el color haciendo clic derecho sobre el Animador y eligiendo una opción del menú.

# Gestionar fotogramas clave

Los fotogramas clave son como marcadores que le indican al Animador cómo debe verse el elemento en un momento determinado.

## Abrir el editor de fotogramas clave

- **Abre el editor:**  
  Haz clic derecho en el elemento Animador y elige **Editar fotogramas clave** (o **Gestionar fotogramas clave**). Esto abre una pantalla donde puedes añadir, editar o eliminar fotogramas clave.

## Grabar y añadir fotogramas clave

- **Iniciar la grabación:**  
  En el editor de fotogramas clave, pulsa la **tecla `R`** para empezar a grabar. Durante la grabación, el cuadro de vista previa cambia de color para indicar que está activo.
  
- **Cambiar la vista previa:**  
  Mueve o cambia el tamaño del cuadro de vista previa para ajustar el aspecto que quieres. En el modo de desplazamiento, la vista previa se mantiene centrada en una cruz, de modo que los cambios se muestran como desplazamientos.
  
- **Añadir un fotograma clave:**  
  Pulsa la **tecla `K`** para guardar el aspecto actual como fotograma clave. Este fotograma clave guarda la posición, el tamaño y los ajustes de anclaje de la vista previa.

## Editar fotogramas clave

- **Seleccionar un fotograma clave:**  
  Haz clic en un marcador de fotograma clave en la línea de tiempo. También puedes mantener pulsado **Ctrl** y hacer clic para seleccionar más de uno.
  
- **Mover un fotograma clave:**  
  Arrastra el marcador del fotograma clave a izquierda o derecha para cambiar su tiempo. También puedes usar:
  - **Flecha izquierda:** para moverlo 100 ms antes.
  - **Flecha derecha:** para moverlo 100 ms después.
  
- **Ajustar la vista previa con precisión:**  
  Cuando hay un fotograma clave seleccionado, ajusta el cuadro de vista previa moviéndolo o cambiando su tamaño. Usa **Ctrl + Z** para deshacer y **Ctrl + Y** para rehacer los cambios si es necesario.

## Eliminar fotogramas clave

- **Eliminar un fotograma clave:**  
  Selecciona un fotograma clave y pulsa la **tecla Supr** para eliminarlo.
  
- **Eliminar varios fotogramas clave:**  
  Puedes seleccionar varios fotogramas clave (por ejemplo, usando **Ctrl + A** para seleccionarlos todos) y pulsar Supr para eliminarlos todos.

## Suavizado de fotogramas clave

El suavizado de fotogramas clave es una función que te ayuda a espaciar uniformemente tus fotogramas clave. Esto hace que la animación se vea más consistente y fluida.

- **Selecciona varios fotogramas clave:**  
  Primero, selecciona dos o más fotogramas clave que quieras suavizar (usa **Ctrl + clic** o **Ctrl + A**).

- **Haz clic en el botón de suavizado:**  
  En la barra inferior del editor de fotogramas clave, haz clic en el botón llamado **Distance Smoothing**.

- **Introduce una nueva distancia:**  
  Aparecerá un pequeño cuadro de entrada. Escribe un valor (en milisegundos) para establecer el mismo intervalo de tiempo entre cada fotograma clave seleccionado.

- **Aplicar el suavizado:**  
  Pulsa Intro para aplicar el suavizado. Los fotogramas clave se ajustarán para que la diferencia de tiempo entre ellos sea uniforme.

# Previsualizar tu animación

Después de grabar los fotogramas clave, puedes ver cómo se verá tu animación:

- **Reproducir la animación:**  
  En el editor de fotogramas clave, pulsa la **tecla `P`** o haz clic en el botón de reproducir. La vista previa empezará desde el principio y mostrará cómo cambia el cuadro de vista previa a lo largo del tiempo.
  
- **Nota sobre el bucle:**  
  Mientras previsualizas en el editor de fotogramas clave, la animación **no** se repetirá en bucle. Esto significa que se reproduce una sola vez, del principio al final. El bucle solo estará activo cuando el elemento Animador se aplique a un elemento objetivo en el diseño final.
  
- **Pausar la vista previa:**  
  Pulsa de nuevo la **tecla `P`** para pausar la animación si quieres detenerte en un punto concreto.
  
- **Arrastrar la barra de progreso:**  
  Si está disponible, puedes arrastrar el marcador de la línea de tiempo para comprobar cómo se ve la animación en un momento específico.

# Elegir elementos objetivo

Después de configurar tus fotogramas clave, debes elegir qué elementos del diseño se animarán:

1. **Abre el gestor de objetivos:**  
   Haz clic derecho en el elemento Animador y elige **Gestionar objetivos**.
  
2. **Añade objetivos:**  
   Haz clic en **Añadir objetivo** para ver una lista de los elementos disponibles. Elige los que quieras animar.
  
3. **Eliminar objetivos:**  
   Para eliminar un objetivo, abre el gestor y haz clic en **Eliminar objetivo**.

Cuando la animación se reproduzca en el diseño final, el Animador utilizará tus fotogramas clave para cambiar el tamaño, la posición y más de los elementos elegidos. El bucle se aplicará aquí si lo has configurado.

# Atajos de teclado

Usa estos atajos en el editor de fotogramas clave para trabajar más rápido:

- **Tecla `R`:** Iniciar o detener la grabación.
- **Tecla `T`:** Pausar o reanudar la grabación.
- **Tecla `P`:** Reproducir o pausar la vista previa de la animación.
- **Tecla `K`:** Añadir un nuevo fotograma clave en el tiempo actual.
- **Teclas de flecha izquierda/derecha:**  
  - **Flecha izquierda:** Mueve un fotograma clave 100 ms antes.
  - **Flecha derecha:** Mueve un fotograma clave 100 ms después.
- **Tecla Supr:** Elimina el/los fotograma(s) clave seleccionado(s).
- **Ctrl + A:** Selecciona todos los fotogramas clave.
- **Ctrl + Z:** Deshace tu último cambio.
- **Ctrl + Y:** Rehace el cambio que acabas de deshacer.
- **Ctrl + arrastrar fotograma clave**: Arrastra varios fotogramas clave seleccionados a la vez.

# Ajustes y consejos extra

- **Animación en bucle:**  
  Puedes configurar el Animador para que se reproduzca en bucle. Cuando el bucle está activado, la animación se reiniciará después del último fotograma clave; pero ten en cuenta que esto solo ocurre para el elemento objetivo final. En la vista previa del editor de fotogramas clave no hay bucle.
  
- **Ignorar tamaño/posición:**  
  Si no quieres que los fotogramas clave cambien el tamaño o la posición de un elemento, desactiva estas opciones.

- **Desplazamientos de tiempo:**
  Puedes aplicar desplazamientos individuales a cada elemento objetivo o usar desplazamientos de tiempo aleatorios dentro de un rango configurado, de modo que una misma animación comience en momentos distintos para cada objetivo.
  
- **Modo de desplazamiento:**  
  En el modo de desplazamiento, las animaciones se aplican como cambios respecto a la posición original del elemento. La vista previa se muestra centrada sobre una cruz.
  
- **Deshacer y rehacer:**  
  Usa **Ctrl + Z** para deshacer y **Ctrl + Y** para rehacer cambios.
  
- **Comprueba el orden:**  
  Asegúrate de que tus fotogramas clave estén en el orden correcto según el tiempo. El sistema los ordena automáticamente, pero si mueves uno, comprueba de nuevo el orden.
  
- **Revisar cambios:**  
  Usa el botón de reproducir o la **tecla `P`** para ver tu animación en acción antes de guardarla.
