---
title: Identificadores de tela
description: Sobre identificadores de tela e como encontrar o identificador de uma tela.
sourceBlobSha: 64414e10bf5f532e075373a6a753e2f667448ceb
---
# Identificadores de tela

O FancyMenu usa identificadores de tela para layouts, widgets do Vanilla, [ações de tela](/action-scripts#open-screen-or-custom-gui) e [substituições de GUI personalizada](/custom-guis#overriding-an-existing-screen). Os identificadores diferenciam maiúsculas de minúsculas, então copie-os exatamente como aparecem na sobreposição de depuração.

As telas integradas normalmente usam um identificador universal curto, como `title_screen`. Outras telas de mods podem usar o nome da classe Java. GUIs personalizadas usam o identificador definido no gerenciador. Esses são identificadores de tela do FancyMenu, não localizações de recursos do Minecraft.

# Como encontrar o identificador de uma tela

Você pode ver o identificador do menu ativo no momento usando a **sobreposição de depuração**.
Ela mostra o identificador da tela atual e permite copiá-lo para a área de transferência clicando nele com o botão esquerdo do mouse.

>[!TIP]
>Você pode ativar a **sobreposição de depuração** pressionando **CTRL + ALT + D** enquanto **não** estiver no editor de layout.

<br>

<img width="553" alt="Captura de tela 3" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/1800351e-f042-4826-8eed-7725b78bc84d">

<br>

<img width="579" alt="Captura de tela 4" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/9e0d1e61-7f2d-4817-9be1-b63ee61978dd">

# Abrindo telas

A ação [**Abrir tela ou GUI personalizada**](/action-scripts#open-screen-or-custom-gui) só pode abrir telas que o FancyMenu consiga criar no estado atual do jogo. Algumas telas exigem que um mundo esteja carregado, uma conexão ativa, um jogador presente ou uma tela original de origem.

Se o FancyMenu não conseguir criar a tela usando o identificador, ele exibirá um erro. Use [**Imitar botão do Vanilla/mod**](/action-scripts#mimic-vanillamod-button) no widget que normalmente abre a tela.
