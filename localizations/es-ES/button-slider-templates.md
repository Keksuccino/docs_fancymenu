---
title: Plantillas de botones y deslizadores
description: >-
  Cómo usar plantillas de botones/deslizadores para aplicar un diseño específico
  de botón/deslizador a TODOS los botones a la vez.
---

# Usar elementos de botón como plantillas para botones y deslizadores

Es posible usar un elemento de botón como plantilla para otros botones e incluso deslizadores. Al hacerlo, puedes aplicar un diseño específico de botón/deslizador a TODOS los botones/deslizadores de un menú o incluso a todos los menús a la vez cuando uses una disposición universal.

> [!IMPORTANT]
> Desde FancyMenu 3.9.0 se recomienda usar [Personalizaciones globales](/global-customizations) en lugar de Plantillas de botón/deslizador siempre que sea posible, ya que pueden reemplazar globalmente las texturas de los botones y deslizadores de Minecraft sin usar un paquete de recursos. Usa las personalizaciones globales para un estilo amplio de la interfaz de usuario de Minecraft, y usa las plantillas solo cuando necesites un comportamiento específico de la disposición.

# Importante antes de empezar

Si solo quieres cambiar la textura de un único botón o deslizador, lo más fácil y recomendable es simplemente hacer **clic derecho** en el botón o deslizador (vanilla y personalizado) en el editor. Hay una opción para establecer las **texturas de fondo** (y las texturas del tirador del deslizador) para botones y deslizadores.

# ¿Qué es un botón de plantilla?

Un botón de plantilla es un tipo especial de botón personalizado en FancyMenu que te permite controlar cómo se ven y se comportan otros botones y deslizadores. Es como crear un diseño maestro que seguirán muchos otros elementos.

Cuando creas un botón de plantilla, puedes hacer que muchos botones o deslizadores compartan el mismo:
- Tamaño (anchura y altura)
- Posición
- Visibilidad
- Opacidad (lo transparentes que son)
- Etiquetas de texto
- **Texturas del botón** (se comparten automáticamente cuando se establecen texturas personalizadas)

¡Esto es muy útil cuando quieres que tu menú tenga un aspecto coherente o cuando necesitas actualizar muchos botones a la vez!

# ¿Quién puede usar plantillas?

Solo los **botones personalizados** pueden funcionar como plantillas. Sin embargo, estas plantillas se pueden aplicar a:
- Botones vanilla (los botones predeterminados de Minecraft)
- Botones personalizados (botones que creas en FancyMenu)
- Deslizadores vanilla (como los controles de volumen)
- Deslizadores personalizados (deslizadores que creas en FancyMenu)

# Cómo crear un botón de plantilla

1. Abre el editor de FancyMenu para la pantalla que quieras personalizar
2. Añade un nuevo elemento de botón personalizado a tu disposición
3. Haz clic derecho en tu nuevo botón
4. Selecciona "Template Settings" en el menú
5. Haz clic en "Is Template: ON" para activar el modo plantilla

¡Tu botón ya estará listo para funcionar como plantilla de otros botones y deslizadores!

# Opciones de compartición de la plantilla

Puedes elegir qué tipos de elementos afectará tu plantilla:
- **Botones** - Tu plantilla solo afectará a los botones (tanto vanilla como personalizados)
- **Deslizadores** - Tu plantilla solo afectará a los deslizadores (tanto vanilla como personalizados)

Para configurar esta opción:
1. Haz clic derecho en tu botón de plantilla
2. Ve a "Template Settings"
3. Haz clic en "Share With: [Current Option]" para alternar entre las opciones

> **Importante**: Puedes tener dos plantillas activas al mismo tiempo: una para botones Y otra para deslizadores. ¡Esto significa que puedes crear diseños de plantilla separados para distintos tipos de elementos en la misma pantalla!
{.is-warning}


# Qué se puede usar como plantilla

