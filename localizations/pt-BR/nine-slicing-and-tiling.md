---
title: Nine-Slicing e Tile
description: Redimensione texturas com bordas ou repita texturas sem emendas.
---

# Nine-Slicing e Tile

Nine-slicing preserva os cantos e bordas de uma textura enquanto estica seu centro. Tile repete uma textura em vez de esticá-la.

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png" alt="Regiões de nine-slice" style="max-width:500px;height:auto;" />

# Suporte a Nine-Slicing

| Área | Destinos compatíveis |
|---|---|
| Widgets | Texturas de [Button](./elements#button) e [Slider](./elements#slider); [estilos globais de botão e slider](./global-customizations#button-visuals) |
| Imagens e painéis | [Elementos de imagem](./elements#image) |
| Barras de progresso | [Texturas de preenchimento e fundo](./elements#progress-bar) |
| Tooltips | [Texturas de fundo personalizadas](./elements#tooltip) |

# Configurando Nine-Slicing

1. Defina a textura de destino.
2. Ative a opção **Nine-Slice**.
3. Defina os tamanhos das bordas para corresponder à área fixa da borda na textura de origem.
4. Redimensione o elemento e ajuste os valores das bordas se os cantos ou as bordas ficarem distorcidos.

As configurações de Button e Image usam tamanhos de borda X/Y. Barras de Progresso e Tooltips expõem valores de borda separados quando necessário.

# Suporte a Tile

Texturas repetidas estão disponíveis para:

- [Elementos de imagem](./elements#image).
- [Planos de fundo de imagem do menu](./menu-backgrounds).
- [Texturas de cabeçalho e rodapé de listas roláveis](./customizing-scrollable-screens).

Ative **Repeat Texture** em um elemento de imagem ou em um plano de fundo de imagem. Para telas roláveis, use as opções de repetição no menu de personalização do cabeçalho/rodapé.

Use uma textura de origem sem emendas; bordas que não se alinham criam linhas visíveis entre os tiles.

Nine-slicing e repetição são modos separados. Se ambas as opções forem exibidas para um destino, escolha a que corresponde ao comportamento de escalonamento desejado.
