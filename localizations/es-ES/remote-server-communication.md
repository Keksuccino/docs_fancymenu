---
title: Comunicación con servidor remoto
description: >-
  Envía y recibe datos de texto personalizados entre clientes de FancyMenu y
  servidores externos.
---

# Comunicación con servidor remoto

El sistema de "Comunicación con servidor remoto" permite a los clientes de FancyMenu comunicarse con servidores externos mediante conexiones WebSocket.

Todos los datos son de texto:

- Se admite texto sin formato
- Se admite JSON (como texto normal)

Cada URL de servidor obtiene un único **ID de solicitud** en caché durante el tiempo de ejecución.
FancyMenu usa este ID para seguir la conexión y exponerlo en variables de los listeners.

# Inicio rápido

1. Añade [**Conectar al servidor remoto**](#connect-to-remote-server) cuando la conexión deba abrirse pronto.
2. Añade [**Enviar datos al servidor remoto**](#send-data-to-remote-server) con la misma URL.
3. Añade [**Al recibir datos del servidor remoto**](#on-remote-server-data-received) para reaccionar a las respuestas.
4. Usa [**Al conectarse al servidor remoto**](#on-remote-server-connected) y [**Al cerrarse la conexión con el servidor remoto**](#on-remote-server-connection-closed) para la lógica del estado de la conexión.
5. Cierra las conexiones con [**Cerrar conexión del servidor remoto**](#close-remote-server-connection) o [**Cerrar todas las conexiones del servidor remoto**](#close-all-remote-server-connections).

# Acciones

## Conectar al servidor remoto

Abre o reutiliza una conexión con un servidor remoto sin enviar datos de carga útil.

Entrada:

- URL del servidor remoto

## Enviar datos al servidor remoto

Se conecta (o reutiliza una conexión existente) y envía datos de texto.

Entradas:

1. URL del servidor remoto
2. Datos

## Cerrar conexión del servidor remoto

Cierra una conexión por ID de solicitud.

Entrada:

- ID de solicitud de la conexión

## Cerrar todas las conexiones del servidor remoto

Cierra todas las conexiones activas con servidores remotos.

# Listeners

## Al conectarse al servidor remoto

Se activa después de que una conexión con un servidor remoto se abra correctamente.

Variables:

- `$$request_id`
- `$$remote_server_url`

## Al recibir datos del servidor remoto

Se activa cuando se reciben datos desde un servidor remoto conectado.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Al cerrarse la conexión con el servidor remoto

Se activa cuando una conexión con un servidor remoto se cierra.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Comportamiento de la conexión

- Las conexiones son **iniciadas por el cliente**
- FancyMenu mantiene las conexiones activas en segundo plano
- Si una conexión falla o agota el tiempo de espera, FancyMenu reintenta cada 10 segundos
- Cuando se restaura una conexión que había fallado, FancyMenu registra un mensaje de restauración
- Los mensajes salientes no enviados se ponen en cola con una **edad máxima de 30 segundos**
- Los mensajes en cola con más de 30 segundos se descartan

# Modos de URL

- `wss://` se usa tal como está escrito y es lo recomendado.
- `ws://` se usa tal como está escrito y no está cifrado.
- `https://` se convierte en `wss://`.
- `http://` se convierte en `ws://`.
- Un host sin prefijo se antepone con `wss://`.
- Se rechazan otros esquemas de URL explícitos.

Preferiblemente usa URLs explícitas `wss://`. Ejemplo de URL local:

- `ws://127.0.0.1:8765`

Usa una URL estable por servicio, gestiona los estados de listener de cerrado/fallo y cierra las conexiones cuando ya no sean necesarias.
