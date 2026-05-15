---
title: FAQ
description: Perguntas frequentes.
---

# FAQ

### Preciso de ajuda com um problema. Que informações devo fornecer?
Para receber a melhor ajuda possível, forneça o máximo de contexto possível:
1.  **Uma descrição clara do problema:** O que você esperava que acontecesse e o que realmente aconteceu?
2.  **Seu arquivo `latest.log`:** Este é o arquivo mais importante para diagnóstico. Encontre-o na pasta `/logs/` da sua instância. **Não envie um crash log**, a menos que seja especificamente solicitado; o `latest.log` é muito mais útil. Use um site como https://gist.github.com para compartilhá-lo.
3.  **Sua versão do Minecraft:** (por exemplo, 1.20.1)
4.  **Seu mod loader e versão:** (por exemplo, Forge 47.2.0, Fabric 0.15.7)
5.  **Sua versão do FancyMenu:** (por exemplo, 3.5.2)
6.  **Capturas de tela ou vídeos** do problema também podem ser muito úteis.

### Como faço para alterar a ordem de camadas dos elementos (colocar algo na frente ou atrás de outro)?
*   **Personalizado vs. Personalizado:** Para alterar a ordem de renderização dos seus próprios elementos personalizados, use o **widget Layers**. Você pode abri-lo pela barra de menus: **Window -> Widgets -> Layers**. A partir daí, você pode arrastar os elementos para cima ou para baixo na hierarquia. Você também pode clicar com o botão direito em um elemento e usar "Move One Layer Up/Down".
*   **Personalizado vs. Vanilla:** Para renderizar todos os seus elementos personalizados atrás de todos os elementos vanilla (por exemplo, para colocar uma imagem de fundo atrás dos botões padrão), **clique com o botão direito no fundo do editor** e ative a opção **"Render Custom Elements Behind Vanilla"**.

### Posso excluir certos botões de um template universal de botão?
**Não. Se um botão de template tiver texturas personalizadas definidas, essas texturas sempre serão compartilhadas com todos os elementos afetados. Você não pode excluir botões individuais.**

