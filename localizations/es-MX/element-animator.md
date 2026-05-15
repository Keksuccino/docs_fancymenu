---
title: Animador de Elementos
description: Cómo animar elementos con fotogramas clave usando el Animador de Elementos.
---

# Animador de Elementos

El **Animador** es un elemento que te permite animar otros elementos. Con este elemento, puedes cambiar suavemente el tamaño, la posición y el punto de anclaje de otro elemento a lo largo del tiempo usando fotogramas clave. Los fotogramas clave son como capturas instantáneas que registran cómo debe verse el elemento en un momento específico. Después, el elemento Animador reproduce estas capturas en orden para crear un movimiento fluido.

> El **Animador de Elementos** te permite controlar la **posición, el tamaño y el punto de anclaje** de los elementos. **NO** es posible controlar ninguna otra configuración de los elementos, como la opacidad, la visibilidad, la rotación, etc.!
{.is-warning}

# Video Tutorial

Como muchos estaban un poco confundidos sobre cómo funciona el animador, hice un pequeño video que muestra cómo usarlo.

[FancyMenu | Cómo usar el editor de elementos - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Agregar el elemento Animador

1. **Clic derecho en el fondo:**  
   En el editor de diseño, haz clic derecho sobre el fondo.

2. **Selecciona Nuevo elemento -> Animador de Elementos:**  
   En el menú que aparece, ve a **Nuevo elemento** y haz clic en **Animador de Elementos**. Esto agrega el elemento Animador a tu diseño.

3. **Configúralo:**  
   Después de agregarlo, el elemento Animador aparece con su configuración predeterminada. Puedes cambiar opciones como el ciclo o el color haciendo clic derecho sobre el Animador y eligiendo una opción del menú.

# Administrar fotogramas clave

Los fotogramas clave son como marcadores que le dicen al Animador cómo debe verse el elemento en cierto momento.

## Abrir el editor de fotogramas clave

- **Abrir el editor:**  
  Haz clic derecho en el elemento Animador y selecciona **Editar fotogramas clave** (o **Administrar fotogramas clave**). Esto abre una pantalla donde puedes agregar, editar o eliminar fotogramas clave.

## Grabar y agregar fotogramas clave

- **Iniciar grabación:**  
  En el editor de fotogramas clave, presiona la tecla **`R`** para comenzar a grabar. Cuando la grabación está activa, el recuadro de vista previa cambia de color para mostrarlo.
  
- **Cambiar la vista previa:**  
  Mueve o cambia el tamaño del recuadro de vista previa para definir el aspecto que quieres. En el modo de desplazamiento, la vista previa se mantiene centrada en una cruz, de modo que los cambios se muestran como desplazamientos.
  
- **Agregar un fotograma clave:**  
  Presiona la tecla **`K`** para guardar el aspecto actual como un fotograma clave. Este fotograma clave guarda la posición, el tamaño y la configuración del anclaje de la vista previa.

## Editar fotogramas clave

- **Seleccionar un fotograma clave:**  
  Haz clic en un marcador de fotograma clave en la línea de tiempo. También puedes mantener presionada la tecla **Ctrl** y hacer clic para seleccionar más de uno.
  
- **Mover un fotograma clave:**  
  Arrastra el marcador del fotograma clave hacia la izquierda o la derecha para cambiar su tiempo. También puedes usar:
  - **Flecha izquierda:** para moverlo 100 ms antes.
  - **Flecha derecha:** para moverlo 100 ms después.
  
- **Ajustar la vista previa:**  
  Cuando un fotograma clave está seleccionado, ajusta el recuadro de vista previa moviéndolo o cambiando su tamaño. Usa **Ctrl + Z** para deshacer y **Ctrl + Y** para rehacer los cambios si es necesario.

## Eliminar fotogramas clave

- **Eliminar un fotograma clave:**  
  Selecciona un fotograma clave y presiona la tecla **Supr** para quitarlo.
  
- **Eliminar varios fotogramas clave:**  
  Puedes seleccionar varios fotogramas clave (por ejemplo, usando **Ctrl + A** para seleccionar todos) y presionar Supr para eliminarlos todos.

## Suavizado de fotogramas clave

El suavizado de fotogramas clave es una función que te ayuda a espaciar de forma uniforme tus fotogramas clave. Esto hace que tu animación se vea más consistente y fluida.

- **Selecciona varios fotogramas clave:**  
  Primero, selecciona dos o más fotogramas clave que quieras suavizar (usa **Ctrl + clic** o **Ctrl + A**).

- **Haz clic en el botón de suavizado:**  
  En la barra inferior del editor de fotogramas clave, haz clic en el botón llamado **Distance Smoothing**.

- **Ingresa una nueva distancia:**  
  Aparecerá un pequeño cuadro de entrada. Escribe un valor (en milisegundos) para establecer el mismo intervalo de tiempo entre cada fotograma clave seleccionado.

- **Aplicar el suavizado:**  
  Presiona Enter para aplicar el suavizado. Los fotogramas clave se ajustarán para que la diferencia de tiempo entre ellos sea uniforme.

# Vista previa de tu animación

Después de grabar fotogramas clave, puedes ver cómo se verá tu animación:

- **Reproducir la animación:**  
  En el editor de fotogramas clave, presiona la tecla **`P`** o haz clic en el botón de reproducir. La vista previa comenzará desde el inicio y mostrará cómo cambia el recuadro de vista previa con el tiempo.
  
- **Nota sobre el ciclo:**  
  Mientras previsualizas en el editor de fotogramas clave, la animación **no** se repetirá en ciclo. Esto significa que se reproduce una sola vez, de inicio a fin. El ciclo solo estará activo cuando el elemento Animador se aplique a un elemento objetivo en el diseño final.
  
- **Pausar la vista previa:**  
  Presiona de nuevo la tecla **`P`** para pausar la animación si quieres detenerte en un punto específico.
  
- **Arrastrar la barra de progreso:**  
  Si está disponible, puedes arrastrar el marcador de la línea de tiempo para ver cómo se ve la animación en cualquier momento específico.

# Elegir elementos objetivo

Después de configurar tus fotogramas clave, necesitas elegir qué elementos del diseño se animarán:

1. **Abrir el administrador de objetivos:**  
   Haz clic derecho en el elemento Animador y selecciona **Administrar objetivos**.
  
2. **Agregar objetivos:**  
   Haz clic en **Agregar objetivo** para ver una lista de elementos disponibles. Elige los que quieras animar.
  
3. **Eliminar objetivos:**  
   Para quitar un objetivo, abre el administrador y haz clic en **Eliminar objetivo**.

Cuando la animación se reproduzca en el diseño final, el Animador usará tus fotogramas clave para cambiar el tamaño, la posición y más de los elementos elegidos. El ciclo se aplicará aquí si lo configuraste.

# Atajos de teclado

Usa estos atajos en el editor de fotogramas clave para trabajar más rápido:

- **Tecla `R`:** Iniciar o detener la grabación.
- **Tecla `T`:** Pausar o reanudar la grabación.
- **Tecla `P`:** Reproducir o pausar la vista previa de la animación.
- **Tecla `K`:** Agregar un nuevo fotograma clave en el tiempo actual.
- **Teclas de flecha izquierda/derecha:**  
  - **Flecha izquierda:** Mueve un fotograma clave 100 ms antes.
  - **Flecha derecha:** Mueve un fotograma clave 100 ms después.
- **Tecla Supr:** Elimina el/los fotograma(s) clave seleccionado(s).
- **Ctrl + A:** Selecciona todos los fotogramas clave.
- **Ctrl + Z:** Deshace tu último cambio.
- **Ctrl + Y:** Rehace el cambio que acabas de deshacer.
- **Ctrl + arrastrar fotogramas clave**: Arrastra varios fotogramas clave seleccionados al mismo tiempo.

# Configuraciones extra y consejos

- **Ciclo de animación:**  
  Puedes configurar el Animador para que se repita en ciclo. Cuando el ciclo está activado, la animación reiniciará después del último fotograma clave, pero ten en cuenta que esto solo ocurre para el elemento objetivo final. En la vista previa del editor de fotogramas clave, no ocurre el ciclo.
  
- **Ignorar tamaño/posición:**  
  Si no quieres que los fotogramas clave cambien el tamaño o la posición de un elemento, desactiva estas opciones.

- **Desplazamientos de tiempo:**
  FancyMenu 3.9.0 agrega desplazamientos de tiempo para los elementos controlados. Puedes aplicar desplazamientos individuales a cada elemento objetivo, o usar desplazamientos de tiempo aleatorios dentro de un rango configurado, para que una animación pueda comenzar en momentos ligeramente distintos para cada objetivo.
  
- **Modo de desplazamiento:**  
  En el modo de desplazamiento, las animaciones se aplican como cambios respecto al lugar original del elemento. La vista previa se muestra centrada sobre una cruz.
  
- **Deshacer y rehacer:**  
  Usa **Ctrl + Z** para deshacer y **Ctrl + Y** para rehacer cambios.
  
- **Revisa el orden:**  
  Asegúrate de que tus fotogramas clave estén en el orden correcto por tiempo. El sistema los ordena por ti, pero si mueves uno, revisa de nuevo el orden.
  
- **Ver cambios en la vista previa:**  
  Usa el botón de reproducir o la tecla **`P`** para ver tu animación en acción antes de guardarla.

# Conclusión

Siguiendo estos pasos sencillos, puedes agregar un elemento Animador a tu diseño y crear animaciones fluidas. Ya sea que grabes cambios en vivo con la vista previa, ajustes fotogramas clave con tu teclado, elijas qué elementos animar o previsualices tu animación para ver cómo se ve, el elemento Animador te ofrece una forma fácil de dar vida a tus menús personalizados.

¡Feliz animación!
