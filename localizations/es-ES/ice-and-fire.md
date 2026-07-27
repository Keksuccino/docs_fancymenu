---
title: Menú principal de Ice & Fire
description: Cómo desactivar el menú principal personalizado de Ice and Fire.
---

# Menú principal de Ice & Fire

Para desactivar la pantalla de título personalizada del mod Ice and Fire, debes cambiar su configuración. Aquí te explicamos cómo hacerlo:

## 1. Localiza el archivo de configuración
- **Nombre del archivo:** La opción se encuentra en el archivo llamado **`iceandfire-client.toml`**.
- **Ubicación de la carpeta:** Este archivo suele estar en **`<game-directory>/config/`**, donde `<game-directory>` es el directorio de instancia/perfil activo del lanzador.

## 2. Edita el archivo de configuración
- **Abre el archivo:** Usa cualquier editor de texto sin formato (como Bloc de notas en Windows o TextEdit en macOS) para abrir `iceandfire-client.toml`.
- **Busca la opción:** Desplázate hacia abajo hasta encontrar una opción relacionada con el menú principal personalizado. Puede estar comentada y verse algo así:
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Cambia el valor:** Establece esta opción en **false** cambiando la línea a:
  ```toml
  B:"Custom main menu"=false
  ```
  Este cambio indica al mod que no muestre su menú principal personalizado (que a menudo incluye al dragón u otros elementos visuales temáticos).

## 3. Guarda y reinicia
- **Guarda el archivo:** Después de hacer el cambio, guarda el archivo.
- **Reinicia Minecraft:** Cierra y vuelve a iniciar Minecraft para que los cambios surtan efecto. Cuando el juego cargue, debería usar ahora el menú principal predeterminado en lugar del personalizado del mod.

## Consejos adicionales
- **Comprueba que estás editando el archivo correcto:** Puede que exista un archivo de configuración común aparte, así que asegúrate de editar **`iceandfire-client.toml`** (esta es la configuración específica del cliente, no la común).
- **Haz una copia de seguridad primero:** Siempre es buena idea hacer una copia del archivo de configuración original antes de modificarlo.
- **Modpacks:** Si usas un modpack, el archivo de configuración puede estar dentro de la estructura de carpetas del pack, pero el principio sigue siendo el mismo.

Siguiendo estos pasos deberías desactivar el menú principal personalizado que proporciona el mod, de modo que puedas usar el fondo de menú principal propio de tu paquete de texturas.
