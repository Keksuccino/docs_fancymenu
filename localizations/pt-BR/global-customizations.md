---
title: Customizações Globais
description: Aplique ajustes globais do FancyMenu que afetam todas as telas.
---

# Customizações Globais

As Customizações Globais são ajustes do FancyMenu que se aplicam à interface do jogo como um todo.
Use-as quando quiser um estilo/comportamento consistente em todos os lugares, em vez de editar o layout de cada tela separadamente.

> [!INFO]
> Ao contrário da maioria dos recursos de personalização do FancyMenu, as Customizações Globais funcionam mesmo se as personalizações normais de tela estiverem desativadas.
> Elas não exigem ativar personalizações por tela, o que significa que uma única mudança pode afetar todas as telas imediatamente.

Exemplos comuns:

- Use um único estilo compartilhado de botão e slider para todas as telas.
- Substitua globalmente o fundo do menu, o panorama e a música do menu.
- Aplique globalmente o comportamento de inicialização/janela (escala da GUI, tela cheia, título/ícone da janela).
- Substitua globalmente as texturas de botões do vanilla sem usar um pacote de recursos.
- Substitua globalmente a música do menu do vanilla sem usar um pacote de recursos.

# Onde Encontrá-las

Abra a **barra de menu** do FancyMenu enquanto **não** estiver no editor de layout e depois vá em **Customization -> Global Customizations**.

# Início Rápido

1. Abra **Customization -> Global Customizations**.
2. Escolha uma categoria para começar (por exemplo, **Custom Button Textures**).
3. Configure as opções dessa categoria (seletores de recursos, alternâncias ou campos numéricos).
4. Teste o resultado em várias telas.
5. Ajuste finamente as configurações relacionadas (por exemplo, transparência, estilos de rótulo, bordas nine-slice).

# O Que Você Pode Personalizar

## Comportamento global e inicialização

- **Game Intro** (um vídeo ou animação de introdução que é reproduzido antes de a tela de título aparecer)
- **Singleplayer Screen World Icons**
- **Multiplayer Screen Server Icons**
- **Seamless World Loading** (usa uma captura de tela do mundo como fundo da tela de carregamento do mundo)
- **Custom Window Icon**
- **Custom Window Title**
- **Default GUI Scale**
- **Force Fullscreen on Launch**

## Visual dos botões

- **Custom Button Textures** (estados Normal/Hover/Inactive, modo transparente, nine-slice + tamanhos de borda)
- **Button Labels** (sublinhado ao passar o mouse, cor base/em hover, escala, sombra)

## Visual dos sliders

- **Custom Slider Textures**
- **Slider Background Texture** (textura, modo transparente, nine-slice + tamanhos de borda)
- **Slider Handle Textures** (estados Normal/Hover/Inactive, nine-slice + tamanhos de borda)
- **Slider Labels** (sublinhado ao passar o mouse, cor base/em hover, escala, sombra)

## Visual e áudio do menu

- **Custom Menu Background Texture**
- **Custom Menu Background Panorama**
- **Play Vanilla Menu Music** (ativar/desativar a reprodução da música do menu do vanilla)
- **Custom Menu Music Tracks**
- **Custom Button/Slider Click Sound**

# Custom Menu Music Tracks

Use **Custom Menu Music Tracks** para montar uma lista aleatória de faixas para os menus.

As faixas personalizadas configuradas substituem a música do menu do vanilla nos menus.

- Abra **Custom Menu Music Tracks** para abrir **Manage Menu Music Tracks**.
- Use **Add Track** para adicionar fontes de áudio.
- Use **Remove Track** para remover uma entrada.
- Use **Clear Tracks** para remover todas as entradas.
