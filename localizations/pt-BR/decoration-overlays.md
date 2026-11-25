---
title: Sobreposições decorativas
description: >-
  Adicione neve, chuva, vaga-lumes, luzes decorativas e outros efeitos animados
  aos seus menus.
sourceBlobSha: ee440d4a4cc4b88b86d876fe233a9638de8bb73b
---
# Sobreposições decorativas

As sobreposições decorativas são efeitos animados que cobrem a tela inteira, como neve caindo, vaga-lumes, neblina ou luzes decorativas. Muitas interagem com o menu: a neve se acumula nos botões, os pássaros pousam neles e a neblina se dissipa ao redor do mouse.

<img width="800" alt="Tela inicial à noite com Neve e Luzes decorativas, e neve se acumulando nos botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_hero.png?raw=true">

# Adicionar uma sobreposição

1. Abra um layout no editor de layouts.
2. Clique com o botão direito no plano de fundo do editor e abra **Sobreposições decorativas**.
3. Abra uma sobreposição, como **Neve**.
4. Clique em **Exibir sobreposição** para ativá-la.

As sobreposições ativadas têm um ✔ na lista. Você pode exibir quantas sobreposições quiser em um layout. Passe o mouse sobre uma sobreposição ou uma de suas configurações para ver o que ela faz.

As sobreposições também são reproduzidas no editor de layouts, mas só interagem com os elementos no menu de verdade. Salve o layout e abra o menu para ver tudo.

Quando vários layouts de uma tela têm sobreposições, todas são reproduzidas, mesmo que a mesma sobreposição apareça duas vezes. Isso também inclui [layouts universais](/universal-layouts).

# Configurações de todas as sobreposições

Todas as sobreposições têm estas duas configurações:

- **Exibir sobreposição** ativa ou desativa a sobreposição.
- **Camadas** define onde a sobreposição é desenhada:
  - **Plano de fundo e primeiro plano**: os elementos distantes são desenhados atrás dos seus elementos, e os próximos, na frente, criando uma boa sensação de profundidade. Esta é a opção padrão.
  - **Somente plano de fundo**: tudo é desenhado atrás dos seus elementos, mas na frente do plano de fundo do menu.
  - **Somente primeiro plano**: tudo é desenhado na frente dos seus elementos.

O que a sobreposição coloca diretamente nos seus elementos, como neve em um botão, sempre permanece sobre eles.

Muitas sobreposições também têm estas configurações:

| Configuração | O que faz |
|---|---|
| **Quantidade (%)** | Define a quantidade, de 25% a 300%. 100% é a quantidade normal. |
| **Tamanho** | Aumenta a arte em pixel art para 2x ou 3x. Cada pixel continua sendo um quadrado bem definido. |
| **Aparência** | **Detalhada** exibe toda a arte em pixel art, com sombreamento e efeitos extras. **Simples** é mais plana e se aproxima mais do visual clássico. |

# Sobreposições e seus elementos

Muitas sobreposições interagem com seus elementos: neve, cinzas e confetes se acumulam neles, pingentes de gelo ficam pendurados neles, musgo cresce neles e pássaros pousam neles.

Para escolher quais elementos participam, clique com o botão direito em um elemento e configure **Deve ser afetado por sobreposições decorativas**:

- Essa opção vem ativada por padrão para botões, controles deslizantes, caixas de seleção, campos de entrada e [elementos vanilla](/vanilla-elements).
- Isso inclui o logotipo, o texto de destaque, a marca e os direitos autorais da tela inicial. Desative a opção nesses elementos se não quiser que nada pouse neles.
- Elementos ocultos não participam. O mesmo vale para a parte de um elemento que é cortada por uma [área rolável](/scrollable-areas).

> [!TIP]
> Deixe pelo menos 13 pixels entre os elementos. O tamanho das coisas que se acumulam em um elemento ou ficam penduradas nele é limitado pelo espaço até o próximo elemento.

Algumas sobreposições reagem a cliques, como Bolhas, Geada e Confetes. Seus botões ainda recebem todos os cliques.

# Todas as sobreposições decorativas

Todas as sobreposições decorativas disponíveis no FancyMenu, organizadas por tema.

## Clima

### Neve

A neve cai e se acumula lentamente nos botões e ao longo da parte inferior da tela.

