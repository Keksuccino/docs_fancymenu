---
title: Efecto Parallax
description: Cómo aplicar un efecto parallax al fondo y a los elementos del menú.
---
# ¿Qué es el efecto Parallax?

El efecto parallax es un truco visual muy chulo que hace que los fondos y elementos de tu menú parezcan tener profundidad. Cuando mueves el cursor del ratón, los elementos con parallax activado se desplazan ligeramente, creando la ilusión de espacio 3D en tu menú 2D. 

Piensa en ello como cuando vas en un coche: las cosas que están más cerca de ti (como las señales de tráfico) parecen moverse más rápido que las que están lejos (como las montañas). En FancyMenu, esta misma idea crea una experiencia más dinámica e interactiva.

# ¿Dónde puedes usar Parallax en FancyMenu?

En FancyMenu, puedes usar el efecto parallax en dos lugares principales:

1. **Fondos del menú**: Haz que el fondo completo de tu menú se mueva ligeramente con el cursor del ratón
2. **Elementos**: Haz que elementos individuales (como imágenes, botones o texto) se muevan de forma independiente

# Cómo usar Parallax en los fondos del menú

Añadir un efecto parallax al fondo de tu menú es facilísimo:

1. Abre el editor del menú pulsando **CTRL+ALT+C** para mostrar la barra de menú, y luego ve a **Personalización**
2. Crea un nuevo diseño o edita uno existente
3. Haz clic en **Diseño → Propiedades** 
4. Abre **Fondos del menú**
5. Elige **Imagen** como tipo de fondo
6. Configura tu fondo de imagen:
   - Elige una imagen (local o de la web)
   - Activa **Efecto Parallax** haciendo clic en el interruptor
   - Ajusta la **Intensidad del efecto Parallax X** y la **Intensidad del efecto Parallax Y** (entre 0.0 y 1.0)
   - Opcionalmente, activa **Invertir movimiento Parallax** para cambiar la dirección

> **Consejo**: Cuanto mayor sea el valor de intensidad, más se moverá tu fondo. FancyMenu 3.9.0 te permite establecer la intensidad de X e Y por separado, así que puedes hacer que el movimiento sea más fuerte en horizontal que en vertical, o al revés.
{.is-info}

# Cómo usar Parallax en elementos individuales

También puedes añadir parallax a elementos individuales para crear efectos por capas:

1. Selecciona cualquier elemento en el editor haciendo clic sobre él
2. Haz clic derecho en el elemento para abrir el menú contextual
3. Desplázate hacia abajo y busca **Efecto Parallax: Activado/Desactivado**
4. Cámbialo a **Activado**
5. Ajusta los valores de **Intensidad Parallax X** e **Intensidad Parallax Y** (entre 0.0 y 1.0)
6. Opcionalmente, activa **Invertir Parallax** para cambiar la dirección del movimiento

# Consejos para crear efectos Parallax increíbles

## Distribuye los elementos en capas

Crea profundidad usando distintos valores de intensidad parallax para diferentes elementos. Puedes ajustar X e Y por separado:

- **Fondo**: Intensidad baja (0.1-0.3)
- **Elementos de la capa intermedia**: Intensidad media (0.3-0.6)
- **Elementos del primer plano**: Intensidad alta (0.6-0.9)

¡Esto crea un efecto 3D convincente al mover el ratón!

## Combina Parallax normal e invertido

Prueba a poner algunos elementos en **Invertir movimiento Parallax: Activado** y otros en **Desactivado**. Esto hace que los elementos se muevan en direcciones opuestas, reforzando el efecto de profundidad.

## No te pases

Demasiado movimiento puede distraer. Usa el efecto parallax con moderación, especialmente con valores de intensidad altos.

# Solución de problemas

## ¿El parallax no funciona?

1. Asegúrate de haber activado el efecto parallax
2. Comprueba que la intensidad del parallax no esté puesta en 0
4. Confirma que la opción "Slide Wide Images From Left To Right" está desactivada (esta opción entra en conflicto con parallax)

## ¿El movimiento parallax es demasiado rápido o demasiado lento?

Ajusta los valores de **Intensidad Parallax X/Y**:
- Valores más bajos (más cerca de 0) = movimiento más lento y sutil
- Valores más altos (más cerca de 1) = movimiento más rápido y más llamativo

## ¿El parallax se ve poco fluido o con lag?

Eso es una limitación del efecto parallax, ya que Minecraft usa coordenadas basadas en números enteros (números completos), así que es posible que el efecto parezca que los elementos dan "saltos", pero no debería notarse demasiado si usas intensidades de parallax "normales" y no valores extremadamente pequeños o grandes.
