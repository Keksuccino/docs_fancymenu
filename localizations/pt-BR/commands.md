---
title: Comandos
description: Os comandos do FancyMenu e como usá-los.
sourceBlobSha: 265258e46a219a12892146238e379af513ff0848
---

# Comandos

O FancyMenu adiciona alguns comandos ao jogo que podem ser muito úteis quando usados em conjunto com outros mods, como o FTB Quests.

> [!WARNING]
> Para usar comandos no modo multijogador, o FancyMenu precisa estar instalado no **SERVIDOR** (e no cliente)!

## Jogadores-alvo e permissões

O argumento de jogador-alvo de `/openguiscreen`, `/closeguiscreen` e `/fmlayout` é opcional. Se o jogador não o informar, o comando afetará esse jogador. Se um alvo for informado, é possível usar nomes de jogadores comuns e seletores como `@a`.

- Informar o argumento de alvo para `/openguiscreen` ou `/closeguiscreen` exige **nível de permissão 2** (Mestre do jogo / OP nível 2), mesmo que o alvo seja quem executou o comando.
- Informar o argumento de alvo para `/fmlayout` exige **nível de permissão 3** (Administrador / OP nível 3), mesmo que o alvo seja quem executou o comando.
- Todos os subcomandos de `/fmdata` exigem **nível de permissão 2** (Mestre do jogo / OP nível 2).

Nos três comandos com alvos opcionais, omitir o alvo só funciona quando quem executa o comando é um jogador. O console do servidor precisa informar um alvo e atender ao requisito de permissão para o argumento de alvo.

## /openguiscreen

O comando `/openguiscreen` abre uma GUI do Vanilla, de um mod ou uma [GUI personalizada](/custom-guis). Ele pode ter como alvo outros jogadores quando o FancyMenu está instalado no servidor e nos clientes deles.

Consulte [Abrir GUIs por comando](/opengui-command) e [Identificadores de tela](/screen-identifiers).

Nem todas as telas de mods podem ser criadas diretamente. O FancyMenu exibe um erro quando a tela-alvo não é compatível. Em um layout local, use [**Imitar botão do Vanilla/mod**](/action-scripts#mimic-vanillamod-button) no widget que normalmente abre essa tela.

**Uso:** `/openguiscreen <screen_identifier> [<target_players>]`

## /closeguiscreen

O comando `/closeguiscreen` fecha a tela atual de quem executa o comando ou dos jogadores selecionados. Ele é útil com mods de missões, eventos ou automação que podem executar comandos.

**Uso:** `/closeguiscreen [<target_players>]`

## /fmlayout

O comando `/fmlayout` define se um layout está ativado em um ou mais clientes. Use o nome do layout exatamente como aparece no FancyMenu e coloque entre aspas os nomes que contêm espaços.

**Uso:** `/fmlayout <layout_name> <true|false> [<target_players>]`

Exemplos:

- `/fmlayout quest_complete true` ativa `quest_complete` para o jogador que executou o comando.
- `/fmlayout quest_complete false @a` desativa o layout para todos os jogadores online. Informar o argumento de alvo exige nível de permissão 3.

## /fmvariable

O comando `/fmvariable` define e consulta [variáveis do FancyMenu](/variables).

Para executar esse comando como outro jogador, use o comando `/execute as` do Vanilla:
`/execute as ExamplePlayer run fmvariable ...`

**Uso:**

- `/fmvariable get <variable_name>`
- `/fmvariable set <variable_name> <send_chat_feedback> <set_to_value>`

### Consultar

Para **consultar o valor de uma variável**, use o subcomando `get` desta forma:
`/fmvariable get some_variable`

O valor dessa variável será exibido no chat.

### Definir

Para **definir uma variável**, coloque o valor booleano de feedback no chat antes do novo valor:
`/fmvariable set some_variable true new_value`

O argumento `send_chat_feedback` controla se o FancyMenu confirma a alteração no chat. O argumento `set_to_value` consome o restante do comando, então o valor pode conter espaços. Por exemplo, `/fmvariable set greeting false Hello from FancyMenu` armazena `Hello from FancyMenu` sem enviar uma mensagem de confirmação.

## /fmdata

O comando `/fmdata` envia dados personalizados entre o servidor e os clientes do FancyMenu, gerencia ouvintes no servidor, configura os dados enviados quando os jogadores entram e exporta essa configuração para [chats de IA](/export-for-ai#servers). Todos os subcomandos de `/fmdata` exigem nível de permissão 2.

Consulte [FM Data](/fm-data) para ver todos os subcomandos, a sintaxe e exemplos.
