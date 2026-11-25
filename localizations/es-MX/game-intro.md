---
title: Intro del juego
description: >-
  Reproduce una animación o un video cada vez que se inicia el juego, antes de
  que aparezca la pantalla de título.
sourceBlobSha: 2f40eb874b4aebaf4b32ffa2b8980310d71510b7
---

# Intro del juego

El intro del juego reproduce una animación o un video cuando se inicia el juego, justo después de la pantalla de carga de Minecraft. Cuando termina, se desvanece y da paso a la pantalla de título. Está pensado para modpacks: puede ser un logo, la presentación de un estudio o un tráiler corto.

<img width="800" alt="El intro de Skyhaven: la noche se convierte en amanecer sobre una isla flotante y el logo aparece letra por letra; después, el intro se desvanece y da paso a la pantalla de título, que tiene la misma isla de fondo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

Los jugadores pueden omitirlo con cualquier tecla o haciendo clic. El intro del juego es una de las [personalizaciones globales](/global-customizations), así que no necesita un diseño.

# Configurar el intro

<img width="800" alt="Abrir Personalización y Personalizaciones globales desde la barra de menú, y luego Intro del juego; elegir skyhaven_intro.apng con Establecer intro del juego, reproducirlo con Volver a reproducir el intro del juego y omitirlo con la barra espaciadora" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. Coloca la animación o el video en `<game-directory>/config/fancymenu/assets/`.
2. Abre **barra de menú -> Personalización -> Personalizaciones globales -> Intro del juego**.
3. Haz clic en **Establecer intro del juego**. Con **Tipo de origen** en **Local**, haz clic en **Elegir archivo de recurso local**, selecciona el archivo y haz clic en **Aceptar**.
4. Haz clic en **Volver a reproducir el intro del juego** para verlo de inmediato.

Para quitar el intro, pasa el mouse sobre **Establecer intro del juego** y haz clic en **Restablecer valores predeterminados**.

## Animaciones y videos

- **Animaciones:** archivos APNG o GIF. Consulta cómo crearlas en [Animaciones](/animations).
- **Videos:** archivos MP4. Necesitan los mods Watermedia V3 y Watermedia Binaries V3; consulta [Videos](/video#requirements). Si no están instalados, durante unos segundos el intro de video solo muestra una nota roja con enlaces de descarga.
- Funcionan los archivos de tu instancia y de los paquetes de recursos, pero no los enlaces web. Consulta [Recursos](/resources).

El intro ocupa toda la pantalla y conserva sus proporciones, así que algunas partes se recortan en pantallas con otras proporciones. La mayoría de las pantallas son 16:9, así que procura que tu intro también lo sea, por ejemplo, de 1920x1080. Las partes transparentes se muestran en negro.

> [!TIP]
> Los jugadores ven el intro cada vez que inician el juego, así que procura que sea corto, de unos 5 a 10 segundos.

## Intro de ejemplo gratuito

El intro de Skyhaven que aparece en los GIF de esta página es gratuito y puedes usarlo para hacer pruebas y en tus modpacks:

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true): el intro, de 1280x720 y 5.4 segundos de duración. Se reproduce una vez.
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true): la última escena, sin el logo, de 1280x720. Úsala como [fondo de imagen](/menu-backgrounds#image) en el diseño de una pantalla de título. Así, el intro se desvanece y da paso a un menú que combina con él, como en el primer GIF.

# Configuración

Toda la configuración está en **barra de menú -> Personalización -> Personalizaciones globales -> Intro del juego**:

| Configuración | Función |
|---|---|
| **Establecer intro del juego** | La animación o el video. |
| **Omitir intro del juego** | Cualquier tecla o clic omite el intro, y en la parte inferior aparece **Presiona cualquier tecla para omitir**. Al omitirlo, el intro termina de inmediato, sin desvanecerse. Si se desactiva, el intro siempre se reproduce hasta el final. |
| **Desvanecimiento del intro del juego** | Hace que el intro se desvanezca y dé paso a la pantalla de título cuando termina. Si se desactiva, la pantalla de título aparece de inmediato. |
| **Ignorar repeticiones del intro del juego** | Termina el intro después de que la animación se reproduce una vez, aunque se repita en bucle. Si se desactiva, el intro reproduce todos los ciclos de la animación. Los videos siempre se reproducen una vez. |
| **Texto personalizado para omitir** | Reemplaza **Presiona cualquier tecla para omitir**, por ejemplo, con `Presiona cualquier tecla para comenzar tu aventura`. Si usas una clave de localización de un paquete de recursos, como `skyhaven.intro.skip`, el texto se muestra en el idioma del jugador. |
| **Volumen del intro del juego** | El volumen del intro de video, de 0 % a 100 %. |
| **Canal de sonido del intro del juego** | El canal de sonido de los intros de video, como Música. También se aplican el volumen de ese canal y el volumen maestro de la configuración de sonido de Minecraft. |
| **Volver a reproducir el intro del juego** | Reproduce el intro de inmediato, encima de la pantalla en la que estás. |

**Omitir intro del juego**, **Desvanecimiento del intro del juego** e **Ignorar repeticiones del intro del juego** están activados de forma predeterminada.

> [!WARNING]
> Si desactivas **Omitir intro del juego** e **Ignorar repeticiones del intro del juego**, una animación que se repite indefinidamente nunca termina y los jugadores no pueden llegar a la pantalla de título.

# Información útil

- El intro se reproduce una vez por cada inicio del juego, antes de la primera pantalla que aparece después de la pantalla de carga. Normalmente, esa pantalla es la de título.
- Para cambiar la pantalla de carga de Minecraft que aparece antes del intro, consulta [Pantalla de carga](/loading-screen).
- El origen del intro puede contener [marcadores de posición](/resources#placeholders-in-resource-sources).
- La configuración del intro del juego se guarda en `options.txt` de FancyMenu, así que forma parte del [perfil](/profiles) cargado. Los modpacks que incluyen `config/fancymenu/` incluyen el intro y su archivo en `assets/`. Consulta [Modpacks](/modpacks).