<img width="800" alt="Neve em uma tela inicial à noite, acumulada nos botões e ao longo da parte inferior" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_snowfall.png?raw=true">

- **Acumular neve** permite que a neve se acumule.
- **Cor da neve [HEX]**, **Velocidade da neve**, **Quantidade (%)** e **Tamanho** alteram a neve.

### Chuva

A chuva cai, forma ondulações em poças rasas e pinga dos seus botões.

<img width="800" alt="Chuva em uma tela inicial à noite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_rainfall.png?raw=true">

- **Poças** cria uma película molhada nos seus elementos e na parte inferior da tela, com ondulações nos pontos onde as gotas caem.
- **Goteiras** permite que gotas fiquem penduradas e caiam dos seus elementos.
- **Clarões de trovão** adiciona relâmpagos de vez em quando, com um raio ramificado e um clarão suave. **Brilho do clarão de trovão** define o brilho.
- **Cor da chuva [HEX]**, **Quantidade (%)** e **Tamanho** alteram a chuva.

> [!WARNING]
> **Clarões de trovão** faz a tela piscar. Deixe essa opção desativada se os jogadores puderem ser sensíveis a luzes piscantes.

### Neblina

Camadas suaves de névoa atravessam a tela e passam sobre seus elementos, ficando mais densas perto do chão.

<img width="800" alt="Neblina atravessando uma tela inicial e ficando mais densa perto da parte inferior" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_fog.png?raw=true">

- **Limpar ao redor do ponteiro** faz a neblina se afastar ao redor do mouse.

### Geada

Seu menu fica coberto de gelo. O gelo avança pelas bordas, pelos cantos e pelos seus elementos. Clique no gelo para arrancar um pedaço.

<img width="800" alt="Geada em uma tela inicial, com gelo nas bordas, nos cantos e nos botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_frost.png?raw=true">

- **Bordas da tela**, **Cantos** e **Nos elementos** ativam ou desativam cada parte do gelo. Os rótulos dos seus elementos continuam visíveis.

## Natureza

### Folhas

Folhas caem e são empurradas por rajadas de vento.

<img width="800" alt="Folhas caindo sobre uma tela inicial" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_leaves.png?raw=true">

- **Aparência** alterna entre folhas **Detalhadas** e **Simples**.
- **Cores** permite escolher **Mistura de outono** (cinco cores quentes de outono) ou **Intervalo personalizado** (cinco cores entre **Cor inicial das folhas [HEX]** e **Cor final das folhas [HEX]**).
- **Vento** ativa ou desativa as rajadas fortes. **Intensidade do vento** define a força do vento.
- **Densidade das folhas**, **Velocidade de queda das folhas** e **Escala da sobreposição de folhas** alteram as folhas.

### Flores de cerejeira

Galhos floridos surgem dos cantos superiores e pétalas flutuam para baixo.

<img width="800" alt="Flores de cerejeira em uma tela inicial, com galhos nos cantos superiores e pétalas sobre os botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_cherry_blossoms.png?raw=true">

- **Galho esquerdo** e **Galho direito** exibem ou ocultam cada galho.
- **Aparência** e **Quantidade (%)** alteram as pétalas.

### Vegetação

A natureza toma conta do seu menu: musgo, trepadeiras, grama e flores crescem lentamente por toda parte.

<img width="800" alt="Vegetação em uma tela inicial, com trepadeiras, grama, flores e musgo sobre os botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_overgrowth.png?raw=true">

- **Grama**, **Trepadeiras à esquerda**, **Trepadeiras à direita** e **Nos elementos** ativam ou desativam cada tipo de vegetação. Os rótulos dos seus elementos continuam visíveis.
- **Flores nas trepadeiras**, **Flores nos elementos** e **Flores na grama** permitem que flores desabrochem nesses locais. **Flores (%)** define a quantidade.

### Nuvens

Nuvens fofas em pixel art flutuam pelo céu atrás dos seus elementos, em três camadas de profundidade. As nuvens não têm configurações próprias.

<img width="800" alt="Nuvens flutuando atrás do logotipo e dos botões de uma tela inicial" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_clouds.png?raw=true">

### Raios de sol

Raios de sol se espalham a partir de um sol fora da tela, enquanto poeira dança sob a luz.

<img width="800" alt="Raios de sol iluminando uma tela inicial a partir do canto superior esquerdo" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_sunbeams.png?raw=true">

