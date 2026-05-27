---
title: Texto em Menus
description: Como adicionar conteúdo de texto aos menus.
---
# Texto em Menus

O FancyMenu permite adicionar conteúdo de texto a menus/telas por meio do elemento **Texto**.

Esse elemento é rolável, tem suporte total a Markdown e quebra automática de linha, o que o torna muito poderoso para exibir até mesmo conteúdo de texto complexo, mas também é ótimo para frases curtas e simples.

# Conteúdo de Texto

O elemento Texto pode buscar seu conteúdo de várias formas. Você pode definir uma origem para o conteúdo de texto, que pode ser uma entrada de texto simples direta, um arquivo de texto local na pasta `assets` do FancyMenu (`/config/fancymenu/assets/`), um arquivo de texto da web (via URL) ou um arquivo de texto local carregado por meio de um resource pack.

Usar o tipo de origem da web como fonte de texto é especialmente útil se você quiser criar algo como um changelog sempre atualizado ou um painel de notícias e coisas semelhantes, sem precisar lançar uma atualização para o seu modpack.

Tenha em mente que o FancyMenu armazena em cache o conteúdo das origens de texto, para que ele não precise buscar o conteúdo constantemente de novo (o que seria muito ruim para o desempenho). O conteúdo é armazenado em cache apenas para a sessão ativa, então reiniciar o jogo limpará o cache. Você também pode limpar o cache recarregando o FancyMenu por meio de **barra de menu -> Personalização -> Recarregar FancyMenu**.

# Substituições

O elemento Texto também oferece suporte ao sistema de substituições do FancyMenu, o que torna possível deixar o conteúdo de texto dinâmico e reagir a várias mudanças em menus, mundos, jogadores etc.

# Personalizando ou Desativando o Markdown

Se você quiser personalizar as cores dos títulos ou outros elementos relacionados ao Markdown, basta **clicar com o botão direito** no elemento Texto e clicar em **Markdown**. No submenu de contexto que abrir, você verá várias opções para personalizar a aparência e o comportamento do analisador de Markdown.

Caso você não queira nenhum processamento de Markdown, o que pode melhorar o desempenho para textos longos, você pode desativar o Markdown completamente no menu **Markdown** ao **clicar com o botão direito** no elemento Texto.

# Desativando a Quebra de Linha

Se você não quiser quebra automática de linha, pode desativá-la **clicando com o botão direito** no elemento Texto.

# Desativando a Rolagem e Ocultando as Barras de Rolagem

Os elementos de texto são roláveis por padrão e, se o elemento entender que o usuário precisa rolar para ver todo o conteúdo, ele mostrará suas barras/controles de rolagem, que são pequenas barras cinzas translúcidas (com bordas arredondadas) nos lados direito e inferior do elemento Texto (rolagens vertical e horizontal). Os controles de rolagem às vezes também podem ser confundidos com sombras.

Você pode desativar esses controles alternando **Rolagem** no menu que se abre ao **clicar com o botão direito** no elemento. Isso desativará a rolagem em geral, e não apenas os controles. Se você só quiser que os controles fiquem invisíveis, mas ainda queira poder rolar, você pode definir texturas personalizadas para os controles de rolagem ao clicar com o botão direito no elemento. Basta definir uma textura totalmente transparente ali.

# Formato de Texto de Componente Bruto do Minecraft (Componentes JSON Serializados)

O elemento Texto NÃO tem suporte ao formato de componente bruto do Minecraft. Esse formato é suportado apenas por rótulos de botões e sliders.
