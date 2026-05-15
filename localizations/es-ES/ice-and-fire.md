---
title: Menú principal de Ice & Fire
description: Cómo desactivar el menú principal personalizado de Ice and Fire.
---

Para desactivar la pantalla de título personalizada del mod Ice and Fire, necesitas cambiar su configuración. Así es como puedes hacerlo:

## 1. Localiza el archivo de configuración
- **Nombre del archivo:** El ajuste se encuentra en el archivo llamado **`iceandfire-client.toml`**.
- **Ubicación de la carpeta:** Este archivo suele estar en tu carpeta **`.minecraft/config`** (o en el directorio de configuración equivalente si usas un lanzador personalizado o un modpack).

## 2. Edita el archivo de configuración
- **Abre el archivo:** Usa cualquier editor de texto sin formato (como el Bloc de notas en Windows o TextEdit en macOS) para abrir `iceandfire-client.toml`.
- **Busca el ajuste:** Desplázate hacia abajo hasta encontrar una opción relacionada con el menú principal personalizado. Puede estar comentada y verse de forma similar a esto:
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Cambia el valor:** Establece esta opción en **false** cambiando la línea a:
  ```toml
  B:"Custom main menu"=false
  ```
  Este cambio indica al mod que no debe mostrar su menú principal personalizado (a menudo con el dragón u otros elementos visuales temáticos).

## 3. Guarda y reinicia
- **Guarda el archivo:** Después de hacer el cambio, guarda el archivo.
- **Reinicia Minecraft:** Cierra y vuelve a abrir Minecraft para que los cambios surtan efecto. Cuando el juego se cargue, debería usar ahora el menú principal predeterminado en lugar del personalizado del mod.

## Consejos adicionales
- **Comprueba que estás editando el archivo correcto:** Puede que exista un archivo de configuración común aparte, así que asegúrate de estar editando **`iceandfire-client.toml`** (esta es la configuración específica del cliente, no la común).
- **Haz una copia de seguridad primero:** Siempre es buena idea hacer una copia del archivo de configuración original antes de modificarlo.
- **Modpacks:** Si estás usando un modpack, el archivo de configuración puede estar dentro de la estructura de carpetas del pack, pero el principio sigue siendo el mismo.

Este método ha sido confirmado por usuarios de la comunidad; por ejemplo, varios usuarios en los foros de Feed The Beast mencionaron que encontrar y cambiar la opción `"Custom main menu"` en **`iceandfire-client.toml`** resolvió su problema. (Consulta la discusión donde un usuario señaló: “set the ice and fire config to not display it in iceandfire-client.toml” y que el archivo está ubicado en la carpeta config.) citeturn0search1

Siguiendo estos pasos deberías desactivar el menú principal personalizado proporcionado por el mod para que puedas usar el fondo de menú principal de tu pack de texturas.