- **Lado do sol** define a borda da tela atrás da qual o sol fica. **Ângulo do sol (°)** desloca o sol ao longo dessa borda.
- **Cor da luz do sol [HEX]** e **Intensidade (%)** alteram a luz.
- **Brilho do sol** espalha um brilho suave a partir do sol.
- **Poeira** permite que a poeira flutue pelos raios. O mouse a agita.
- **Atingir elementos** faz os raios pararem nos seus elementos, iluminarem suas bordas e projetarem sombras. Quando essa opção está desativada, os raios brilham na frente dos seus elementos.

### Bolhas

Bolhas sobem em fileiras ondulantes e deslizam pela parte de baixo dos seus elementos. Clique nelas para estourá-las! As bolhas não têm configurações próprias.

<img width="800" alt="Bolhas subindo sobre uma tela inicial" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_bubbles.png?raw=true">

## Animais

### Pássaros

Pequenos pássaros voam até a tela, pulam pelos seus elementos e levantam voo quando o mouse se aproxima demais.

<img width="800" alt="Pássaros no tamanho 2x e em quantidade de 50% pousados nos botões de uma tela inicial" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_birds.png?raw=true">

### Borboletas

Borboletas coloridas esvoaçam, descansam nos seus elementos e se afastam do mouse.

<img width="800" alt="Borboletas esvoaçando ao redor dos botões de uma tela inicial" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_butterflies.png?raw=true">

### Morcegos

Morcegos atravessam a tela em pequenos grupos e ficam pendurados, dormindo, sob seus elementos. Chegue perto demais e eles acordam!

<img width="800" alt="Morcegos no tamanho 2x voando sobre uma tela inicial e pendurados sob os botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_bats.png?raw=true">

Pássaros, Borboletas e Morcegos têm as configurações **Quantidade (%)** e **Tamanho**.

### Vaga-lumes

Grupos de vaga-lumes brilham e vagam pela tela, e alguns pousam nos seus elementos.

<img width="800" alt="Vaga-lumes na escala 2x brilhando ao redor de um botão em uma tela inicial noturna" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_fireflies.png?raw=true">

- **Aparência** alterna entre vaga-lumes **Detalhados** e **Simples**. **Corpos apagados** exibe os pequenos corpos escuros entre os clarões.
- **Seguir o mouse** permite que os grupos sigam o mouse quando ele está por perto.
- **Pouso** permite que os vaga-lumes pousem nos seus elementos de vez em quando.
- **Cor dos vaga-lumes [HEX]**, **Quantidade de grupos**, **Densidade dos grupos**, **Tamanho dos grupos** e **Escala dos vaga-lumes** alteram os vaga-lumes.

### Buddy

Buddy é um pequeno animal de estimação virtual que vive na parte inferior do seu menu. Ele anda por aí, mostra o que precisa em balões de pensamento, reage quando você brinca com ele e se lembra de tudo entre as sessões de jogo.

<img width="480" alt="Buddy, um pequeno animal de estimação rosa, andando pela parte inferior de uma tela inicial" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_buddy.png?raw=true">

#### Cuidar do Buddy

Buddy tem quatro necessidades, de `0` a `100`:

- **Fome** diminui com o tempo. A comida a sacia.
- **Felicidade** diminui com o tempo. Carinho, comida e brincadeiras aumentam essa necessidade.
- **Energia** diminui enquanto Buddy está acordado e se recupera enquanto ele dorme.
- **Diversão** diminui com o tempo. Brincar aumenta essa necessidade.

Para cuidar do Buddy:

- Clique com o botão esquerdo no Buddy para fazer carinho. Acordá-lo dessa forma diminui um pouco a felicidade dele.
- Clique com o botão direito no Buddy para abrir a tela de status. A aba **Estatísticas** mostra as necessidades, o nível e o XP. A aba **Conquistas** mostra as conquistas dele.
- Clique em **Alimentar** na tela de status e arraste a comida até o Buddy.
- Clique em **Brincar** na tela de status, arraste a bola e solte-a para arremessá-la. Buddy corre atrás dela e a pega.
- Clique em **Dormir** para deixar Buddy descansar. Ele também adormece sozinho quando sua energia fica muito baixa.
- Buddy faz cocô de vez em quando. Clique com o botão esquerdo no cocô para limpá-lo. Se houver três ou mais cocôs espalhados, a felicidade do Buddy continua diminuindo.

