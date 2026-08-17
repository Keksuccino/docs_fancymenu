---
title: Imagens
description: Tudo o que é importante sobre recursos de imagem no FancyMenu.
---
# Imagens

O FancyMenu oferece suporte a recursos de imagem em vários lugares, como planos de fundo de menus, texturas de botões e muito mais.

Você pode usar arquivos de imagem PNG, JPEG, GIF e APNG no FancyMenu, mas é recomendável usar PNG para imagens estáticas sempre que possível. Para animações, em vez de usar GIF e APNG, é melhor usar [um arquivo AFMA](/fma), o próprio tipo de imagem animada do FancyMenu, pois os arquivos AFMA são muito mais otimizados do que GIF/APNG, usam menos RAM e têm um impacto menor no desempenho.

# Convertendo imagens para formatos compatíveis

Quando precisar converter imagens para um dos formatos compatíveis com o FancyMenu, ou simplesmente quiser converter um formato compatível para outro por vários motivos, confira a lista a seguir de sites que funcionam bem para converter imagens online, sem a necessidade de baixar nenhum software.

## GIF para APNG
Para converter uma imagem GIF para APNG, use este site: https://ezgif.com/gif-to-apng.

## APNG para GIF
Para converter um APNG para GIF, é disso que você precisa: https://ezgif.com/apng-to-gif.

## MP4 para APNG
Caso precise converter uma sequência curta de vídeo para APNG, experimente este site: https://ezgif.com/video-to-apng

## PNG para JPEG
Às vezes, usar JPEG pode tornar os recursos menores. Nesse caso, pode ser uma boa ideia usar JPEG em vez de PNG: https://www.freeconvert.com/png-to-jpeg. Lembre-se de que arquivos JPEG não oferecem suporte a transparência.

## JPEG para PNG
Para o caso comum de converter JPEG para PNG, experimente este site: https://jpg2png.com/

## WebP para PNG
Arquivos WebP não são compatíveis com o FancyMenu, então você precisa convertê-los para PNG: https://convertio.co/webp-png/

# Limitações de texturas animadas

O FancyMenu usa seu próprio [formato AFMA](/fma) para animações otimizadas, permitindo que [arquivos AFMA](/fma) tenham muitos quadros em alta resolução. No entanto, para formatos de arquivo animado mais antigos, como GIF e APNG, você deve seguir os limites recomendados abaixo para não encher demais a sua RAM nem prejudicar excessivamente o desempenho do jogo:

- Use no máximo **200 quadros** por animação.
- Use uma resolução máxima de **1080p** para os seus quadros.
- Você não deve ultrapassar um total de **1000 quadros para TODAS as animações combinadas**, pois, mesmo que use apenas 200 quadros por animação, todos eles serão carregados na memória. Portanto, usar muitas animações ao mesmo tempo ainda pode esgotar a sua RAM.

> [!IMPORTANT]
> Esses limites NÃO se aplicam a [arquivos AFMA](/fma), pois os arquivos AFMA não carregam todos os seus quadros na memória e são muito mais otimizados. Portanto, eles não causarão um impacto tão grande no desempenho quanto os formatos de animação mais antigos.
