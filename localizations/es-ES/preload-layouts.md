---
title: Precargar recursos
description: >-
  Cómo precargar recursos para que estén listos cuando termine de cargar el
  juego.
sourceBlobSha: 8eca400e05987468c1fd0dc29faa5267083e38d0
---

# Precargar recursos

La precarga prepara recursos seleccionados antes de que un menú los necesite. Úsala con recursos que, de otro modo, parpadeen, muestren un primer fotograma negro o tarden en iniciarse.

# Añadir recursos al precargador

Abre **Personalización -> Precargar recursos**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

La lista admite recursos compatibles de imagen, animación, audio, vídeo y texto, procedentes de archivos locales, URL web o paquetes de recursos. No precarga una página activa de [Navegador](/elements#browser).

El precargador se inicia durante el arranque del juego y al recargar los recursos de Minecraft. Espera a que cada elemento termine o falle antes de continuar, con un límite de dos minutos por elemento.

Los recursos cargados permanecen en caché hasta que FancyMenu los libera durante una recarga o al cerrar el cliente. **Personalización -> Recargar FancyMenu** libera la caché, pero no vuelve a ejecutar el precargador.

La precarga aumenta el tiempo de carga y el uso de RAM/VRAM. Añade únicamente los recursos que deban estar listos de inmediato; elimina los elementos grandes si el cliente se queda sin memoria.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Precargar presentaciones y panorámicas

Al añadir una [presentación](/slideshows), se cargan todas sus imágenes y la superposición opcional. Al añadir una [panorámica](/panoramas), se cargan sus seis caras y la superposición opcional.

**Personalización -> Recargar FancyMenu** no ejecuta el precargador. Recarga los recursos de Minecraft o reinicia el juego después de cambiar la lista de precarga.
