---
title: GUIs Personalizadas
description: Como adicionar uma nova tela de GUI ao jogo.
---

# GUIs Personalizadas

O FancyMenu permite personalizar telas de GUI existentes, mas também permite adicionar telas totalmente novas e preenchê-las com elementos.

# Adicionando uma Nova Tela

Para adicionar uma nova tela, navegue até **Personalização -> GUIs Personalizadas -> Gerenciar GUIs Personalizadas**.

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

No próximo menu, clique em **Nova GUI**.

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

Aqui você precisa dar à sua nova GUI um identificador exclusivo e pode personalizar outras partes do comportamento básico da tela.
Quando terminar, pressione **Concluído**.

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

Agora você tem uma nova GUI vazia. Para abri-la, selecione a GUI no menu **Gerenciar GUIs Personalizadas** e clique em **Abrir GUI**.

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

Isso abrirá a tela de GUI ainda bem vazia. Para deixá-la menos vazia, basta criar um novo layout para ela, como faria com qualquer outra tela.

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# Abrindo a GUI via Ação

A última etapa é dar aos usuários normais acesso à sua GUI. A maneira mais fácil de fazer isso é usar a ação **Abrir Tela ou GUI Personalizada** com um botão, slider ou ticker.

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# Abrindo a GUI via Comando

Você também pode abrir sua GUI personalizada por meio de um [comando no jogo](./commands#openguiscreen).
Isso até permite abrir a GUI remotamente para outros usuários!

# Modo Popup

A partir do FancyMenu v3.8.0, as GUIs Personalizadas oferecem suporte a um "Modo Popup" que faz com que elas pareçam um popup sendo aberto sobre outra tela (a tela anterior de onde a GUI Personalizada foi aberta). Essa configuração pode ser ativada individualmente para cada GUI Personalizada em suas configurações.

O FancyMenu 3.9.0 também adiciona uma opção para ativar ou desativar a sobreposição de fundo da tela para GUIs Personalizadas enquanto estiver em um mundo. Use-a quando quiser desativar ou manter o desfoque/escurecimento atrás de uma GUI Personalizada aberta sobre a jogabilidade.
