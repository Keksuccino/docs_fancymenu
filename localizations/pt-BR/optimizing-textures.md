---
title: Otimizando Texturas
description: Como otimizar texturas para o FancyMenu.
---

# Otimizando Texturas para o FancyMenu

O FancyMenu usa as texturas que você fornece como estão, o que significa que ele **não** compacta, reduz nem amplia seus arquivos de imagem. Para garantir que seus menus tenham boa aparência e desempenho, é importante otimizar suas texturas ao usá-las na sua interface.

# Dicas Principais para Otimização de Texturas

As dicas a seguir são as etapas básicas mais importantes que você deve ter em mente ao trabalhar com texturas no FancyMenu.

## 1. Use a Resolução Correta
- **Evite imagens de baixa resolução**: Se uma imagem for pequena demais e for esticada para caber em uma área maior, ela pode ficar borrada.
- **Evite exagerar na alta resolução**: Texturas muito grandes exibidas em um tamanho pequeno também podem parecer distorcidas ou "estranhas" e podem desperdiçar desempenho.

> 📌 **Dica:** Use texturas na resolução em que elas aparecerão no menu, ou próxima dela.
{.is-info}

## 2. Preserve a Proporção
- Sempre mantenha a proporção da imagem ao redimensioná-la.
- Esticar uma imagem de forma desproporcional pode causar artefatos visuais e uma aparência ruim.

> 📌 **Dica:** Você pode clicar com o botão direito nos elementos de Imagem e selecionar **Restaurar Proporção** para redimensioná-los para a proporção correta. Depois, ao redimensioná-los manualmente, segure **SHIFT** enquanto redimensiona para fazer com que o redimensionamento respeite a proporção do elemento.
{.is-info}

## 3. Considere Nine-Slicing e Tiling
- Para elementos de interface escaláveis (como painéis ou botões), use os recursos de [Nine-Slicing e Tiling](/nine-slicing-and-tiling) do FancyMenu.
- Isso garante que as bordas das texturas permaneçam nítidas quando redimensionadas.
