---
title: GUIs personalizadas
description: >-
  Crie seus próprios menus do zero, abra-os com botões, teclas ou comandos,
  mostre-os como pop-ups e substitua outros menus por eles.
sourceBlobSha: 0b336708473ae2964b3d9e777498c6cd40eaffc6
---

# GUIs personalizadas

GUIs personalizadas são menus que você mesmo cria, como uma tela de informações do modpack, um hub do servidor ou uma página de regras. Elas começam vazias, e você as preenche com um [layout](/layout-editor), como qualquer outro menu. Depois, botões, teclas e comandos podem abri-las.

<img width="800" alt="Clicar em um botão de informações do modpack na tela de título abre uma GUI personalizada como pop-up sobre a tela de título desfocada, e o botão Voltar a fecha" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_popup.gif?raw=true">

# Criando uma GUI personalizada

<img width="800" alt="Abrindo Gerenciar GUIs personalizadas, clicando em Nova GUI, digitando o identificador modpack_info, ativando o Modo pop-up e abrindo a nova GUI personalizada" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/custom_guis_new.gif?raw=true">

1. Abra **barra de menu -> Personalização -> GUIs personalizadas -> Gerenciar GUIs personalizadas**.
2. Clique em **Nova GUI**.
3. Digite um **Identificador da GUI personalizada**, como `modpack_info`, configure as [opções](#opções) e clique em **Concluir**.
4. Clique na nova GUI personalizada na lista e em **Abrir GUI**.
5. Clique em **Concluir** para fechar **Gerenciar GUIs personalizadas**.

**Gerenciar GUIs personalizadas** só salva suas alterações quando você clica em **Concluir** ou **Abrir GUI**. **Cancelar** descarta as alterações.

## O identificador

Botões, comandos e layouts localizam uma GUI personalizada pelo identificador dela.

- Use apenas letras minúsculas, números, `.`, `_` e `-`. Cada GUI personalizada precisa ter um identificador exclusivo.
- Não use o [identificador de outra tela](/screen-identifiers), como `title_screen`. A GUI personalizada compartilharia os layouts dessa tela.
- Se você mudar o identificador depois, os layouts, botões e comandos que usam o identificador antigo deixarão de encontrá-la. Se você voltar a usar o identificador antigo, eles voltarão a funcionar.

## Criando o layout

1. Abra a GUI personalizada.
2. Clique em **barra de menu -> Personalização -> Layouts -> Novo -> Para a tela atual**. A personalização está sempre ativada para GUIs personalizadas.
3. Adicione elementos e salve o layout. Consulte [Editor de layouts](/layout-editor).

Uma GUI personalizada não contém nada, nem mesmo um botão Voltar. Adicione a ela um [Botão](/elements#button) com a ação [**Voltar à última tela**](/action-scripts#back-to-last-screen), ou deixe **Permitir fechar a GUI com ESC** ativado para que os jogadores possam sair dela.

# Opções

**Editar GUI**, em **Gerenciar GUIs personalizadas**, altera as opções da GUI personalizada selecionada.

| Opção | O que faz |
|---|---|
| **Identificador da GUI personalizada** | O nome da GUI personalizada. Consulte [O identificador](#o-identificador). |
| **Título da tela (opcional)** | Um título branco na parte superior da GUI. Deixe em branco para não exibir nenhum. [Placeholders](/placeholders) funcionam, e as chaves de localização do jogo, dos mods e dos pacotes de recursos são exibidas no idioma do jogador. |
| **Permitir fechar a GUI com ESC** | `Esc` fecha a GUI. Ativado por padrão. |
| **Pausar jogo/mundo** | Pausa mundos para um jogador enquanto a GUI está aberta. Ativado por padrão. |
| **Renderizar plano de fundo do mundo** | Exibe o mundo atrás da GUI durante o jogo. Fora dos mundos, ou quando esta opção está desativada, é exibido o panorama do Minecraft. Ativado por padrão. |
| **Renderizar sobreposição do plano de fundo do mundo** | Desfoca e escurece o mundo ou panorama atrás da GUI, como no menu de pausa. Só funciona com **Renderizar plano de fundo do mundo**: sem essa opção, o panorama fica sempre desfocado e escurecido. Ativado por padrão. |
| **Modo pop-up** | Exibe a GUI sobre o menu a partir do qual ela foi aberta. Consulte [Modo pop-up](#modo-pop-up). |
| **Sobreposição do plano de fundo no modo pop-up** | Desfoca o menu atrás do pop-up. Só funciona com **Modo pop-up**. Ativado por padrão. |

- O desfoque tem a mesma intensidade da opção **Desfoque do plano de fundo do menu** do Minecraft.
- Um [plano de fundo de menu](/menu-backgrounds) no layout cobre tudo isso: o mundo, o panorama e o menu atrás de um pop-up.
- O editor de layouts não pode alterar o título (**Título da tela personalizada**) das GUIs personalizadas. Altere **Título da tela (opcional)**. Para usar um título com fonte, cor ou posição próprios, deixe essa opção em branco e adicione um [elemento de texto](/elements#text).

## Modo pop-up

Com o **Modo pop-up**, o menu a partir do qual a GUI personalizada foi aberta continua visível atrás dela, com seu layout. Não é possível clicar nesse menu enquanto o pop-up estiver aberto.

- Pop-ups funcionam melhor para coisas pequenas, como uma caixa de informações, uma confirmação ou um painel de configurações. Deixe algum espaço livre para que o menu atrás continue visível.
- Não adicione um plano de fundo de menu ao layout de um pop-up, ou o menu atrás dele desaparecerá.
- Se a GUI personalizada for aberta quando não houver nenhum menu aberto, como ao pressionar uma tecla durante o jogo, não haverá um menu atrás dela. Nesse caso, ela exibirá seu plano de fundo normal.

# Abrindo uma GUI personalizada

Tudo o que abre telas pode abrir GUIs personalizadas usando o identificador delas:

- **Botões:** use a ação [**Abrir tela ou GUI personalizada**](/action-scripts#open-screen-or-custom-gui) com o valor `modpack_info`.
- **Teclas:** use um [ouvinte **Ao pressionar uma tecla do teclado**](/listeners#listener-variables) com a mesma ação. Ele abre a GUI personalizada nos menus e durante o jogo.
- **Comandos:** `/openguiscreen modpack_info`, inclusive em servidores, blocos de comando e recompensas de missões. Consulte [Comandos](/commands#openguiscreen).
- **Ao sair de um mundo:** a ação [**Sair do mundo ou servidor**](/action-scripts#leave-world-or-server) com o identificador abre a GUI personalizada depois que você sair.

As GUIs personalizadas fazem parte da configuração individual do FancyMenu de cada jogador. Um servidor só pode abrir as GUIs personalizadas que os jogadores têm, como as do modpack.

Para sair de uma GUI personalizada:

- `Esc` (com **Permitir fechar a GUI com ESC**) e a ação **Voltar à última tela** retornam ao menu a partir do qual ela foi aberta. Se nenhum menu estava aberto, `Esc` volta ao jogo.
- A ação [**Fechar tela**](/action-scripts#close-screen) fecha a GUI. Fora dos mundos, a tela de título será aberta.

# Substituindo uma tela existente

Uma GUI personalizada pode substituir um menu do jogo ou de um mod. Sempre que esse menu fosse aberto, a GUI personalizada será aberta no lugar dele.

> [!WARNING]
> O menu substituído nunca é aberto, então nada do que ele faria acontece, e outros mods que dependem dele podem parar de funcionar. Sempre que possível, altere os menus usando um layout normal. Substitua um menu apenas quando um layout não puder fazer o que você precisa.

1. Ative **barra de menu -> Personalização -> Configurações -> Modo de personalização avançado**.
2. Abra o menu que deseja substituir.
3. Clique em **barra de menu -> Personalização -> GUIs personalizadas -> Substituir tela atual por GUI personalizada**.
4. Confirme o aviso e escolha a GUI personalizada em **Escolher GUI personalizada**.

A GUI personalizada será aberta imediatamente. `Esc` e **Voltar à última tela**, dentro dela, retornam ao menu que estava aberto antes do menu substituído.

Para desfazer a alteração, abra **barra de menu -> Personalização -> GUIs personalizadas -> Gerenciar telas substituídas**, clique em **Excluir regra de substituição** abaixo da tela e clique em **Concluir**.

> [!TIP]
> Para substituir um menu apenas em algumas situações, como somente enquanto uma [variável](/variables) estiver definida, use um [ouvinte **Ao abrir a tela**](/listeners#on-screen-opened) com uma instrução IF.

# Gerenciando GUIs personalizadas

- **Nova GUI**, **Editar GUI** e **Abrir GUI**, em **Gerenciar GUIs personalizadas**, permitem adicionar, alterar e abrir GUIs personalizadas.
- **Excluir GUI** exclui a GUI personalizada selecionada após pedir confirmação. Os layouts dela são mantidos e voltarão a aparecer em uma nova GUI personalizada com o mesmo identificador.
- A barra de pesquisa localiza GUIs personalizadas pelo identificador.
- **barra de menu -> Ajuda -> Exportar para IA -> GUIs personalizadas** exporta todas as GUIs personalizadas e regras de substituição para uma [conversa com IA](/export-for-ai).

As GUIs personalizadas e as regras de substituição são salvas em `config/fancymenu/custom_gui_screens.txt`; seus layouts são salvos em `config/fancymenu/customization/`, como os demais (consulte [Locais de armazenamento de dados](/data-storage-locations)). Cada [perfil](/profiles) tem suas próprias GUIs personalizadas.
