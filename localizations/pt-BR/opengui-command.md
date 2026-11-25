---
title: Abrir GUIs por comando
description: Como abrir GUIs vanilla e personalizadas por comando.
sourceBlobSha: 9d0c8fbc3fa1d1cb15dc19e94f1f0fc1ba37ae05
---

# Abrir GUIs por comando

O comando `/openguiscreen` abre GUIs vanilla, de mods e [personalizadas](/custom-guis). Ele pode ser usado para abrir GUIs para outros jogadores quando o FancyMenu está instalado no servidor e nos clientes deles.

Para abrir uma GUI, use `/openguiscreen <screen_identifier> [<target_players>]`.

Substitua `<screen_identifier>` pelo identificador exato, respeitando maiúsculas e minúsculas, da GUI personalizada ou da tela vanilla/de um mod.

Para encontrar um identificador, abra a tela desejada e ative a sobreposição de depuração com **CTRL + ALT + D**. Selecione o identificador na primeira linha para copiá-lo. Consulte [Identificadores de tela](/screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omita `[<target_players>]` para abrir a GUI para você ou use o nome de um jogador ou um seletor, como `@a`, para abri-la para um ou mais jogadores. O uso do argumento de destino exige o nível de permissão 2 (Mestre do jogo / OP nível 2), mesmo que ele indique você mesmo, e todos os jogadores de destino precisam ter o FancyMenu instalado no cliente.

Nem todas as telas de mods podem ser criadas diretamente. O FancyMenu exibe um erro quando a tela desejada não é compatível. Em um layout local, use [**Imitar botão vanilla/de mod**](/action-scripts#mimic-vanillamod-button) no widget que normalmente abre essa tela.

# Fechar GUIs por comando

Caso raro em que isso seja necessário, `/closeguiscreen [<target_players>]` fecha a tela atual. Se o destino for omitido, o comando afeta você; o uso do argumento de destino exige o nível de permissão 2.