Puedes controlar exactamente qué propiedades compartirá tu plantilla con otros elementos:

## Propiedades que se pueden activar o desactivar:

1. Haz clic derecho en tu botón de plantilla
2. Ve a "Template Settings" 
3. Activa o desactiva cualquiera de estas opciones:
   - **Anchura** - Hace que todos los elementos afectados tengan la misma anchura que tu plantilla
   - **Altura** - Hace que todos los elementos afectados tengan la misma altura que tu plantilla
   - **Posición X** - Coloca todos los elementos afectados en la misma coordenada X que tu plantilla
   - **Posición Y** - Coloca todos los elementos afectados en la misma coordenada Y que tu plantilla
   - **Opacidad** - Da a todos los elementos afectados la misma transparencia que tu plantilla
   - **Visibilidad** - Controla si los elementos afectados se muestran o se ocultan
   - **Etiqueta** - Hace que todos los elementos afectados usen el mismo texto que tu plantilla

## Propiedades que siempre se comparten:

- **Texturas del botón** - Cuando estableces texturas personalizadas en tu plantilla, se aplicarán automáticamente a todos los elementos afectados
  - A diferencia de otras propiedades, no se puede desactivar la compartición de texturas
  - Las texturas solo se aplican cuando realmente hay texturas personalizadas establecidas en la plantilla
  - Si no se establecen texturas personalizadas, se usarán las texturas originales del elemento

# Personalizar el aspecto de la plantilla

Tu botón de plantilla se puede personalizar igual que cualquier otro botón:

1. Haz clic derecho en tu botón de plantilla
2. Puedes establecer:
   - Texturas del botón (estados normal, al pasar el cursor y inactivo)
   - Etiquetas (normal y al pasar el cursor)
   - Sonidos (al pasar el cursor y al hacer clic)
   - Descripciones emergentes

Para los botones, puedes establecer texturas personalizadas para distintos estados:
- Fondo normal (cuando no se está interactuando)
- Fondo al pasar el cursor (cuando el ratón está encima)
- Fondo inactivo (cuando el botón está deshabilitado)

Para los deslizadores, también puedes establecer:
- Texturas del tirador del deslizador
- Texturas de fondo del deslizador

# Consejos importantes

1. **Los botones de plantilla no aparecerán en el juego** - Solo son visibles en el editor, así que colócalos donde te resulte más cómodo.

2. **Puedes tener dos plantillas activas simultáneamente** - Una plantilla para botones y una para deslizadores pueden estar activas al mismo tiempo.

3. **Solo está activa una plantilla por tipo** - Si tienes varias plantillas de botones, solo se usará para los botones la que esté más arriba en tu lista de elementos. Lo mismo se aplica a las plantillas de deslizadores.

4. **Los cambios en la plantilla se actualizan al instante** - Cuando edites tu plantilla, todos los botones y deslizadores afectados se actualizarán enseguida.

5. **Usa el modo de compartición correcto** - Recuerda que el modo "Botones" no afectará a los deslizadores, y el modo "Deslizadores" no afectará a los botones.

6. **Aplica las propiedades de forma selectiva** - No tienes que aplicar todas las propiedades. Por ejemplo, quizá quieras usar la plantilla solo para las texturas y el tamaño, pero permitir que los elementos conserven sus posiciones originales.

7. **Las texturas siempre se comparten cuando se establecen** - A diferencia de otras propiedades, cualquier textura personalizada que apliques a la plantilla se compartirá automáticamente con los elementos coincidentes. No necesitas activar o desactivar esta función.

# Usos de ejemplo

- Crear un estilo coherente para todos los botones de una pantalla
- Hacer que todos los deslizadores coincidan con tu tema personalizado con una plantilla aparte
- Crear un "modo oculto" en el que puedas mostrar u ocultar varios botones a la vez
- Cambiar el tamaño de muchos botones con una sola edición
- Dar a todos los botones de tu menú las mismas texturas y sonidos personalizados
