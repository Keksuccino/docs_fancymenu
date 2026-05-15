---
title: Comunicación con Servidor Remoto
description: >-
  Envía y recibe datos de texto personalizados entre clientes de FancyMenu y
  servidores externos.
---

# Comunicación con Servidor Remoto

El sistema de "Comunicación con Servidor Remoto" permite que los clientes de FancyMenu se comuniquen con servidores externos mediante conexiones WebSocket.

Todos los datos se basan en texto:

- Se admite texto plano
- Se admite JSON (como texto normal)

Cada URL de servidor obtiene un solo **ID de solicitud** en caché durante el tiempo de ejecución.
FancyMenu usa este ID para rastrear la conexión y exponerlo en las variables del listener.

# Inicio rápido

1. Agrega la acción **Conectar al servidor remoto** (opcional, pero útil para abrir la conexión antes)
2. Agrega la acción **Enviar datos al servidor remoto** con la misma URL
3. Agrega el listener **Al recibir datos del servidor remoto** para reaccionar a las respuestas
4. Usa **Al conectar al servidor remoto** / **Al cerrar la conexión con el servidor remoto** para la lógica de estado de conexión
5. Cierra las conexiones cuando sea necesario con las acciones de cierre

# Acciones

## Conectar al servidor remoto

Inicializa una conexión con un servidor remoto sin enviar datos de carga útil.

Entrada:

- URL del servidor remoto

## Enviar datos al servidor remoto

Se conecta (o reutiliza una conexión existente) y envía datos de texto.

Entradas:

1. URL del servidor remoto
2. Datos

## Cerrar conexión con servidor remoto

Cierra una conexión por ID de solicitud.

Entrada:

- ID de solicitud de conexión

## Cerrar todas las conexiones con servidores remotos

Cierra todas las conexiones activas con servidores remotos.

# Listeners

## Al conectar al servidor remoto

Se activa cuando se inicializa una conexión con un servidor remoto.

Variables:

- `$$request_id`
- `$$remote_server_url`

## Al recibir datos del servidor remoto

Se activa cuando se reciben datos de un servidor remoto conectado.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Al cerrar la conexión con el servidor remoto

Se activa cuando se cierra una conexión con un servidor remoto.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Comportamiento de la conexión

- Las conexiones son **iniciadas por el cliente**
- FancyMenu mantiene las conexiones activas en segundo plano
- Si una conexión falla o expira, FancyMenu lo reintenta cada 10 segundos
- Cuando una conexión fallida se restablece, FancyMenu registra un mensaje de restauración
- Los mensajes salientes no enviados se ponen en cola con una **edad máxima de 30 segundos**
- Los mensajes en cola con más de 30 segundos de antigüedad se descartan

# Modos de URL

- `wss://` = seguro (TLS), recomendado
- `ws://` = sin cifrado, útil para pruebas locales

Ejemplo de URL local:

- `ws://127.0.0.1:8765`

# Mejores prácticas

1. Usa una URL estable por cada servicio de backend.
2. Mantén un formato de carga útil consistente para cada caso de uso.
3. Maneja las conexiones cerradas o fallidas con lógica de interfaz de respaldo.
4. Usa las acciones de cierre cuando tu flujo termine.
5. Usa `wss://` para entornos de producción.
