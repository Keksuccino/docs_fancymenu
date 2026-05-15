---
title: Comunicación con servidor remoto
description: >-
  Envía y recibe datos de texto personalizados entre los clientes de FancyMenu y
  servidores externos.
---

# Comunicación con servidor remoto

El sistema de "Comunicación con servidor remoto" permite a los clientes de FancyMenu comunicarse con servidores externos mediante conexiones WebSocket.

Todos los datos son de texto:

- Se admite texto plano
- Se admite JSON (como texto normal)

Cada URL de servidor obtiene una sola **ID de solicitud** en caché durante la ejecución.
FancyMenu usa esta ID para hacer seguimiento de la conexión y exponerla en las variables de los listeners.

# Inicio rápido

1. Añade la acción **Conectar al servidor remoto** (opcional, pero útil para abrir la conexión antes)
2. Añade la acción **Enviar datos al servidor remoto** con la misma URL
3. Añade el listener **Al recibir datos del servidor remoto** para reaccionar a las respuestas
4. Usa **Al conectar con el servidor remoto** / **Al cerrar la conexión con el servidor remoto** para la lógica de estado de conexión
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

## Cerrar conexión con el servidor remoto

Cierra una conexión por ID de solicitud.

Entrada:

- ID de solicitud de la conexión

## Cerrar todas las conexiones con el servidor remoto

Cierra todas las conexiones activas con servidores remotos.

# Listeners

## Al conectar con el servidor remoto

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

- Las conexiones se **inician desde el cliente**
- FancyMenu mantiene las conexiones activas en segundo plano
- Si una conexión falla o agota el tiempo de espera, FancyMenu reintenta cada 10 segundos
- Cuando se restaura una conexión fallida, FancyMenu registra un mensaje de restauración
- Los mensajes salientes no enviados se ponen en cola con una **edad máxima de 30 segundos**
- Los mensajes en cola con más de 30 segundos se descartan

# Modos de URL

- `wss://` = seguro (TLS), recomendado
- `ws://` = sin cifrar, útil para pruebas locales

Ejemplo de URL local:

- `ws://127.0.0.1:8765`

# Buenas prácticas

1. Usa una URL estable por cada servicio de backend.
2. Mantén un formato de carga útil coherente para cada caso de uso.
3. Gestiona las conexiones cerradas o fallidas con lógica de interfaz de respaldo.
4. Usa las acciones de cierre cuando tu flujo haya terminado.
5. Usa `wss://` en entornos de producción.
