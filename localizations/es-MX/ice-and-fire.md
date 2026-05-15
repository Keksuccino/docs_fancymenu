---
title: Menú principal de Ice & Fire
description: Cómo desactivar el menú principal personalizado de Ice and Fire.
---

Para desactivar la pantalla de título personalizada en el mod Ice and Fire, necesitas cambiar su configuración. Aquí te explicamos cómo hacerlo:

## 1. Ubica el archivo de configuración
- **Nombre del archivo:** La opción se encuentra en el archivo llamado **`iceandfire-client.toml`**.
- **Ubicación de la carpeta:** Este archivo normalmente está en tu carpeta **`.minecraft/config`** (o en el directorio de configuración equivalente si usas un launcher personalizado o un modpack).

## 2. Edita el archivo de configuración
- **Abre el archivo:** Usa cualquier editor de texto sin formato (como Notepad en Windows o TextEdit en macOS) para abrir `iceandfire-client.toml`.
- **Busca la opción:** Desplázate hacia abajo hasta encontrar una opción relacionada con el menú principal personalizado. Puede estar comentada y verse similar a esto:
  ```toml
  # Si se muestra o no el dragón en el menú principal [valor predeterminado: true]
  B:"Custom main menu"=true
  ```
- **Cambia el valor:** Establece esta opción en **false** cambiando la línea a:
  ```toml
  B:"Custom main menu"=false
  ```
  Este cambio le indica al mod que no muestre su menú principal personalizado (a menudo con un dragón u otros elementos visuales temáticos).

## 3. Guarda y reinicia
- **Guarda el archivo:** Después de hacer el cambio, guarda el archivo.
- **Reinicia Minecraft:** Cierra y vuelve a abrir Minecraft para que los cambios surtan efecto. Cuando el juego cargue, ahora debería usar el menú principal predeterminado en lugar del personalizado del mod.

## Consejos adicionales
- **Verifica que estés editando el archivo correcto:** Puede haber un archivo de configuración común por separado, así que asegúrate de estar editando **`iceandfire-client.toml`** (esta es la configuración específica del cliente, no la común).
- **Haz una copia de seguridad primero:** Siempre es buena idea respaldar el archivo de configuración original antes de modificarlo.
- **Modpacks:** Si usas un modpack, el archivo de configuración podría estar dentro de la estructura de carpetas del paquete, pero el principio sigue siendo el mismo.

Este método ha sido confirmado por usuarios de la comunidad; por ejemplo, varios usuarios en los foros de Feed The Beast mencionaron que encontrar y cambiar la opción `"Custom main menu"` en **`iceandfire-client.toml`** resolvió su problema. (Consulta la discusión donde un usuario señaló: “set the ice and fire config to not display it in iceandfire-client.toml” y que el archivo se encuentra en la carpeta config.) citeturn0search1

Siguiendo estos pasos deberías desactivar el menú principal personalizado proporcionado por el mod, para que puedas usar el fondo del menú principal de tu paquete de texturas.
