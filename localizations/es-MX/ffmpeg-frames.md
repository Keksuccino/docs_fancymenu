---
title: Obtener fotogramas de videos
description: Cómo obtener fotogramas de un archivo de video.
---

# Cómo obtener fotogramas de un video usando FFmpeg

*Esta página fue generada en parte por ChatGPT AI.*

FFmpeg es una herramienta gratuita que te ayuda a trabajar con videos y archivos de audio. Una cosa muy útil que puedes hacer con ella es sacar imágenes (fotogramas) de un video, como un archivo MP4. Aquí te explicamos cómo hacerlo paso a paso.

En los siguientes comandos se usará MP4, pero FFmpeg también admite otros formatos de video como AVI, MOV, MKV y MPEG.

# Lo que necesitas

Antes de empezar, asegúrate de tener lo siguiente:

1. **FFmpeg instalado**:

   - Descarga FFmpeg desde el sitio oficial de [FFmpeg](https://ffmpeg.org/download.html). Asegúrate de descargar la versión completa ("full").
   - Sigue las instrucciones de instalación para tu computadora.

2. **Acceso a la línea de comandos**:

   - Usa la terminal (Linux/macOS) o el símbolo del sistema (Windows) para ejecutar comandos de FFmpeg.

3. **Un archivo de video**:

    - Ten listo un archivo de video MP4, AVI, MOV, MKV o MPEG.

# Antes de empezar

Antes de ejecutar cualquier comando, asegúrate de preparar lo siguiente:

## Habilitar las extensiones de archivo

  - Es importante ver las extensiones de archivo como `.mp4` o `.avi` cuando cambies el nombre de tu video.

    - **En Windows**:

      - Abre el Explorador de archivos.
      - Haz clic en la pestaña "Vista" en la parte superior.
      - Marca la casilla que dice "Extensiones de nombre de archivo".

    - **En macOS**:

      - Abre Finder.
      - Haz clic en "Finder" en la barra de menús y selecciona "Preferencias".
      - Ve a la pestaña "Avanzado" y marca la casilla "Mostrar todas las extensiones de nombre de archivo".

## Crear una carpeta de salida

- Crea una carpeta llamada `output_frames` en el directorio donde se encuentra el ejecutable de FFmpeg. Ahí se guardarán los fotogramas extraídos.

## Preparar tu archivo de video

- Coloca el archivo de video del que quieras extraer los fotogramas en el mismo directorio que el ejecutable de FFmpeg.
- Cambia el nombre del archivo de video a `input` seguido de su extensión (por ejemplo, `input.mp4`, `input.avi`, etc.). Esto asegura que los comandos de abajo funcionen sin modificar nada.

<br>
<img width="579" alt="Screenshot_4" src="https://gist.github.com/user-attachments/assets/1cb4ddf9-a17a-4219-b7d4-aa344adaa87c" />

# Cómo abrir FFmpeg

Antes de poder usar FFmpeg, necesitas abrirlo desde la línea de comandos. Aquí te explicamos cómo hacerlo paso a paso en Windows y macOS.

## En Windows:

1. **Abre el Símbolo del sistema**:
   - Presiona la tecla `Windows` y la tecla `R` al mismo tiempo para abrir el cuadro Ejecutar.
   - Escribe `cmd` y presiona Enter. Esto abre el Símbolo del sistema.

2. **Ve a la carpeta de FFmpeg**:
   - Necesitas decirle a la computadora dónde está FFmpeg. Usa el comando `cd` para ir a la carpeta donde guardaste FFmpeg.
   - Por ejemplo, si FFmpeg está en una carpeta llamada `ffmpeg-2024\bin` en tu escritorio, escribe esto:
     ```bash
     cd C:\Users\TuNombreDeUsuario\Desktop\ffmpeg-2024\bin
     ```
     (Reemplaza "TuNombreDeUsuario" con tu nombre de usuario real en la computadora.)

3. **Verifica que FFmpeg funcione**:
   - Para asegurarte de que FFmpeg esté funcionando, escribe este comando:
     ```bash
     ffmpeg -version
     ```
   - Si funciona, verás información sobre FFmpeg aparecer en la pantalla.

## En macOS:

1. **Abre la Terminal**:
   - Presiona `Command` y `Space` al mismo tiempo para abrir Spotlight.
   - Escribe `Terminal` y presiona Enter para abrirla.

2. **Ve a la carpeta de FFmpeg**:
   - Usa el comando `cd` para ir a la carpeta donde guardaste FFmpeg.
   - Por ejemplo, si FFmpeg está en tu carpeta `Downloads`, escribe esto:
     ```bash
     cd ~/Downloads/ffmpeg-2024/bin
     ```

3. **Verifica que FFmpeg funcione**:
   - Para asegurarte de que FFmpeg esté listo, escribe este comando:
     ```bash
     ./ffmpeg -version
     ```
   - Si FFmpeg está funcionando, verás detalles sobre él aparecer en la pantalla.

# Cómo guardar todos los fotogramas

Para guardar todos los fotogramas de un video, usa este comando:

```bash
ffmpeg -i input.mp4 output_frames/%d.png
```

## Qué significa esto:

- `-i input.mp4`: Este es tu archivo de video de entrada. Debe estar en el mismo directorio que el ejecutable de FFmpeg. Asegúrate de cambiar `input.mp4` por el nombre y la extensión correctos del archivo.
- `output_frames/frame_%04d.png`: Así se guardarán los fotogramas:
- `output_frames/`: Guarda todos los fotogramas en una carpeta llamada `output_frames`.
- `%d.png`: Los fotogramas se nombrarán con números como `1.png`, `2.png` y así sucesivamente, manteniéndolos en orden.

# Guardar fotogramas en momentos específicos

Si no quieres todos los fotogramas, puedes guardar un fotograma cada segundo (u otros intervalos). Usa este comando:

```bash
ffmpeg -i input.mp4 -vf "fps=1" output_frames/%d.png
```

## Qué significa esto:

- `-i input.mp4`: Este es tu archivo de video de entrada. Debe estar en el mismo directorio que el ejecutable de FFmpeg. Asegúrate de cambiar `input.mp4` por el nombre y la extensión correctos del archivo.
- `-vf "fps=1"`: Esto guarda un fotograma por segundo. Cambia el `1` por otro número si quieres fotogramas más o menos seguidos (por ejemplo, `fps=0.5` guarda un fotograma cada dos segundos, y `fps=2` guarda dos fotogramas por segundo).
- `output_frames/%d.png`: Guarda los fotogramas en una carpeta llamada `output_frames` con nombres como `1.png`, `2.png` y así sucesivamente.

# Cambiar el tamaño y la calidad de los fotogramas

También puedes ajustar el tamaño y la calidad de los fotogramas que guardes. Así se hace:

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" -q:v 2 output_frames/%d.png
```

## Qué significa esto:

- `-i input.mp4`: Este es tu archivo de video de entrada. Debe estar en el mismo directorio que el ejecutable de FFmpeg. Asegúrate de cambiar `input.mp4` por el nombre y la extensión correctos del archivo.
- `-vf "scale=1280:720"`: Cambia el tamaño del fotograma a 1280x720 píxeles.
- `-q:v 2`: Establece la calidad de la imagen (1 es la mejor; números más altos significan menor calidad).
- `output_frames/%d.png`: Guarda los fotogramas en una carpeta llamada `output_frames` con nombres como `1.png`, `2.png` y así sucesivamente.

# Consejos para guardar fotogramas

1. **Ahorra espacio**:

   - Si el video es largo, puedes guardar fotogramas en intervalos en lugar de guardar cada fotograma. Esto es especialmente útil cuando los uses como fotogramas de animación FMA en FancyMenu.

2. **Aprende más**:

   - Ejecuta `ffmpeg -h` en tu terminal para ver todo lo que FFmpeg puede hacer.

<br>
¡Ahora ya estás listo para usar FFmpeg para guardar fotogramas de tu video!&#x20;

