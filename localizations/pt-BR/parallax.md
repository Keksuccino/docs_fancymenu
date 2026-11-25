---
title: Efeito de paralaxe
description: >-
  Faça planos de fundo e elementos se moverem um pouco com o mouse para dar
  profundidade aos seus menus.
sourceBlobSha: f8481cfcc8d4f90bf2f261d436188763c8f23cba
---

# Efeito de paralaxe

O efeito de paralaxe move um pouco o plano de fundo de um menu ou um elemento quando o mouse se move. Faça as camadas mais distantes se moverem menos e as mais próximas, mais, para dar profundidade ao seu menu.

<img width="640" alt="Uma tela de título com uma paisagem ao entardecer em quatro camadas: enquanto o mouse se move, a árvore em primeiro plano se move mais, as colinas se movem menos e as montanhas e o céu se movem só um pouco" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_scene.gif?raw=true">

O efeito funciona com [elementos](/elements) e com planos de fundo de menu de **Imagem** e **Vídeo** [menu backgrounds](/menu-backgrounds).

# Elementos

<img width="640" alt="Em uma tela de título com os botões em uma coluna à esquerda, selecionar os cinco botões no editor de layout com um clique e Ctrl + clique, definir Efeito de paralaxe como Ativado e Intensidade da paralaxe (X) como 1,0 para todos e, em seguida, salvar e fechar o editor. Na tela de título, os botões se movem um pouco enquanto o mouse vai de um lado para o outro, mas o logotipo e a paisagem ficam parados" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_element_settings.gif?raw=true">

1. Clique com o botão direito no elemento no editor de layout e role a tela até **Efeito de paralaxe**.
2. Clique em **Efeito de paralaxe** para defini-lo como **Ativado**.
3. Clique em **Intensidade da paralaxe (X)** e **Intensidade da paralaxe (Y)** para definir o quanto o elemento se move.
4. Salve o layout e feche o editor. Os elementos só se movem fora do editor.

Para aplicar o efeito a vários elementos de uma só vez, [selecione](/layout-editor#selecting) os elementos primeiro (`Ctrl` + clique adiciona um elemento à seleção) e, em seguida, clique com o botão direito em um deles.

| Configuração | O que ela faz |
|---|---|
| **Efeito de paralaxe** | Ativa o efeito. |
| **Intensidade da paralaxe (X)** | O quanto o elemento se move para a esquerda e para a direita, de `0.0` (não se move) a `1.0`. Elementos novos têm o valor `0.5`. |
| **Intensidade da paralaxe (Y)** | O mesmo para os movimentos para cima e para baixo. |
| **Inverter movimento da paralaxe** | Move o elemento na mesma direção do mouse. Sem essa opção, ele se move na direção oposta. |

Com o valor `1.0`, o elemento pode se mover até 5% da largura da tela para os lados e até 5% da altura da tela para cima ou para baixo quando o mouse estiver na borda da tela. No centro da tela, os elementos ficam onde você os colocou.

- Elementos [ancorados](/positioning-elements) a um elemento com o efeito se movem junto com ele, e o efeito aplicado a eles se soma a isso.
- **Manter na tela** não mantém na tela os elementos com o efeito, então eles podem passar das bordas.
- Elementos esticados não se movem na direção em que estão esticados.
- [Botões e controles deslizantes do Vanilla](/vanilla-elements) só se movem depois que você os move. Com o ponto de ancoragem **Vanilla (Original)**, eles ficam onde o jogo os coloca.
- Os botões continuam clicáveis onde são exibidos.
- [Áreas roláveis](/scrollable-areas), os elementos dentro delas e os elementos de dica de ferramenta não têm efeito de paralaxe.

# Planos de fundo de menus

<img width="800" alt="O menu de contexto do editor de layout com Planos de fundo de menu e Imagem abertos, mostrando Efeito de paralaxe, Definir intensidade do efeito de paralaxe (X), Definir intensidade do efeito de paralaxe (Y) e Inverter movimento da paralaxe" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/parallax_background_settings.png?raw=true">

1. Clique com o botão direito no plano de fundo do editor e abra **Planos de fundo de menu -> Imagem** (ou **Vídeo**).
2. Clique em **Efeito de paralaxe** para defini-lo como **Ativado**.
3. Defina **Definir intensidade do efeito de paralaxe (X)** e **Definir intensidade do efeito de paralaxe (Y)**.

Os planos de fundo reagem com muito mais intensidade do que os elementos. O plano de fundo aumenta de tamanho de acordo com a intensidade para que suas bordas nunca apareçam: com o valor `1.0`, ele fica com o dobro do tamanho da tela e se move até meia tela para os lados. Mantenha os valores baixos: planos de fundo novos têm o valor `0.02`, e valores entre `0.01` e `0.1` funcionam bem.

- **Inverter movimento da paralaxe** move o plano de fundo na mesma direção do mouse.
- **Deslizar imagens largas da esquerda para a direita** e **Efeito de paralaxe** não podem estar ativados ao mesmo tempo.
- **Repetir textura** e **Preservar proporção do plano de fundo** funcionam em conjunto com o efeito.
- Os planos de fundo também se movem no editor de layout.

# Criar uma cena com profundidade

A cena no início desta página é composta por um céu e três camadas na tela de título:

1. Desenhe sua cena em camadas, da mais distante à mais próxima, como céu, montanhas, colinas e primeiro plano. Todas as camadas, exceto o céu, devem ser imagens PNG com partes transparentes.
2. Defina o céu como plano de fundo de menu de **Imagem** e ative o efeito de paralaxe.
3. Adicione cada uma das outras camadas como um [elemento de imagem](/elements#image), da mais distante à mais próxima, para que a mais próxima fique por cima.
4. Faça as camadas um pouco maiores do que a tela para que suas bordas nunca apareçam quando elas se moverem. Uma camada com intensidade `1.0` precisa de 5% a mais da largura da tela à esquerda e à direita, e de 5% a mais da altura da tela em cima e embaixo. Desative **Manter na tela** para posicioná-las além das bordas da tela.
5. Ative o efeito de paralaxe em todas as camadas: use intensidades baixas para as camadas distantes e altas para as próximas.
6. Clique com o botão direito no plano de fundo do editor e defina **Elementos personalizados atrás dos elementos Vanilla** como **Ativado**, para que as camadas fiquem atrás dos botões e do logotipo.

Estas são as intensidades usadas na cena:

| Camada | Intensidade (X) | Intensidade (Y) |
|---|---|---|
| Céu (plano de fundo de menu) | `0.02` | `0.01` |
| Montanhas | `0.35` | `0.2` |
| Colinas | `0.6` | `0.3` |
| Primeiro plano | `1.0` | `0.5` |

> [!TIP]
> Use uma intensidade Y equivalente a cerca de metade da intensidade X. Assim, o chão da paisagem não fica subindo e descendo tanto.

# Informações úteis

- Tudo se move em pixels inteiros da interface, então intensidades baixas fazem os elementos se moverem em pequenos incrementos.
- As configurações de intensidade aceitam [placeholders](/placeholders): aponte para um deles e clique em **Definir como texto simples** no pequeno menu ao lado. Com uma [variável](/variables), você pode permitir que os jogadores reduzam a intensidade do efeito no seu próprio menu de configurações.
