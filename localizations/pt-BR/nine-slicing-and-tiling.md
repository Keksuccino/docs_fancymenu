---
title: Fatiamento em Nove Partes e Repetição
description: >-
  Faça com que texturas com molduras se ajustem a qualquer tamanho sem
  distorcê-las, ou repita um padrão em vez de esticá-lo.
sourceBlobSha: 0dca8e7070606cdafccd9edc23a77535048d4ba3
---

# Fatiamento em Nove Partes e Repetição

Suas texturas são esticadas para preencher o elemento. Isso funciona bem para fotos, mas molduras, painéis e botões com bordas ficam distorcidos quando aumentam de largura ou altura. Duas configurações resolvem isso:

- O fatiamento em nove partes mantém os cantos e as bordas da textura no formato original e preenche apenas o meio.
- A repetição usa a textura várias vezes em vez de esticá-la, preservando o tamanho do padrão.

<img width="800" alt="Uma textura quadrada de painel dividida em nove partes por quatro linhas e a mesma textura como um painel largo, com os cantos e as bordas mantendo o formato original" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/nine_slicing_example.png">

# Como Funciona o Fatiamento em Nove Partes

Quatro linhas dividem a textura em nove partes. Os quatro cantos mantêm sempre o mesmo tamanho, as bordas ficam mais compridas e o meio preenche o espaço restante.

1. Defina a textura.
2. Ative a configuração de fatiamento em nove partes. Consulte [Onde Funciona](#where-it-works) para ver o nome dessa configuração.
3. Defina o tamanho das bordas de acordo com a espessura da moldura da textura, em pixels da textura. Para uma moldura com 4 pixels de espessura, use `4`.

É bom saber:

- As bordas aparecem na tela com o mesmo tamanho que têm na textura. Por isso, uma textura com bordas de 40 pixels fica grosseira em um botão pequeno. Use uma textura com tamanho semelhante ao do elemento.
- A maioria das texturas tem um tamanho para as bordas esquerda e direita (bordas X) e outro para as bordas superior e inferior (bordas Y). Barras de Progresso, Dicas de Ferramenta e Personalizações Globais têm um tamanho para cada lado.
- Se as bordas forem grandes demais para a textura, elas serão reduzidas automaticamente.

# Onde Funciona

| Textura | Fatiamento em nove partes | Repetição |
|---|---|---|
| Texturas de [Botão](/elements#button), em **Texturas de Botão** | **Plano de Fundo Personalizado com Fatiamento em Nove Partes** | - |
| Texturas de [Controle Deslizante](/elements#slider), em **Texturas de Controle Deslizante** | **Plano de Fundo Personalizado com Fatiamento em Nove Partes** e **Alça Personalizada com Fatiamento em Nove Partes** | - |
| Elementos de [Imagem](/elements#image) | **Textura com Fatiamento em Nove Partes** | **Repetir Textura** |
| O **Plano de Fundo** de elementos de [Texto](/text-in-menus#background) e [Áreas Roláveis](/scrollable-areas#background) | **Plano de Fundo Personalizado com Fatiamento em Nove Partes** | **Repetir Textura em Mosaico** |
| **Planos de Fundo das Barras de Rolagem** de elementos de Texto e Áreas Roláveis | sempre ativado | - |
| O **Plano de Fundo** de elementos de [Dica de Ferramenta](/elements#tooltip) | sempre ativado; tamanhos em **Configurações de Fatiamento em Nove Partes** | - |
| Texturas de [Barra de Progresso](/elements#progress-bar) | **Textura da Barra com Fatiamento em Nove Partes** e **Textura de Fundo com Fatiamento em Nove Partes** | - |
| [Texturas globais de botões e controles deslizantes](/global-customizations#buttons-and-sliders) | **Planos de Fundo de Botão com Fatiamento em Nove Partes**, **Plano de Fundo de Controle Deslizante com Fatiamento em Nove Partes** e **Alça de Controle Deslizante com Fatiamento em Nove Partes** | - |
| [Planos de fundo de menu com imagem](/menu-backgrounds#image) | - | **Repetir Textura** |
| Cabeçalho e rodapé de [telas roláveis](/customizing-scrollable-screens) | - | **Repetir Textura do Cabeçalho** e **Repetir Textura do Rodapé** |

## Planos de Fundo de Elementos de Texto e Áreas Roláveis

Abra **Plano de Fundo** no menu de contexto de um elemento de Texto ou de uma Área Rolável:

- **Textura de Fundo Personalizada** substitui o painel escuro integrado pela sua própria textura. Redefina a configuração para restaurar o painel.
- **Plano de Fundo Personalizado com Fatiamento em Nove Partes** fica ativado por padrão. Defina as bordas usando **Bordas X do Fundo com Fatiamento em Nove Partes (Esquerda e Direita)** e **Bordas Y do Fundo com Fatiamento em Nove Partes (Superior e Inferior)**.
- **Repetir Textura em Mosaico** repete a textura em vez de esticá-la. Quando usada junto com o fatiamento em nove partes, as bordas e o meio são repetidos, enquanto os cantos permanecem como estão.
- **Exibir Plano de Fundo** desativa todo o plano de fundo.

## Planos de Fundo das Barras de Rolagem

Abra **Barras de Rolagem -> Planos de Fundo das Barras de Rolagem** em um elemento de Texto ou em uma Área Rolável. **Textura da Barra Vertical** e **Textura da Barra Horizontal** aplicam uma textura ao longo do percurso do controle deslizante. Elas sempre usam o fatiamento em nove partes, para que as extremidades mantenham o formato em barras de qualquer comprimento. Defina as bordas usando as duas configurações de borda logo abaixo.

# Como Funciona a Repetição

A repetição posiciona cópias da textura lado a lado, no tamanho original, até preencher o espaço. Use uma textura contínua, em que a borda esquerda se encaixe na direita e a borda superior se encaixe na inferior. Caso contrário, linhas ficarão visíveis entre as repetições.

Em elementos de Imagem, **Repetir Textura** e **Textura com Fatiamento em Nove Partes** não funcionam juntos. Se ambos estiverem ativados, a imagem será repetida.
