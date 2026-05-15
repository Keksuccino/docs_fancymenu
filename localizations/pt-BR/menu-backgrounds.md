---
title: Fundos de Menu
description: 'Como definir fundos personalizados de menu (imagens, animações) para telas.'
---

# Fundos de Menu

O FancyMenu permite definir fundos personalizados para menus. Você pode usar imagens, texturas animadas, slideshows, panoramas cúbicos, cores, navegadores, vídeos, shaders GLSL e muito mais.

# Definindo um Fundo

No FancyMenu 3.9.0+, a personalização do fundo do menu é feita diretamente pelo menu de contexto do editor de layout:

1. Abra o editor de layout.
2. Clique com o botão direito no fundo do editor.
3. Abra **Fundos de Menu**.
4. Ative e configure o(s) tipo(s) de fundo que você quiser.

Os tipos comuns de fundo incluem:

- Vanilla
- Imagem
- Slideshow
- Panorama Cúbico
- Cor (HEX)
- Navegador
- Vídeo
- Shader GLSL
- Vídeo [MCEF] (obsoleto)
- e mais..

O antigo tipo de fundo **Vídeo [MCEF]** está obsoleto no FancyMenu 3.9.0. Use o novo fundo nativo **Vídeo**, alimentado pelo Watermedia V3, para novos layouts.

# Removendo o Fundo Personalizado

Abra **Fundos de Menu** novamente e desative/remova o tipo de fundo personalizado que você não quer mais. Se nenhum tipo de fundo personalizado estiver ativo, a tela voltará ao comportamento normal de fundo vanilla.

# Empilhando Fundos

O FancyMenu 3.9.0 permite que vários tipos de fundo de menu sejam ativados no mesmo layout. Os fundos ativos são renderizados em pilha, então você pode combinar uma imagem base ou panorama com sobreposições translúcidas, camadas de navegador, camadas de shader, camadas de paralaxe e outros efeitos.

Se você também tiver vários layouts ativos, as pilhas de fundo deles também podem ser combinadas. Para organizar os layouts e fazê-los aparecer em uma ordem específica, clique com o botão direito no fundo do editor e clique em **Índice do Layout**.

# Fundos Transparentes

Como não há nada atrás dos fundos, não é possível tornar transparente o fundo que está na camada mais baixa, porque isso resultaria em falhas gráficas, mas é totalmente possível usar transparência em configurações com fundos empilhados, desde que o de baixo permaneça com opacidade total. Dessa forma, você pode ter camadas de fundo translúcidas sobre a camada inferior.

Para deixar uma imagem de fundo translúcida, use o editor de imagens de sua preferência.

# Fundos de Navegador

O tipo de fundo **Navegador** funciona como o elemento Browser, mas ocupa a tela inteira e recebe foco automaticamente. Isso é útil para conteúdo web em tela cheia, páginas HTML locais ou camadas de vídeo da web.

# Fundos com Shader GLSL

O tipo de fundo **Shader GLSL** renderiza shaders GLSL personalizados e oferece suporte à criação de shaders no estilo Shadertoy. Consulte a página [API de Shader GLSL](/glsl-shader-api) para ver os uniforms suportados e a estrutura do shader.
