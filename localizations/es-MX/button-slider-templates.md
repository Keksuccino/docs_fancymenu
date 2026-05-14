---
title: Plantillas de botones y deslizadores
description: >-
  Cómo usar plantillas de botones y deslizadores para aplicar un diseño
  específico a TODOS los botones a la vez.
---

# Usar elementos de botón como plantillas para botones y deslizadores

Es posible usar un elemento de botón como plantilla para otros botones e incluso deslizadores. Al hacerlo, puedes aplicar un diseño específico de botón o deslizador a TODOS los botones o deslizadores de un menú, o incluso a todos los menús a la vez cuando usas un diseño universal.

> [!IMPORTANT]
> Desde FancyMenu 3.9.0 se recomienda usar [Personalizaciones globales](/global-customizations) en lugar de Plantillas de botón/deslizador siempre que sea posible, ya que pueden reemplazar globalmente las texturas de botones y deslizadores de Minecraft sin usar un paquete de recursos. Usa las personalizaciones globales para estilizar de forma amplia la interfaz vanilla, y usa plantillas solo cuando necesites un comportamiento específico por diseño.

# Importante antes de empezar

Si solo quieres cambiar la textura de un solo botón o deslizador, lo más fácil y recomendable es simplemente hacer **clic derecho** sobre el botón o deslizador (vanilla y personalizado) en el editor. Hay una opción para configurar las **Texturas de fondo** (y las texturas del control deslizante) para botones y deslizadores.

# ¿Qué es un botón plantilla?

Un botón plantilla es un tipo especial de botón personalizado en FancyMenu que te permite controlar cómo se ven y cómo se comportan otros botones y deslizadores. Es como crear un diseño maestro que muchos otros elementos seguirán.

Cuando creas un botón plantilla, puedes hacer que muchos botones o deslizadores compartan lo mismo:
- Tamaño (ancho y alto)
- Posición
- Visibilidad
- Opacidad (qué tan transparentes son)
- Etiquetas de texto
- **Texturas del botón** (se comparten automáticamente cuando se configuran texturas personalizadas)

¡Esto es muy útil cuando quieres que tu menú tenga un estilo consistente o cuando necesitas actualizar muchos botones a la vez!

# ¿Quién puede usar plantillas?

Solo los **botones personalizados** pueden funcionar como plantillas. Sin embargo, estas plantillas se pueden aplicar a:
- Botones vanilla (los botones predeterminados de Minecraft)
- Botones personalizados (botones que creas en FancyMenu)
- Deslizadores vanilla (como los controles de volumen)
- Deslizadores personalizados (deslizadores que creas en FancyMenu)

# Cómo crear un botón plantilla

1. Abre el editor de FancyMenu para la pantalla que quieres personalizar
2. Agrega un nuevo elemento de botón personalizado a tu diseño
3. Haz clic derecho en tu nuevo botón
4. Selecciona "Template Settings" en el menú
5. Haz clic en "Is Template: ON" para activar el modo de plantilla

¡Tu botón ya estará listo para funcionar como plantilla para otros botones y deslizadores!

# Opciones de uso compartido de la plantilla

Puedes elegir qué tipos de elementos afectará tu plantilla:
- **Buttons** - Tu plantilla solo afectará a botones (tanto vanilla como personalizados)
- **Sliders** - Tu plantilla solo afectará a deslizadores (tanto vanilla como personalizados)

Para configurar esta opción:
1. Haz clic derecho en tu botón plantilla
2. Ve a "Template Settings"
3. Haz clic en "Share With: [Current Option]" para alternar entre las opciones

> **Importante**: Puedes tener dos plantillas activas al mismo tiempo: una para botones y otra para deslizadores. ¡Esto significa que puedes crear diseños de plantilla separados para distintos tipos de elementos en la misma pantalla!
{.is-warning}


# Qué se puede convertir en plantilla

