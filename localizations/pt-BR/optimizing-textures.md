---
title: Otimizando Texturas
description: Como otimizar texturas para o FancyMenu.
---

# Otimizando Texturas para o FancyMenu

O FancyMenu usa as texturas que você fornece exatamente como elas são, ou seja, ele **não** comprime, reduz ou amplia seus arquivos de imagem. Para garantir que seus menus fiquem nítidos e tenham bom desempenho, é importante otimizar suas texturas ao usá-las na interface.

# Dicas Principais para Otimização de Texturas

As dicas a seguir são os passos básicos mais importantes que você deve ter em mente ao trabalhar com texturas no FancyMenu.

## 1. Use a Resolução Correta
- **Evite imagens em baixa resolução**: Se uma imagem for pequena demais e for esticada para caber em uma área maior, ela pode ficar borrada.
- **Evite exagerar na resolução**: Texturas muito grandes exibidas em um tamanho pequeno também podem parecer distorcidas ou "estranhas" e podem desperdiçar desempenho.

> [!NOTE]
> 📌 **Dica:** Use texturas na resolução em que elas serão exibidas no menu, ou próxima dela.

## 2. Preserve a Proporção
- Sempre mantenha a proporção da imagem ao redimensioná-la.
- Esticar uma imagem de forma desproporcional pode gerar artefatos visuais e deixar a aparência ruim.

> [!NOTE]
> 📌 **Dica:** Você pode clicar com o botão direito nos elementos de Imagem e clicar em **Restaurar Proporção** para redimensioná-los até a proporção correta. Depois, ao redimensioná-los manualmente, segure **SHIFT** enquanto redimensiona para que o redimensionamento respeite a proporção do elemento.

## 3. Considere Nine-Slicing e Tiling
- Para elementos de UI escaláveis (como painéis ou botões), use os recursos de [Nine-Slicing & Tiling](/nine-slicing-and-tiling) do FancyMenu.
- Isso garante que as bordas das texturas permaneçam nítidas quando forem redimensionadas.
