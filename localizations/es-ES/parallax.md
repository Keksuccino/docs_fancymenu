---
title: Efecto Parallax
description: Cómo aplicar un efecto parallax al fondo y a los elementos del menú.
---

# ¿Qué es el efecto Parallax?

El efecto parallax es un truco visual muy interesante que hace que los fondos y elementos de tu menú parezcan tener profundidad. Cuando mueves el cursor del ratón, los elementos con parallax activado se desplazan ligeramente, creando una ilusión de espacio 3D en tu menú 2D.

Piensa en ello como cuando vas en coche: las cosas que están más cerca de ti (como las señales de tráfico) parecen moverse más rápido que las lejanas (como las montañas). En FancyMenu, esta misma idea crea una experiencia más dinámica e interactiva.

# ¿Dónde puedes usar el parallax en FancyMenu?

En FancyMenu, puedes usar el efecto parallax en dos lugares principales:

1. **Fondos del menú**: Haz que el fondo completo del menú se mueva ligeramente con el cursor del ratón
2. **Elementos**: Haz que elementos individuales (como imágenes, botones o texto) se muevan de forma independiente

# Cómo usar el parallax en los fondos del menú

Añadir un efecto parallax al fondo del menú es muy sencillo:

1. Abre el editor de menús pulsando **CTRL+ALT+C** para mostrar la barra de menús y luego ve a **Personalización**
2. Crea un nuevo diseño o edita uno existente
3. Haz clic en **Layout → Properties** 
4. Abre **Menu Backgrounds**
5. Elige **Image** como tipo de fondo
6. Configura el fondo de imagen:
   - Elige una imagen (local o desde la web)
   - Activa **Parallax Effect** haciendo clic en el interruptor
   - Ajusta la **Parallax Effect Intensity X** y la **Parallax Effect Intensity Y** (entre 0.0 y 1.0)
   - Opcionalmente, activa **Invert Parallax Movement** para cambiar la dirección

> **Consejo**: Cuanto mayor sea el valor de intensidad, más se moverá el fondo. FancyMenu 3.9.0 te permite establecer la intensidad X e Y por separado, así que puedes hacer que el movimiento sea más fuerte horizontalmente que verticalmente, o al revés.
{.is-info}

# Cómo usar el parallax en elementos individuales

También puedes añadir parallax a elementos individuales para crear efectos por capas:

1. Selecciona cualquier elemento en el editor haciendo clic sobre él
2. Haz clic derecho en el elemento para abrir el menú contextual
3. Desplázate hacia abajo y busca **Parallax Effect: Enabled/Disabled**
4. Cámbialo a **Enabled**
5. Ajusta los valores de **Parallax Intensity X** y **Parallax Intensity Y** (entre 0.0 y 1.0)
6. Opcionalmente, activa **Invert Parallax** para cambiar la dirección del movimiento

# Consejos para crear efectos de parallax increíbles

## Distribuye los elementos por capas

Crea profundidad usando distintos valores de intensidad de parallax para diferentes elementos. Puedes ajustar X e Y por separado:

- **Fondo**: Intensidad baja (0.1-0.3)
- **Elementos de la capa intermedia**: Intensidad media (0.3-0.6)
- **Elementos del primer plano**: Intensidad alta (0.6-0.9)

¡Esto crea un efecto 3D muy convincente al mover el ratón!

## Combina parallax normal e invertido

Prueba a poner algunos elementos con **Invert Parallax Movement: Enabled** y otros con **Disabled**. Esto hace que los elementos se muevan en direcciones opuestas, potenciando el efecto de profundidad.

## No te pases

Demasiado movimiento puede resultar molesto. Usa el efecto parallax con moderación, especialmente con valores de intensidad altos.

# Solución de problemas

## ¿El parallax no funciona?

1. Asegúrate de que has activado el efecto parallax
2. Comprueba que la intensidad del parallax no esté configurada en 0
4. Confirma que la opción "Slide Wide Images From Left To Right" esté desactivada (esta opción entra en conflicto con el parallax)

## ¿El movimiento del parallax es demasiado rápido o lento?

Ajusta los valores de **Parallax Intensity X/Y**:
- Valores más bajos (más cerca de 0) = movimiento más lento y sutil
- Valores más altos (más cerca de 1) = movimiento más rápido y más llamativo

# Reflexión final

El efecto parallax es una forma estupenda de hacer que los menús de Minecraft se sientan más vivos e interactivos. Experimenta con distintas combinaciones de parallax en el fondo y en los elementos para crear diseños impresionantes y dinámicos que respondan a los movimientos de tu ratón.

Recuerda: los mejores efectos suelen ser sutiles; un poco de movimiento da para mucho a la hora de crear una experiencia envolvente.
