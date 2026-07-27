---
title: FAQ
description: Perguntas frequentes.
---
# FAQ

### Preciso de ajuda com um problema. Que informações devo fornecer?

Para receber a melhor ajuda possível, forneça o máximo de contexto que conseguir:
1.  **Uma descrição clara do problema:** O que você esperava que acontecesse e o que realmente aconteceu?
2.  **Seu arquivo `latest.log`:** Encontre-o em `<game-directory>/logs/latest.log`. **Não envie um crash log** a menos que seja solicitado especificamente; o `latest.log` normalmente contém o contexto necessário. Use um site como https://gist.github.com ao publicá-lo.
3.  **Sua versão do Minecraft:** (ex.: 1.20.1)
4.  **Seu mod loader e versão:** (ex.: Forge 47.2.0, Fabric 0.15.7)
5.  **Sua versão do FancyMenu:** (ex.: 3.5.2)
6.  **Capturas de tela ou vídeos** do problema também podem ser muito úteis.

### Como altero a ordem de camadas dos elementos (colocar algo na frente de ou atrás de outro)?

*   **Personalizado vs. Personalizado:** Abra **Window -> Editor Widgets -> Layers** e arraste os elementos na hierarquia. Você também pode clicar com o botão direito em um elemento e usar **Move One Layer Up/Down**. Veja [Layers and Groups](./layers-and-groups).
*   **Personalizado vs. Vanilla:** Para renderizar todos os seus elementos personalizados atrás de todos os elementos vanilla (por exemplo, para colocar uma imagem de fundo atrás dos botões padrão), **clique com o botão direito no fundo do editor** e ative a opção **"Render Custom Elements Behind Vanilla"**.

### Posso excluir certos botões de um modelo universal de botão?

**Não. Se um botão de modelo tiver texturas personalizadas definidas, essas texturas serão sempre compartilhadas com todos os elementos afetados. Você não pode excluir botões individuais.**

### Como faço para que um botão execute algo ao ser clicado?

