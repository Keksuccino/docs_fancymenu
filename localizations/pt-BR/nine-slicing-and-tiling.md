---
title: Nine-Slicing e Tiling
description: Como usar nine-slicing e tiling no FancyMenu.
---

# Nine-Slicing e Tiling

Ao criar menus legais no Minecraft com o FancyMenu, talvez você queira usar imagens que precisem ser redimensionadas corretamente ou repetidas em padrões. Este guia explica como usar **Nine-Slicing** e **Tiling** (também chamado de texturas repetidas) para deixar seus menus incríveis!

# O que é Nine-Slicing?

Nine-slicing é uma técnica que permite esticar uma imagem para qualquer tamanho sem deixá-la com aparência estranha. Ela funciona dividindo sua imagem em nove partes (como um jogo da velha). Os cantos permanecem do mesmo tamanho, as bordas se esticam em uma direção e o centro se estica nas duas direções.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Exemplo de Nine-Slice" style="max-width: 500px; height: auto;" />

## Onde posso usar Nine-Slicing?

No FancyMenu, o Nine-Slicing está disponível para:
- **Elementos de Botão** (tanto botões personalizados quanto ao editar botões do Vanilla)
- **Texturas de Barra de Progresso** (texturas da barra e do fundo)

## Como usar Nine-Slicing com Botões

1. **Crie ou selecione um Elemento de Botão** no editor de layout.
2. Clique com o botão direito no botão e procure a opção "Button Textures".
3. Defina as texturas de fundo do botão (estados normal, hover e inativo).
4. Ative a opção "Nine-Slice Custom Background".
5. Defina as **Nine-Slice Background X-Borders** (tamanho das bordas esquerda e direita).
6. Defina as **Nine-Slice Background Y-Borders** (tamanho das bordas superior e inferior).

### Dicas para Nine-Slicing em Botões

- Use uma imagem com bordas e cantos bem definidos.
- Os valores de borda (X e Y) informam ao FancyMenu quantos pixels de cada extremidade devem ser tratados como borda.
- Um valor típico pode ser 5 pixels tanto para as bordas X quanto Y.
- Os cantos sempre permanecerão do mesmo tamanho, enquanto as partes centrais se esticarão para preencher o botão.

# O que é Tiling?

Tiling (também chamado de texturas repetidas) permite preencher uma área grande com uma imagem pequena, repetindo-a como azulejos em um piso. Isso é perfeito para fundos ou imagens grandes em que você quer que um padrão continue.

## Onde posso usar Tiling?

No FancyMenu, o Tiling está disponível para:
- **Elementos de Imagem**
- **Fundos de Menu de Imagem**

## Como usar Tiling com Elementos de Imagem

1. **Crie ou selecione um Elemento de Imagem** no editor de layout.
2. Clique com o botão direito na imagem e procure "Image Source" para definir sua textura.
3. Encontre e ative a opção **"Repeat Texture"**.
4. Redimensione seu elemento de imagem para ver a textura se repetir e preencher o espaço.

## Como usar Tiling com Fundos de Menu

1. Abra **Menu Backgrounds** no menu de contexto de fundo do editor de layout.
2. Escolha o tipo de fundo **Image**.
3. Selecione sua imagem de fundo.
4. Ative a opção **"Repeat Texture"**.
5. Seu fundo agora repetirá a textura para preencher toda a tela.

# Criando Boas Texturas para Nine-Slicing e Tiling

## Para Nine-Slicing:
- Crie texturas com bordas e cantos bem definidos.
- Certifique-se de que suas bordas estejam claras e com largura consistente.
- Teste diferentes tamanhos de borda para encontrar o que funciona melhor.
- Botões geralmente funcionam bem com bordas de 3 a 5 pixels.

## Para Tiling:
- Crie texturas contínuas que possam se conectar consigo mesmas em todos os lados.
- Mantenha os padrões simples para evitar confusão visual.
- Teste sua textura repetindo-a primeiro em uma área pequena.

# Exemplos

## Exemplo de Botão com Nine-Slice
Um botão simples pode começar como uma imagem de 30x30 com bordas de 5 pixels em todos os lados. Quando você torna o botão maior, os cantos permanecem com 5x5 pixels, enquanto as bordas e o centro se esticam para se ajustar ao tamanho do botão.

## Exemplo de Fundo em Tiling
Um pequeno tile de 64x64 com um padrão discreto pode ser repetido para preencher todo o fundo do seu menu, independentemente do tamanho da tela.

# Problemas Comuns e Soluções

## Meu botão com nine-slicing parece esticado ou distorcido:
- Seus valores de borda podem estar muito pequenos ou muito grandes
- Tente alterar os valores de borda para combinar com sua textura real

## Meu fundo com tiling tem emendas visíveis:
- Sua textura não é contínua
- Tente editar sua imagem para garantir que as bordas se encaixem perfeitamente

## Minhas texturas ficam borradas quando redimensionadas:
- Use texturas de maior resolução
- Mantenha seus designs simples, com linhas limpas

# Lembre-se

- **Nine-Slicing** é perfeito para elementos de UI que precisam mudar de tamanho sem perder a aparência (como botões).
- **Tiling** é ótimo para preencher áreas grandes com um padrão (como fundos).
- Ambos os recursos ajudam sua interface a ficar bonita em qualquer resolução ou tamanho de tela!

Agora vá criar menus incríveis no Minecraft com botões perfeitamente esticados e belos fundos em tiling!
