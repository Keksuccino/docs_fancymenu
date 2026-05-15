---
title: Animador de Elementos
description: Como animar elementos com keyframes usando o Animador de Elementos.
---

# Animador de Elementos

O **Animator** é um elemento que permite animar outros elementos. Com esse elemento, você pode alterar suavemente o tamanho, a posição e o ponto de ancoragem de outro elemento ao longo do tempo usando keyframes. Keyframes são como instantâneos que registram como o elemento deve parecer em um momento específico. O elemento Animator então reproduz esses instantâneos em ordem para criar um movimento suave.

> O **Animador de Elementos** permite controlar a **posição, o tamanho e o ponto de ancoragem** dos elementos. **NÃO** é possível controlar nenhuma outra configuração dos elementos, como opacidade, visibilidade, rotação etc.!
{.is-warning}

# Tutorial em Vídeo

Como muitos de vocês ficaram um pouco confusos sobre como o animator funciona, eu fiz um pequeno vídeo mostrando como usá-lo.

[FancyMenu | Como Usar o Editor de Elementos - YouTube](https://www.youtube.com/watch?v=F9S8cIPssww) (youtu.be/F9S8cIPssww)

<a href="https://www.youtube.com/watch?v=F9S8cIPssww" target="_blank" rel="noopener noreferrer">
  <img width="636" alt="Screenshot_2" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/element_animator_video_thumbnail.png" />
</a>

# Adicionando o Elemento Animator

1. **Clique com o botão direito no fundo:**  
   No editor de layout, clique com o botão direito no fundo.

2. **Selecione Novo Elemento -> Element Animator:**  
   No menu que aparecer, vá em **New Element** e clique em **Element Animator**. Isso adiciona o elemento Animator ao seu layout.

3. **Configure-o:**  
   Depois de adicionar, o elemento Animator aparece com suas configurações padrão. Você pode alterar opções como repetição ou cor clicando com o botão direito no Animator e escolhendo no menu.

# Gerenciando Keyframes

Keyframes são como marcadores que dizem ao Animator como o elemento deve parecer em um determinado momento.

## Abrindo o Editor de Keyframes

- **Abra o editor:**  
   Clique com o botão direito no elemento Animator e escolha **Edit Keyframes** (ou **Manage Keyframes**). Isso abre uma tela onde você pode adicionar, editar ou excluir keyframes.

## Gravando e Adicionando Keyframes

- **Inicie a gravação:**  
   No editor de keyframes, pressione a tecla **`R`** para iniciar a gravação. Durante a gravação, a caixa de pré-visualização muda de cor para indicar que está ativa.
  
- **Altere a pré-visualização:**  
   Mova ou redimensione a caixa de pré-visualização para definir a aparência desejada. No modo de offset, a pré-visualização permanece centralizada em uma mira, então as alterações são mostradas como offsets.
  
- **Adicione um keyframe:**  
   Pressione a tecla **`K`** para salvar a aparência atual como um keyframe. Esse keyframe salva a posição, o tamanho e as configurações de ancoragem da pré-visualização.

## Editando Keyframes

- **Selecione um keyframe:**  
   Clique em um marcador de keyframe na linha do tempo. Você também pode segurar **Ctrl** e clicar para selecionar mais de um.
  
- **Mova um keyframe:**  
   Arraste o marcador do keyframe para a esquerda ou para a direita para alterar seu tempo. Você também pode usar:
  - **Seta para a esquerda:** para movê-lo 100 ms para trás.
  - **Seta para a direita:** para movê-lo 100 ms para frente.
  
- **Ajuste fino da pré-visualização:**  
   Quando um keyframe está selecionado, ajuste a caixa de pré-visualização movendo-a ou redimensionando-a. Use **Ctrl + Z** para desfazer e **Ctrl + Y** para refazer as alterações, se necessário.

## Removendo Keyframes

- **Excluir um keyframe:**  
   Selecione um keyframe e pressione a tecla **Delete** para removê-lo.
  
- **Excluir vários keyframes:**  
   Você pode selecionar vários keyframes (por exemplo, usando **Ctrl + A** para selecionar todos) e pressionar Delete para removê-los todos.

## Suavização de Keyframes

A suavização de keyframes é um recurso que ajuda a espaçar os keyframes de forma uniforme. Isso faz sua animação parecer mais consistente e suave.

- **Selecione vários keyframes:**  
   Primeiro, selecione dois ou mais keyframes que você quer suavizar (use **Ctrl + Clique** ou **Ctrl + A**).

- **Clique no botão de suavização:**  
   Na barra de ferramentas inferior do editor de keyframes, clique no botão **Distance Smoothing**.

- **Digite uma nova distância:**  
   Uma pequena caixa de entrada aparecerá. Digite um valor (em milissegundos) para definir o mesmo intervalo de tempo entre cada keyframe selecionado.

- **Aplique a suavização:**  
   Pressione Enter para aplicar a suavização. Os keyframes serão ajustados para que a diferença de tempo entre eles fique uniforme.

# Visualizando sua Animação

Depois de gravar keyframes, você pode ver como sua animação ficará:

- **Reproduza a animação:**  
   No editor de keyframes, pressione a tecla **`P`** ou clique no botão de reprodução. A pré-visualização começará do início e mostrará como a caixa de pré-visualização muda ao longo do tempo.
  
- **Observação sobre repetição:**  
   أثناء a pré-visualização no editor de keyframes, a animação **não** ficará em loop. Isso significa que ela é reproduzida do início ao fim apenas uma vez. O loop só ficará ativo quando o elemento Animator for aplicado a um elemento de destino no layout final.
  
- **Pause a pré-visualização:**  
   Pressione a tecla **`P`** novamente para pausar a animação se quiser parar em um ponto específico.
  
- **Arraste a barra de progresso:**  
   Se disponível, você pode arrastar o marcador da linha do tempo para verificar como a animação fica em qualquer momento específico.

# Escolhendo Elementos de Destino

Depois de configurar seus keyframes, você precisa escolher quais elementos do layout serão animados:

1. **Abra o Gerenciador de Destinos:**  
   Clique com o botão direito no elemento Animator e escolha **Manage Targets**.
  
2. **Adicione destinos:**  
   Clique em **Add Target** para ver uma lista de elementos disponíveis. Escolha aqueles que você quer animar.
  
3. **Remova destinos:**  
   Para remover um destino, abra o gerenciador e clique em **Remove Target**.

Quando a animação for reproduzida no layout final, o Animator usará seus keyframes para alterar o tamanho, a posição e mais dos elementos escolhidos. A repetição será aplicada aqui, se você a tiver configurado.

# Atalhos de Teclado

Use estes atalhos no editor de keyframes para trabalhar mais rápido:

- **Tecla `R`:** Inicia ou para a gravação.
- **Tecla `T`:** Pausa ou retoma a gravação.
- **Tecla `P`:** Reproduz ou pausa a pré-visualização da animação.
- **Tecla `K`:** Adiciona um novo keyframe no tempo atual.
- **Setas Esquerda/Direita:**  
  - **Seta para a esquerda:** Move um keyframe 100 ms para trás.
  - **Seta para a direita:** Move um keyframe 100 ms para frente.
- **Tecla Delete:** Remove o(s) keyframe(s) selecionado(s).
- **Ctrl + A:** Seleciona todos os keyframes.
- **Ctrl + Z:** Desfaz a última alteração.
- **Ctrl + Y:** Refaz a alteração que você acabou de desfazer.
- **Ctrl + arrastar keyframes**: Arrasta vários keyframes selecionados ao mesmo tempo.

# Configurações e Dicas Extras

- **Loop da animação:**  
   Você pode configurar o Animator para repetir em loop. Quando o loop está ativado, a animação reinicia após o último keyframe — mas observe que isso só acontece para o elemento de destino final. Na pré-visualização do editor de keyframes, o loop não ocorre.
  
- **Ignorar tamanho/posição:**  
   Se você não quiser que os keyframes alterem o tamanho ou a posição de um elemento, desative essas opções.

- **Offsets de tempo:**
   O FancyMenu 3.9.0 adiciona offsets de tempo para elementos controlados. Você pode aplicar offsets de tempo individuais aos elementos de destino ou usar offsets de tempo aleatórios em um intervalo configurado, para que uma animação possa começar em horários ligeiramente diferentes para cada destino.
  
- **Modo de offset:**  
   No modo de offset, as animações são aplicadas como alterações em relação à posição original do elemento. A pré-visualização é exibida centralizada em uma mira.
  
- **Desfazer e refazer:**  
   Use **Ctrl + Z** para desfazer e **Ctrl + Y** para refazer alterações.
  
- **Confira a ordem:**  
   Certifique-se de que seus keyframes estejam na ordem correta por tempo. O sistema os classifica automaticamente, mas, se você mover um, verifique novamente a ordem.
  
- **Pré-visualize as alterações:**  
   Use o botão de reprodução ou a tecla **`P`** para ver sua animação em ação antes de salvá-la.

# Conclusão

Seguindo estes passos simples, você pode adicionar um elemento Animator ao seu layout e criar animações suaves. Seja gravando alterações ao vivo com a pré-visualização, ajustando keyframes com o teclado, escolhendo quais elementos animar ou visualizando sua animação para ver como ela fica, o elemento Animator oferece uma maneira fácil de dar vida aos seus menus personalizados.

Boa animação!