### Como faço para que um botão faça algo quando clicado?
Use um **Action Script**.
1.  Clique com o botão direito no botão no editor.
2.  Selecione **Edit Action Script**.
3.  Clique em **Add Action** e escolha na lista (por exemplo, `Open Screen or Custom GUI`, `Join Server`, `Set Variable Value`).
*   Mais informações: [Action Scripts](https://docs.fancymenu.net/en/action-scripts)

### Posso criar uma tela de menu completamente nova do zero?
Sim, isso é feito usando **Custom GUIs**.
1.  Na barra de menus, vá em **Customization -> Custom GUIs -> Manage Custom GUIs**.
2.  Clique em **"New GUI"** e dê a ela um identificador exclusivo.
3.  Em seguida, você pode abrir essa nova tela vazia e criar um layout para ela, adicionando quaisquer elementos que desejar.
4.  Depois, essa Custom GUI pode ser aberta por meio de uma ação de botão.
*   Mais informações: [Custom GUIs](https://docs.fancymenu.net/en/custom-guis)

### Meu jogo está demorando muito para carregar depois de ativar o pré-carregamento.
Isso é um comportamento esperado. Pré-carregar recursos grandes, como animações ou sons em alta resolução, durante a inicialização aumentará naturalmente o tempo de carregamento do jogo.

### Minha animação FMA está consumindo RAM demais!
Arquivos FMA clássicos podem consumir muita memória quando contêm muitos quadros em alta resolução. O FancyMenu 3.9.0 adiciona o AFMA, que é muito melhor para texturas animadas grandes ou complexas. Para arquivos FMA clássicos, mantenha as animações curtas e evite contagens de quadros/resoluções muito altas. Animações foram feitas para loops decorativos curtos, não para reproduzir vídeos completos.

### O FancyMenu funciona com OptiFine?
Não. O OptiFine **não é compatível** e é conhecido por quebrar vários mods, incluindo o FancyMenu. É altamente recomendado usar alternativas modernas como Sodium/Embeddium + Iris/Oculus.
*   Mais informações: [OptiFine Alternatives](https://docs.fancymenu.net/en/optifine-alternatives)

### Meu jogo está crashando. Como descubro se é conflito de mods?
A melhor forma de verificar um conflito de mods é **rodar o jogo apenas com o FancyMenu e suas dependências** (Konkrete, Melody). Se o crash não ocorrer mais, você pode adicionar os outros mods de volta em pequenos grupos até que o crash aconteça novamente para identificar o mod conflitante.

### Um botão de outro mod desaparece ou não funciona quando tento editá-lo.
Isso normalmente significa que o outro mod adiciona seus botões de uma forma não padrão, com a qual o FancyMenu não consegue interagir. Esse é um problema que o desenvolvedor do outro mod precisaria corrigir. O FancyMenu não pode personalizar elementos que não consegue "ver".

### Posso usar layouts do FancyMenu em um servidor?
O FancyMenu é um mod do lado do cliente. Todos os layouts e personalizações ficam no cliente do jogador. Você não pode colocar layouts em um servidor para forçar os jogadores a vê-los. No entanto, você pode distribuir sua pasta `config/fancymenu` como parte de um modpack. Se quiser usar comandos como `/fmvariable` ou `/openguiscreen` a partir do servidor, então o FancyMenu (ou o plugin Spigot dele) precisa estar instalado no servidor.

### Qual é a diferença entre o FancyMenu v2 (para versões antigas do MC) e o v3?
O FancyMenu v3 é uma reescrita completa, com muitos recursos novos, uma arquitetura mais estável e melhor desempenho. O v2 está desatualizado, não recebe mais suporte e não tem muitos recursos, como placeholders avançados e scripting. É altamente recomendado usar o v3 em uma versão moderna do Minecraft (1.18.2+). Layouts do v2 podem ser convertidos automaticamente para o v3 quando você os carrega, mas algumas correções manuais podem ser necessárias.

### Onde posso encontrar layouts e templates prontos?
A comunidade do FancyMenu compartilha layouts no canal `#layout-templates` no servidor oficial do Discord de mods do Keksuccino.

### Como posso fazer o Player Entity renderizar atrás de outros elementos?
Você não pode. Devido à forma como o Minecraft renderiza entidades, o elemento Player Entity quase sempre será renderizado na frente de outros elementos 2D, independentemente das configurações de camada.

### Meu Player Entity ficou com apenas uma perna! O que aconteceu?
Isso é uma falha visual, provavelmente causada por um conflito com outro mod que altera animações ou modelos de jogador. Verifique as configurações de Pose do Player Entity para ver se as pernas foram giradas ou movidas acidentalmente.

### Como faço para criar um atraso entre ações em um script?
O FancyMenu 3.9.0 adiciona blocos **Delay** e **Execute Later** aos action scripts. Use esses blocos para a maioria da lógica de ações com atraso. Para lógica recorrente em segundo plano, use [Schedulers](https://docs.fancymenu.net/en/schedulers).

### Posso personalizar menus do mod Create?
Não. O FancyMenu tem incompatibilidades conhecidas com as GUIs complexas do Create. A personalização das telas do Create foi desativada intencionalmente para evitar crashes.

### Por que botões do mod X desaparecem no editor?
Isso significa que o mod adiciona seus botões de uma forma personalizada, não vanilla. O FancyMenu não consegue "ver" ou interagir com esses elementos, então não pode personalizá-los. O desenvolvedor do outro mod precisaria mudar a forma como adiciona seus botões para que eles sejam compatíveis.

### Qual é a resolução recomendada para imagens de fundo e texturas de botões?
Fundos: uma imagem padrão de 1920x1080 (1080p) é um ótimo ponto de partida e será redimensionada bem para a maioria dos usuários.
Botões: a maioria dos botões vanilla tem cerca de 150-200 pixels de largura e 20 pixels de altura. Combinar esse tamanho em texturas personalizadas é uma boa prática para manter a consistência.

### Existe uma forma de abrir automaticamente um menu ou executar um comando quando um jogador completa um objetivo no jogo (como uma quest)?
O FancyMenu, por si só, não consegue detectar eventos do jogo como esse. No entanto, você pode integrá-lo com um mod de quests como o FTB Quests. A maioria dos mods de quests permite executar um comando como recompensa de quest. Você definiria a recompensa para executar o comando `/openguiscreen` ou `/fmvariable` para interagir com seus menus.

### Como faço para deixar um botão inativo ou "acinzentado"?
Você pode controlar o estado ativo de um botão usando Loading Requirements.
Clique com o botão direito no botão no editor e selecione "Active State".
Adicione um requisito que precisa ser atendido para o botão ficar ativo. Por exemplo, para desativar permanentemente um botão, você pode adicionar um requisito Is Number que verifique se 0 é igual a 1 (o que é sempre falso).
Agora o botão usará sua textura de "Inactive Background" e não poderá ser clicado.

### Como posso remover o cabeçalho e o rodapé (as barras de textura de terra) em telas roláveis?
No FancyMenu v3, você pode personalizá-los. No editor de layout, clique com o botão direito no fundo do editor e procure opções como "Customize Header/Footer". Você pode definir as texturas deles para ficarem totalmente transparentes, removendo-os visualmente. Observe que isso pode não funcionar em todas as telas, especialmente nas mais antigas ou muito modificadas.

### Não consigo criar um layout "para a tela atual". O botão está acinzentado.
Você precisa primeiro habilitar as personalizações para essa tela em **menu bar -> Customization -> Current Screen Customizations -> toggle it to Enabled**.

### Não consigo personalizar nenhum elemento de uma tela ao abri-la no editor. Ela fica apenas vazia.

Isso pode significar que você criou acidentalmente um layout universal em vez de um **para a tela atual**.

Também pode significar que a tela que você está personalizando é uma tela rolável, e esse é um tipo de tela que o FancyMenu não consegue personalizar por padrão.

A terceira possibilidade é que seja uma tela de um mod que adiciona elementos de uma forma não vanilla, o que impede o FancyMenu de personalizar esses elementos.

### Há caixas cinzas estranhas no meu elemento de texto.

Essas caixas/retângulos translúcidos (baixa opacidade) podem aparecer na borda direita ou inferior do seu elemento de texto e não são um bug. Eles são os puxadores de rolagem do elemento de texto, já que o elemento é rolável.

Se você não quiser que essas caixas fiquem visíveis, você pode clicar com o botão direito no elemento e desativar completamente a rolagem OU também pode definir as texturas dos puxadores para texturas totalmente transparentes no mesmo menu de clique com o botão direito, se quiser que o elemento continue rolável.

### Como posso mostrar o changelog mais recente do Minecraft nos meus menus?

Existe um ótimo [projeto no GitHub](https://github.com/ClaytonTDM/minecraft-changelogs-markdown) que converte os changelogs do Minecraft para Markdown compatível com o FancyMenu, permitindo mostrar o changelog mais recente do MC nos seus menus! Ele é atualizado diariamente para buscar novos changelogs.

Por exemplo, para mostrar o changelog mais recente do Minecraft em um elemento de texto, defina o **Source Mode** como **Resource** e defina a origem do recurso como **Web**. Em seguida, use esta URL como fonte: `https://clay.is-a.dev/minecraft-changelogs-markdown/{"placeholder":"mcversion"}/fancymenu.md`

### Qual é a maneira mais fácil de esticar qualquer elemento para o tamanho da tela?

A maioria dos elementos tem uma opção nos menus de contexto do clique com o botão direito para esticá-los horizontalmente e verticalmente. Ativar isso fará com que eles sempre se estendam para toda a largura e/ou altura da tela. O esticamento horizontal e vertical pode ser ativado independentemente.

### Não consigo clicar em botões nem interagir com sliders quando eles estão atrás ou na frente de um elemento de texto.

Isso acontece porque elementos de texto são interativos por padrão (para permitir pegar o puxador de rolagem ou clicar em hyperlinks Markdown), o que significa que eles consomem cliques do mouse e eventos de rolagem. O ideal seria simplesmente não mover botões para trás/à frente de elementos de texto, mas, se não houver alternativa, você pode tornar o elemento de texto não interativo clicando com o **botão direito** nele e definindo **Interactable** como **Disabled**. Lembre-se de que isso transforma o elemento de texto em texto estático, sem interação, então você não poderá mais rolar nem clicar em hyperlinks.

### Como faço para que botões e sliders não sejam mais selecionados/focados ao navegar em telas com as teclas de seta e Tab do teclado?

Para que botões e sliders não possam ser navegados, você precisa **clicar com o botão direito** neles e definir **Navigable** como **Disabled**. O botão/slider ainda poderá ser clicado, mas você não conseguirá mais focá-lo com a navegação por Setas/Tab.

Isso também é útil se você quiser adicionar botões/sliders à tela de Chat, para que ainda possa usar a tecla Seta para Cima para rolar mensagens antigas sem selecionar acidentalmente botões/sliders na tela.

### Um dos menus de contexto do FancyMenu está sem uma opção que deveria estar lá.

Os menus de contexto do FancyMenu (os menus que abrem quando você clica com o botão direito em algum lugar ou interage com as barras de menu) são ROLÁVEIS. Isso significa que você pode usar a roda de rolagem enquanto o cursor do mouse está sobre o menu para rolar para cima ou para baixo, o que permite ver mais opções que antes não estavam visíveis.