#### Níveis e conquistas

Cuidar do Buddy dá XP a ele. Buddy sobe de nível do 1 ao 30. Quanto maior o nível, mais lentamente diminuem a fome, a felicidade e a energia — no nível 30, a velocidade é reduzida pela metade.

#### Quando Buddy morre

Se a fome ou a felicidade permanecer em `0` por 10 horas reais, Buddy morre e deixa uma lápide. Clique com o botão esquerdo na lápide para recomeçar com um Buddy novo. Desative **Buddy pode morrer** para impedir que ele morra.

**Redefinir o salvamento do Buddy** permite recomeçar a qualquer momento.

> [!WARNING]
> Redefinir o Buddy apaga de vez suas necessidades, nível, XP, conquistas e cocôs.

#### Salvamento e personalização

Buddy salva o progresso a cada dois minutos, aproximadamente, e quando a tela dele é fechada, em `<game-directory>/fancymenu_data/buddy/`. Cada sobreposição do Buddy tem seu próprio salvamento. Consulte [Locais de armazenamento de dados](/data-storage-locations).

- **Texturas personalizadas** substitui os sprites, itens, ícones, a tela de status e a lápide do Buddy pelas suas próprias texturas.
- **Ajuste de atributos** altera a velocidade com que as necessidades diminuem, o custo e os benefícios das atividades, e a quantidade máxima de cocôs espalhados (**Máximo de cocôs**).

## Céu noturno

### Aurora

Luzes do norte brilhantes ocupam a parte superior do céu e ondulam lentamente atrás dos seus elementos.

<img width="800" alt="Aurora brilhando atrás do logotipo de uma tela inicial à noite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_aurora.png?raw=true">

- **Cor da borda [HEX]** define a cor da borda inferior brilhante. **Cor da ponta [HEX]** define a cor para a qual os raios se esmaecem.

### Estrelas cadentes

Um céu noturno cintilante atrás dos seus elementos, com uma estrela cadente a cada poucos segundos e, de vez em quando, uma chuva inteira de meteoros. Estrelas cadentes não têm configurações próprias.

<img width="800" alt="Céu noturno estrelado com uma estrela cadente atrás de uma tela inicial" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_shooting_stars.png?raw=true">

### Lanternas celestes

Lanternas de papel brilhantes flutuam pelo céu noturno, às vezes em um grupo inteiro. As lanternas celestes têm as configurações **Quantidade (%)** e **Tamanho**.

<img width="800" alt="Lanternas celestes no tamanho 2x e em quantidade de 25% flutuando sobre uma tela inicial à noite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_sky_lanterns.png?raw=true">

## Festa

### Confetes

Lançadores de confete nos cantos inferiores disparam confetes a cada poucos segundos, e eles se acumulam nos seus elementos.

<img width="800" alt="Confetes caindo sobre uma tela inicial e acumulados nos botões" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_confetti.png?raw=true">

- **Lançadores nos cantos** ativa ou desativa os lançadores.
- **Explosão ao clicar** dispara uma pequena rajada de confetes onde você clicar.
- **Modo de mistura de cores** usa cores aleatórias. Desative essa opção para usar **Cor dos confetes [HEX]** em todos os confetes.
- **Limite de partículas caídas** define quantas partículas podem ficar acumuladas ao mesmo tempo.
- **Quantidade (%)**, **Tamanho** e **Velocidade de queda dos confetes** alteram os confetes.

### Fogos de artifício

Foguetes sobem e explodem em fogos de artifício.

<img width="800" alt="Fogos de artifício explodindo sobre uma tela inicial à noite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_fireworks.png?raw=true">

- **Exibir trajetória dos foguetes** exibe os foguetes enquanto sobem.
- **Quantidade (%)**, **Tamanho** e **Tamanho da explosão** alteram os fogos de artifício.

### Luzes decorativas

Fios de luzes ficam pendurados pelo menu e balançam ao vento.

<img width="800" alt="Fios de luzes decorativas pendurados por uma tela inicial à noite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_string_lights.png?raw=true">

- **Aparência** alterna entre luzes **Simples** e **Detalhadas**. **Guirlanda de pinheiro** troca o fio por agulhas de pinheiro com enfeites.
- **Programa de iluminação** define como as luzes brilham e piscam (veja abaixo).
- **Escala das luzes decorativas**, **Força do vento** e **Velocidade de oscilação** alteram todos os fios.
- **Fios** tem um menu para cada um dos oito locais onde um fio pode ser pendurado. Ative um deles com **Exibir fio de luzes**.

