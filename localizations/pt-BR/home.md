---
title: Primeiros passos
description: >-
  Seus primeiros passos com o FancyMenu. A barra de menus, seu primeiro layout
  do começo ao fim e para onde ir depois.
sourceBlobSha: 0a9f8343e6964d75860fb6143e9b6fdecb6cf0ea
---

# Primeiros passos

O FancyMenu permite alterar todos os menus do Minecraft, como a tela inicial, o menu de pausa e os menus de outros mods. Dê a eles seus próprios planos de fundo, logotipos, botões, textos, sons e animações; mova ou oculte o que já existe; faça os botões terem novas funções; ou crie menus inteiramente novos. Tudo isso acontece dentro do jogo, sem código.

<img width="800" alt="A tela inicial de um modpack chamado Wildwood, criada com o FancyMenu: um vale em pixel art ao anoitecer, com uma cabana, um lago e o sol se pondo, cujas camadas se movem com o mouse; um logotipo dourado; botões de madeira que brilham ao passar o mouse; e vaga-lumes" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_hero.gif?raw=true">

Esta página apresenta o básico passo a passo. Ao longo dela, você vai criar uma versão mais simples desta tela inicial, e [Como o exemplo foi criado](#how-the-example-is-made) mostra o que a versão completa acrescenta.

> [!TIP]
> Use esta tela inicial no seu próprio jogo: baixe [wildwood_title_screen.fmp](https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/wildwood_title_screen.fmp?raw=true) e depois [importe](/profiles#importing) e [carregue](/profiles#loading-a-profile) o arquivo em **barra de menus -> Personalização -> Perfis**. Você pode usá-lo gratuitamente para qualquer finalidade, como experimentar o FancyMenu, aprender com ele ou incluí-lo no seu modpack, com ou sem alterações. Não é necessário dar créditos.

# A barra de menus

A barra de menus, no topo de cada menu, é onde ficam todos os recursos do FancyMenu.

<img width="800" alt="A barra de menus no topo da tela inicial, com o menu Personalização aberto" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_menu_bar.png?raw=true">

- **Personalização**: os layouts do menu em que você está e tudo o que diz respeito à sua configuração completa, como [Personalizações globais](/global-customizations), [GUIs personalizadas](/custom-guis), [Variáveis](/variables), [Ouvintes](/listeners), [Agendadores](/schedulers), [Perfis](/profiles) e as configurações do FancyMenu.
- **Ferramentas**: ferramentas auxiliares como [Instâncias de tela de teste](/dummy-screen-instances), o [Criador de AFMA](/animations#fma-and-afma), **Explorar recursos do jogo** e **Abrir diretório do FancyMenu**, que abre a pasta da sua configuração (veja [Locais de armazenamento de dados](/data-storage-locations)).
- **Ajuda**: esta documentação, o servidor do Discord, **Relatar um erro** e [Exportar para IA](/export-for-ai).
- O ícone de porta à direita fecha o menu em que você está, nos casos em que não há outra forma de sair.
- As setas duplas à direita recolhem a barra de menus para deixá-la como um pequeno botão e a expandem novamente.

Quem jogar seu modpack não precisa da barra de menus. Consulte [Modpacks](/modpacks#disabling-the-menu-bar-and-hotkeys) para saber como desativá-la.

## Atalhos da barra de menus

Eles funcionam em todos os menus, mas não no editor de layout nem quando o Modo Modpack está ativado. No macOS, use `Cmd + Option` no lugar de `Ctrl + Alt`.

| Atalho | O que faz |
|---|---|
| `Ctrl + Alt + C` | Mostra ou oculta a barra de menus. Se ela sumir de repente, use este atalho para trazê-la de volta. |
| `Ctrl + Alt + R` | Recarrega o FancyMenu, como **barra de menus -> Personalização -> Recarregar FancyMenu**. |
| `Ctrl + Alt + D` | Mostra ou oculta a **Sobreposição de depuração**, que exibe o [identificador](/screen-identifiers) do menu e outras informações. |
| `Ctrl + Alt + L` | Abre o [editor de layout](/layout-editor) com o último layout que você editou. |

# Seu primeiro layout

Um layout reúne suas alterações em um menu: o plano de fundo, os elementos que você adiciona e as mudanças feitas nos botões e textos que já existem. Um menu pode ter vários layouts, e você pode ativar ou desativar cada um deles.

## Criar um layout

<img width="800" alt="Abrindo Personalização na barra de menus da tela inicial, ativando Personalização da tela atual, abrindo Personalização novamente e clicando em Layouts, Novo, Para a tela atual, o que abre o editor de layout" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_new_layout.gif?raw=true">

1. Abra o menu que você quer alterar, como a tela inicial.
2. Clique em **barra de menus -> Personalização -> Personalização da tela atual** até que apareça **Ativado**. O FancyMenu só altera os menus em que essa opção está ativada.
3. Clique em **barra de menus -> Personalização -> Layouts -> Novo -> Para a tela atual**.

O editor de layout será aberto. Ele mostra o menu como os jogadores o veem, para que você possa conferir cada alteração na hora. Consulte [Editor de layout](/layout-editor) para saber mais, incluindo como mover, redimensionar e copiar elementos.

**Para todas as telas [Universal]** cria um [Layout universal](/universal-layouts), que aparece em todos os menus.

## Definir um plano de fundo

Primeiro, coloque suas imagens na pasta `config/fancymenu/assets` do jogo. **barra de menus -> Ferramentas -> Abrir diretório do FancyMenu** abre `config/fancymenu`.

<img width="800" alt="Clicando com o botão direito no plano de fundo do editor, abrindo Planos de fundo do menu, Imagem, ativando Exibir plano de fundo, depois Escolher imagem, mudando Tipo de origem para Local e selecionando background.png na pasta wildwood; o vale aparece atrás dos botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_background.gif?raw=true">

1. Clique com o botão direito no plano de fundo do editor e abra **Planos de fundo do menu -> Imagem**.
2. Clique em **Exibir plano de fundo** até que apareça **Ativado**.
3. Clique em **Escolher imagem**, defina **Tipo de origem** como **Local** e clique em **Escolher arquivo de recurso local**.
4. Clique na sua imagem e depois em **OK**. Para abrir pastas, clique duas vezes.

Os planos de fundo também podem ser panoramas, apresentações de slides, vídeos, cores e muito mais. Consulte [Planos de fundo do menu](/menu-backgrounds).

## Adicionar um logotipo

<img width="800" alt="Excluindo o logotipo do Minecraft e o texto amarelo, adicionando um elemento de imagem por Elemento, Novo, Imagem e selecionando logo.png como Origem da imagem; o logotipo aparece comprimido em um quadrado" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_add.gif?raw=true">

1. Clique no logotipo do Minecraft e pressione `Delete`. Faça o mesmo com o texto amarelo.
2. Na barra de menus do editor, clique em **Elemento -> Novo -> Imagem**.
3. Clique com o botão direito no novo elemento, clique em **Origem da imagem** e escolha seu logotipo, como você fez com o plano de fundo.

Os elementos originais do Minecraft que você exclui ficam apenas ocultos. **Elemento -> Elementos originais excluídos** permite restaurá-los.

<img width="800" alt="Clicando em Restaurar proporção no menu de contexto do logotipo, para que ele fique com a largura correta; fechando o menu com Esc e arrastando o logotipo de Wildwood para cima dos botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_logo_place.gif?raw=true">

4. Clique nele com o botão direito outra vez e clique em **Restaurar proporção**, para que não fique comprimido. `Esc` fecha o menu.
5. Arraste-o até o lugar desejado.

Há muito mais coisas que você pode adicionar, como botões, textos, vídeos e jogadores. Consulte [Elementos](/elements).

## Alterar os botões

<img width="800" alt="Clicando no botão Singleplayer e, com Ctrl pressionado, clicando nos outros quatro botões; depois, aplicando uma textura de madeira aos cinco de uma só vez em Texturas dos botões, Definir, Plano de fundo normal" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_normal.gif?raw=true">

1. Clique no primeiro botão, depois mantenha `Ctrl` pressionado (`Cmd` no macOS) e clique nos outros, para selecionar todos. Ao clicar com o botão direito em um deles, você altera todos os selecionados de uma só vez.
2. Clique com o botão direito em um deles, selecione **Texturas dos botões -> Definir -> Plano de fundo normal** e escolha sua textura, como você fez com o plano de fundo.

<img width="800" alt="Definindo uma textura brilhante em Texturas dos botões, Definir, Plano de fundo ao passar o mouse; ativando Plano de fundo personalizado de nove fatias, que mantém as bordas da madeira nítidas; e passando o mouse sobre o botão Multiplayer, que brilha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_buttons_hover.gif?raw=true">

3. Faça o mesmo em **Plano de fundo ao passar o mouse**, que define a textura exibida quando o ponteiro está sobre um botão.
4. Clique em **Texturas dos botões -> Plano de fundo personalizado de nove fatias** até que apareça **Ativado**. Isso mantém as bordas da textura nítidas em botões de qualquer largura. Consulte [Divisão em nove partes](/nine-slicing-and-tiling).

O menu de contexto de vários elementos só exibe as configurações que todos eles têm, então selecione apenas botões. Clique com o botão direito em um único botão para acessar todas as configurações dele, como o rótulo, os sons, o que acontece quando ele é clicado ([Scripts de ação](/action-scripts)) e quando aparece ([Visibilidade dos elementos](/element-visibility)). Consulte [Elementos originais/de mods](/vanilla-elements).

## Salvar

<img width="800" alt="Pressionando Ctrl + S, clicando em Salvar na janela Salvar arquivo, fechando o editor com o X e vendo a tela inicial pronta com o vale, o logotipo de Wildwood e os botões de madeira" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/getting_started_save.gif?raw=true">

1. Pressione `Ctrl + S` (`Cmd + S` no macOS) ou clique em **Layout -> Salvar**.
2. Na primeira vez, o FancyMenu pedirá um nome de arquivo. Mantenha o nome sugerido ou digite outro e clique em **Salvar**.
3. Feche o editor clicando no X à direita da barra de menus.

Seu layout aparecerá no menu imediatamente. Para alterá-lo depois, passe o mouse sobre ele em **barra de menus -> Personalização -> Layouts** e clique em **Editar layout**, ou pressione `Ctrl + Alt + L`.

# Como o exemplo foi criado

A tela inicial no topo desta página acrescenta algumas coisas àquela que você criou:

- O céu, as colinas e as árvores são três imagens que se movem com o mouse, e as árvores se movem mais. Consulte [Efeito de paralaxe](/parallax).
- As colinas e as árvores são elementos de imagem do tamanho da tela. Assim, elas ficam atrás dos botões e dos textos: no menu de contexto do plano de fundo do editor, a opção **Elementos personalizados atrás dos originais** está ativada.
- Os vaga-lumes são uma [Sobreposição decorativa](/decoration-overlays#fireflies).
- As colinas, as árvores e o logotipo têm o tamanho definido com base no tamanho da tela, por meio de [Posicionamento e dimensionamento avançados](/advanced-positioning-sizing) com espaços reservados. Assim, o menu se ajusta a qualquer tamanho de janela. O logotipo fica menor em telas mais baixas, para nunca cobrir os botões.

Para conferir tudo isso no editor de layout, carregue o [perfil de exemplo](#getting-started) e edite o layout dele.

# Para onde ir agora

**Deixe tudo com uma ótima aparência**

- [Elementos](/elements): tudo o que você pode adicionar aos menus.
- [Posicionamento de elementos](/positioning-elements): mantenha os elementos no lugar em janelas de qualquer tamanho.
- [Planos de fundo do menu](/menu-backgrounds), [Animações](/animations), [Vídeos](/video), [Sobreposições decorativas](/decoration-overlays) e [Música de fundo](/background-music).

**Faça as coisas acontecerem**

- [Scripts de ação](/action-scripts): o que os botões e outros elementos fazem.
- [Visibilidade dos elementos](/element-visibility) e [Requisitos](/conditions): exiba elementos apenas em determinadas situações.
- [Espaços reservados](/placeholders): informações dinâmicas nos textos, como o nome do jogador.
- [Variáveis](/variables), [Ouvintes](/listeners) e [Agendadores](/schedulers): guarde informações, reaja ao jogo e execute ações em intervalos programados.

**Crie mais coisas**

- [GUIs personalizadas](/custom-guis): menus inteiramente novos.
- [Layouts universais](/universal-layouts): alterações para todos os menus.
- [Personalizações globais](/global-customizations): ajustes para o jogo inteiro, como o título da janela.
- [Tela de carregamento](/loading-screen) e [Introdução do jogo](/game-intro).

**Compartilhe sua criação**

- [Modpacks](/modpacks): inclua sua configuração em um modpack.
- [Perfis](/profiles): alterne entre configurações e exporte-as.

# Como obter ajuda

- A [FAQ](/faq) responde às perguntas mais frequentes.
- **barra de menus -> Ajuda -> Entrar no Discord** leva você ao servidor do FancyMenu no Discord.
- [Exportar para IA](/export-for-ai) transforma sua configuração em texto para conversas com IAs, como o bot de suporte no servidor do Discord.
- Use **barra de menus -> Ajuda -> Relatar um erro** se algo não funcionar como deveria.

# Para desenvolvedores

Para criar um complemento para o FancyMenu ou usá-lo no seu mod, consulte a [documentação para desenvolvedores](https://github.com/Keksuccino/FancyMenu-Dev-Docs/wiki).
