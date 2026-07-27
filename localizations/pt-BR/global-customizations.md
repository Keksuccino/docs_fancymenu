---
title: Customizações Globais
description: Aplique ajustes globais do FancyMenu que afetam todas as telas.
---

# Customizações Globais

As Customizações Globais aplicam configurações compartilhadas de interface e inicialização sem editar o layout de cada tela. Elas funcionam mesmo quando a personalização normal de telas está desativada.

Exemplos comuns:

- Use um único estilo compartilhado de botão e slider para todas as telas.
- Substitua globalmente o plano de fundo do menu, o panorama e a música do menu.
- Aplique o comportamento global de inicialização/janela (escala da GUI, tela cheia, título/ícone da janela).
- Substitua globalmente as texturas dos botões do vanilla sem usar um resource pack.
- Substitua globalmente a música do menu do vanilla sem usar um resource pack.

# Onde Encontrar

Abra a **barra de menu** do FancyMenu enquanto **não** estiver no editor de layout e, então, **Personalização -> Customizações Globais**.

# O Que Você Pode Personalizar

## Comportamento global e inicialização

- [**Game Intro**](./game-intro) (um vídeo de introdução ou animação que é reproduzido antes da tela de Título)
- **Ícones de Mundo da Tela de Jogador Individual**
- **Ícones de Servidor da Tela Multijogador**
- [**Carregamento Contínuo do Mundo**](./seamless-world-loading) (usa uma captura de tela recente do mundo como fundo da tela de carregamento)
- [**Ícone Personalizado da Janela**](./window-customization#custom-icon)
- [**Título Personalizado da Janela**](./window-customization#custom-title)
- **Escala Padrão da GUI**
- **Forçar Tela Cheia na Inicialização**

## Aparência dos botões

- **Texturas Personalizadas de Botão** (estados Normal/Sobre/Inativo, modo transparente, [nine-slice](./nine-slicing-and-tiling) + tamanhos de borda)
- **Rótulos dos Botões** (sublinhado ao passar o mouse, cor base/hover, escala, sombra)

## Aparência dos sliders

- **Texturas Personalizadas de Slider**
- **Textura de Fundo do Slider** (textura, modo transparente, [nine-slice](./nine-slicing-and-tiling) + tamanhos de borda)
- **Texturas do Controle do Slider** (estados Normal/Sobre/Inativo, [nine-slice](./nine-slicing-and-tiling) + tamanhos de borda)
- **Rótulos dos Sliders** (sublinhado ao passar o mouse, cor base/hover, escala, sombra)

## Aparência e áudio do menu

- [**Textura Personalizada de Fundo do Menu**](./menu-backgrounds)
- [**Panorama Personalizado de Fundo do Menu**](./panoramas)
- **Reproduzir Música do Menu do Vanilla** (ativar/desativar a reprodução da música do menu do Vanilla)
- [**Faixas de Música Personalizadas do Menu**](./background-music)
- **Som Personalizado de Clique de Botão/Slider**

# Faixas de Música Personalizadas do Menu

Use **Faixas de Música Personalizadas do Menu** para criar uma lista aleatória de faixas para os menus.

> [!IMPORTANT]
> As faixas globais personalizadas do menu tocam somente quando nenhum mundo está carregado, como na tela de Título. Use um elemento [**Áudio**](./elements#audio) para áudio de menu dentro do mundo.

As faixas configuradas usam o canal de som Music e substituem a música do menu do Vanilla em menus sem mundo compatíveis.

- A primeira faixa começa após cerca de cinco segundos.
- As faixas seguintes começam após um atraso aleatório de cerca de um a trinta segundos.
- As faixas são selecionadas aleatoriamente.
- Com várias faixas, a faixa anterior não é selecionada duas vezes seguidas.

Gerencie a lista de faixas em **Faixas de Música Personalizadas do Menu**:

- Abra **Faixas de Música Personalizadas do Menu** para abrir **Gerenciar Faixas de Música do Menu**.
- Use **Adicionar Faixa** para adicionar fontes de áudio.
- Use **Remover Faixa** para remover uma entrada.
- Use **Limpar Faixas** para remover todas as entradas.
