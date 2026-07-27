---
title: Comunicação com Servidor Remoto
description: >-
  Envie e receba dados de texto personalizados entre clientes FancyMenu e
  servidores externos.
---

# Comunicação com Servidor Remoto

O sistema de "Comunicação com Servidor Remoto" permite que os clientes FancyMenu se comuniquem com servidores externos usando conexões WebSocket.

Todos os dados são baseados em texto:

- Texto simples é compatível
- JSON é compatível (como texto normal)

Cada URL de servidor recebe um único **ID de solicitação** em cache durante a execução.
O FancyMenu usa esse ID para rastrear a conexão e expô-lo nas variáveis dos listeners.

# Início Rápido

1. Adicione [**Conectar ao Servidor Remoto**](#connect-to-remote-server) quando a conexão deve ser aberta cedo.
2. Adicione [**Enviar Dados ao Servidor Remoto**](#send-data-to-remote-server) com a mesma URL.
3. Adicione [**Ao Receber Dados do Servidor Remoto**](#on-remote-server-data-received) para reagir às respostas.
4. Use [**Ao Servidor Remoto Conectado**](#on-remote-server-connected) e [**Ao Servidor Remoto com Conexão Fechada**](#on-remote-server-connection-closed) para lógica de estado da conexão.
5. Feche conexões com [**Fechar Conexão com Servidor Remoto**](#close-remote-server-connection) ou [**Fechar Todas as Conexões com Servidores Remotos**](#close-all-remote-server-connections).

# Ações

## Conectar ao Servidor Remoto

Abre ou reutiliza uma conexão com servidor remoto sem enviar dados de payload.

Entrada:

- URL do Servidor Remoto

## Enviar Dados ao Servidor Remoto

Conecta-se (ou reutiliza uma conexão existente) e envia dados de texto.

Entradas:

1. URL do Servidor Remoto
2. Dados

## Fechar Conexão com Servidor Remoto

Fecha uma conexão pelo ID de solicitação.

Entrada:

- ID da Solicitação da Conexão

## Fechar Todas as Conexões com Servidores Remotos

Fecha todas as conexões com servidores remotos que estiverem ativas no momento.

# Listeners

## Ao Servidor Remoto Conectado

Dispara após uma conexão com servidor remoto ser aberta com sucesso.

Variáveis:

- `$$request_id`
- `$$remote_server_url`

## Ao Receber Dados do Servidor Remoto

Dispara quando dados são recebidos de um servidor remoto conectado.

Variáveis:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Ao Servidor Remoto com Conexão Fechada

Dispara quando uma conexão com servidor remoto é encerrada.

Variáveis:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Comportamento da Conexão

- As conexões são **iniciadas pelo cliente**
- O FancyMenu mantém as conexões ativas em segundo plano
- Se uma conexão travar ou expirar, o FancyMenu tenta novamente a cada 10 segundos
- Quando uma conexão travada é restaurada, o FancyMenu registra uma mensagem de restauração
- Mensagens de saída não enviadas são enfileiradas com uma **idade máxima de 30 segundos**
- Mensagens na fila com mais de 30 segundos são descartadas

# Modos de URL

- `wss://` é usado como escrito e é recomendado.
- `ws://` é usado como escrito e não é criptografado.
- `https://` é convertido para `wss://`.
- `http://` é convertido para `ws://`.
- Um host sem esquema é prefixado com `wss://`.
- Outros esquemas de URL explícitos são rejeitados.

Prefira URLs explícitas com `wss://`. Exemplo de URL local:

- `ws://127.0.0.1:8765`

Use uma URL estável por serviço, trate os estados de listener de conexão fechada/travada e feche as conexões quando elas não forem mais necessárias.
