---
title: Texto em Menus
description: Como adicionar conteúdo de texto aos menus.
---

# Texto em Menus

O FancyMenu permite adicionar conteúdo de texto a menus/telas por meio do elemento **Texto**.

Esse elemento é rolável, oferece suporte completo a Markdown e quebra automática de linha, o que o torna muito poderoso para exibir até mesmo conteúdo de texto complexo, mas também é ótimo para frases simples de uma linha.

## Conteúdo de Texto

O elemento Texto pode obter seu conteúdo de várias maneiras. Ele permite definir uma origem para o conteúdo do texto, que pode ser uma entrada direta de texto simples, um arquivo de texto local na pasta `assets` do FancyMenu (`/config/fancymenu/assets/`), um arquivo de texto na web (via URL) ou um arquivo de texto local carregado por meio de um resource pack.

Usar o tipo de origem da web como fonte de texto é especialmente útil se você quiser criar algo como um changelog sempre atualizado ou um ticker de notícias e coisas semelhantes, sem a necessidade de lançar uma atualização para o seu modpack.

Lembre-se de que o FancyMenu armazena em cache o conteúdo das fontes de texto, para não precisar buscar o conteúdo novamente o tempo todo (o que seria muito ruim para o desempenho). O conteúdo fica em cache apenas durante a sessão ativa, então reiniciar o jogo limpará o cache. Você também pode limpar o cache recarregando o FancyMenu em **barra de menus -> Customização -> Recarregar FancyMenu**.

## Placeholders

O elemento Texto também oferece suporte ao sistema de placeholders do FancyMenu, o que torna possível deixar o conteúdo do texto dinâmico e reagir a várias mudanças em menus, mundos, jogadores etc.

## Personalizando ou Desativando o Markdown

Se você quiser personalizar as cores dos títulos ou outras coisas relacionadas ao Markdown, basta **clicar com o botão direito** no elemento Texto e clicar em **Markdown**. No submenu de contexto que abrir, você verá várias opções para personalizar a aparência e o comportamento do interpretador de Markdown.

Caso não queira nenhuma análise de Markdown, o que pode melhorar o desempenho em conteúdos de texto longos, você pode desativar completamente o Markdown no menu **Markdown** ao **clicar com o botão direito** no elemento Texto.

## Desativando a Quebra de Linha

Se você não quiser quebra automática de linha, pode desativá-la **clicando com o botão direito** no elemento Texto.

## Desativando a Rolagem

Os elementos de texto têm rolagem ativada por padrão e, se o elemento entender que o usuário precisa rolar para ver todo o conteúdo, ele exibirá suas barras de rolagem, que são pequenas barras cinzas no lado direito e na parte inferior do elemento Texto (barras de rolagem vertical e horizontal).

Você pode desativar essas barras desmarcando **Rolagem** no menu que se abre ao **clicar com o botão direito** no elemento. Isso desativará a rolagem em geral, não apenas as barras. Se preferir que as barras fiquem invisíveis, você pode definir texturas personalizadas para as barras de rolagem clicando com o botão direito no elemento. Basta definir uma textura totalmente transparente ali.

## Formato Bruto de Texto de Componentes do Minecraft (Componentes JSON Serializados)

O elemento Texto NÃO oferece suporte ao formato bruto de componentes do Minecraft. Esse formato é compatível apenas com os rótulos de botões e sliders.
