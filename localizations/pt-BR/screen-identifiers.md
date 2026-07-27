---
title: Identificadores de Tela
description: Sobre identificadores de tela e como encontrar o identificador de uma tela.
---
# Identificadores de Tela

O FancyMenu usa identificadores de tela para layouts, widgets da Vanilla, [ações de tela](./action-scripts#open-screen-or-custom-gui-opengui) e [substituições de GUI Personalizadas](./custom-guis#overriding-an-existing-screen). Os identificadores diferenciam maiúsculas de minúsculas, então copie-os exatamente do overlay de depuração.

As telas встроídas normalmente usam um identificador universal curto, como `title_screen`. Outras telas de mods podem usar o nome da classe Java. GUIs Personalizadas usam o identificador informado no gerenciador delas. Estes são identificadores de tela do FancyMenu, não localizadores de recursos do Minecraft.

# Encontrando o Identificador de uma Tela

Você pode ver o identificador do menu atualmente ativo usando o **overlay de depuração**.
Ele contém o identificador da tela atual e permite copiá-lo para a área de transferência com um clique esquerdo.

>[!TIP]
>Você pode ativar o **overlay de depuração** pressionando **CTRL + ALT + D** enquanto você **não** estiver no editor de layout.

<br>

<img width="553" alt="Screenshot_3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Screenshot_4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Abrindo Telas

A [ação **Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) pode abrir apenas telas que o FancyMenu consegue construir no estado atual do jogo. Algumas telas exigem um mundo carregado, conexão, jogador ou a tela pai original.

Se o FancyMenu não conseguir construir o identificador, ele exibirá um erro. Use [**Mimic Vanilla/Mod Button**](./action-scripts#mimic-vanillamod-button-mimicbutton) no widget que normalmente abre a tela.