Cada fio tem estas configurações:

- **Quantidade de luzes** define quantas luzes ficam penduradas nele. `0` preenche o fio de acordo com o comprimento.
- **Cor das luzes [HEX]** define a cor das luzes. **Modo luzes de Natal** faz com que elas sejam coloridas.
- **Cor do fio [HEX]** define a cor do fio. Use o canal alfa para deixá-lo translúcido ou ocultá-lo.
- **Cores individuais das luzes** e **Tamanhos individuais das luzes** atribuem uma cor ou um tamanho diferente a cada luz, em uma lista separada por vírgulas. Quando houver mais luzes do que valores, a lista recomeça:

```
#FF0000, #00FF00, #0000FF
```

| Programa de iluminação | O que as luzes fazem |
|---|---|
| **Ligado** | Todas as luzes brilham e, de vez em quando, uma delas diminui levemente de brilho, como luzes de verdade. |
| **Totalmente aceso** | Todas as luzes brilham com intensidade máxima. |
| **Metade acesa** | Todas as luzes brilham com metade da intensidade. |
| **Desligado** | Todas as luzes ficam apagadas. |
| **Ciclo** | Alterna entre Cintilar, Perseguir, Alternar e Respirar, mudando a cada 7 segundos. |
| **Cintilar** | As luzes piscam aleatoriamente. |
| **Perseguir** | Uma luz brilhante percorre o fio. |
| **Alternar** | Uma luz sim, outra não, fica acesa; depois, a outra metade assume. |
| **Respirar** | Todas as luzes aumentam e diminuem de brilho juntas, lentamente. |

## Assustador

### Teias de aranha

Teias empoeiradas ficam penduradas nos cantos superiores, com pequenas aranhas descendo pelos fios.

<img width="800" alt="Teias de aranha nos cantos superiores de uma tela inicial, com uma aranha pendurada" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_cobwebs.png?raw=true">

- **Teia esquerda** e **Teia direita** exibem ou ocultam cada teia e sua aranha.
- **Aranhas** permite que as aranhas desçam, fiquem penduradas e subam de volta. Elas fogem do mouse.
- **Frente fechada** une as pontas dos fios com uma borda, para que nenhum fio solto termine na tela.

### Brasas

Brasas brilhantes sobem da parte inferior enquanto cinzas flutuam para baixo e se acumulam.

<img width="800" alt="Brasas subindo e cinzas acumuladas nos botões de uma tela inicial à noite" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/decoration_overlay_embers.png?raw=true">

- **Cinzas no chão** adiciona uma camada espessa de cinzas ao longo da parte inferior da tela, com pontos fumegantes e brasas brilhantes.
- **Cinzas nos elementos** permite que as cinzas se acumulem nos seus elementos.

## Personalizado

### Navegador

A sobreposição Navegador exibe um site na tela inteira.

> [!IMPORTANT]
> A sobreposição Navegador precisa do mod [Rinku](https://modrinth.com/mod/rinku).

- **URL** define o site a ser exibido.
- **Consumir cliques do mouse**, **Consumir rolagem do mouse** e **Consumir pressionamentos de teclas** impedem que a entrada chegue ao menu atrás do navegador.
- **Processar cliques do mouse**, **Processar rolagem do mouse** e **Processar pressionamentos de teclas** permitem que o próprio navegador reaja à entrada.
- **Ocultar controles de vídeo**, **Repetir vídeos**, **Silenciar navegador** e **Volume de áudio/vídeo** controlam os vídeos e o som do site.

As configurações de consumo e processamento vêm ativadas por padrão, então o navegador funciona como um navegador normal na frente do seu menu. Para exibir um site apenas como plano de fundo, desative todas elas.

Os sites também podem executar ações do FancyMenu e ler marcadores de posição. Consulte [API JavaScript do navegador](/browser-api).

### Shader GLSL

A sobreposição Shader GLSL desenha seu próprio shader na tela inteira, para criar efeitos animados ou estáticos. Cole o código do shader em **Código-fonte do shader**.

Consulte [API de shader GLSL](/glsl-shader-api) para saber como escrever shaders para o FancyMenu.