Use um [**Action Script**](./action-scripts).
1.  Clique com o botão direito no botão no editor.
2.  Selecione **Edit Action Script**.
3. Clique em **Add Action** e escolha uma ação, como [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui), [**Join Server**](./action-scripts#join-server-joinserver) ou [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

### Posso criar uma tela de menu completamente nova do zero?

Use uma [**Custom GUI**](./custom-guis).
1.  Na barra de menu, vá em **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Clique em **"New GUI"** e dê a ela um identificador exclusivo.
3.  Em seguida, você pode abrir essa nova tela vazia e criar um layout para ela, adicionando quaisquer elementos que quiser.
4. Abra a Custom GUI com a [**Open Screen or Custom GUI** action](./action-scripts#open-screen-or-custom-gui-opengui).

### Meu jogo está demorando muito para carregar depois de habilitar o pré-carregamento.

Esse comportamento é esperado. Pré-carregar recursos grandes, como animações em alta resolução ou sons, durante a inicialização naturalmente aumenta o tempo de carregamento do jogo.

### Minha animação FMA está usando RAM demais!

As animações clássicas [FMA](./fma) podem consumir muita memória quando contêm muitos quadros em alta resolução. O AFMA é mais adequado para texturas animadas grandes ou complexas. Mantenha animações FMA clássicas curtas; use [Video](./video) para reprodução de vídeo completa.

### O FancyMenu funciona com OptiFine?

Não. O OptiFine **não é compatível** e é conhecido por quebrar vários mods, incluindo o FancyMenu. É altamente recomendável usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
Veja [OptiFine Alternatives](./optifine-alternatives).

### Meu jogo está travando. Como descubro se é um conflito entre mods?

A melhor forma de verificar um conflito entre mods é **executar o jogo apenas com o FancyMenu e suas dependências** (Konkrete, Melody). Se a falha não ocorrer mais, você pode adicionar seus outros mods de volta em pequenos grupos até o problema acontecer novamente, identificando assim o mod em conflito.

### Um botão de outro mod desaparece ou não funciona quando tento editá-lo.

Alguns mods adicionam widgets de maneiras que o FancyMenu não consegue detectar ou personalizar. Verifique [Vanilla/Mod Elements](./vanilla-elements) e, para telas baseadas em listas, [Customizing Scrollable Screens](./customizing-scrollable-screens). Se o widget ainda não aparecer, o mod que o adiciona precisa expô-lo como um widget de tela compatível.

### Posso usar layouts do FancyMenu em um servidor?

Layouts e personalizações visuais são armazenados no cliente do jogador; um servidor não pode forçá-los em um cliente não configurado. Distribua-os como parte de um modpack. Instale o FancyMenu no servidor quando precisar de [server commands](./commands), [FM Data](./fm-data), [server-side NBT access](./nbt-data-placeholder#server-side-placeholder), gamerules, estruturas ou listeners do servidor.

### Qual é a diferença entre o FancyMenu v2 (para versões antigas do MC) e o v3?

O FancyMenu v3 é uma reescrita completa com muitos recursos novos, uma arquitetura mais estável e melhor desempenho. O v2 está desatualizado, não tem mais suporte e carece de muitos recursos, como placeholders avançados e scripting. É altamente recomendável usar o v3 em uma versão moderna do Minecraft (1.18.2+). Layouts do v2 podem ser convertidos automaticamente para o v3 ao carregá-los, mas talvez seja necessário fazer alguns ajustes manuais.

### Onde posso encontrar layouts e modelos prontos?

A comunidade do FancyMenu compartilha layouts no canal `#layout-templates` no servidor oficial do Discord de Keksuccino's Mods ("Kekscord").

### Como posso fazer a entidade do jogador renderizar atrás de outros elementos?

Em geral, você não pode forçar um [Player Entity element](./elements#player-entity) a ficar atrás de elementos 2D normais por meio do [Layers widget](./layers-and-groups). O renderizador dele pode ignorar a ordem normal das camadas da GUI. Crie o layout levando essa limitação em conta ou use uma imagem pré-renderizada quando for necessário manter uma ordem de camadas rigorosa.

### Minha Player Entity está com apenas uma perna! O que aconteceu?

Isso é uma falha visual, provavelmente causada por um conflito com outro mod que altera animações ou modelos de jogador. Verifique as configurações de Pose da Player Entity para ver se as pernas foram giradas ou movidas acidentalmente.

### Como crio um atraso entre ações em um script?

Use blocos [**Delay** ou **Execute Later**](./action-scripts#what-are-statements) para lógica de ação com atraso. Para lógica de fundo repetitiva, use [Schedulers](./schedulers).

### Posso personalizar menus do mod Create?

Não. A personalização é intencionalmente desativada para telas do Create. Veja [Screens where customization is intentionally disabled](./incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Qual é a resolução recomendada para imagens de fundo e texturas de botões?

Fundos: uma imagem padrão de 1920x1080 (1080p) é um ótimo ponto de partida e se adapta bem à maioria dos usuários.
Botões: a maioria dos botões vanilla tem cerca de 150 a 200 pixels de largura e 20 pixels de altura. Combinar esse tamanho em texturas personalizadas é uma boa prática para manter a consistência.

### Existe uma forma de abrir automaticamente um menu ou executar um comando quando um jogador conclui um objetivo no jogo (como uma quest)?
O FancyMenu tem muitos [listeners de eventos de jogo integrados](./listeners), mas não existe um listener genérico para cada sistema de quests de terceiros. Se o mod de quest oferecer recompensas por comando, use uma delas para executar [`/openguiscreen`](./commands#openguiscreen), [`/fmvariable`](./commands#fmvariable) ou outro [comando do FancyMenu](./commands) مناسب.

### Como faço para deixar um botão inativo ou "acinzentado"?

Você pode controlar o estado ativo de um botão usando [Loading Requirements](./conditions).
Clique com o botão direito no botão no editor e selecione **Control Active State**.
Adicione um requisito que precise ser atendido para que o botão fique ativo. Para desativá-lo permanentemente, use [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) para verificar se 0 é igual a 1.
O botão agora usará a textura "Inactive Background" e não poderá ser clicado.

### Como posso remover o cabeçalho e o rodapé (as barras com textura de terra) em telas roláveis?

No editor de layout, abra **Layout Properties -> Header/Footer Customizations**. Defina as texturas como transparentes. Essa opção pode não estar disponível em algumas telas modificadas.

### Não consigo criar um layout "for the current screen". O botão está cinza.

Você precisa habilitar primeiro as personalizações para essa tela em **menu bar -> Customization -> Current Screen Customizations -> Enabled**.

### Não consigo personalizar nenhum elemento de uma tela ao abri-la no editor. Ela fica apenas vazia.

Isso pode significar que você criou um [Universal Layout](./universal-layouts) em vez de um layout **for the current screen**.

Também pode ser uma [scrollable screen](./customizing-scrollable-screens), que o FancyMenu não consegue personalizar por padrão.

A terceira possibilidade é que seja uma tela de um mod que adiciona elementos de forma não vanilla, o que impede o FancyMenu de personalizar esses elementos.

### Há caixas cinzas estranhas no meu elemento de texto.

Essas caixas translúcidas são os seletores de rolagem do [Text element](./elements#text), não um bug de renderização.

Se você não quiser que essas caixas fiquem visíveis, você pode clicar com o botão direito no elemento e desativar completamente a rolagem OU também pode definir as texturas dos seletores como totalmente transparentes no mesmo menu de clique direito, se quiser que o elemento continue rolável.

### Como posso exibir o changelog mais recente do Minecraft nos meus menus?

Há um ótimo [projeto no GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que converte os changelogs do Minecraft para Markdown compatível com o FancyMenu, permitindo exibir o changelog mais recente do MC nos seus menus! Ele é atualizado diariamente para buscar novos changelogs.

Para exibi-lo em um [Text element](./elements#text), defina **Source Mode** como **Resource** e a origem do recurso como **Web**. Use `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Qual é a forma mais fácil de esticar qualquer elemento até o tamanho da tela?

A maioria dos elementos tem uma opção em seus menus de contexto de clique direito para esticá-los horizontal e verticalmente. Ativar isso fará com que eles sempre ocupem toda a largura e/ou altura da tela. O esticamento horizontal e vertical pode ser alternado independentemente.

### Não consigo clicar em botões nem interagir com sliders quando eles estão atrás ou na frente de um elemento de texto.

Isso acontece porque os elementos de texto são interativos por padrão (para permitir pegar o seletor de rolagem ou clicar em hyperlinks Markdown), o que significa que eles consomem cliques do mouse e eventos de rolagem. A melhor solução seria simplesmente não mover botões para trás/à frente de elementos de texto, mas, se não houver outra opção, você pode tornar o elemento de texto não interativo **clicando com o botão direito nele** e definindo **Interactable** como **Disabled**. Lembre-se de que isso transforma o elemento de texto em texto estático e não interativo, então você não poderá mais rolar nem clicar em hyperlinks.

### Como posso fazer com que botões e sliders não sejam mais selecionados/focados ao navegar em telas com as teclas de seta e Tab do teclado?

Para que botões e sliders não sejam navegáveis, você precisa **clicar com o botão direito** neles e definir **Navigable** como **Disabled**. O botão/slider ainda poderá ser clicado, mas você não conseguirá mais focá-lo com a navegação por Setas/Tab.

Isso também é útil se você quiser adicionar botões/sliders à tela de Chat, pois assim você ainda poderá usar a tecla Seta para cima para rolar pelas mensagens mais antigas sem selecionar acidentalmente botões/sliders na tela.

### Um dos menus de contexto do FancyMenu está sem uma opção que deveria estar lá.

Os menus de contexto do FancyMenu (os menus que abrem quando você clica com o botão direito em algum lugar ou interage com barras de menu) são ROLÁVEIS. Isso significa que você pode usar a roda do mouse enquanto o cursor estiver sobre o menu para rolar para cima ou para baixo, o que permite ver mais opções que antes não estavam visíveis.

### Não consigo personalizar a tela de título; ela continua mostrando a original quando saio do editor.

Outro mod está substituindo a `title_screen` original. Desative a tela de título personalizada desse mod nas configurações dele. Se ele não tiver essa opção, o FancyMenu não poderá aplicar o layout à tela substituída.
