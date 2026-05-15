---
title: Localización de diseños
description: Cómo localizar el contenido de los diseños.
---

# Localización de diseños

FancyMenu te permite localizar contenido de texto e incluso elementos completos o diseños enteros.

# Contenido de texto

FancyMenu te permite agregar tus propias localizaciones al juego.
Estas luego se pueden usar con el marcador de posición **Localize Text** para localizar texto al idioma actual del juego.

## Uso de claves de localización vanilla de Minecraft

Antes de crear localizaciones personalizadas, quizá quieras usar claves de localización existentes de Minecraft. Esto ahorra tiempo y garantiza coherencia con el texto vanilla de Minecraft.

### Cómo encontrar claves de localización vanilla

La forma más sencilla de encontrar las claves de localización de Minecraft es revisar en línea los archivos de recursos del juego:

1. **Visita MCAsset.cloud:**  
   Ve a [https://mcasset.cloud/](https://mcasset.cloud/) — este sitio te permite explorar los recursos de Minecraft sin extraerlos del juego.

2. **Ve a los archivos de idioma:**  
   - Selecciona tu versión de Minecraft en el menú desplegable
   - Ve a: `assets` → `minecraft` → `lang`
   - Abre `en_us.json` para ver todas las localizaciones en inglés

3. **Encuentra la clave que necesitas:**  
   - Usa la función de búsqueda de tu navegador (Ctrl+F o Cmd+F) para encontrar texto específico
   - El formato es `"key": "text"`; la primera parte entre comillas antes de los dos puntos (`:`) es la clave
   - Por ejemplo: `"menu.singleplayer": "Singleplayer"` — la clave es `menu.singleplayer`

### Uso de claves de localización de mods

Si tienes otros mods instalados, también puedes usar sus claves de localización:

1. Revisa la documentación del mod para ver las claves disponibles
2. Explora los archivos de idioma del mod si es de código abierto

## Archivos de localización personalizados

Los archivos de localización son archivos de texto con todo el contenido que debe estar disponible en varios idiomas. Cada texto traducible tiene una clave única, así Minecraft puede encontrar el texto traducible correcto en los archivos de localización.

- **Archivo predeterminado (en_us.json):**  
  Inglés (EE. UU.). Este archivo se usa cuando no se elige otro archivo de idioma. Funciona como archivo de respaldo.

- **Otros archivos de idioma:**  
  Por ejemplo, puedes crear un archivo alemán llamado `de_de.json` para los jugadores que usan alemán.

### Cómo crear un archivo de localización personalizado

¡Siempre necesitas un archivo `en_us.json`! Sin él, el juego no tiene un respaldo cuando algo sale mal o cuando se establece un idioma no compatible.

1. **Abre un editor de texto:**  
   Usa Bloc de notas (Windows), TextEdit (Mac) o cualquier editor de texto simple.

2. **Escribe tu código JSON:**  
   Crea tu archivo con tus claves personalizadas. Una clave es un nombre único que Minecraft usa para encontrar el texto. Por ejemplo:
   
   ```json
   {
     "modpack_name.custom.localization.key": "Tu texto personalizado aquí",
     "modpack_name.another.key": "Otro mensaje"
   }
   ```

3. **Guarda el archivo:**  
   Guarda el archivo como `en_us.json` para el texto predeterminado en inglés.

Si ahora quieres agregar versiones traducidas, como alemán, copia el contenido del archivo `en_us.json` al nuevo archivo y traduce solo el texto real, ¡NO las claves! Las claves deben seguir siendo las mismas, para que el juego aún pueda encontrar el texto.

Para alemán, guardarías el archivo como `de_de.json`. Para otros idiomas, consulta [esta página de la wiki de Minecraft](https://minecraft.wiki/w/Language) para obtener el código de idioma correcto y nombra el archivo con ese código. Busca el **"in-game locale code"** de tu idioma.

## Crear un paquete de recursos de Minecraft para MC 1.21.4

Ahora que tus archivos de localización están listos, necesitamos una forma de cargarlos en Minecraft. Para eso usaremos un paquete de recursos. Haremos que el paquete esté habilitado de forma predeterminada e incluso podemos ocultarlo si no queremos que los usuarios del modpack lo modifiquen.

Un **paquete de recursos** es un archivo ZIP que contiene archivos que cambian la apariencia y el estilo del juego.

### Pasos para crear tu paquete de recursos

1. **Crea una carpeta nueva:**  
   Crea una carpeta con un nombre como `my_custom_pack` donde agregarás tus archivos de localización personalizados.

2. **Crea el archivo del paquete (`pack.mcmeta`):**  
   Dentro de tu carpeta, crea un archivo llamado `pack.mcmeta` con el siguiente contenido:
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "Mi paquete personalizado con localizaciones"
     }
   }
   ```
   
   *Nota: `pack_format` 16 es para Minecraft 1.21.4.*

3. **Agrega tus archivos de localización:**  
   Dentro de la carpeta de tu paquete de recursos, crea la siguiente estructura de carpetas:
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   Coloca tu `en_us.json` personalizado (y cualquier otro archivo de idioma como `de_de.json`) en la carpeta `lang`.

4. **Comprime el paquete de recursos en ZIP:**  
   Una vez que tu carpeta esté lista, **comprime toda la carpeta en un archivo ZIP**. Nombra el archivo ZIP **my_custom_pack.zip**. Este es el nombre de ejemplo que se usa en toda la guía.

## Dónde colocar el paquete de recursos

Coloca tu archivo **my_custom_pack.zip** en la **carpeta de paquetes de recursos de Minecraft**. Esta carpeta normalmente se encuentra en:

- **Windows:** `%appdata%\.minecraft\resourcepacks`
- **Mac:** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux:** `~/.minecraft/resourcepacks`

> Para modpacks, la carpeta `resourcepacks` está en el directorio de la instancia de tu pack.
{.is-warning}

## Carga automática del paquete con "Resource Pack Overrides"

El mod **Resource Pack Overrides** permite habilitar paquetes de recursos de forma predeterminada.

### Pasos para cargar automáticamente tu paquete

1. **Instala el mod:**  
   Descarga e instala el mod desde [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) o [Modrinth](https://modrinth.com/mod/resource-pack-overrides).

2. **Ubica el archivo de configuración:**  
   Encuentra el archivo en `.minecraft/config/resourcepackoverrides.json`.  
   *Si el archivo no existe, créalo manualmente.*

3. **Edita el archivo de configuración:**  
   Abre el archivo y agrega tu paquete de recursos a la lista `default_packs` usando su nombre de archivo:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   Esto le indica a Minecraft que cargue tu paquete de recursos automáticamente al iniciar el juego.

   **¡Es importante agregar el prefijo `file/`!**


*Nota: Los paquetes de recursos de la lista se aplican en orden inverso. Eso significa que el paquete que está al inicio de la lista aparecerá debajo de los demás en el menú de paquetes de recursos del juego.*

## Ocultar el paquete de recursos en la pantalla de selección

Puedes ocultar tu paquete de recursos para que los jugadores no lo vean en la pantalla de selección de paquetes de recursos.

### Cómo ocultarlo

1. **Edita de nuevo el archivo de configuración:**  
   En el mismo archivo `.minecraft/config/resourcepackoverrides.json`, agrega una sobrescritura para tu paquete:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   Esta configuración ocultará **my_custom_pack.zip** de la pantalla de selección mientras sigue cargándose automáticamente.

## Usar tus nuevas claves de localización con FancyMenu

Ahora que tus archivos de localización personalizados están cargados, puedes usar tus nuevas claves en los diseños de FancyMenu.

1. **Edita un elemento basado en texto:**  
   Abre FancyMenu y elige un elemento como un botón o un elemento de texto.

2. **Haz clic en el botón Placeholders:**  
   Busca el botón Placeholders en la esquina superior derecha del editor de texto. (Si no lo ves, es posible que el elemento no admita placeholders.)

3. **Inserta el marcador de posición Localize Text:**  
   El marcador de posición Localize Text aparece como un fragmento JSON. Se ve así:
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   Reemplaza `localization.key` con tu propia clave personalizada. Por ejemplo, si quieres usar la clave de tu archivo de localización, cámbiala a:
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

Y bueno, ¡eso es básicamente todo! El marcador de posición debería reemplazarse con el contenido localizado real cuando no lo estés editando en el editor de texto.

Ten en cuenta que el marcador de posición siempre localizará el contenido de texto al idioma actual del juego.

# Contenido no textual (imágenes, etc.)

FancyMenu también te permite localizar imágenes y prácticamente cualquier elemento que quieras.

Para hacerlo, necesitarás usar **requisitos de carga**.
Más específicamente, el requisito **Is Game Language**.

El requisito **Is Game Language** te permite mostrar elementos o diseños solo si está seleccionado un idioma específico del juego, así que puedes, por ejemplo, crear dos elementos de imagen que contengan texto y localizar esa imagen a una versión con texto en japonés cuando el idioma esté en japonés, o a una versión con texto en inglés si el idioma está en inglés.

Para establecer requisitos de carga en un **elemento**, haz clic derecho sobre él y luego en **Loading Requirements**.

Para establecer requisitos de carga en **diseños completos**, haz clic derecho en el fondo del editor del diseño y luego en **Loading Requirements [Layout-Wide]**.
