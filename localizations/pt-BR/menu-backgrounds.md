---
title: Fundos de Menu
description: 'Como definir fundos de menu personalizados (imagens, animações) para telas.'
---
# Fundos de Menu

O FancyMenu permite definir fundos personalizados para menus. Você pode usar imagens, texturas animadas, apresentações de slides, panoramas cúbicos, cores, navegadores, vídeos, shaders GLSL e muito mais.

# Definindo um Fundo

A personalização do fundo do menu está disponível no menu de contexto do editor de layout:

1. Abra o editor de layout.
2. Clique com o botão direito no fundo do editor.
3. Abra **Fundos de Menu**.
4. Ative e configure o(s) tipo(s) de fundo desejado(s).

Os tipos de fundo mais comuns incluem:

- Vanilla
- Image
- Slideshow
- Cubic Panorama
- Color (HEX)
- Browser
- Video
- GLSL Shader
- Video [MCEF] (obsoleto)
- Tipos de fundo adicionais de complementos

O antigo tipo de fundo **Video [MCEF]** está obsoleto. Use o [fundo **Video** nativo](./video), alimentado pelo Watermedia V3, para novos layouts.

# Removendo o Fundo Personalizado

Abra **Fundos de Menu** novamente e desative/remova o tipo de fundo personalizado que você não quer mais. Se nenhum tipo de fundo personalizado estiver ativo, a tela voltará ao comportamento normal do fundo vanilla.

# Empilhando Fundos

Vários tipos de fundo de menu podem ser ativados em um único layout. Os fundos ativos são renderizados em forma de pilha, então uma imagem base ou panorama pode ser combinado com camadas translúcidas de navegador, shader, paralaxe ou outras.

Se você também tiver vários layouts ativos, as pilhas de fundo deles também podem ser combinadas. Para ordenar os layouts e fazê-los aparecer em uma ordem específica, clique com o botão direito no fundo do editor e clique em **Índice do Layout**.

# Fundos Transparentes

O FancyMenu renderiza uma camada preta atrás dos fundos personalizados ativos. Por isso, pixels transparentes no fundo mais abaixo revelam preto. Use um fundo base opaco e, acima dele, empilhe fundos translúcidos.

Para deixar uma imagem de fundo translúcida, use o editor de imagens de sua preferência.

# Fundos de Navegador

O tipo de fundo **Browser** funciona como o [elemento Browser](./elements#browser), mas preenche a tela inteira e recebe foco automaticamente. Isso é útil para conteúdo web em tela cheia, páginas HTML locais ou camadas de vídeo da web.

# Fundos de Shader GLSL

O tipo de fundo **GLSL Shader** renderiza shaders GLSL personalizados e oferece suporte à criação de shaders no estilo Shadertoy. Consulte a página [API de Shader GLSL](/glsl-shader-api) para ver os uniforms e a estrutura de shader suportados.
