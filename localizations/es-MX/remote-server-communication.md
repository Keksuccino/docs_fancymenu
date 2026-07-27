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

A cada URL de servidor se le asigna una sola **ID de solicitud** en caché durante el tiempo de ejecución.
FancyMenu usa esta ID para rastrear la conexión y mostrarla en variables de los listeners.

# Inicio rápido

1. Agrega [**Conectar al Servidor Remoto**](#connect-to-remote-server) cuando la conexión deba abrirse con anticipación.
2. Agrega [**Enviar Datos al Servidor Remoto**](#send-data-to-remote-server) con la misma URL.
3. Agrega [**Al Recibir Datos del Servidor Remoto**](#on-remote-server-data-received) para reaccionar a las respuestas.
4. Usa [**Al Conectarse al Servidor Remoto**](#on-remote-server-connected) y [**Al Cerrarse la Conexión con el Servidor Remoto**](#on-remote-server-connection-closed) para la lógica de estado de conexión.
5. Cierra las conexiones con [**Cerrar Conexión del Servidor Remoto**](#close-remote-server-connection) o [**Cerrar Todas las Conexiones del Servidor Remoto**](#close-all-remote-server-connections).

# Acciones

## Conectar al Servidor Remoto

Abre o reutiliza una conexión con el servidor remoto sin enviar datos de carga útil.

Entrada:

- URL del Servidor Remoto

## Enviar Datos al Servidor Remoto

Se conecta (o reutiliza una conexión existente) y envía datos de texto.

Entradas:

1. URL del Servidor Remoto
2. Datos

## Cerrar Conexión del Servidor Remoto

Cierra una conexión por ID de solicitud.

Entrada:

- ID de Solicitud de la Conexión

## Cerrar Todas las Conexiones del Servidor Remoto

Cierra todas las conexiones activas del servidor remoto.

# Listeners

## Al Conectarse al Servidor Remoto

Se activa después de que una conexión con el servidor remoto se abre correctamente.

Variables:

- `$$request_id`
- `$$remote_server_url`

## Al Recibir Datos del Servidor Remoto

Se activa cuando se reciben datos de un servidor remoto conectado.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Al Cerrarse la Conexión con el Servidor Remoto

Se activa cuando se cierra una conexión con el servidor remoto.

Variables:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Comportamiento de la Conexión

- Las conexiones son **iniciadas por el cliente**
- FancyMenu mantiene las conexiones activas en segundo plano
- Si una conexión falla o expira, FancyMenu reintenta cada 10 segundos
- Cuando se restaura una conexión fallida, FancyMenu registra un mensaje de restauración
- Los mensajes salientes no enviados se ponen en cola con una **edad máxima de 30 segundos**
- Los mensajes en cola con más de 30 segundos se descartan

# Modos de URL

- `wss://` se usa tal cual y es lo recomendado.
- `ws://` se usa tal cual y no está cifrado.
- `https://` se convierte en `wss://`.
- `http://` se convierte en `ws://`.
- Un host sin esquema se antepone con `wss://`.
- Otros esquemas de URL explícitos se rechazan.

Prefiere URLs explícitas con `wss://`. Ejemplo de URL local:

- `ws://127.0.0.1:8765`

Usa una URL estable por servicio, maneja los estados de listener de conexión cerrada/fallida y cierra las conexiones cuando ya no sean necesarias.
