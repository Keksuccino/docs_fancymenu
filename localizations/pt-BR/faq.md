---
title: Perguntas frequentes
description: Perguntas frequentes.
---
# Perguntas frequentes

### Preciso de ajuda com um problema. Que informações devo fornecer?

Para obter a melhor ajuda possível, forneça o máximo de contexto possível:
1.  **Uma descrição clara do problema:** O que você esperava que acontecesse e o que realmente aconteceu?
2.  **Seu arquivo `latest.log`:** Encontre-o em `<game-directory>/logs/latest.log`. **Não envie um log de crash** a menos que seja solicitado especificamente; geralmente, o `latest.log` contém o contexto necessário. Use um site como https://gist.github.com ao publicá-lo.
3.  **Sua versão do Minecraft:** (por exemplo, 1.20.1)
4.  **Seu Mod Loader e versão:** (por exemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Sua versão do FancyMenu:** (por exemplo, 3.5.2)
6.  **Capturas de tela ou vídeos** do problema também podem ser muito úteis.

### Como altero a ordem de sobreposição dos elementos (mover algo para frente ou para trás de outro elemento)?

*   **Personalizado vs. personalizado:** Abra **Window -> Editor Widgets -> Layers** e arraste os elementos na hierarquia. Você também pode clicar com o botão direito em um elemento e usar **Move One Layer Up/Down**. Consulte [Camadas e grupos](./layers-and-groups).
*   **Personalizado vs. vanilla:** Para renderizar todos os seus elementos personalizados atrás de todos os elementos vanilla (por exemplo, para colocar uma imagem de fundo atrás dos botões padrão), **clique com o botão direito no fundo do editor** e ative a opção **"Render Custom Elements Behind Vanilla"**.

### Posso excluir determinados botões de um modelo universal de botões?

**Não. Se um botão de modelo tiver texturas personalizadas definidas, essas texturas sempre serão compartilhadas com todos os elementos afetados. Não é possível excluir botões individuais.**

### Como faço um botão executar uma ação quando clicado?

Use um [**Action Script**](./action-scripts).
1.  Clique com o botão direito no botão dentro do editor.
2.  Selecione **Edit Action Script**.
3. Clique em **Add Action** e escolha uma ação, como [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) ou [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Posso criar uma tela de menu completamente nova do zero?

Use uma [**Custom GUI**](./custom-guis).
1.  Na barra de menu, acesse **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Clique em **"New GUI"** e forneça um identificador exclusivo.
3.  Depois, você poderá abrir essa nova tela vazia e criar um layout para ela, adicionando os elementos que quiser.
4. Abra a Custom GUI usando a ação [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui).

### Meu jogo está demorando muito para carregar depois que ativei o pré-carregamento.

Esse comportamento é esperado. O pré-carregamento de recursos grandes, como animações ou sons de alta resolução, durante a inicialização aumenta naturalmente o tempo de carregamento do jogo.

### Minha animação FMA está usando muita RAM!

As [animações FMA](./fma) clássicas podem consumir muita memória quando contêm muitos quadros de alta resolução. A AFMA é mais adequada para texturas animadas grandes ou complexas. Mantenha as animações FMA clássicas curtas; use [Video](./video) para reproduzir vídeos completos.

### O FancyMenu funciona com o OptiFine?

Não. O OptiFine **não é compatível** e é conhecido por quebrar muitos mods, incluindo o FancyMenu. É altamente recomendável usar alternativas modernas, como Sodium/Embeddium + Iris/Oculus.
Consulte [Alternativas ao OptiFine](./optifine-alternatives).

### Meu jogo está fechando. Como descubro se é um conflito entre mods?

A melhor maneira de verificar se há um conflito entre mods é **executar o jogo apenas com o FancyMenu e suas dependências** (Konkrete, Melody). Se o crash não ocorrer mais, adicione os outros mods novamente em pequenos grupos até que o crash volte a acontecer, identificando assim o mod conflitante.

### Um botão de outro mod desaparece ou não funciona quando tento editá-lo.

Alguns mods adicionam widgets de maneiras que o FancyMenu não consegue detectar ou personalizar. Consulte [Elementos vanilla/de mods](./vanilla-elements) e, para telas baseadas em listas, [Personalizando telas roláveis](./customizing-scrollable-screens). Se o widget ainda não aparecer, o mod que o adiciona precisa disponibilizá-lo como um widget de tela compatível.

### Posso usar layouts do FancyMenu em um servidor?

Os layouts e as personalizações visuais são armazenados no cliente do jogador; um servidor não pode impô-los a um cliente não configurado. Distribua-os como parte de um modpack. Instale o FancyMenu no servidor quando precisar de [comandos do servidor](./commands), [FM Data](./fm-data), [acesso a NBT no lado do servidor](./nbt-data-placeholder#server-side-placeholder), regras do jogo, estruturas ou listeners do servidor.

### Qual é a diferença entre o FancyMenu v2 (para versões antigas do MC) e o v3?

O FancyMenu v3 é uma reescrita completa, com muitos recursos novos, uma arquitetura mais estável e melhor desempenho. A v2 está desatualizada, não recebe mais suporte e não possui muitos recursos, como placeholders avançados e scripts. É altamente recomendável usar a v3 em uma versão moderna do Minecraft (1.18.2+). Os layouts da v2 podem ser convertidos automaticamente para a v3 ao serem carregados, mas talvez seja necessário fazer alguns ajustes manuais.

### Onde posso encontrar layouts e modelos prontos?

A comunidade do FancyMenu compartilha layouts no canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) do servidor oficial do Discord do Keksuccino's Mods ("Kekscord").

### Como faço a entidade do jogador ser renderizada atrás de outros elementos?

Em geral, não é possível forçar um [elemento Entidade do jogador](./elements#player-entity) a ficar atrás de elementos 2D comuns por meio do widget [Camadas](./layers-and-groups). O renderizador da entidade pode ignorar a ordem normal das camadas da GUI. Planeje o layout levando essa limitação em conta ou use uma imagem pré-renderizada quando for necessário manter uma ordem de camadas rígida.

### Minha entidade do jogador tem apenas uma perna! O que aconteceu?

Isso é um erro visual, provavelmente causado por um conflito com outro mod que altera as animações ou os modelos dos jogadores. Verifique as configurações de Pose da Entidade do jogador para ver se as pernas foram giradas ou movidas acidentalmente.

### Como crio um atraso entre ações em um script?

Use os blocos [**Delay** ou **Execute Later**](./action-scripts#what-are-statements) para lógica de ações atrasadas. Para lógica repetitiva em segundo plano, use [Agendadores](./schedulers).

### Posso personalizar menus do mod Create?

Não. A personalização está intencionalmente desativada para as telas do Create. Consulte [Telas nas quais a personalização está intencionalmente desativada](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Qual é a resolução recomendada para imagens de fundo e texturas de botões?

Fundos: uma imagem padrão de 1920x1080 (1080p) é um ótimo ponto de partida e será redimensionada adequadamente para a maioria dos usuários.
Botões: a maioria dos botões vanilla tem aproximadamente 150–200 pixels de largura e 20 pixels de altura. Usar esse tamanho nas texturas personalizadas é uma boa prática para manter a consistência.

### Existe uma maneira de abrir automaticamente um menu ou executar um comando quando um jogador conclui um objetivo no jogo (como uma missão)?
O FancyMenu possui vários [listeners de eventos do jogo integrados](./listeners), mas não há um listener genérico para todos os sistemas de missões de terceiros. Se o mod de missões aceitar recompensas em forma de comandos, use uma delas para executar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) ou outro [comando adequado do FancyMenu](./commands).

### Como faço um botão ficar inativo ou "acinzentado"?

Você pode controlar o estado ativo de um botão usando [Requisitos de carregamento](./conditions).
Clique com o botão direito no botão dentro do editor e selecione **Control Active State**.
Adicione um requisito que precise ser atendido para que o botão fique ativo. Para desativá-lo permanentemente, use [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para verificar se 0 é igual a 1.
O botão passará a usar sua textura de "Inactive Background" e não poderá ser clicado.

### Como removo o cabeçalho e o rodapé (as barras de textura de terra) das telas roláveis?

No editor de layout, abra **Layout Properties -> Header/Footer Customizations**. Defina as texturas como transparentes. Essa opção pode não estar disponível em algumas telas modificadas.

### Não consigo criar um layout "para a tela atual". O botão está acinzentado.

Primeiro, é necessário ativar as personalizações dessa tela em **menu bar -> Customization -> Current Screen Customizations -> Enabled**.

### Não consigo personalizar nenhum elemento de uma tela ao abri-la no editor. Ela aparece apenas como uma tela vazia.

Isso pode significar que você criou um [Layout universal](./universal-layouts), em vez de um layout **para a tela atual**.

Também pode ser uma [tela rolável](./customizing-scrollable-screens), que o FancyMenu não consegue personalizar por padrão.

A terceira possibilidade é que seja uma tela de um mod que adiciona elementos de uma maneira diferente da vanilla, fazendo com que o FancyMenu não consiga personalizar esses elementos.

### Há caixas cinzas estranhas no meu elemento de texto.

Essas caixas translúcidas são as alças de rolagem do [elemento de texto](./elements#text), não um erro de renderização.

Se não quiser que essas caixas fiquem visíveis, você pode clicar com o botão direito no elemento e desativar completamente a rolagem OU definir as texturas das alças como totalmente transparentes no mesmo menu do botão direito, caso ainda queira que o elemento possa ser rolado.

### Como exibo o changelog mais recente do Minecraft nos meus menus?

Existe um excelente [projeto no GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que converte os changelogs do Minecraft para Markdown compatível com o FancyMenu, permitindo exibir o changelog mais recente do MC nos seus menus! Ele é atualizado diariamente para buscar novos changelogs.

Para exibi-lo em um [elemento de texto](./elements#text), defina **Source Mode** como **Resource** e a origem do recurso como **Web**. Use `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Qual é a maneira mais fácil de redimensionar qualquer elemento para o tamanho da tela?

A maioria dos elementos possui uma opção nos menus de contexto do botão direito para estendê-los horizontal e verticalmente. Ativá-la fará com que eles sempre ocupem toda a largura e/ou altura da tela. O redimensionamento horizontal e vertical pode ser ativado de forma independente.

### Não consigo clicar em botões nem interagir com controles deslizantes quando eles estão atrás ou na frente de um elemento de texto.

Isso acontece porque os elementos de texto são interativos por padrão (para permitir agarrar a alça de rolagem ou clicar em hiperlinks Markdown), o que faz com que consumam cliques do mouse e eventos de rolagem. O ideal é simplesmente não mover botões para trás ou para a frente de elementos de texto, mas, se não houver alternativa, você pode tornar o elemento de texto não interativo **clicando nele com o botão direito** e definindo **Interactable** como **Disabled**. Lembre-se de que isso transforma o elemento de texto em um texto estático e não interativo, portanto não será mais possível rolá-lo nem clicar em hiperlinks.

### Como faço para que botões e controles deslizantes não sejam mais selecionados ou focalizados ao navegar pelas telas usando as teclas de seta e Tab?

Para impedir que botões e controles deslizantes possam ser navegados, **clique neles com o botão direito** e defina **Navigable** como **Disabled**. O botão ou controle deslizante continuará podendo ser clicado, mas não será mais possível focalizá-lo usando a navegação pelas teclas de seta ou Tab.

Isso também é útil se você quiser adicionar botões ou controles deslizantes à tela de bate-papo, pois ainda poderá usar a tecla de seta para cima para percorrer mensagens antigas sem selecionar acidentalmente botões ou controles deslizantes na tela.

### Está faltando uma opção que deveria existir em um dos menus de contexto do FancyMenu.

Os menus de contexto do FancyMenu (os menus que abrem quando você clica com o botão direito em algum lugar ou interage com as barras de menu) **podem ser rolados**. Isso significa que você pode usar a roda do mouse enquanto o cursor estiver sobre o menu para rolar para cima ou para baixo e ver mais opções que antes não estavam visíveis.

### Não consigo personalizar a tela de título; ela continua mostrando a original quando saio do editor.

Outro mod está substituindo a `title_screen` original. Desative a tela de título personalizada desse mod nas configurações dele. Se não houver essa opção, o FancyMenu não poderá aplicar o layout à tela substituta.
