---
title: Compartilhamento de Dados Cliente < - > Servidor
description: Envie e receba dados personalizados entre servidor e cliente com o FancyMenu.
---

# FM Data

O sistema "FM Data" permite enviar dados de texto personalizados entre o servidor e o cliente.

Toda mensagem do FM Data tem:

1. Um **identificador de dados** (que tipo de mensagem é esta)
2. Um **valor de dados** (o conteúdo em si)

Ideia de exemplo:

- Identificador: `hud.food`
- Dados: `18/20`

# Início Rápido

1. O servidor envia dados com `/fmdata send ...`
2. O cliente os recebe com o listener do FancyMenu **On FM Data Received**
3. O cliente também pode enviar dados de volta com a ação **Send FM Data To Server**
4. O servidor pode reagir automaticamente com `/fmdata listener ...`
5. O servidor pode enviar dados automaticamente ao entrar com `/fmdata welcome_data ...`

# Servidor -> Cliente

Use:

```mcfunction
/fmdata send <target_player> <data_identifier> <string_data>
```

Exemplos:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "atualização do valor de comida" "18 de 20"
```

Observações:

- `<target_player>` aceita seletores normais de jogadores, como `@a`, `@p`, `@s`
- Use aspas para valores com espaços

# Cliente: Receber Dados

Use o listener do FancyMenu:

- **On FM Data Received**

Variáveis disponíveis:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` é:

- IP do servidor no modo multijogador
- `integrated_server` no modo individual

Casos de uso comuns:

- Atualizar elementos de texto
- Disparar ações de menu
- Executar lógica com base no identificador/dados recebidos

# Cliente -> Servidor

Use a ação do FancyMenu:

- **Send FM Data To Server**

A ação tem 2 entradas:

1. Identificador de Dados
2. Dados

O servidor pode então processar os dados recebidos com `/fmdata listener ...`.

# Listeners do Servidor

Os listeners do servidor escutam dados recebidos dos clientes e podem executar um ou vários comandos quando são acionados.

Os listeners do servidor são salvos e permanecem ativos após reiniciar.

Gerencie-os com:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Sintaxe de Adição / Edição

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Sintaxe de Remoção

```mcfunction
/fmdata listener remove <listener_name>
```

## Tipos de Correspondência

`matching_type_identifier` e `matching_type_data` podem ser:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Regras de Correspondência

- `ignore_case_identifier` e `ignore_case_data` são alternâncias true/false
- `listen_for_identifier` aceita curinga `*` (sempre corresponde)
- `listen_for_data` aceita curinga `*` (sempre corresponde)
- `fire_for_player` usa seletores normais de jogadores (por exemplo `@a`, `@p`, `Player761`)

## Comandos ao Ser Acionado

`commands_to_execute_on_fire` é uma única entrada de texto.

- Separe vários comandos com `|||`
- Escape um separador literal como `\|\|\|`

Você pode usar dois placeholders especiais aqui que são substituídos imediatamente antes da execução dos comandos:

- `%fm_sender%` -> jogador que enviou o FM Data
- `%fm_data%` -> valor de dados recebido do cliente

Os comandos são executados como comandos do servidor.

## Exemplos de Comandos

Reaja a um clique de botão de qualquer jogador:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressionou o botão\"}"
```

Execute vários comandos quando os dados contiverem `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Recompensa de %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Dados de Boas-vindas

Os dados de boas-vindas enviam FM Data para os jogadores correspondentes quando eles entram.

Gerencie as entradas com:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Sintaxe de Adição / Edição

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Sintaxe de Remoção

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Observações:

- `<target_player>` aceita seletores normais como `@a`, `@p`, `@s`
- Os dados são enviados aos jogadores correspondentes quando eles entram
- As entradas são salvas e carregadas automaticamente

## Exemplos de Comandos

Envie dados de boas-vindas para todos os jogadores que entrarem:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Bem-vindo!"
```

Envie dados de boas-vindas apenas para um jogador:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "Benefícios VIP ativados"
```

# Boas Práticas

1. Use identificadores claros como `hud.food`, `menu.shop.open`, `quest.progress`.
2. Mantenha o formato dos dados consistente para cada identificador.
3. Comece simples: teste com `/fmdata send` antes de criar listeners complexos.
4. Use `@a` somente quando você realmente quiser um comportamento global.
5. Use `/fmdata listener list` e `/fmdata welcome_data list` para manter as configurações organizadas.
