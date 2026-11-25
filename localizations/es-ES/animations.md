---
title: Animaciones
description: Cómo usar imágenes animadas en FancyMenu y cómo crearlas.
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# Animaciones

FancyMenu reproduce imágenes animadas en casi cualquier lugar donde puedas usar una imagen: en [elementos de imagen](/elements#image), [fondos de menú con imágenes](/menu-backgrounds#image), texturas de botones y controles deslizantes, la [intro del juego](/game-intro) y mucho más.

Usa archivos **APNG** o **GIF** para tus animaciones:

- **APNG** (PNG animado) ofrece mayor calidad: todos los colores de un PNG normal y transparencia real con bordes suaves. Es la mejor opción para logotipos, fondos y cualquier elemento con transparencia.
- **GIF** es más común, por lo que hay más herramientas para crear y editar GIF. Sin embargo, un GIF solo tiene 256 colores por fotograma, y sus píxeles son totalmente transparentes o totalmente opacos.

> [!NOTE]
> Los formatos de animación propios de FancyMenu, FMA y AFMA, están obsoletos. Los archivos que ya tengas seguirán funcionando, pero usa APNG o GIF para las animaciones nuevas. Consulta [FMA y AFMA](#fma-and-afma).

# Usar animaciones

1. Coloca el archivo en `<game-directory>/config/fancymenu/assets/` para que aparezca en el selector de archivos de FancyMenu. También puedes usar URL web y archivos de paquetes de recursos; consulta [Recursos](/resources).
2. Selecciónalo como cualquier otra imagen, por ejemplo, en **Origen de imagen** de un elemento de imagen.

> [!WARNING]
> Los archivos APNG deben terminar en `.apng`. Muchas herramientas guardan los APNG con la extensión `.png`, así que cambia el nombre del archivo; de lo contrario, FancyMenu lo mostrará como una imagen fija. Lo mismo se aplica a las URL web: deben terminar en `.apng`.

## Cómo se reproducen las animaciones

- Una animación se reproduce tantas veces como indique su archivo y, después, se queda en el último fotograma. Al crear el archivo, puedes definir cuántas veces se repite.
- Las animaciones solo se reproducen mientras están en pantalla. Cuando vuelven a aparecer, continúan desde donde se habían detenido.
- **Reiniciar texturas animadas al abrir la pantalla** hace que los elementos de imagen y los fondos de menú con imágenes vuelvan al principio de la animación cada vez que se abre la pantalla.
- **Reiniciar texturas animadas al pasar el cursor** hace que las texturas de botones y controles deslizantes vuelvan al principio cada vez que el cursor pasa sobre ellos.
- Los activadores [**La textura animada ha empezado a reproducirse**](/listeners#animated-texture-started-playing) y [**La textura animada ha terminado de reproducirse**](/listeners#animated-texture-finished-playing) ejecutan acciones cuando una animación empieza o termina.

## Rendimiento

FancyMenu decodifica los APNG y los GIF mientras se reproducen, solo unos pocos fotogramas por adelantado, por lo que incluso las animaciones largas ocupan poca memoria.

Los fotogramas grandes y las tasas de fotogramas elevadas siguen afectando al rendimiento. Procura que los fotogramas tengan un tamaño similar al que tendrán en pantalla; consulta [Optimizar texturas](/optimizing-textures). Para clips largos con sonido, usa un [vídeo](/video).

# Crear animaciones

Estas herramientas gratuitas permiten crear APNG y GIF a partir de fotogramas sueltos o vídeos:

- [ScreenToGif](https://www.screentogif.com/) (Windows): haz clic en **Editor**, arrastra los fotogramas PNG hasta él, configura la duración de cada fotograma y guarda la animación como APNG o GIF. Puedes configurar la repetición en el menú de guardado.
- [ezgif](https://ezgif.com/) (en línea, sin descargas): crea un [GIF](https://ezgif.com/maker) o un [APNG](https://ezgif.com/apng-maker) a partir de imágenes, convierte un vídeo en [GIF](https://ezgif.com/video-to-gif) o [APNG](https://ezgif.com/video-to-apng), o convierte de [GIF a APNG](https://ezgif.com/gif-to-apng) y de [APNG a GIF](https://ezgif.com/apng-to-gif).
- [FFmpeg](https://ffmpeg.org/download.html) (línea de comandos): consulta la sección siguiente.

## Con FFmpeg

Convierte fotogramas PNG numerados, como `frame_0001.png`, `frame_0002.png`, etc., en un APNG que se repite indefinidamente. `-framerate 20` reproduce 20 fotogramas por segundo:

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

Convierte un vídeo en un APNG. `fps=20` mantiene 20 fotogramas por segundo y `scale=960:-1` establece un ancho de 960 píxeles:

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

Convierte un vídeo en un GIF que se repite indefinidamente. La parte `palettegen` selecciona los 256 mejores colores:

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

Convierte un GIF en un APNG:

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA y AFMA

FMA y AFMA son formatos de animación propios de FancyMenu. Ambos están obsoletos: todavía se reproducen, pero APNG y GIF son mejores opciones para las animaciones nuevas.

Aun así, para crear un AFMA:

1. Coloca los fotogramas como archivos PNG en una carpeta. Se reproducen en el orden de sus nombres, por ejemplo, `frame_1.png`, `frame_2.png`, ..., `frame_10.png`.
2. Abre **barra de menú -> Herramientas -> Creador de AFMA**.
3. Establece **Directorio principal de fotogramas** como la carpeta. Los fotogramas del **Directorio de fotogramas de introducción** se reproducen una vez antes que los principales.
4. Configura **Duración del fotograma principal (ms)** y **Número de repeticiones**. Si el número de repeticiones es `0`, la animación se repite indefinidamente.
5. Establece **Archivo AFMA de salida** y haz clic en **Exportar**.
