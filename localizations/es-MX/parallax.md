---
title: Efecto Parallax
description: Cómo aplicar un efecto parallax al fondo del menú y a los elementos.
---
# ¿Qué es el efecto Parallax?

El efecto parallax es un truco visual genial que hace que los fondos y elementos de tu menú parezcan tener profundidad. Cuando mueves el cursor del mouse, los elementos con parallax activado se moverán ligeramente, creando la ilusión de espacio 3D en tu menú 2D.

Piénsalo como cuando vas en un coche: las cosas que están más cerca de ti (como las señales de tráfico) parecen moverse más rápido que las cosas lejanas (como las montañas). En FancyMenu, esta misma idea crea una experiencia más dinámica e interactiva.

# ¿Dónde puedes usar parallax en FancyMenu?

En FancyMenu, puedes usar el efecto parallax en dos lugares principales:

1. **Fondos del menú**: haz que todo el fondo de tu menú se mueva ligeramente con el cursor del mouse
2. **Elementos**: haz que elementos individuales (como imágenes, botones o texto) se muevan de forma independiente

# Cómo usar parallax en los fondos del menú

Agregar un efecto parallax al fondo de tu menú es súper fácil:

1. Abre el editor del menú presionando **CTRL+ALT+C** para mostrar la barra de menú, luego ve a **Personalización**
2. Crea un nuevo diseño o edita uno existente
3. Haz clic en **Diseño → Propiedades** 
4. Abre **Fondos del menú**
5. Elige **Imagen** como tipo de fondo
6. Configura tu fondo de imagen:
   - Elige una imagen (local o de la web)
   - Activa **Efecto Parallax** haciendo clic en el interruptor
   - Establece la **Intensidad del efecto parallax X** y la **Intensidad del efecto parallax Y** (entre 0.0 y 1.0)
   - Opcionalmente, activa **Invertir movimiento de parallax** para cambiar la dirección

> **Consejo**: Mientras más alto sea el valor de intensidad, más se moverá tu fondo. FancyMenu 3.9.0 te permite configurar la intensidad de X e Y por separado, así puedes hacer que el movimiento sea más fuerte horizontalmente que verticalmente, o al revés.
{.is-info}

# Cómo usar parallax en elementos individuales

También puedes agregar parallax a elementos individuales para crear efectos por capas:

1. Selecciona cualquier elemento en el editor haciendo clic sobre él
2. Haz clic derecho en el elemento para abrir el menú contextual
3. Desplázate hacia abajo y busca **Efecto Parallax: Activado/Desactivado**
4. Cámbialo a **Activado**
5. Ajusta los valores de **Intensidad Parallax X** e **Intensidad Parallax Y** (entre 0.0 y 1.0)
6. Opcionalmente, activa **Invertir Parallax** para cambiar la dirección del movimiento

# Consejos para crear efectos parallax increíbles

## Distribuye tus elementos por capas

Crea profundidad usando distintos valores de intensidad parallax para diferentes elementos. Puedes ajustar X e Y por separado:

- **Fondo**: intensidad baja (0.1-0.3)
- **Elementos de la capa intermedia**: intensidad media (0.3-0.6)
- **Elementos del primer plano**: intensidad alta (0.6-0.9)

¡Esto crea un efecto 3D convincente cuando mueves el mouse!

## Combina parallax normal e invertido

Intenta configurar algunos elementos con **Invertir movimiento de parallax: Activado** y otros con **Desactivado**. Esto hace que los elementos se muevan en direcciones opuestas, lo que mejora el efecto de profundidad.

## No exageres

Demasiado movimiento puede distraer. Usa el efecto parallax con moderación, especialmente con valores de intensidad altos.

# Solución de problemas

## ¿El parallax no funciona?

1. Asegúrate de haber activado el efecto parallax
2. Verifica que la intensidad del parallax no esté configurada en 0
4. Confirma que la opción "Slide Wide Images From Left To Right" esté desactivada (esta opción entra en conflicto con el parallax)

## ¿El movimiento del parallax es demasiado rápido o lento?

Ajusta los valores de **Intensidad Parallax X/Y**:
- Valores más bajos (más cerca de 0) = movimiento más lento y sutil
- Valores más altos (más cerca de 1) = movimiento más rápido y más dramático

## ¿El parallax se siente poco fluido o con lag?

Eso es una limitación del efecto parallax, ya que Minecraft usa coordenadas basadas en enteros (números completos), por lo que es posible que el efecto se sienta un poco como si los elementos estuvieran "brincando", pero no debería notarse mucho si usas intensidades de parallax "normales" y no valores demasiado pequeños o grandes.
