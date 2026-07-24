---
title: Plantillas de botones y deslizadores
description: >-
  Cómo usar plantillas de botones/deslizadores para aplicar un diseño específico
  de botón/deslizador a TODOS los botones a la vez.
---
# Uso de elementos de botón como plantillas para botones y deslizadores

Es posible usar un elemento de botón como plantilla para otros botones e incluso deslizadores. Al hacerlo, puedes aplicar un diseño específico de botón/deslizador a TODOS los botones/deslizadores de un menú o incluso a todos los menús a la vez cuando usas un diseño universal.

> [!IMPORTANT]
> Prefiere [Personalizaciones globales](./global-customizations) para dar estilo general a los botones y deslizadores Vanilla. Usa Plantillas de botones/deslizadores cuando el comportamiento deba ser específico del diseño.

# Importante antes de empezar

Para un solo botón o deslizador, haz **clic derecho** sobre él en el editor y edita directamente sus **Texturas de fondo** o las texturas del control deslizante.

# ¿Qué es un botón de plantilla?

Un botón de plantilla es un tipo especial de botón personalizado en FancyMenu que te permite controlar cómo se ven y se comportan otros botones y deslizadores. Es como crear un diseño maestro que muchos otros elementos seguirán.

Cuando creas un botón de plantilla, puedes hacer que muchos botones o deslizadores compartan lo mismo:
- Tamaño (ancho y alto)
- Posición
- Visibilidad
- Opacidad (qué tan transparente es)
- Etiquetas de texto
- **Texturas del botón** (se comparten automáticamente cuando se configuran texturas personalizadas)

¡Esto es muy útil cuando quieres que tu menú se vea uniforme o cuando necesitas actualizar muchos botones a la vez!

# ¿Quién puede usar plantillas?

Solo los **botones personalizados** pueden funcionar como plantillas. Sin embargo, estas plantillas se pueden aplicar a:
- Botones Vanilla (los botones predeterminados de Minecraft)
- Botones personalizados (botones que creas en FancyMenu)
- Deslizadores Vanilla (como los controles de volumen)
- Deslizadores personalizados (deslizadores que creas en FancyMenu)

# Cómo crear un botón de plantilla

1. Abre el editor de FancyMenu para la pantalla que quieres personalizar
2. Agrega un nuevo elemento de botón personalizado a tu diseño
3. Haz clic derecho sobre tu nuevo botón
4. Selecciona "Template Settings" en el menú
5. Haz clic en "Is Template: ON" para habilitar el modo plantilla

¡Tu botón ahora estará listo para funcionar como plantilla para otros botones y deslizadores!

# Opciones de compartición de la plantilla

Puedes elegir qué tipos de elementos afectará tu plantilla:
- **Buttons** - Tu plantilla solo afectará a los botones (tanto Vanilla como personalizados)
- **Sliders** - Tu plantilla solo afectará a los deslizadores (tanto Vanilla como personalizados)

Para configurar esta opción:
1. Haz clic derecho sobre tu botón de plantilla
2. Ve a "Template Settings"
3. Haz clic en "Share With: [Current Option]" para alternar entre las opciones

> [!WARNING]
> **Importante**: Puedes tener dos plantillas activas al mismo tiempo: una para botones Y otra para deslizadores. ¡Esto significa que puedes crear diseños de plantilla separados para distintos tipos de elementos en la misma pantalla!

# Qué se puede convertir en plantilla

Puedes controlar exactamente qué propiedades compartirá tu plantilla con otros elementos:

## Propiedades que se pueden activar/desactivar:

1. Haz clic derecho sobre tu botón de plantilla
2. Ve a "Template Settings"
3. Activa o desactiva cualquiera de estas opciones:
   - **Width** - Hace que todos los elementos afectados tengan el mismo ancho que tu plantilla
   - **Height** - Hace que todos los elementos afectados tengan la misma altura que tu plantilla
   - **X Position** - Coloca todos los elementos afectados en la misma coordenada X que tu plantilla
   - **Y Position** - Coloca todos los elementos afectados en la misma coordenada Y que tu plantilla
   - **Opacity** - Hace que todos los elementos afectados tengan la misma transparencia que tu plantilla
   - **Visibility** - Controla si los elementos afectados se muestran u ocultan
   - **Label** - Hace que todos los elementos afectados usen el mismo texto que tu plantilla

## Propiedades que siempre se comparten:

- **Texturas del botón** - Cuando configuras texturas personalizadas en tu plantilla, se aplicarán automáticamente a todos los elementos afectados
  - A diferencia de otras propiedades, no se puede desactivar la compartición de texturas
  - Las texturas solo se aplican cuando realmente se configuran texturas personalizadas en la plantilla
  - Si no se configuran texturas personalizadas, se usarán las texturas originales del elemento

# Personalizar la apariencia de la plantilla

Tu botón de plantilla se puede personalizar igual que cualquier otro botón:

1. Haz clic derecho sobre tu botón de plantilla
2. Puedes configurar:
   - Texturas del botón (estados normal, al pasar el cursor e inactivo)
   - Etiquetas (normal y al pasar el cursor)
   - Sonidos (al pasar el cursor y al hacer clic)
   - Descripciones emergentes

Para los botones, puedes establecer texturas personalizadas para diferentes estados:
- Fondo normal (cuando no se interactúa con él)
- Fondo al pasar el cursor (cuando el mouse está encima)
- Fondo inactivo (cuando el botón está deshabilitado)

Para los deslizadores, también puedes configurar:
- Texturas del control deslizante
- Texturas del fondo del deslizador

# Consejos importantes

1. **Los botones de plantilla no aparecerán en el juego** - Solo son visibles en el editor, así que colócalos donde sea más conveniente.

2. **Puedes tener dos plantillas activas al mismo tiempo** - Una plantilla para botones y una para deslizadores pueden estar activas al mismo tiempo.

3. **Solo una plantilla por tipo está activa** - Si tienes varias plantillas de botones, solo se usará la que esté más arriba en tu lista de elementos para los botones. Lo mismo aplica para las plantillas de deslizadores.

4. **Los cambios en la plantilla se actualizan al instante** - Cuando editas tu plantilla, todos los botones y deslizadores afectados se actualizarán de inmediato.

5. **Usa el modo de compartición correcto** - Recuerda que el modo "Buttons" no afectará a los deslizadores, y el modo "Sliders" no afectará a los botones.

6. **Aplica propiedades de forma selectiva** - No tienes que aplicar todas las propiedades. Por ejemplo, podrías querer usar una plantilla solo para las texturas y el tamaño, pero permitir que los elementos conserven sus posiciones originales.

7. **Las texturas siempre se comparten cuando se configuran** - A diferencia de otras propiedades, cualquier textura personalizada que apliques a la plantilla se compartirá automáticamente con los elementos que coincidan. No necesitas activar o desactivar esta función.

# Casos de uso de ejemplo

- Crear un estilo uniforme para todos los botones de una pantalla
- Hacer que todos los deslizadores coincidan con tu tema personalizado usando una plantilla separada
- Crear un "modo oculto" donde puedas mostrar/ocultar varios botones a la vez
- Cambiar el tamaño de muchos botones con una sola edición
- Darles a todos los botones de tu menú las mismas texturas y sonidos personalizados
