---
title: Menú principal de Ice & Fire
description: Cómo desactivar el menú principal personalizado de Ice and Fire.
---

# Menú principal de Ice & Fire

Para desactivar la pantalla de título personalizada en el mod Ice and Fire, necesitas cambiar su configuración. Así es como puedes hacerlo:

## 1. Ubica el archivo de configuración
- **Nombre del archivo:** La opción se encuentra en el archivo llamado **`iceandfire-client.toml`**.
- **Ubicación de la carpeta:** Este archivo normalmente está en **`<game-directory>/config/`**, donde `<game-directory>` es el directorio de instancia/perfil activo del iniciador.

## 2. Edita el archivo de configuración
- **Abre el archivo:** Usa cualquier editor de texto plano (como Bloc de notas en Windows o TextEdit en macOS) para abrir `iceandfire-client.toml`.
- **Busca la opción:** Desplázate hacia abajo hasta encontrar una opción relacionada con el menú principal personalizado. Puede estar comentada y verse similar a esto:
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Cambia el valor:** Establece esta opción en **false** cambiando la línea a:
  ```toml
  B:"Custom main menu"=false
  ```
  Este cambio le indica al mod que no debe mostrar su menú principal personalizado (a menudo con el dragón u otros elementos visuales temáticos).

## 3. Guarda y reinicia
- **Guarda el archivo:** Después de hacer el cambio, guarda el archivo.
- **Reinicia Minecraft:** Cierra y vuelve a abrir Minecraft para que los cambios tengan efecto. Cuando se cargue el juego, ahora debería usar el menú principal predeterminado en lugar del personalizado del mod.

## Consejos adicionales
- **Verifica que estés editando el archivo correcto:** Puede haber un archivo de configuración común por separado, así que asegúrate de estar editando **`iceandfire-client.toml`** (esta es la configuración específica del cliente, no la común).
- **Haz una copia de seguridad primero:** Siempre es buena idea hacer una copia de seguridad del archivo de configuración original antes de modificarlo.
- **Modpacks:** Si estás usando un modpack, el archivo de configuración podría estar dentro de la estructura de carpetas del paquete, pero el principio sigue siendo el mismo.

Seguir estos pasos debería desactivar el menú principal personalizado que proporciona el mod para que puedas usar el fondo del menú principal de tu paquete de texturas.