Puedes controlar exactamente qué propiedades compartirá tu plantilla con otros elementos:

## Propiedades que se pueden activar o desactivar:

1. Haz clic derecho en tu botón plantilla
2. Ve a "Template Settings" 
3. Activa o desactiva cualquiera de estas opciones:
   - **Width** - Hace que todos los elementos afectados tengan el mismo ancho que tu plantilla
   - **Height** - Hace que todos los elementos afectados tengan la misma altura que tu plantilla
   - **X Position** - Coloca todos los elementos afectados en la misma coordenada X que tu plantilla
   - **Y Position** - Coloca todos los elementos afectados en la misma coordenada Y que tu plantilla
   - **Opacity** - Da a todos los elementos afectados la misma transparencia que tu plantilla
   - **Visibility** - Controla si los elementos afectados se muestran u ocultan
   - **Label** - Hace que todos los elementos afectados usen el mismo texto que tu plantilla

## Propiedades que siempre se comparten:

- **Texturas del botón** - Cuando configuras texturas personalizadas en tu plantilla, se aplicarán automáticamente a todos los elementos afectados
  - A diferencia de otras propiedades, el uso compartido de texturas no se puede desactivar
  - Las texturas solo se aplican cuando realmente hay texturas personalizadas configuradas en la plantilla
  - Si no hay texturas personalizadas configuradas, se usarán las texturas originales del elemento

# Personalizar la apariencia de la plantilla

Tu botón plantilla se puede personalizar igual que cualquier otro botón:

1. Haz clic derecho en tu botón plantilla
2. Puedes configurar:
   - Texturas del botón (estados normal, al pasar el cursor e inactivo)
   - Etiquetas (normal y al pasar el cursor)
   - Sonidos (al pasar el cursor y al hacer clic)
   - Tooltips

Para los botones, puedes configurar texturas personalizadas para diferentes estados:
- Fondo normal (cuando no se está interactuando)
- Fondo al pasar el cursor (cuando el mouse está encima)
- Fondo inactivo (cuando el botón está deshabilitado)

Para los deslizadores, también puedes configurar:
- Texturas del control deslizante
- Texturas del fondo del deslizador

# Consejos importantes

1. **Los botones plantilla no aparecerán en el juego** - Solo son visibles en el editor, así que colócalos donde te resulte más conveniente.

2. **Puedes tener dos plantillas activas al mismo tiempo** - Una plantilla para botones y una para deslizadores pueden estar activas al mismo tiempo.

3. **Solo una plantilla por tipo está activa** - Si tienes varias plantillas de botones, solo se usará la que esté más arriba en tu lista de elementos para los botones. Lo mismo aplica para las plantillas de deslizadores.

4. **Los cambios en la plantilla se actualizan al instante** - Cuando editas tu plantilla, todos los botones y deslizadores afectados se actualizarán de inmediato.

5. **Usa el modo de uso compartido correcto** - Recuerda que el modo "Buttons" no afectará a los deslizadores, y el modo "Sliders" no afectará a los botones.

6. **Aplica las propiedades de forma selectiva** - No tienes que aplicar todas las propiedades. Por ejemplo, tal vez quieras usar la plantilla solo para las texturas y el tamaño, pero permitir que los elementos conserven sus posiciones originales.

7. **Las texturas siempre se comparten cuando se configuran** - A diferencia de otras propiedades, cualquier textura personalizada que apliques a la plantilla se compartirá automáticamente con los elementos coincidentes. No necesitas activar o desactivar esta función.

# Ejemplos de uso

- Crear un estilo consistente para todos los botones de una pantalla
- Hacer que todos los deslizadores coincidan con tu tema personalizado usando una plantilla separada
- Crear un "modo oculto" en el que puedas mostrar u ocultar varios botones a la vez
- Cambiar el tamaño de muchos botones con una sola edición
- Darles a todos los botones de tu menú las mismas texturas y sonidos personalizados
