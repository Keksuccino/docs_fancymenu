---
title: Precargar recursos
description: >-
  Cómo precargar recursos para que estén listos cuando termine de cargarse el
  juego.
sourceBlobSha: 8eca400e05987468c1fd0dc29faa5267083e38d0
---

# Precargar recursos

La precarga prepara los recursos seleccionados antes de que un menú los necesite. Úsala con recursos que, de otro modo, parpadean, muestran un primer fotograma negro o tardan en aparecer.

# Agregar recursos al precargador

Abre **Personalización -> Precargar recursos**.

<br>

<img width="350" alt="Captura_de_pantalla_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

La lista admite recursos compatibles de imagen, animación, audio, video y texto, provenientes de archivos locales, URL web o paquetes de recursos. No precarga una página activa de [Navegador](/elements#browser).

El precargador se inicia durante el arranque del juego y cuando Minecraft vuelve a cargar los recursos. Espera a que cada elemento termine de cargarse o falle antes de continuar, con un límite de dos minutos por elemento.

Los recursos cargados permanecen en caché hasta que FancyMenu los libera durante una recarga o al cerrar el cliente. **Personalización -> Recargar FancyMenu** libera la caché, pero no vuelve a ejecutar el precargador.

La precarga aumenta el tiempo de carga y el uso de RAM/VRAM. Agrega solo los recursos que deben estar listos de inmediato; elimina los elementos grandes si el cliente se queda sin memoria.

<br>

<img width="731" alt="Captura_de_pantalla_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Precargar presentaciones y panoramas

Al agregar una [presentación](/slideshows), se cargan todas sus imágenes y la superposición opcional. Al agregar un [panorama](/panoramas), se cargan sus seis caras y la superposición opcional.

**Personalización -> Recargar FancyMenu** no ejecuta el precargador. Después de cambiar la lista de precarga, vuelve a cargar los recursos de Minecraft o reinicia el juego.
