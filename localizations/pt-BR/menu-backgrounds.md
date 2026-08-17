---
title: Fundos do menu
description: 'Como definir fundos de menu personalizados (imagens, animações) para as telas.'
---
# Fundos do menu

O FancyMenu permite definir fundos personalizados para os menus. Você pode usar imagens, texturas animadas, apresentações de slides, panoramas cúbicos, cores, navegadores, vídeos, shaders GLSL e muito mais.

# Definindo um fundo

A personalização do fundo do menu está disponível no menu de contexto do editor de layout:

1. Abra o editor de layout.
2. Clique com o botão direito no fundo do editor.
3. Abra **Fundos do menu**.
4. Ative e configure os tipos de fundo desejados.

Os tipos de fundo mais comuns incluem:

- Vanilla
- Imagem
- Apresentação de slides
- Panorama cúbico
- Cor (HEX)
- Navegador
- Vídeo
- Shader GLSL
- Vídeo [Rinku] (obsoleto)
- Tipos de fundo adicionais de complementos

O antigo tipo de fundo **Vídeo [Rinku]** está obsoleto. Para novos layouts, use o fundo [**Vídeo** nativo](./video), desenvolvido com o Watermedia V3.

# Removendo o fundo personalizado

Abra **Fundos do menu** novamente e desative/remova o tipo de fundo personalizado que você não deseja mais usar. Se nenhum tipo de fundo personalizado estiver ativo, a tela voltará ao comportamento normal do fundo vanilla.

# Empilhando fundos

É possível ativar vários tipos de fundo de menu em um único layout. Os fundos ativos são renderizados em uma pilha, portanto, uma imagem ou panorama base pode ser combinado com camadas translúcidas de navegador, shader, paralaxe ou outros tipos.

Se você também tiver vários layouts ativos, as pilhas de fundos deles também poderão ser combinadas. Para ordenar os layouts e definir uma ordem específica de exibição, clique com o botão direito no fundo do editor e clique em **Índice do layout**.

# Fundos transparentes

O FancyMenu renderiza uma camada preta atrás dos fundos personalizados ativos. Portanto, os pixels transparentes do fundo que estiver na camada mais inferior revelarão a cor preta. Use um fundo base opaco e empilhe fundos translúcidos acima dele.

Para tornar uma imagem de fundo translúcida, use o editor de imagens de sua preferência.

# Fundos de navegador

O tipo de fundo **Navegador** funciona como o [elemento Navegador](./elements#browser), mas preenche a tela inteira e recebe foco automaticamente. Isso é útil para conteúdo web em tela cheia, páginas HTML locais ou camadas de vídeo da web.

# Fundos de shader GLSL

O tipo de fundo **Shader GLSL** renderiza shaders GLSL personalizados e oferece suporte à criação de shaders no estilo Shadertoy. Consulte a página da [API de Shader GLSL](/glsl-shader-api) para ver os uniforms compatíveis e a estrutura dos shaders.
