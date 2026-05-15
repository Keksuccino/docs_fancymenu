---
title: Comunicação com Servidor Remoto
description: >-
  Envie e receba dados de texto personalizados entre clientes FancyMenu e
  servidores externos.
---

# Comunicação com Servidor Remoto

O sistema de "Comunicação com Servidor Remoto" permite que clientes do FancyMenu se comuniquem com servidores externos usando conexões WebSocket.

Todos os dados são baseados em texto:

- Texto simples é suportado
- JSON é suportado (como texto normal)

Cada URL de servidor recebe um único **ID de requisição** em cache durante a execução.
O FancyMenu usa esse ID para rastrear a conexão e expô-lo em variáveis de listener.

# Início Rápido

1. Adicione a ação **Conectar ao Servidor Remoto** (opcional, mas útil para abrir antecipadamente)
2. Adicione a ação **Enviar Dados ao Servidor Remoto** com a mesma URL
3. Adicione o listener **Ao Receber Dados do Servidor Remoto** para reagir às respostas
4. Use **Ao Conectar ao Servidor Remoto** / **Ao Fechar Conexão com o Servidor Remoto** para lógica de estado da conexão
5. Feche as conexões quando necessário com as ações de fechamento

# Ações

## Conectar ao Servidor Remoto

Inicializa uma conexão com um servidor remoto sem enviar dados de payload.

Entrada:

- URL do Servidor Remoto

## Enviar Dados ao Servidor Remoto

Conecta-se (ou reutiliza uma conexão existente) e envia dados de texto.

Entradas:

1. URL do Servidor Remoto
2. Dados

## Fechar Conexão com o Servidor Remoto

Fecha uma conexão por ID da requisição.

Entrada:

- ID da Requisição da Conexão

## Fechar Todas as Conexões com Servidores Remotos

Fecha todas as conexões com servidores remotos atualmente ativas.

# Listeners

## Ao Conectar ao Servidor Remoto

Dispara quando uma conexão com servidor remoto é inicializada.

Variáveis:

- `$$request_id`
- `$$remote_server_url`

## Ao Receber Dados do Servidor Remoto

Dispara quando dados são recebidos de um servidor remoto conectado.

Variáveis:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Ao Fechar Conexão com o Servidor Remoto

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
- Se uma conexão travar ou atingir timeout, o FancyMenu tenta novamente a cada 10 segundos
- Quando uma conexão com falha é restaurada, o FancyMenu registra uma mensagem de restauração
- Mensagens de saída não enviadas são enfileiradas com uma **idade máxima de 30 segundos**
- Mensagens enfileiradas com mais de 30 segundos são descartadas

# Modos de URL

- `wss://` = seguro (TLS), recomendado
- `ws://` = sem criptografia, útil para testes locais

Exemplo de URL local:

- `ws://127.0.0.1:8765`

# Melhores Práticas

1. Use uma URL estável por serviço de backend.
2. Mantenha o formato do payload consistente para cada caso de uso.
3. Trate conexões fechadas/com falha com lógica de interface de fallback.
4. Use as ações de fechamento quando seu fluxo terminar.
5. Use `wss://` para ambientes de produção.
