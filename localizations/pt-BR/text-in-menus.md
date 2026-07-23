---
title: Texto em Menus
description: Como adicionar conteúdo de texto aos menus.
---
# Texto em Menus

O FancyMenu permite adicionar conteúdo de texto aos menus/telas por meio do elemento **Text**.

Esse elemento é rolável, tem suporte completo a Markdown e quebra automática de linha, o que o torna muito poderoso para exibir até conteúdos de texto complexos, mas ele também é ótimo para mensagens simples de uma linha.

# Conteúdo de Texto

O elemento Text pode obter seu conteúdo de várias maneiras. Ele permite definir uma fonte para o conteúdo do texto, que pode ser uma entrada de texto simples direta, um arquivo de texto local no diretório de assets do FancyMenu (`<game-directory>/config/fancymenu/assets/`), um arquivo de texto da web (via URL) ou um arquivo de texto local carregado por meio de um resource pack.

Usar o tipo de origem da web como fonte de texto é especialmente útil se você quiser criar algo como um changelog que esteja sempre atualizado, um ticker de notícias ou coisas semelhantes, sem precisar lançar uma atualização do seu modpack.

Tenha em mente que o FancyMenu armazena em cache o conteúdo das fontes de texto, para não precisar buscar o conteúdo novamente o tempo todo (o que seria muito ruim para o desempenho). O conteúdo é armazenado em cache apenas para a sessão ativa, então reiniciar o jogo limpará o cache. Você também pode limpar o cache recarregando o FancyMenu por meio de **menu bar -> Customization -> Reload FancyMenu**.

# Placeholders

O elemento Text também suporta o sistema de placeholders do FancyMenu, o que torna possível deixar o conteúdo do texto dinâmico e reagir a várias mudanças nos menus, mundos, jogadores etc.

# Personalizando ou Desativando Markdown

Se você quiser personalizar as cores dos títulos ou outros elementos relacionados ao Markdown, basta **clicar com o botão direito** no elemento Text e clicar em **Markdown**. No submenu que se abrir, você verá várias opções para personalizar a aparência e o comportamento do analisador de Markdown.

Caso você não queira usar a análise de Markdown, o que pode melhorar o desempenho com conteúdos de texto longos, você pode desativar completamente o Markdown no menu **Markdown** ao **clicar com o botão direito** no elemento Text.

# Desativando a Quebra de Linha

Se você não quiser a quebra automática de linha, pode desativá-la com **clique com o botão direito** no elemento Text.

# Desativando a Rolagem e Ocultando os Controles de Rolagem

Por padrão, elementos Text são roláveis e, se o elemento entender que o usuário precisa rolar para ver todo o conteúdo, ele mostrará suas barras/controles de rolagem, que são pequenas barras cinzas translúcidas (com bordas arredondadas) nos lados direito e inferior do elemento Text (barras de rolagem vertical e horizontal). Às vezes, os controles de rolagem também são confundidos com sombras.

Você pode desativar esses controles desmarcando **Scrolling** no menu que se abre ao **clicar com o botão direito** no elemento. Isso desativará a rolagem em geral, não apenas os controles. Se você quiser apenas que os controles fiquem invisíveis, mas ainda assim poder rolar, pode definir texturas personalizadas para os controles de rolagem ao clicar com o botão direito no elemento. Basta definir ali uma textura totalmente transparente.

# Formato de Texto de Componentes Brutos do Minecraft (Componentes JSON Serializados)

O elemento Text NÃO oferece suporte ao formato de componentes brutos do Minecraft. Esse formato é compatível apenas com os rótulos de botões e sliders.
