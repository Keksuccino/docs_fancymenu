---
title: Comandos
description: Os comandos do FancyMenu e como usá-los.
---

# Comandos

O FancyMenu adiciona alguns comandos ao jogo que podem ser muito úteis quando combinados com outros mods, como o FTB Quests.

> O FancyMenu precisa estar no **SERVIDOR** (e no cliente) para usar comandos no Multijogador!
{.is-warning}

## /openguiscreen

O comando `/openguiscreen` permite abrir uma GUI (vanilla/mod e GUIs personalizadas).
Ele pode até abrir GUIs remotamente para outros jogadores quando o FancyMenu está instalado tanto no servidor quanto nos clientes.

Para uma descrição mais detalhada deste comando, confira a página [Abrir GUIs por Comando](/opengui-command).

Este comando não funcionará com todas as telas, especialmente telas de mods. Se o comando falhar ao abrir uma tela, ele exibirá um erro. Não há muito o que fazer nesse caso, porque provavelmente é uma tela complexa demais para ser aberta automaticamente pelo FancyMenu.

Também não vou mais adicionar compatibilidade manualmente para telas de mods, porque adicionar compatibilidade para todos os mods existentes me levaria uma eternidade, desculpe.

**Uso:** `/openguiscreen <screen_identifier> <target_player>`

## /closeguiscreen

O comando `/closeguiscreen` permite fechar a GUI atual.

Hã? Isso é totalmente inútil, você diz?
Bem, sim, mas na verdade não.

Esse comando é útil quando se usam mods que acionam comandos em ações específicas.
Então sim, esse comando é absolutamente inútil quando usado sem outros mods, mas pode ser muito útil se você tiver os mods certos instalados!

**Uso:** `/closeguiscreen <target_player>`

## /fmvariable

O comando `/fmvariable` permite definir e obter variáveis do FancyMenu.

Para executar este comando como outro jogador em servidores, você pode usar o comando vanilla `/execute as`.
Então, digamos que você queira executar o comando `/fmvariable` como o jogador `ExamplePlayer`. Nesse caso, você digitaria:
`/execute as ExamplePlayer run fmvariable...`.

**Uso:** `/fmvariable <get_or_set> <variable_name> [<set_to_value>] [<send_chat_feedback>]`

### Obter
Para **obter o valor de uma variável**, use o subcomando `get` assim:
`/fmvariable get some_variable`

Então o valor dessa variável será exibido no seu chat.

### Definir
Para **definir uma variável**, use o subcomando `set` assim:
`/fmvariable set some_variable new_value true`

O último argumento aqui serve para definir se você quer receber retorno no chat, ou seja, se deseja que este comando exiba mensagens no seu chat.
