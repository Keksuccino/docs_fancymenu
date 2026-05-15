---
title: Abrir GUIs por Comando
description: Como abrir GUIs Vanilla e personalizadas via comando.
---

# Abrindo GUIs por Comando

O FancyMenu vem com um comando que permite abrir GUIs Vanilla e personalizadas via comando.
Você até pode abrir GUIs remotamente para **outros jogadores** ao instalar o FancyMenu tanto no **servidor quanto nos clientes**.

Para abrir uma GUI, basta usar o comando `/openguiscreen <screen_identifier> <target_player>`.

Substitua `<screen_identifier>` pelo identificador real do menu da GUI que você quer abrir.
Isso pode ser o identificador da sua GUI personalizada (criada com o FancyMenu) ou o identificador normal de um menu Vanilla/mod.

Para obter o **identificador do menu de GUIs Vanilla/mod**, abra o menu do qual você quer saber o identificador e ative a **sobreposição de depuração** do FancyMenu em **Customization -> Debug Overlay**; depois, você pode clicar no identificador exibido na primeira linha para copiá-lo para a sua área de transferência.

![copy_identifier](https://github.com/Keksuccino/FancyMenu/assets/35544624/dd6c53d9-d2bd-4810-be03-3741e326bd5a)

Deixe o argumento `<target_player>` vazio para abrir a GUI no seu cliente ou escolha um jogador (ou vários jogadores) para abrir a GUI.
Lembre-se de que o outro jogador também precisa ter o FancyMenu instalado no cliente dele.

Este comando não funcionará para todas as telas, especialmente telas de mods. Se o comando falhar ao abrir uma tela, ele mostrará um erro. Não há muito o que fazer nesse caso, porque provavelmente é uma tela complexa demais para ser aberta automaticamente pelo FancyMenu.

Também não vou mais adicionar manualmente compatibilidade para telas de mods, porque adicionar compatibilidade para todos os mods existentes levaria uma eternidade, desculpe.

# Fechando GUIs por Comando

No caso raro em que você precisar, também existe o comando `/closeguiscreen <target_player>` que fecha a tela atual.
