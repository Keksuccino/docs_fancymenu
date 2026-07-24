---
title: Animador de Elementos
description: Como animar elementos com keyframes usando o Animador de Elementos.
---
# Animador de Elementos

O **Animator** é um elemento que permite animar outros elementos. Com ele, você pode alterar suavemente o tamanho, a posição e o ponto de ancoragem de outro elemento ao longo do tempo usando keyframes. Keyframes são como instantâneos que capturam como o elemento deve ficar em um momento específico. O elemento Animator então reproduz esses instantâneos em ordem para criar um movimento suave.

> [!WARNING]
> O **Animador de Elementos** permite controlar a **posição, o tamanho e o ponto de ancoragem** dos elementos. **NÃO** é possível controlar nenhuma outra configuração dos elementos, como opacidade, visibilidade, rotação etc.!

# Tutorial em Vídeo

Como muitas pessoas ficaram um pouco confusas sobre como o animator funciona, fiz um pequeno vídeo mostrando como usá-lo.

[FancyMenu | Como Usar o Editor de Elementos - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Adicionando o Elemento Animator

1. **Clique com o botão direito no fundo:**  
   No editor de layout, clique com o botão direito no fundo.

2. **Selecione Novo Elemento -> Element Animator:**  
   No menu que aparecer, vá em **Novo Elemento** e clique em **Element Animator**. Isso adiciona o elemento Animator ao seu layout.

3. **Configure-o:**  
   Após adicionar, o elemento Animator aparece com as configurações padrão. Você pode alterar opções como repetição ou cor clicando com o botão direito no Animator e escolhendo no menu.

# Gerenciando Keyframes

Keyframes são como marcadores que dizem ao Animator como o elemento deve parecer em um determinado momento.

## Abrindo o Editor de Keyframes

- **Abra o Editor:**  
  Clique com o botão direito no elemento Animator e escolha **Editar Keyframes** (ou **Gerenciar Keyframes**). Isso abre uma tela onde você pode adicionar, editar ou excluir keyframes.

## Gravando e Adicionando Keyframes

- **Inicie a Gravação:**  
  No editor de keyframes, pressione a tecla **`R`** para começar a gravar. أثناء a gravação, a caixa de pré-visualização muda de cor para mostrar que está ativa.
  
- **Altere a Pré-visualização:**  
  Mova ou redimensione a caixa de pré-visualização para definir o visual desejado. No modo de offset, a pré-visualização permanece centralizada em uma mira, de modo que as alterações são mostradas como offsets.
  
- **Adicione um Keyframe:**  
  Pressione a tecla **`K`** para salvar o visual atual como um keyframe. Esse keyframe salva a posição, o tamanho e as configurações de ancoragem da pré-visualização.

## Editando Keyframes

- **Selecione um Keyframe:**  
  Clique em um marcador de keyframe na linha do tempo. Você também pode manter **Ctrl** pressionado e clicar para selecionar mais de um.
  
- **Mova um Keyframe:**  
  Arraste o marcador do keyframe para a esquerda ou direita para alterar seu tempo. Você também pode usar:
  - **Seta para a Esquerda:** para movê-lo 100 ms para trás.
  - **Seta para a Direita:** para movê-lo 100 ms para frente.
  
- **Ajuste Fino da Pré-visualização:**  
  Quando um keyframe estiver selecionado, ajuste a caixa de pré-visualização movendo-a ou redimensionando-a. Use **Ctrl + Z** para desfazer e **Ctrl + Y** para refazer as alterações, se necessário.

## Removendo Keyframes

- **Exclua um Keyframe:**  
  Selecione um keyframe e pressione a tecla **Delete** para removê-lo.
  
- **Exclua Vários Keyframes:**  
  Você pode selecionar vários keyframes (por exemplo, usando **Ctrl + A** para selecionar todos) e pressionar Delete para removê-los todos.

## Suavização de Keyframes

A suavização de keyframes é um recurso que ajuda a espaçar os keyframes de forma uniforme. Isso faz com que sua animação pareça mais consistente e suave.

- **Selecione Vários Keyframes:**  
  Primeiro, selecione dois ou mais keyframes que você deseja suavizar (use **Ctrl + Clique** ou **Ctrl + A**).

- **Clique no Botão de Suavização:**  
  Na barra de ferramentas inferior do editor de keyframes, clique no botão **Distance Smoothing**.

- **Digite uma Nova Distância:**  
  Uma pequena caixa de entrada aparecerá. Digite um valor (em milissegundos) para definir o mesmo intervalo de tempo entre cada keyframe selecionado.

- **Aplique a Suavização:**  
  Pressione Enter para aplicar a suavização. Os keyframes serão ajustados para que a diferença de tempo entre eles fique uniforme.

# Pré-visualizando Sua Animação

Depois de gravar os keyframes, você pode ver como sua animação ficará:

- **Reproduza a Animação:**  
  No editor de keyframes, pressione a tecla **`P`** ou clique no botão de reproduzir. A pré-visualização começará do início e mostrará como a caixa de pré-visualização muda ao longo do tempo.
  
- **Observação sobre Repetição:**  
  Ao pré-visualizar no editor de keyframes, a animação **não** ficará em loop. Isso significa que ela é reproduzida do início ao fim apenas uma vez. A repetição só ficará ativa quando o elemento Animator for aplicado a um elemento-alvo no layout final.
  
- **Pause a Pré-visualização:**  
  Pressione a tecla **`P`** novamente para pausar a animação se quiser parar em um determinado ponto.
  
- **Arraste a Barra de Progresso:**  
  Se disponível, você pode arrastar o marcador da linha do tempo para verificar como a animação fica em qualquer momento específico.

# Escolhendo Elementos de Destino

Depois de configurar seus keyframes, você precisa escolher quais elementos do layout serão animados:

1. **Abra o Gerenciador de Destinos:**  
   Clique com o botão direito no elemento Animator e escolha **Gerenciar Destinos**.
  
2. **Adicione Destinos:**  
   Clique em **Adicionar Destino** para ver uma lista dos elementos disponíveis. Escolha os que você quer animar.
  
3. **Remova Destinos:**  
   Para remover um destino, abra o gerenciador e clique em **Remover Destino**.

Quando a animação for reproduzida no layout final, o Animator usará seus keyframes para alterar o tamanho, a posição e mais dos elementos escolhidos. A repetição será aplicada aqui, se você a tiver configurado.

# Atalhos de Teclado

Use estes atalhos no editor de keyframes para trabalhar mais rápido:

- **Tecla `R`:** Inicia ou para a gravação.
- **Tecla `T`:** Pausa ou retoma a gravação.
- **Tecla `P`:** Reproduz ou pausa a pré-visualização da animação.
- **Tecla `K`:** Adiciona um novo keyframe no tempo atual.
- **Teclas de Seta Esquerda/Direita:**  
  - **Seta para a Esquerda:** Move um keyframe 100 ms para trás.
  - **Seta para a Direita:** Move um keyframe 100 ms para frente.
- **Tecla Delete:** Remove o(s) keyframe(s) selecionado(s).
- **Ctrl + A:** Seleciona todos os keyframes.
- **Ctrl + Z:** Desfaz sua última alteração.
- **Ctrl + Y:** Refaz a alteração que você acabou de desfazer.
- **Ctrl + Arrastar Keyframe**: Arrasta vários keyframes selecionados ao mesmo tempo.

# Configurações e Dicas Extras

- **Repetir Animação:**  
  Você pode configurar o Animator para repetir. Quando a repetição estiver ativada, a animação recomeçará após o último keyframe — mas observe que isso só acontece para o elemento-alvo final. Na pré-visualização do editor de keyframes, a repetição não ocorre.
  
- **Ignorar Tamanho/Posição:**  
  Se você não quiser que os keyframes alterem o tamanho ou a posição de um elemento, desative essas opções.

- **Offsets de Tempo:**
  Você pode aplicar offsets de tempo a elementos-alvo individuais ou usar offsets de tempo aleatórios em um intervalo configurado, para que uma animação comece em momentos diferentes para cada alvo.
  
- **Modo de Offset:**  
  No modo de offset, as animações são aplicadas como alterações a partir da posição original do elemento. A pré-visualização é mostrada centralizada em uma mira.
  
- **Desfazer e Refazer:**  
  Use **Ctrl + Z** para desfazer e **Ctrl + Y** para refazer alterações.
  
- **Verifique a Ordem:**  
  Certifique-se de que seus keyframes estejam na ordem correta por tempo. O sistema os organiza para você, mas se você mover um, confira novamente a ordem.
  
- **Pré-visualize as Alterações:**  
  Use o botão de reproduzir ou a tecla **`P`** para ver sua animação em ação antes de salvá-la.
