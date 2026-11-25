---
title: Perguntas frequentes
description: Perguntas frequentes.
sourceBlobSha: 4ae872e8e4a54fc6a89de7c87c8a137a89292455
---
# Perguntas frequentes

### Preciso de ajuda com um problema. Que informações devo fornecer?

Para receber a melhor ajuda possível, forneça o máximo de contexto que puder:
1.  **Uma descrição clara do problema:** O que você esperava que acontecesse e o que aconteceu de fato?
2.  **Seu arquivo `latest.log`:** Encontre-o em `<game-directory>/logs/latest.log`. **Não envie um log de falha**, a menos que isso seja solicitado especificamente; geralmente, o `latest.log` contém o contexto necessário. Use um site como https://gist.github.com para compartilhá-lo.
3.  **Sua versão do Minecraft:** (por exemplo, 1.20.1)
4.  **Seu carregador de mods e a versão dele:** (por exemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Sua versão do FancyMenu:** (por exemplo, 3.5.2)
6.  **Capturas de tela ou vídeos** do problema também podem ajudar bastante.

> [!TIP]
> Vai pedir ajuda à Alice ou a outra IA? Adicione uma [Exportação para IA](/export-for-ai) do que não está funcionando. Ela mostra à IA exatamente como tudo está configurado e já inclui as versões do Minecraft, do carregador de mods e do FancyMenu.

### Como altero a ordem das camadas dos elementos (movo algo para a frente ou para trás de outro elemento)?

- **Seus próprios elementos:** arraste as camadas no widget Camadas do editor de layouts ou clique com o botão direito em um elemento e escolha **Mover uma camada para cima** ou **Mover uma camada para baixo**. Consulte [Camadas e grupos](/layout-editor#layers-and-groups).
- **Seus elementos e os elementos do Minecraft:** não é possível alterar a ordem dos elementos do Minecraft. Para colocar todos os seus elementos atrás deles, como uma imagem de fundo atrás dos botões padrão, clique com o botão direito no fundo do editor e defina **Elementos personalizados atrás dos elementos do Minecraft** como **Ativado**.

### Posso excluir determinados botões de um modelo universal de botões?

**Não. Se um botão do modelo tiver texturas personalizadas definidas, essas texturas serão sempre compartilhadas com todos os elementos afetados. Não é possível excluir botões individuais.**

### Como faço um botão executar uma ação quando clicado?

Use um [**Script de ação**](/action-scripts).
1.  Clique com o botão direito no botão no editor.
2.  Selecione **Editar script de ação**.
3. Clique em **Adicionar ação** e escolha uma ação, como [**Abrir tela ou GUI personalizada**](/action-scripts#open-screen-or-custom-gui), [**Entrar no servidor**](/action-scripts#join-server) ou [**Definir valor da variável**](/action-scripts#set-variable-value-fm-variable).

### Posso criar uma tela de menu totalmente nova do zero?

Sim, com uma [GUI personalizada](/custom-guis):

1. Abra **Barra de menus -> Personalização -> GUIs personalizadas -> Gerenciar GUIs personalizadas** e clique em **Nova GUI**.
2. Dê a ela um identificador, como `modpack_info`, e clique em **Concluído**.
3. Abra-a com **Abrir GUI** e crie um layout para ela, como faria para qualquer outro menu.
4. Abra-a por meio de um botão com a ação [**Abrir tela ou GUI personalizada**](/action-scripts#open-screen-or-custom-gui) e o identificador dela.

### Meu jogo está demorando muito para carregar depois que ativei o pré-carregamento.

Esse comportamento é esperado. Pré-carregar recursos grandes, como animações em alta resolução ou sons, durante a inicialização aumenta naturalmente o tempo de carregamento do jogo.

### Minha animação usa muita RAM ou deixa o jogo lento!

Quadros grandes e taxas de quadros altas consomem memória e afetam o desempenho. Use quadros com dimensões próximas às que terão na tela e menos quadros por segundo. Consulte [Animações](/animations#performance). Para clipes longos com som, use um [vídeo](/video).

### O FancyMenu funciona com o OptiFine?

Não. O OptiFine **não é compatível** e é conhecido por causar problemas em muitos mods, inclusive no FancyMenu. É altamente recomendável usar alternativas modernas, como Sodium/Embeddium + Iris/Oculus.
Consulte [Alternativas ao OptiFine](/optifine-alternatives).

### Meu jogo está travando. Como descubro se há um conflito entre mods?

A melhor maneira de verificar se há um conflito entre mods é **executar o jogo somente com o FancyMenu e suas dependências** (Konkrete, Melody). Se o travamento não acontecer mais, adicione os outros mods em pequenos grupos até que o problema volte, para identificar o mod em conflito.

### Um botão de outro mod desaparece ou não funciona quando tento editá-lo.

Alguns mods adicionam widgets de uma forma que o FancyMenu não consegue detectar ou personalizar. Consulte [Elementos do Minecraft/mods](/vanilla-elements) e, para telas com listas, [Personalizar telas com rolagem](/customizing-scrollable-screens). Se o widget ainda não aparecer, o mod que o adiciona precisa expô-lo como um widget de tela compatível.

### Posso usar layouts do FancyMenu em um servidor?

Os layouts e as personalizações visuais ficam armazenados no cliente do jogador; um servidor não pode aplicá-los à força em um cliente sem configuração. Distribua-os como parte de um modpack. Instale o FancyMenu no servidor quando precisar de [comandos de servidor](/commands), [dados do FM](/fm-data), [acesso ao NBT no servidor](/nbt-data-placeholder#server-side-placeholder), regras de jogo, estruturas ou listeners do servidor.

### Qual é a diferença entre o FancyMenu v2 (para versões antigas do Minecraft) e o v3?

O FancyMenu v3 foi completamente reescrito e tem muitos recursos novos, uma arquitetura mais estável e melhor desempenho. O v2 está desatualizado, não é mais compatível e não tem muitos recursos, como placeholders avançados e scripts. É altamente recomendável usar o v3 em uma versão moderna do Minecraft (1.18.2+). Os layouts do v2 podem ser convertidos automaticamente para o v3 ao serem carregados, mas talvez seja necessário fazer alguns ajustes manualmente.

### Onde encontro layouts e modelos prontos?

A comunidade do FancyMenu compartilha configurações completas no canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) do servidor oficial do Discord ("Kekscord"). Instale-os como um perfil separado; consulte [Modelos de layout](/profiles#layout-templates).

### Como faço a entidade do jogador ser renderizada atrás dos outros elementos?

Em geral, não é possível forçar um [elemento Entidade do jogador](/elements#player-entity) a ficar atrás de elementos 2D comuns usando o [widget Camadas](/layout-editor#layers-and-groups). O renderizador desse elemento pode ignorar a ordem normal das camadas da GUI. Crie o layout levando essa limitação em conta ou use uma imagem pré-renderizada quando for essencial controlar a ordem das camadas.

### Minha entidade do jogador só tem uma perna! O que aconteceu?

Isso é uma falha visual, provavelmente causada por um conflito com outro mod que altera as animações ou os modelos dos jogadores. Confira as configurações de Pose da entidade do jogador para ver se as pernas foram giradas ou movidas por acidente.

### Como crio um intervalo entre ações em um script?

Clique com o botão direito na área do script do editor de scripts de ação, clique em **Adicionar bloco EXECUTAR MAIS TARDE** e coloque dentro dele as ações que devem aguardar. Elas serão executadas uma vez, após o tempo definido em milissegundos, e o restante do script continuará imediatamente. Consulte [Executar mais tarde](/action-scripts#execute-later).

Para ações que devem se repetir, use [Agendadores](/schedulers).

### Posso personalizar os menus do mod Create?

Não. A personalização das telas do Create está desativada intencionalmente. Consulte [Telas cuja personalização está intencionalmente desativada](/incompatibility-list#screens-where-customization-is-intentionally-disabled).

### Qual é a resolução recomendada para imagens de fundo e texturas de botões?

Planos de fundo: uma imagem padrão de 1920x1080 (1080p) é um ótimo ponto de partida e será redimensionada corretamente para a maioria dos usuários.
Botões: a maioria dos botões padrão tem cerca de 150 a 200 pixels de largura e 20 pixels de altura. Usar esse tamanho para texturas personalizadas é uma boa prática para manter a consistência.

### Existe uma maneira de abrir um menu ou executar um comando automaticamente quando um jogador conclui um objetivo do jogo (como uma missão)?
O FancyMenu tem vários [listeners de eventos do jogo integrados](/listeners), mas não há um listener genérico para todos os sistemas de missões de terceiros. Se o mod de missões aceitar recompensas em forma de comandos, use um para executar [`/openguiscreen`](/commands#openguiscreen), [`/fmvariable`](/commands#fmvariable) ou outro [comando do FancyMenu](/commands) apropriado.

### Como desativo um botão ou faço com que ele fique "acinzentado"?

Você pode controlar o estado ativo de um botão usando [requisitos](/conditions).
Clique com o botão direito no botão no editor e selecione **Controlar estado ativo**.
Adicione um requisito que precise ser atendido para que o botão fique ativo. Para desativá-lo permanentemente, use [**É número**](/conditions#is-number) para verificar se 0 é igual a 1.
O botão passará a usar a textura de "fundo inativo" e não poderá ser clicado.

### Como removo o cabeçalho e o rodapé (as barras com textura de terra) das telas com rolagem?

No editor de layouts, abra **Propriedades do layout -> Personalizações de cabeçalho/rodapé**. Defina as texturas como transparentes. Essa opção pode não estar disponível em algumas telas modificadas.

### Não consigo criar um layout "para a tela atual". O botão está acinzentado.

Ative primeiro as personalizações dessa tela: clique em **Barra de menus -> Personalização -> Personalização da tela atual** e confira se aparece **Ativado**.

### Não consigo personalizar nenhum elemento de uma tela quando a abro no editor. Ela fica vazia.

Talvez você tenha criado um [Layout universal](/universal-layouts) em vez de um layout **para a tela atual**.

Também pode ser uma [tela com rolagem](/customizing-scrollable-screens), que o FancyMenu não consegue personalizar por padrão.

Outra possibilidade é que seja uma tela de um mod que adiciona elementos de uma forma diferente da padrão, impedindo que o FancyMenu os personalize.

### Há umas caixas cinzas estranhas no meu elemento de texto.

São as barras de rolagem do [elemento de texto](/elements#text). Elas aparecem quando o texto não cabe no elemento, permitindo que os jogadores rolem o conteúdo.

- Aumente o tamanho do elemento ou encurte o texto para que elas desapareçam.
- Clique com o botão direito no elemento e abra **Barras de rolagem**. **Exibir** define quando elas aparecem: **Sempre**, apenas **Durante a rolagem** ou **Nunca**. Mesmo com **Nunca**, ainda é possível rolar usando a roda do mouse.
- No mesmo menu, as opções **Estilo do controle deslizante**, **Texturas do controle deslizante** e **Cor do controle deslizante [HEX]** alteram a aparência.

Consulte [Texto nos menus](/text-in-menus#scroll-bars) para ver todas as configurações das barras de rolagem.

### Como exibo nos meus menus as notas de atualização mais recentes do Minecraft?

Há um ótimo [projeto no GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que converte as notas de atualização do Minecraft para Markdown compatível com o FancyMenu, permitindo exibir as notas de atualização mais recentes do MC nos seus menus! Ele é atualizado diariamente para buscar novas notas.

Para exibi-las em um [elemento de texto](/elements#text), defina **Modo de origem** como **Recurso** e a origem do recurso como **Web**. Use `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`.

### Qual é a maneira mais fácil de redimensionar qualquer elemento para ocupar a tela inteira?

A maioria dos elementos tem uma opção nos menus de contexto, abertos com o botão direito, para esticá-los horizontal e verticalmente. Ao ativá-la, o elemento sempre será esticado para ocupar toda a largura e/ou altura da tela. O esticamento horizontal e o vertical podem ser ativados separadamente.

### Não consigo clicar nos botões nem interagir com os controles deslizantes quando eles ficam atrás ou na frente de um elemento de texto.

Isso acontece porque os elementos de texto são interativos por padrão (para permitir arrastar o controle deslizante ou clicar em links Markdown), então eles consomem cliques do mouse e eventos de rolagem. O melhor é simplesmente não colocar botões atrás ou na frente de elementos de texto. Se não houver outra opção, você pode desativar a interação do elemento de texto: **clique com o botão direito nele** e defina **Interativo** como **Desativado**. Tenha em mente que isso transforma o elemento de texto em um texto estático e não interativo, que não poderá mais ser rolado nem terá links clicáveis.

### Como faço para que botões e controles deslizantes não sejam mais selecionados ou recebam foco ao navegar pelas telas com as teclas de seta e Tab?

Para que não seja possível navegar até botões e controles deslizantes, **clique com o botão direito** neles e defina **Navegável** como **Desativado**. Ainda será possível clicar no botão ou controle deslizante, mas não será possível focá-lo usando as teclas de seta ou Tab.

Isso também é útil se você quiser adicionar botões ou controles deslizantes à tela de bate-papo, pois ainda poderá usar a tecla de seta para cima para percorrer mensagens antigas sem selecionar esses elementos por acidente.

### Está faltando uma opção em um dos menus de contexto do FancyMenu.

Os menus de contexto do FancyMenu (os menus que aparecem quando você clica com o botão direito em algum lugar ou interage com as barras de menu) têm rolagem. Isso significa que você pode usar a roda do mouse sobre o menu para rolar para cima ou para baixo e ver mais opções que antes não estavam visíveis.

### Não consigo personalizar a tela de título; ela continua mostrando a original quando saio do editor.

Outro mod está substituindo a `title_screen` original. Desative a tela de título personalizada desse mod nas configurações dele. Se não houver essa opção, o FancyMenu não poderá aplicar o layout à tela substituta.

### Quando tento personalizar a tela do inventário, não consigo personalizar o contêiner do inventário.

Isso é esperado. O FancyMenu não oferece suporte à edição do contêiner em si de nenhum tipo de tela de inventário (inventário do jogador, baú, bancada de trabalho etc.), pois seria muito difícil adicionar esse suporte.

Ainda é possível adicionar novos elementos a essas telas; só não é possível editar os contêineres.

Aliás, o SpiffyHUD também não ajudará nesse caso, pois serve para editar o HUD (por exemplo, a barra de itens), mas não pode editar telas (como as telas de inventário).
