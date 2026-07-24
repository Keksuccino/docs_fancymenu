---
title: Precargar recursos
description: >-
  Cómo precargar recursos para que estén listos para usar en cuanto el juego
  termine de cargar.
---
# Precargar recursos

La precarga prepara los recursos seleccionados antes de que un menú los necesite. Úsala para recursos que, de lo contrario, parpadean, muestran un primer fotograma negro o aparecen con retraso.

# Añadir recursos al precargador

Abre **Personalización -> Precargar recursos**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

La lista acepta recursos compatibles de imagen, animación, audio, vídeo y texto desde archivos locales, URL web o paquetes de recursos. No precarga una página en vivo de [Browser](./elements#browser).

El precargador se inicia durante el arranque del juego y al recargar recursos de Minecraft. Espera a que cada entrada termine o falle antes de continuar, con un límite de dos minutos por entrada.

Los recursos cargados permanecen en caché hasta que FancyMenu libere los recursos durante una recarga o al cerrar el cliente. **Personalización -> Recargar FancyMenu** libera la caché, pero no vuelve a ejecutar el precargador.

La precarga aumenta el tiempo de carga y el uso de RAM/VRAM. Añade solo los recursos que deban estar listos de inmediato; elimina entradas grandes si el cliente se queda sin memoria.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Precargar presentaciones y panoramas

Añadir una [presentación](./slideshows) carga todas sus imágenes y la superposición opcional. Añadir un [panorama](./panoramas) carga las seis caras y su superposición opcional.

**Personalización -> Recargar FancyMenu** no ejecuta el precargador. Usa una recarga de recursos de Minecraft o reinicia el juego después de cambiar la lista de precarga.
