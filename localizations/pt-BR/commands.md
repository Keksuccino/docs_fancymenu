---
title: Comandos
description: Os comandos do FancyMenu e como usá-los.
---

# Comandos

O FancyMenu adiciona alguns comandos ao jogo que podem ser muito úteis ao combiná-los com outros mods, como o FTB Quests.

> [!WARNING]
> O FancyMenu precisa estar no **SERVIDOR** (e no cliente) para usar comandos no Multiplayer!

## Jogadores-alvo e permissões

O argumento de jogador-alvo de `/openguiscreen`, `/closeguiscreen` e `/fmlayout` é opcional. Quando um jogador o omite, o comando afeta esse próprio jogador. Quando um alvo é fornecido, podem ser usados nomes normais de jogadores e seletores como `@a`.

- Fornecer o argumento de alvo para `/openguiscreen` ou `/closeguiscreen` exige **nível de permissão 2** (Game Master / nível OP 2), mesmo que ele aponte para a origem do comando.
- Fornecer o argumento de alvo para `/fmlayout` exige **nível de permissão 3** (Admin / nível OP 3), mesmo que ele aponte para a origem do comando.
- Todos os subcomandos de `/fmdata` exigem **nível de permissão 2** (Game Master / nível OP 2).

Para os três comandos com alvos opcionais, omitir o alvo só funciona quando a origem do comando é um jogador. O console do servidor deve fornecer um alvo e atender ao requisito de permissão do argumento de alvo.

## /openguiscreen

O comando `/openguiscreen` abre uma GUI Vanilla, de mod ou [GUI Personalizada](./custom-guis). Ele pode apontar para outros jogadores quando o FancyMenu estiver instalado no servidor e nos clientes deles.

Consulte [Abrindo GUIs por Comando](./opengui-command) e [Identificadores de Tela](./screen-identifiers).

Nem toda tela de mod pode ser criada diretamente. O FancyMenu mostra um erro quando uma tela de destino não é compatível. Em um layout local, use [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) no widget que normalmente a abre.

**Uso:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

O comando `/closeguiscreen` fecha a tela atual para a origem do comando ou para os jogadores selecionados. Ele é útil com mods de missões, eventos ou automação que podem executar comandos.

**Uso:** `/closeguiscreen [<target_players>]`

## /fmlayout

O comando `/fmlayout` define se um layout está ativado em um ou mais clientes. Use o nome do layout exatamente como ele aparece no FancyMenu e coloque entre aspas nomes que contenham espaços.

**Uso:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Exemplos:

- `/fmlayout quest_complete true` ativa `quest_complete` para o jogador que está executando o comando.
- `/fmlayout quest_complete false @a` desativa isso para todos os jogadores online. Fornecer o argumento de alvo exige nível de permissão 3.

## /fmvariable

O comando `/fmvariable` define e lê [variáveis do FancyMenu](./variables).

Para executar este comando como outro jogador, use o comando `/execute as` do Vanilla:
`/execute as ExamplePlayer run fmvariable ...`

**Uso:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Get

Para **obter o valor de uma variável**, use o subcomando `get` assim:
`/fmvariable get some_variable`

Então o valor dessa variável será exibido no chat.

### Set

Para **definir uma variável**, coloque o booleano de feedback no chat antes do novo valor:
`/fmvariable set some_variable true new_value`

O argumento `send_chat_feedback` controla se o FancyMenu confirma a alteração no chat. O argumento `set_to_value` consome o restante do comando, então o valor pode conter espaços. Por exemplo, `/fmvariable set greeting false Hello from FancyMenu` armazena `Hello from FancyMenu` sem enviar feedback de sucesso.

## /fmdata

O comando `/fmdata` envia dados personalizados entre o servidor e os clientes do FancyMenu, gerencia listeners no lado do servidor e configura os dados enviados quando os jogadores entram. Todos os subcomandos de `/fmdata` exigem nível de permissão 2.

Consulte [FM Data](./fm-data) para todos os subcomandos, sintaxe e exemplos.
