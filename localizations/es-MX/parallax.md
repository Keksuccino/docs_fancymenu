---
title: Efecto Parallax
description: Cómo aplicar un efecto parallax al fondo del menú y a los elementos.
---

# ¿Qué es el efecto Parallax?

El efecto parallax es un truco visual muy útil que hace que los fondos y elementos de tu menú parezcan tener profundidad. Cuando mueves el cursor del mouse, los elementos con parallax activado se moverán ligeramente, creando la ilusión de un espacio 3D dentro de tu menú 2D. 

Piensa en cuando vas en un coche: las cosas que están más cerca de ti (como los señalamientos de la carretera) parecen moverse más rápido que las cosas lejanas (como las montañas). En FancyMenu, esta misma idea crea una experiencia más dinámica e interactiva.

# ¿Dónde puedes usar Parallax en FancyMenu?

En FancyMenu, puedes usar el efecto parallax en dos lugares principales:

1. **Fondos del menú**: haz que todo el fondo de tu menú se mueva ligeramente con el cursor del mouse
2. **Elementos**: haz que elementos individuales (como imágenes, botones o texto) se muevan de forma independiente

# Cómo usar Parallax en los fondos del menú

Agregar un efecto parallax al fondo de tu menú es muy fácil:

1. Abre el editor del menú presionando **CTRL+ALT+C** para mostrar la barra de menú, luego ve a **Customization**
2. Crea un nuevo layout o edita uno existente
3. Haz clic en **Layout → Properties** 
4. Abre **Menu Backgrounds**
5. Elige **Image** como tipo de fondo
6. Configura tu fondo de imagen:
   - Elige una imagen (local o de la web)
   - Activa **Parallax Effect** haciendo clic en el botón de alternancia
   - Ajusta la **Parallax Effect Intensity X** y la **Parallax Effect Intensity Y** (entre 0.0 y 1.0)
   - Opcionalmente, activa **Invert Parallax Movement** para cambiar la dirección

> **Consejo**: Mientras más alto sea el valor de intensidad, más se moverá tu fondo. FancyMenu 3.9.0 te permite configurar la intensidad X y Y por separado, así que puedes hacer que el movimiento sea más fuerte horizontalmente que verticalmente, o al revés.
{.is-info}

# Cómo usar Parallax en elementos individuales

También puedes agregar parallax a elementos individuales para crear efectos por capas:

1. Selecciona cualquier elemento en el editor haciendo clic sobre él
2. Haz clic derecho en el elemento para abrir el menú contextual
3. Desplázate hacia abajo y busca **Parallax Effect: Enabled/Disabled**
4. Cámbialo a **Enabled**
5. Ajusta los valores de **Parallax Intensity X** y **Parallax Intensity Y** (entre 0.0 y 1.0)
6. Opcionalmente, activa **Invert Parallax** para cambiar la dirección del movimiento

# Consejos para crear efectos Parallax increíbles

## Distribuye tus elementos en capas

Crea profundidad usando diferentes valores de intensidad de parallax para distintos elementos. Puedes ajustar X e Y por separado:

- **Fondo**: intensidad baja (0.1-0.3)
- **Elementos de la capa media**: intensidad media (0.3-0.6)
- **Elementos del primer plano**: intensidad alta (0.6-0.9)

¡Esto crea un efecto 3D convincente cuando mueves el mouse!

## Combina parallax normal e invertido

Prueba configurando algunos elementos con **Invert Parallax Movement: Enabled** y otros con **Disabled**. Esto hace que los elementos se muevan en direcciones opuestas, lo que refuerza el efecto de profundidad.

## No te excedas

Demasiado movimiento puede distraer. Usa el efecto parallax con moderación, especialmente con valores de intensidad altos.

# Solución de problemas

## ¿El parallax no funciona?

1. Asegúrate de haber activado el efecto parallax
2. Verifica que la intensidad del parallax no esté configurada en 0
4. Confirma que la opción "Slide Wide Images From Left To Right" esté desactivada (esta opción entra en conflicto con parallax)

## ¿El movimiento del parallax es demasiado rápido o lento?

Ajusta los valores de **Parallax Intensity X/Y**:
- Valores más bajos (más cerca de 0) = movimiento más lento y sutil
- Valores más altos (más cerca de 1) = movimiento más rápido y más notorio

# Reflexión final

El efecto parallax es una excelente forma de hacer que tus menús de Minecraft se sientan más vivos e interactivos. Experimenta con distintas combinaciones de parallax en fondos y elementos para crear diseños impresionantes y dinámicos que respondan a los movimientos de tu mouse.

Recuerda: los mejores efectos suelen ser sutiles; un poco de movimiento basta para crear una experiencia envolvente.
