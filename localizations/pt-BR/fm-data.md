---
title: Compartilhamento de dados Cliente < - > Servidor
description: >-
  Envie e receba dados personalizados entre o servidor e o cliente com o
  FancyMenu.
sourceBlobSha: 35ae4605e43ac917f11c24e5d97a5c311c9aa01a
---

# Dados do FM

O sistema "Dados do FM" permite enviar dados de texto personalizados entre o servidor e o cliente.

Todos os subcomandos de `/fmdata` exigem **nível de permissão 2** (Mestre do Jogo / nível OP 2).

Todas as mensagens de Dados do FM têm:

1. Um **identificador de dados** (o tipo da mensagem)
2. Um **valor de dados** (o conteúdo propriamente dito)

Exemplo:

- Identificador: `hud.food`
- Dados: `18/20`

# Início rápido

1. O servidor envia dados com `/fmdata send ...`
2. O cliente os recebe pelo listener do FancyMenu **On FM Data Received**
3. O cliente também pode enviar dados de volta com a ação **Send FM Data To Server**
4. O servidor pode reagir automaticamente com `/fmdata listener ...`
5. O servidor pode enviar dados automaticamente quando alguém entra com `/fmdata welcome_data ...`

# Servidor -> Cliente

Use:

```mcfunction
/fmdata send <target_players> <data_identifier> <string_data>
```

Exemplos:

```mcfunction
/fmdata send Player761 hud.food 18/20
/fmdata send @a "food value update" "18 of 20"
```

Observações:

- `<target_players>` aceita nomes de jogadores e seletores como `@a`, `@p` e `@s`
- Use aspas em valores que contenham espaços

# Cliente: receber dados

Use o listener do FancyMenu:

- **On FM Data Received**

Variáveis disponíveis:

- `$$data_identifier`
- `$$data`
- `$$sent_by`

`$$sent_by` corresponde a:

- IP do servidor no modo multijogador
- `integrated_server` no modo para um jogador

Usos comuns:

- Atualizar elementos de texto
- Acionar ações de menu
- Executar lógica com base no identificador/dado recebido

# Cliente -> Servidor

Use a ação do FancyMenu:

- **Send FM Data To Server**

A ação tem 2 entradas:

1. Identificador de dados
2. Dados

Em seguida, o servidor pode processar os dados recebidos com `/fmdata listener ...`.

# Listeners do servidor

Os listeners do servidor aguardam dados recebidos dos clientes e podem executar um ou mais comandos quando são acionados.

Os listeners do servidor são salvos e permanecem ativos após uma reinicialização.

Gerencie-os com:

- `/fmdata listener list`
- `/fmdata listener add ...`
- `/fmdata listener edit ...`
- `/fmdata listener remove ...`

## Sintaxe para adicionar/editar

```mcfunction
/fmdata listener add <unique_listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

```mcfunction
/fmdata listener edit <listener_name> <matching_type_identifier> <matching_type_data> <ignore_case_identifier> <ignore_case_data> <fire_for_player> <listen_for_identifier> <listen_for_data> <commands_to_execute_on_fire>
```

## Sintaxe para remover

```mcfunction
/fmdata listener remove <listener_name>
```

## Tipos de correspondência

`matching_type_identifier` e `matching_type_data` podem ser:

- `equals`
- `contains`
- `starts_with`
- `ends_with`

## Regras de correspondência

- `ignore_case_identifier` e `ignore_case_data` são opções true/false
- `listen_for_identifier` aceita o curinga `*` (corresponde sempre)
- `listen_for_data` aceita o curinga `*` (corresponde sempre)
- `fire_for_player` usa seletores de jogador comuns (por exemplo, `@a`, `@p`, `Player761`)

## Comandos ao acionar

`commands_to_execute_on_fire` é um único campo de texto.

- Separe vários comandos com `|||`
- Escape um separador literal como `\|\|\|`

Você pode usar dois marcadores especiais, que serão substituídos imediatamente antes da execução dos comandos:

- `%fm_sender%` -> jogador que enviou os Dados do FM
- `%fm_data%` -> valor recebido do cliente

Os comandos são executados como comandos do servidor.

## Exemplos de comandos

Reaja ao pressionamento de um botão por qualquer jogador:

```mcfunction
/fmdata listener add button_ping equals equals false false @a ui.button pressed "tellraw @a {\"text\":\"%fm_sender% pressed the button\"}"
```

Execute vários comandos quando os dados contiverem `gold`:

```mcfunction
/fmdata listener add reward equals contains false true @a reward "gold" "say Reward from %fm_sender%: %fm_data%|||effect give %fm_sender% minecraft:speed 3 1 true"
```

# Dados de boas-vindas

Os dados de boas-vindas enviam Dados do FM aos jogadores correspondentes quando eles entram no servidor.

Gerencie as entradas com:

- `/fmdata welcome_data list`
- `/fmdata welcome_data add ...`
- `/fmdata welcome_data edit ...`
- `/fmdata welcome_data remove ...`

## Sintaxe para adicionar/editar

```mcfunction
/fmdata welcome_data add <unique_welcome_data_name> <target_player> <data_identifier> <string_data>
```

```mcfunction
/fmdata welcome_data edit <welcome_data_name> <target_player> <data_identifier> <string_data>
```

## Sintaxe para remover

```mcfunction
/fmdata welcome_data remove <welcome_data_name>
```

Observações:

- `<target_player>` aceita seletores comuns, como `@a`, `@p` e `@s`
- Os dados são enviados aos jogadores correspondentes quando eles entram
- As entradas são salvas e carregadas automaticamente

## Exemplos de comandos

Envie dados de boas-vindas a todos os jogadores que entrarem:

```mcfunction
/fmdata welcome_data add welcome_all @a hud.welcome "Welcome!"
```

Envie dados de boas-vindas a apenas um jogador:

```mcfunction
/fmdata welcome_data add welcome_vip Player761 hud.vip "VIP perks enabled"
```

# Exportar para IA

Para pedir ajuda à Alice ou a outra IA, exporte os listeners e os dados de boas-vindas do servidor com [Exportar para IA](/export-for-ai#servers):

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

`copy` envia uma mensagem no chat. Ao clicar nela, o conteúdo da exportação é copiado. `file` salva o conteúdo no servidor, em `fancymenu_data/ai_exports/`.

# Boas práticas

1. Use identificadores claros, como `hud.food`, `menu.shop.open` e `quest.progress`.
2. Mantenha um formato de dados consistente para cada identificador.
3. Comece pelo básico: teste com `/fmdata send` antes de criar listeners complexos.
4. Use `@a` somente quando quiser que a ação seja global.
5. Use `/fmdata listener list` e `/fmdata welcome_data list` para manter as configurações organizadas.
