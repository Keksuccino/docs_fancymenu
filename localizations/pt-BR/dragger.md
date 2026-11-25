---
title: Dragger
description: >-
  Permita que os jogadores peguem um painel, uma nota ou qualquer outro elemento
  dos seus menus e o movam para onde quiserem.
sourceBlobSha: 5cfe57388c5b839c5a98045d0086a94df6b4110c
---

# Dragger

Um Dragger é uma área invisível que os jogadores podem pegar com o mouse e mover. Tudo que estiver ancorado a ele também se move, como um painel com notas de atualização ou uma nota com as regras do servidor. O menu lembra onde os jogadores o deixaram, mesmo depois de reiniciar o jogo.

<img width="800" alt="Um jogador pega um banner de notas de atualização pela empunhadura de couro da haste e o arrasta do lado esquerdo para o lado direito da tela de título, abre as opções, volta e o banner continua à direita" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_hero.gif?raw=true">

Os jogadores só podem arrastá-lo fora do editor de layouts. No editor, o Dragger é um retângulo vermelho com seu nome (**Cor no editor** no menu de clique com o botão direito altera o vermelho), e tudo permanece onde o layout determina.

# Tornando algo móvel

<img width="800" alt="Adicionando um Dragger por meio de Novo elemento, redimensionando-o para o tamanho do banner, arrastando-o até o banner e movendo-o duas camadas para baixo; em seguida, arrastando o banner para fora do Dragger e de volta, mantendo-o ali até a barra encher, o que ancora o banner ao Dragger" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/dragger_setup.gif?raw=true">

1. Crie o que você quer mover, como uma imagem de banner com um elemento de texto sobre ela.
2. Clique com o botão direito em um espaço vazio no editor de layouts e escolha **Novo elemento -> Dragger**.
3. Deixe o Dragger do tamanho do banner e mova-o até o banner.
4. Clique com o botão direito no Dragger e escolha **Mover uma camada para baixo** até que ele fique abaixo de todos os elementos do banner. Os elementos selecionados sempre aparecem na frente, então clique em um espaço vazio para ver a alteração.
5. Ancore o banner ao Dragger: arraste o banner um pouco para fora do Dragger e de volta, mantendo-o ali até a barra encher. Saiba mais em [Posicionando elementos](/positioning-elements#anchoring-elements-to-other-elements).
6. Salve o layout e teste-o fora do editor.

Os elementos ancorados a algo que se move também se movem. No GIF, o texto está ancorado ao banner, então o banner é o único elemento que precisa do Dragger.

Para ancorar vários elementos de uma só vez, clique com o botão direito no Dragger e escolha **Copiar ID do elemento** antes da etapa 4. Em seguida, selecione os elementos, clique com o botão direito em um deles, escolha **Ponto de ancoragem -> Outro elemento** e cole o ID.

> [!TIP]
> Os jogadores não conseguem ver o Dragger, então indique onde devem segurá-lo, por exemplo, com uma barra de título ou uma empunhadura.

# Salvando a posição

A opção **Salvar deslocamento do arrasto do usuário** no menu de clique com o botão direito do Dragger vem ativada para novos Draggers.

- **Ativada**: a posição é salva quando o jogador solta o elemento. Ela é mantida depois que a tela é fechada e o jogo é reiniciado.
- **Desativada**: tudo volta ao lugar definido no layout quando a tela é aberta novamente e quando o tamanho da janela ou a escala da interface muda.

Desativar essa opção no editor também apaga a posição que os jogadores salvaram para esse Dragger.

As posições são salvas para cada Dragger usando seu [ID do elemento](/element-identifiers), em `fancymenu_data/dragger_metas.json`. Essa pasta não faz parte dos [perfis](/profiles), então as posições que você arrastou durante os testes não vão parar na pasta `config/fancymenu/` do seu modpack. Consulte [Locais de armazenamento de dados](/data-storage-locations#instance-data).

Para devolver todos os Draggers às posições definidas no layout, exclua `dragger_metas.json` com o jogo fechado.

# O que os jogadores podem pegar

Os jogadores pegam o Dragger nos pontos em que nenhum elemento sobre ele intercepta o clique:

- As imagens sobre ele deixam o clique passar, então os jogadores pegam o próprio banner.
- Os botões e o texto dos elementos de texto sobre ele recebem o clique, então continuam funcionando em um painel móvel.
- Nos pontos em que o Dragger fica sobre um botão, o botão não recebe cliques. Por isso, nas etapas acima, o Dragger fica abaixo do banner.

Enquanto os [requisitos](/element-visibility#showing-elements-only-sometimes) dele ocultarem o Dragger, os jogadores não poderão pegá-lo.

# Mantendo na tela

A opção **Permanecer na tela** vem ativada para novos elementos. Ela faz o Dragger parar nas bordas da tela, impedindo que os jogadores o arrastem para fora de vista. Se o Dragger tiver o mesmo tamanho do banner inteiro, o banner também para na borda.

Um Dragger que cobre apenas uma parte do elemento, como uma barra de título, também funciona. Mas os elementos ancorados a ele têm a própria opção **Permanecer na tela**: na borda, eles param sozinhos enquanto o Dragger continua se movendo, e o painel se desmonta. Desative **Permanecer na tela** nesses elementos para que acompanhem o Dragger e apenas a barra de título permaneça na tela.
