---
title: Abrir GUIs por Comando
description: Como abrir GUIs Vanilla e personalizadas via comando.
---

# Abrindo GUIs por Comando

O comando `/openguiscreen` abre GUIs Vanilla, de mods e [GUIs Personalizadas](./custom-guis). Ele pode ser usado para outros jogadores quando o FancyMenu estiver instalado no servidor e nos clientes deles.

Para abrir uma GUI, use `/openguiscreen <screen_identifier> [<target_players>]`.

Substitua `<screen_identifier>` pelo identificador exato e sensível a maiúsculas e minúsculas da GUI Personalizada ou da tela Vanilla/de mod.

Para encontrar um identificador, abra a tela desejada e ative a sobreposição de depuração com **CTRL + ALT + D**. Selecione o identificador na primeira linha para copiá-lo. Veja [Identificadores de Tela](./screen-identifiers).

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Omitir `[<target_players>]` abre a GUI para você. Você também pode usar o nome de um jogador ou um seletor, como `@a`, para abri-la para um ou mais jogadores. Informar o argumento de destino requer nível de permissão 2 (Game Master / OP nível 2), mesmo que o alvo seja você mesmo, e cada jogador alvo precisa ter o FancyMenu instalado no cliente.

Nem toda tela de mod pode ser criada diretamente. O FancyMenu mostra um erro quando a tela de destino não é compatível. Em um layout local, use [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) no widget que normalmente a abriria.

# Fechando GUIs por Comando

No caso raro de você precisar, `/closeguiscreen [<target_players>]` fecha a tela atual. Ele afeta você quando o alvo é omitido; informar o argumento de destino requer nível de permissão 2.
