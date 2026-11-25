---
title: Animaciones
description: Cómo usar imágenes animadas en FancyMenu y cómo crearlas.
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# Animaciones

FancyMenu reproduce imágenes animadas en casi cualquier lugar donde puedas usar una imagen: en [elementos de imagen](/elements#image), [fondos de menú con imágenes](/menu-backgrounds#image), texturas de botones y controles deslizantes, la [introducción del juego](/game-intro) y más.

Usa archivos **APNG** o **GIF** para tus animaciones:

- **APNG** (PNG animado) ofrece mejor calidad: todos los colores de un PNG normal y transparencia adecuada con bordes suaves. Es la mejor opción para logotipos, fondos y cualquier elemento con transparencia.
- **GIF** es más común, así que hay más herramientas para crear y editar GIF. Pero un GIF solo tiene 256 colores por fotograma, y sus píxeles son totalmente transparentes o no lo son en absoluto.

> [!NOTE]
> Los formatos de animación propios de FancyMenu, FMA y AFMA, están obsoletos. Tus archivos actuales siguen funcionando, pero para las animaciones nuevas usa APNG o GIF. Consulta [FMA y AFMA](#fma-and-afma).

# Usar animaciones

1. Coloca el archivo en `<game-directory>/config/fancymenu/assets/` para que aparezca en el selector de archivos de FancyMenu. También funcionan las URL web y los archivos de paquetes de recursos; consulta [Recursos](/resources).
2. Selecciónalo como cualquier otra imagen, por ejemplo, en **Origen de imagen** de un elemento de imagen.

> [!WARNING]
> Los archivos APNG deben terminar en `.apng`. Muchas herramientas guardan los APNG con la extensión `.png`, así que cambia el nombre del archivo o FancyMenu lo mostrará como una imagen fija. Lo mismo aplica a las URL web: deben terminar en `.apng`.

## Cómo se reproducen las animaciones

- Una animación se reproduce la cantidad de veces indicada en su archivo y luego se queda en el último fotograma. Puedes configurar cuántas veces se repite al crear el archivo.
- Las animaciones solo se reproducen mientras están en pantalla. Cuando vuelven a aparecer, continúan desde donde se quedaron.
- **Reiniciar texturas animadas al abrir la pantalla** hace que los elementos de imagen y los fondos de menú con imágenes reinicien su animación cada vez que se abre la pantalla.
- **Reiniciar texturas animadas al pasar el cursor** hace que las texturas de botones y controles deslizantes se reinicien cada vez que el cursor pasa sobre ellos.
- Los listeners [**La textura animada empezó a reproducirse**](/listeners#animated-texture-started-playing) y [**La textura animada terminó de reproducirse**](/listeners#animated-texture-finished-playing) ejecutan acciones cuando una animación empieza o termina.

## Rendimiento

FancyMenu decodifica los APNG y GIF mientras se reproducen, solo unos cuantos fotogramas por adelantado, así que incluso las animaciones largas requieren poca memoria.

Los fotogramas grandes y las velocidades de fotogramas altas siguen afectando el rendimiento. Procura que tus fotogramas tengan un tamaño similar al que se mostrarán en pantalla; consulta [Optimizar texturas](/optimizing-textures). Para clips largos con sonido, usa un [video](/video).

# Crear animaciones

Estas herramientas gratuitas crean APNG y GIF a partir de fotogramas individuales o videos:

- [ScreenToGif](https://www.screentogif.com/) (Windows): haz clic en **Editor**, arrastra tus fotogramas PNG y suéltalos ahí, configura la duración de cada fotograma y guarda la animación como APNG o GIF. Puedes configurar la repetición en el menú para guardar.
- [ezgif](https://ezgif.com/) (en línea, no requiere descarga): crea un [GIF](https://ezgif.com/maker) o un [APNG](https://ezgif.com/apng-maker) a partir de imágenes, convierte un video en [GIF](https://ezgif.com/video-to-gif) o [APNG](https://ezgif.com/video-to-apng), o convierte [GIF a APNG](https://ezgif.com/gif-to-apng) y [APNG a GIF](https://ezgif.com/apng-to-gif).
- [FFmpeg](https://ffmpeg.org/download.html) (línea de comandos): consulta más abajo.

## Con FFmpeg

Convierte fotogramas PNG numerados, como `frame_0001.png`, `frame_0002.png`, etc., en un APNG que se repite indefinidamente. `-framerate 20` reproduce 20 fotogramas por segundo:

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

Convierte un video en un APNG. `fps=20` mantiene 20 fotogramas por segundo y `scale=960:-1` establece un ancho de 960 píxeles:

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

Convierte un video en un GIF que se repite indefinidamente. La parte `palettegen` elige los 256 mejores colores:

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

Convierte un GIF en un APNG:

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA y AFMA

FMA y AFMA son los formatos de animación propios de FancyMenu. Ambos están obsoletos: siguen reproduciéndose, pero APNG y GIF son mejores opciones para las animaciones nuevas.

Si de todas formas quieres crear un AFMA:

1. Coloca tus fotogramas como archivos PNG en una carpeta. Se reproducen según el orden de sus nombres, como `frame_1.png`, `frame_2.png`, ..., `frame_10.png`.
2. Abre **barra de menú -> Herramientas -> Creador de AFMA**.
3. En **Directorio de fotogramas principales**, selecciona la carpeta. Los fotogramas de **Directorio de fotogramas de introducción** se reproducen una vez antes de los fotogramas principales.
4. Configura **Duración del fotograma principal (ms)** y **Cantidad de repeticiones**. Una cantidad de `0` hace que se repita indefinidamente.
5. Selecciona **Archivo AFMA de salida** y haz clic en **Exportar**.
