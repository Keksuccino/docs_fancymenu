---
title: Introducción del juego
description: >-
  Reproduce una animación o un vídeo cada vez que se inicia el juego, antes de
  que aparezca la pantalla de título.
sourceBlobSha: 2f40eb874b4aebaf4b32ffa2b8980310d71510b7
---

# Introducción del juego

La introducción del juego reproduce una animación o un vídeo cuando se inicia el juego, justo después de la pantalla de carga de Minecraft. Cuando termina, se funde con la pantalla de título. Está pensada para modpacks: un logotipo, una presentación del estudio o un tráiler breve.

<img width="800" alt="La introducción de Skyhaven: la noche se convierte en amanecer sobre una isla flotante y el logotipo aparece letra a letra; después, la introducción se funde con la pantalla de título, cuyo fondo muestra la misma isla" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_showcase.gif?raw=true">

Los jugadores pueden saltársela con cualquier tecla o haciendo clic. La introducción del juego es una de las [personalizaciones globales](/global-customizations), por lo que no necesita ningún diseño.

# Configurar la introducción

<img width="800" alt="Abrir Personalización global e Introducción del juego desde la barra de menú, seleccionar skyhaven_intro.apng con Establecer introducción del juego, reproducirla con Volver a activar la introducción del juego y saltársela con la barra espaciadora" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/game_intro_setup.gif?raw=true">

1. Coloca la animación o el vídeo en `<game-directory>/config/fancymenu/assets/`.
2. Abre **barra de menú -> Personalización -> Personalización global -> Introducción del juego**.
3. Haz clic en **Establecer introducción del juego**. Con **Tipo de origen** en **Local**, haz clic en **Elegir archivo de recurso local**, selecciona el archivo y haz clic en **Aceptar**.
4. Haz clic en **Volver a activar la introducción del juego** para verla inmediatamente.

Para quitar la introducción, coloca el ratón sobre **Establecer introducción del juego** y haz clic en **Restablecer valores predeterminados**.

## Animaciones y vídeos

- **Animaciones:** archivos APNG o GIF. Aquí se explica cómo crearlas: [Animaciones](/animations).
- **Vídeos:** archivos MP4. Necesitan los mods Watermedia V3 y Watermedia Binaries V3; consulta [Vídeos](/video#requirements). Sin ellos, la introducción en vídeo solo muestra durante unos segundos un aviso rojo con enlaces de descarga.
- Funcionan los archivos de tu instancia y de los paquetes de recursos, pero no los enlaces web. Consulta [Recursos](/resources).

La introducción ocupa toda la pantalla y conserva sus proporciones, por lo que algunas partes quedan recortadas en pantallas con otras proporciones. La mayoría de las pantallas son 16:9, así que crea también la introducción en 16:9, por ejemplo, a 1920x1080. Las partes transparentes se muestran en negro.

> [!TIP]
> Los jugadores ven la introducción cada vez que inician el juego, así que procura que sea breve: entre 5 y 10 segundos.

## Ejemplo de introducción gratuito

La introducción de Skyhaven que aparece en los GIF de esta página se puede usar gratis, tanto para probarla como en tus modpacks:

- [skyhaven_intro.apng](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_intro.apng?raw=true): la introducción, de 1280x720 y 5,4 segundos de duración. Se reproduce una vez.
- [skyhaven_menu.png](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/skyhaven_menu.png?raw=true): su escena final sin el logotipo, de 1280x720. Úsala como [fondo de imagen](/menu-backgrounds#image) de un diseño de pantalla de título para que la introducción se funda con un menú a juego, como en el primer GIF.

# Ajustes

Todos los ajustes están en **barra de menú -> Personalización -> Personalización global -> Introducción del juego**:

| Ajuste | Qué hace |
|---|---|
| **Establecer introducción del juego** | La animación o el vídeo. |
| **Permitir saltar la introducción del juego** | Cualquier tecla o clic permite saltarse la introducción, y en la parte inferior aparece **Pulsa cualquier tecla para saltar**. Al saltársela, la introducción termina inmediatamente, sin fundido. Si se desactiva, la introducción siempre se reproduce hasta el final. |
| **Fundido de salida de la introducción del juego** | Hace que la introducción se funda con la pantalla de título al terminar. Si se desactiva, la pantalla de título aparece inmediatamente. |
| **Ignorar bucles de la introducción del juego** | Termina la introducción después de que la animación se reproduzca una vez, aunque se repita en bucle. Si se desactiva, la introducción reproduce todos los bucles de la animación. Los vídeos siempre se reproducen una vez. |
| **Texto de salto personalizado** | Sustituye **Pulsa cualquier tecla para saltar**, por ejemplo, por `Pulsa cualquier tecla para comenzar tu aventura`. Una clave de localización de un paquete de recursos, como `skyhaven.intro.skip`, muestra el texto en el idioma del jugador. |
| **Volumen de la introducción del juego** | El volumen de una introducción en vídeo, del 0 % al 100 %. |
| **Canal de sonido de la introducción del juego** | El canal de sonido de las introducciones en vídeo, como Música. Se aplican además el volumen de ese canal y el volumen principal de los ajustes de sonido de Minecraft. |
| **Volver a activar la introducción del juego** | Reproduce la introducción inmediatamente, sobre la pantalla en la que estés. |

**Permitir saltar la introducción del juego**, **Fundido de salida de la introducción del juego** e **Ignorar bucles de la introducción del juego** están activados de forma predeterminada.

> [!WARNING]
> Si **Permitir saltar la introducción del juego** e **Ignorar bucles de la introducción del juego** están desactivados, una animación que se repita infinitamente nunca terminará y los jugadores no podrán llegar a la pantalla de título.

# Información útil

- La introducción se reproduce una vez en cada inicio del juego, antes de la primera pantalla que aparece tras la pantalla de carga. Normalmente, esa pantalla es la de título.
- Para cambiar la pantalla de carga de Minecraft que aparece antes, consulta [Pantalla de carga](/loading-screen).
- El origen de la introducción puede contener [marcadores de posición](/resources#placeholders-in-resource-sources).
- Los ajustes de la introducción del juego se guardan en el archivo `options.txt` de FancyMenu, por lo que pertenecen al [perfil](/profiles) cargado. Los modpacks que incluyen `config/fancymenu/` incorporan la introducción y su archivo en `assets/`. Consulta [Modpacks](/modpacks).
