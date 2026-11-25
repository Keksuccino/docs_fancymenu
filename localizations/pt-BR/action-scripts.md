---
title: Scripts de ação
description: >-
  Faça botões e menus executarem ações com scripts de ação e conheça todas as
  ações do FancyMenu.
sourceBlobSha: 07ed5af6f189a91c518131cf3a7ab7a1e0a8305d
---

# Scripts de ação

Um script de ação é uma lista de coisas que o FancyMenu faz quando algo acontece, como um botão ser clicado ou um menu ser aberto. Cada item é uma ação: abrir um menu, entrar em um servidor, exibir uma mensagem, reproduzir um som e muito mais. Instruções como IF e WHILE determinam quais ações são executadas e com que frequência.

> [!CAUTION]
> Scripts de ação podem alterar arquivos, contatar servidores, abrir links e executar comandos. Use apenas scripts de layouts em que você confia.

<img width="800" alt="O script de ação de um botão é criado no editor de layout: Edit Action Script, o seletor de ações com Show Toast e o título e a mensagem do toast" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_make.gif?raw=true">

# Criar um script de ação

1. No editor de layout, clique com o botão direito em um botão e clique em **Edit Action Script**.
2. Pressione `A` para abrir o seletor de ações.
3. Pesquise a ação, clique nela e clique em **Next Step**.
4. Configure a ação na janela e clique em **Done**. Ações sem configurações só precisam de **Done** no seletor.
5. Clique em **Done** no editor de scripts e salve o layout.

Fora do editor, o botão executa o script quando é clicado:

<img width="800" alt="Clicar no botão What's New? na tela inicial exibe um toast com o título e a mensagem da atualização" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/action_script_use.gif?raw=true">

> [!TIP]
> Clique com o botão direito na área do script e abra **Add Action** para ver uma lista de todas as ações. Clique com o botão direito em uma ação da lista para adicioná-la aos favoritos e fazê-la aparecer no topo.

# Onde você pode usar scripts de ação

| Onde | Executado quando | Onde editar |
|---|---|---|
| [Botão](/elements#button) | O botão é clicado. | Clique com o botão direito no botão -> **Edit Action Script** |
| [Controle deslizante](/elements#slider) | O valor do controle deslizante muda. `$$value` é o novo valor. | Clique com o botão direito no controle deslizante -> **Edit Action Script** |
| [Caixa de seleção](/elements#checkbox) | A caixa de seleção é marcada ou desmarcada. `$$value` é seu novo estado: `true` ou `false`. | Clique com o botão direito na caixa de seleção -> **Edit Action Script** |
| [Ticker](/elements#ticker) | Conforme indicado em **Tick Mode**: repetidamente, uma vez por sessão de jogo ou uma vez quando o menu é carregado. | Clique com o botão direito no ticker -> **Edit Action Script** |
| Abertura de um menu | O menu do layout é aberto. | Clique com o botão direito no plano de fundo do editor -> **Edit 'Open Screen' Action Script** |
| Fechamento de um menu | O menu do layout é fechado. | Clique com o botão direito no plano de fundo do editor -> **Edit 'Close Screen' Action Script** |
| [Ouvintes](/listeners) | O evento deles ocorre, como o pressionamento de uma tecla ou o recebimento de uma mensagem no chat. | **barra de menus -> Customization -> Manage Listeners** |
| [Agendadores](/schedulers) | No intervalo definido, mesmo quando nenhum menu está aberto. | **barra de menus -> Customization -> Manage Schedulers** |

Os scripts de abertura e fechamento também ficam no menu **Layout -> Layout Properties** do editor.

# O editor de scripts

- As ações são executadas de cima para baixo. Os itens dentro de uma instrução ou pasta aparecem recuados abaixo dela.
- Novos itens são adicionados abaixo do item selecionado. Se uma instrução ou pasta estiver selecionada, eles são adicionados no início dela.
- Clique duas vezes em um valor para editá-lo diretamente na lista. Valores que exibem um resumo curto abrem a janela correspondente.
- Arraste os itens para movê-los. Cadeias IF, loops e pastas podem ser recolhidos com o pequeno botão à frente deles. Isso altera apenas a visualização.
- A barra à direita é um mapa do script inteiro. Clique nela para ir até uma parte do script.
- Clique com o botão direito na área do script para acessar as demais opções, como adicionar instruções e **Export Action Script for AI** (consulte [Exportar para IA](/export-for-ai)).
- **Cancel** ou fechar a janela descarta suas alterações. Se houver alguma, o editor perguntará antes.

## Atalhos

No macOS, `Ctrl` corresponde a `Cmd`.

| Atalho | O que faz |
|---|---|
| `A` | Abre o seletor de ações. |
| `Enter` | Edita o item selecionado. |
| `Delete` | Exclui o item selecionado. |
| `Up` / `Down` | Seleciona o item acima ou abaixo. |
| `Shift + Up` / `Shift + Down` | Move o item selecionado para cima ou para baixo. |
| `Ctrl + C` / `Ctrl + V` | Copia e cola uma ação. Instruções e blocos não podem ser copiados. |
| `Ctrl + Z` | Desfaz. |
| `Ctrl + Y` ou `Ctrl + Shift + Z` | Refaz. |
| `Ctrl + S` | Salva o script e fecha o editor, como **Done**. |

# Instruções

As instruções determinam quais ações são executadas e com que frequência. Adicione-as clicando com o botão direito na área do script.

## If, Else-If e Else

**Add IF Statement** solicita [requisitos](/conditions). As ações dentro do IF só são executadas quando eles são atendidos.

Clique com o botão direito em um IF para adicionar outros itens à cadeia:

- **Append ELSE-IF Statement**: verifica os próprios requisitos se o IF acima não tiver sido executado.
- **Append ELSE Statement**: é executado quando nenhum item anterior da cadeia tiver sido executado.

Por exemplo, um IF com **Is Layout Enabled** pode exibir um toast apenas enquanto o layout de inverno estiver ativado, e um ELSE pode reproduzir um som caso contrário.

## Loop While

**Add WHILE Loop** repete suas ações enquanto os [requisitos](/conditions) forem atendidos.

Cada execução é interrompida após 3 segundos, para que um loop infinito não congele o jogo. Isso não é um temporizador: para executar ações mais tarde ou repetidamente, use [Execute Later](#execute-later), um [Ticker](/elements#ticker) ou um [Scheduler](/schedulers).

## Loop For Each

**Add FOR EACH Loop** executa suas ações uma vez para cada item de uma [variável de lista](/variables#text-and-list-variables), do primeiro ao último.

- `$$list_entry` é o item atual e `$$list_index` é o índice dele. O índice do primeiro item é 0.
- Ambos podem ser usados nos valores das ações e nos requisitos dentro do loop.
- Digite o nome da lista sem `$$`, como `quest_log`. Também é possível usar placeholders no nome.
- O loop lê a lista uma única vez quando começa, então as ações dentro dele podem alterá-la sem problemas.
- Assim como nos loops WHILE, cada execução é interrompida após 3 segundos.

Consulte [Percorrer uma lista](/variables#going-through-a-list) para ver exemplos.

# Blocos

Os blocos alteram o momento em que as ações são executadas ou ajudam a manter o script organizado. Adicione-os clicando com o botão direito na área do script.

## Bloco Delay Gate

**Add DELAY GATE Block** atrasa suas ações por um período em milissegundos (`1000` equivale a um segundo).

- Na primeira vez que o script chega ao bloco, o temporizador começa e as ações são ignoradas. O restante do script continua sendo executado imediatamente.
- Sempre que o script chegar ao bloco novamente antes de o tempo acabar, as ações serão ignoradas outra vez.
- Depois disso, as ações serão executadas sempre que o script chegar ao bloco.
- Em scripts de elementos, o temporizador recomeça quando o menu é aberto novamente ou redimensionado.

Esse bloco é útil para [Tickers](/elements#ticker), por exemplo, para exibir algo apenas depois de o menu ficar aberto por alguns segundos. Ele nunca executa ações por conta própria: use Execute Later para isso.

## Execute Later

**Add EXECUTE LATER Block** executa suas ações uma vez após um período em milissegundos. O restante do script continua sendo executado imediatamente.

Sempre que o script chega ao bloco, uma nova contagem regressiva começa. Isso é útil para scripts que são executados apenas uma vez, como ao clicar em um botão ou abrir um menu.

## Pasta

**Add Folder** agrupa ações com um nome. Ela executa tudo o que está dentro e serve apenas para organizar scripts longos. Clique duas vezes no nome para alterá-lo.

## Comentário

**Add Comment** adiciona uma anotação para você. Não faz nada. Clique duas vezes nela para editá-la.

# Como os scripts são executados

- As ações são executadas de cima para baixo. Se uma ação falhar, um erro será registrado no log do jogo, mas o restante do script continuará sendo executado.
- Os placeholders nos valores são substituídos pelos valores atuais no momento em que a ação é executada. Assim, uma ação vê as alterações feitas pelas ações anteriores.
- Downloads, extração de arquivos ZIP e solicitações web são concluídos em segundo plano. A ação seguinte não espera por eles. Para executar ações quando terminarem, use os ouvintes [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action) e [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action), ou uma variável de resposta de [**Send HTTP Request**](#send-http-request).

# Valores das ações

A maioria das ações precisa de um valor, como o endereço de um servidor. Valores simples são textos digitados por você. Ações com mais configurações têm uma janela própria.

## Placeholders

Os valores podem conter [placeholders](/placeholders), como o nome do jogador. Eles são substituídos quando a ação é executada:

```
/say Bem-vindo de volta, {"placeholder":"playername"}!
```

## Variáveis $$

Digite `$$` seguido do nome de uma variável para usar o valor dela em uma ação ou requisito. Letras maiúsculas e minúsculas nos nomes são diferentes. Isso funciona com dois tipos de variáveis:

### Suas próprias variáveis

Todas as variáveis criadas em **barra de menus -> Customization -> Manage Variables** podem ser usadas com `$$` e seus nomes. Uma variável chamada `coins` é `$$coins` em qualquer script. Por exemplo, **Display In Chat [Client-Side]** com este valor informa ao jogador quantas moedas ele tem:

```
&6Você tem $$coins moedas!
```

Consulte [Variáveis](/variables) para saber como criá-las e alterá-las.

### Variáveis do script

Alguns recursos fornecem variáveis próprias ao script:

- Um [controle deslizante](/elements#slider) fornece `$$value`, seu novo valor.
- Uma [caixa de seleção](/elements#checkbox) fornece `$$value`, seu novo estado: `true` ou `false`.
- Um [Loop For Each](#loop-for-each) fornece `$$list_entry` e `$$list_index`.
- Cada [ouvinte](/listeners#listener-variables) lista as variáveis que fornece, como a tecla que foi pressionada.

Elas só existem enquanto o script está sendo executado. Se uma variável do script tiver o mesmo nome que uma das suas variáveis, `$$name` se refere à variável do script.

# Todas as ações

Todas as ações disponíveis no FancyMenu, organizadas pelo que fazem.

## Telas e menus

### Abrir tela ou GUI personalizada

**Identifier:** `opengui`

Abre um menu do jogo, de um mod ou uma [GUI personalizada](/custom-guis).

**Value:** o [identificador da tela](/screen-identifiers), como `options_screen`

Letras maiúsculas e minúsculas são diferentes. Alguns menus de mods não podem ser abertos dessa forma. Nesse caso, use [**Mimic Vanilla/Mod Button**](#mimic-vanillamod-button) em um botão que abra o menu.

### Fechar tela

**Identifier:** `closegui`

Fecha o menu aberto. Fora dos mundos, a tela inicial é aberta.

**Value:** nenhum

### Atualizar tela

**Identifier:** `update_screen`

Reconstrói o menu aberto, como acontece ao redimensionar a janela. É útil após alterar a escala da GUI ou outras opções.

**Value:** nenhum

### Voltar à tela anterior

**Identifier:** `back_to_last_screen`

Volta ao menu que estava aberto antes. Para uma [GUI personalizada](/custom-guis), volta ao menu a partir do qual ela foi aberta.

**Value:** nenhum

### Exibir toast

**Identifier:** `show_toast`

Exibe uma notificação toast no canto superior direito, configurada na própria janela:

- **Toast Width**: de 120 a 320 pixels.
- **Duration (ms)**: por quanto tempo ela permanece visível, de 1 segundo (`1000`) a 10 minutos.
- **Title** e **Message**: texto com [códigos de formatação](/text-formatting#minecraft-text-formatting) ou JSON de componente de texto do Minecraft.
- **Icon Texture Source** e **Background Texture Source**: [imagens](/resources) opcionais. Ícones ficam melhores em 20x20 pixels; o plano de fundo deve ter 32 pixels de altura e a mesma largura do toast.

### Simular clique em botão vanilla/mod

**Identifier:** `mimicbutton`

Clica em um botão do jogo ou de um mod como se o jogador tivesse clicado nele.

**Value:** o [localizador do widget](/widget-locators) do botão, como `title_screen:mc_titlescreen_options_button`

Para obtê-lo, clique com o botão direito no botão no editor e clique em **Copy Widget Locator**.

## Layouts e elementos

### Alternar layout

**Identifier:** `toggle_layout`

Desativa um layout se ele estiver ativado e o ativa se estiver desativado.

**Value:** o nome do layout, sem `.txt`, como `winter_title_screen`

### Ativar layout

**Identifier:** `enable_layout`

Ativa um layout.

**Value:** o nome do layout, sem `.txt`

### Desativar layout

**Identifier:** `disable_layout`

Desativa um layout.

**Value:** o nome do layout, sem `.txt`

As três ações de layout salvam a alteração e atualizam o menu aberto imediatamente. Letras maiúsculas e minúsculas no nome são diferentes.

### Alternar animador de elemento

**Identifier:** `toggle_element_animator`

Ativa um [Animador de elemento](/element-animator) se ele estiver desativado e o desativa se estiver ativado. A animação recomeça do início. O estado é salvo.

**Value:** o identificador do Animador de elemento

### Ativar animador de elemento

**Identifier:** `enable_element_animator`

Ativa um [Animador de elemento](/element-animator). Se ele estava desativado, a animação recomeça do início.

**Value:** o identificador do Animador de elemento

### Desativar animador de elemento

**Identifier:** `disable_element_animator`

Desativa um [Animador de elemento](/element-animator) e reinicia a animação.

**Value:** o identificador do Animador de elemento

### Reiniciar animador de elemento

**Identifier:** `reset_element_animator`

Recomeça a animação de um [Animador de elemento](/element-animator) desde o início, sem ativá-lo nem desativá-lo.

**Value:** o identificador do Animador de elemento

### Definir valor do campo de entrada de texto

**Identifier:** `set_text_input_field_value`

Define o texto de um [Campo de entrada de texto](/elements#text-input-field), do FancyMenu ou do jogo.

**Value:** `element_identifier|||text|||force`

Se `force` estiver definido como `true`, o texto também será alterado quando o campo estiver desativado (inativo).

### Rolar um elemento

**Identifier:** `scroll_scroll_area`

Rola uma [Área rolável](/scrollable-areas) ou um elemento de [Texto](/elements#text), configurado na própria janela:

- **Identifier of the Element to Scroll**: a área ou o texto a ser rolado.
- **Scroll To**:
  - **Start** ou **End**.
  - **Position**: **Horizontal Position** e **Vertical Position** em pixels. Deixe uma delas vazia para mantê-la como está.
  - **Element** (somente áreas): rola até que o elemento com o **Identifier of the Element to Scroll To** fique no início.
  - **Line Number** (somente textos): a primeira linha é `1`.
  - **Line with Text** (somente textos): a primeira linha que contém o **Text in the Line**. Letras maiúsculas e minúsculas não fazem diferença.
- **Glide There**: desliza até a posição em vez de pular para ela. A rolagem suave precisa estar ativada para o elemento.

Não faz nada se o elemento não existir.

## Áudio e vídeo

### Próxima faixa

**Identifier:** `audio_next_track`

Avança para a próxima faixa de um [elemento de Áudio](/elements#audio).

**Value:** o identificador do elemento de Áudio, como `menu_music`

### Faixa anterior

**Identifier:** `audio_previous_track`

Volta à faixa anterior de um [elemento de Áudio](/elements#audio).

**Value:** o identificador do elemento de Áudio

### Definir volume da faixa

**Identifier:** `set_audio_element_volume`

Define o volume de um [elemento de Áudio](/elements#audio), de `0.0` (0%) a `1.0` (100%).

**Value:** `element_identifier:volume`, como `menu_music:0.5`

### Alternar reprodução/pausa da faixa

**Identifier:** `audio_toggle_play`

Pausa um [elemento de Áudio](/elements#audio) em reprodução ou reproduz um que esteja pausado.

**Value:** o identificador do elemento de Áudio

### Reproduzir áudio

**Identifier:** `play_audio`

Reproduz um arquivo de áudio uma vez, com as configurações da própria janela: **Audio Source**, **Sound Channel** e **Base Volume** (até 100%).

- O FancyMenu aguarda até dez segundos para o áudio carregar.
- Não funciona em um [Ticker](/elements#ticker) executado em segundo plano (de forma assíncrona). Em vez disso, o FancyMenu exibe um erro.

[**Stop All Action Audios**](#stop-all-action-audios) interrompe os áudios iniciados por esta ação.

### Interromper todos os áudios de ações

**Identifier:** `stop_all_action_audios`

Interrompe todos os áudios iniciados por [**Play Audio**](#play-audio). Elementos de áudio, sons de menu e sons de botão continuam sendo reproduzidos.

**Value:** nenhum

### Definir volume do elemento de vídeo

**Identifier:** `set_video_element_volume`

Define o volume de um [elemento de Vídeo](/video), de `0.0` (0%) a `1.0` (100%).

**Value:** `video_element_identifier:volume`

### Definir tempo de reprodução do elemento de vídeo

**Identifier:** `set_video_element_play_time`

Avança para um ponto de um [elemento de Vídeo](/video), em milissegundos.

**Value:** `video_element_identifier:time_in_ms`, como `intro_video:30000`

### Alternar estado de pausa do elemento de vídeo

**Identifier:** `toggle_video_element_pause_state`

Pausa um [elemento de Vídeo](/video) em reprodução ou reproduz um que esteja pausado.

**Value:** o identificador do elemento de Vídeo

### Definir volume do plano de fundo de vídeo

**Identifier:** `set_video_menu_background_volume`

Define o volume de um [plano de fundo de vídeo do menu](/video), de `0.0` (0%) a `1.0` (100%).

**Value:** `background_identifier:volume`

> [!NOTE]
> Para obter o identificador de um plano de fundo do menu, clique com o botão direito no plano de fundo do editor e clique em **Copy Background Identifier**.

### Definir tempo de reprodução do plano de fundo de vídeo

**Identifier:** `set_video_menu_background_play_time`

Avança para um ponto de um [plano de fundo de vídeo do menu](/video), em milissegundos.

**Value:** `background_identifier:time_in_ms`

### Alternar estado de pausa do plano de fundo de vídeo

**Identifier:** `toggle_video_menu_background_pause_state`

Pausa um [plano de fundo de vídeo do menu](/video) em reprodução ou reproduz um que esteja pausado.

**Value:** o identificador do plano de fundo do menu

## Mundos e servidores

### Entrar em servidor

**Identifier:** `joinserver`

Conecta-se a um servidor do Minecraft.

**Value:** `address` ou `address:port`, como `play.example.net`

Se nenhuma porta for informada, será usada a porta `25565`. Se um mundo ou servidor estiver carregado, a ação exibirá um erro. Servidores que não estão na lista de servidores serão adicionados a ela.

### Entrar em mundo

**Identifier:** `loadworld`

Carrega um mundo para um jogador.

**Value:** o nome da pasta do mundo em `saves`, como `Survival Island`

Não faz nada se o mundo não existir. Se um mundo ou servidor estiver carregado, a ação exibirá um erro.

### Entrar no último mundo/servidor

**Identifier:** `join_last_world`

Carrega o mundo ou entra no servidor em que o jogador esteve pela última vez.

**Value:** nenhum

Se um mundo ou servidor estiver carregado, a ação exibirá um erro. Um servidor que não está na lista de servidores será adicionado a ela.

### Sair do mundo ou servidor

**Identifier:** `disconnect_server_or_world`

Sai do mundo ou servidor e abre um menu.

**Value:** o [identificador da tela](/screen-identifiers) do menu a ser aberto, como `title_screen`

Só funciona enquanto um mundo está carregado. [GUIs personalizadas](/custom-guis) também funcionam. Se não for possível abrir o menu, a tela inicial será aberta.

## Chat e comandos

### Enviar mensagem/comando no chat

**Identifier:** `sendmessage`

Envia uma mensagem no chat ou executa um comando como se o jogador o tivesse digitado.

**Value:** a mensagem ou um comando com `/`, como `/spawn`

### Executar comando como servidor integrado

**Identifier:** `execute_command_as_integrated_server`

Executa um comando no modo para um jogador como servidor, independentemente das permissões do jogador ou da configuração de trapaças.

**Value:** o comando, como `/give @p minecraft:diamond 1`

> [!WARNING]
> Só funciona no modo para um jogador quando o mundo não está aberto para LAN. Em qualquer outro caso, não faz nada.

### Colar no chat

**Identifier:** `paste_to_chat`

Insere texto no campo de entrada do chat enquanto um mundo está carregado. Se o chat não estiver aberto, ele será aberto com o texto.

**Value:** `true:text` adiciona o texto ao que já foi digitado; `false:text` substitui o texto existente

### Exibir no chat [lado do cliente]

**Identifier:** `display_in_chat_client_side`

Exibe uma mensagem no chat que só este jogador pode ver. Nada é enviado ao servidor.

**Value:** o texto, com [códigos de formatação](/text-formatting#minecraft-text-formatting) ou em JSON de componente de texto do Minecraft, como `&aBem-vindo de volta!`

Não faz nada se nenhum mundo estiver carregado.

## Variáveis e listas

### Definir valor de variável (variável do FM)

**Identifier:** `set_variable`

Define uma [variável](/variables).

**Value:** `variable_name:value`, como `coins:100`

- Apenas o primeiro `:` separa o nome do valor.
- [Variáveis de lista](/variables#text-and-list-variables) continuam sendo listas: um array JSON como `["a","b"]` vira seus itens; qualquer outro texto vira o único item; e um texto vazio deixa a lista vazia.

### Excluir variável (variável do FM)

**Identifier:** `delete_variable`

Exclui completamente uma [variável](/variables). As demais variáveis permanecem. Para apenas deixá-la vazia, use [**Definir valor de variável (variável do FM)**](#definir-valor-de-variável-variável-do-fm).

**Value:** o nome da variável

### Limpar todas as variáveis (variáveis do FM)

**Identifier:** `clear_variables`

Exclui todas as [variáveis](/variables), incluindo as variáveis de texto e de lista.

**Value:** nenhum

### Adicionar à lista (variável do FM)

**Identifier:** `add_to_list`

Adiciona um item a uma [variável de lista](/variables#list-actions).

- **List Variable**: o nome da lista. Se ainda não houver uma variável com esse nome, a ação cria a lista.
- **New Entry**: o texto do item.
- **Index (Optional)**: onde o item será inserido. Se estiver vazio, ele será adicionado ao final. Os itens a partir dessa posição avançam uma posição.
- **Skip If Already in List**: não adiciona nada se a lista já contiver um item com o mesmo texto. **Ignore Case** faz com que `Apple` corresponda a `apple`.

### Definir item da lista (variável do FM)

**Identifier:** `set_list_entry`

Substitui o item no **Index** de uma [variável de lista](/variables#list-actions) por um **New Value**. Não faz nada se a lista não tiver um item nessa posição.

### Remover da lista (variável do FM)

**Identifier:** `remove_from_list`

Remove itens de uma [variável de lista](/variables#list-actions). **Remove** determina quais:

- **Entry at Index**: o item no índice indicado.
- **First Match**: o primeiro item cujo texto corresponda exatamente a **Value to Remove**.
- **All Matches**: todos os itens com esse texto.

**Ignore Case** faz com que `Apple` corresponda a `apple`.

### Limpar lista (variável do FM)

**Identifier:** `clear_list`

Remove todos os itens de uma [variável de lista](/variables#list-actions). A lista vazia permanece.

### Definir lista (variável do FM)

**Identifier:** `set_list`

Substitui todos os itens de uma [variável de lista](/variables#list-actions). **Entries From** determina a origem dos itens:

- **Split Text**: divide o **Text to Split** usando o **Separator**, como `,`. Se o separador estiver vazio, o texto será dividido nas quebras de linha. **Trim Entries** remove os espaços no início e no fim dos itens; **Skip Empty Entries** ignora os itens vazios.
- **JSON Array**: usa os itens de um array como `["Diamonds","Emeralds"]`, ou `$$other_list` para copiar outra lista. Qualquer outro texto vira o único item, e um texto vazio deixa a lista vazia.

A janela exibe uma prévia dos itens.

### Organizar lista (variável do FM)

**Identifier:** `arrange_list`

Altera a ordem dos itens de uma [variável de lista](/variables#list-actions). **Arrangement**:

- **Sort A–Z** e **Sort Z–A**: ordena alfabeticamente.
- **Numbers, Smallest First** e **Numbers, Biggest First**: ordena numericamente. Itens que não são números vão para o final.
- **Reverse Order**: transforma o último item no primeiro.
- **Shuffle**: embaralha os itens aleatoriamente.
- **Remove Duplicates**: mantém apenas a primeira ocorrência de cada valor.

Em todas as ações de lista, o índice do primeiro item é `0` e `-1` representa o último. O nome da lista pode conter placeholders e, se for precedido por `$$`, a ação usa o valor dessa variável como nome da lista. Variáveis de texto que já têm um valor permanecem inalteradas, e a ação registra um aviso no log do jogo.

## Web e rede

### Abrir URL no navegador

**Identifier:** `openlink`

Abre um link no navegador padrão sem pedir confirmação.

**Value:** o link, como `https://discord.gg/example`

Use apenas links em que você confia.

### Enviar solicitação HTTP

**Identifier:** `send_http_request`

Envia uma solicitação web em segundo plano. A resposta pode ser registrada no log do jogo ou armazenada em uma variável.

| Configuração | O que faz |
|---|---|
| URL | O endereço HTTP ou HTTPS. |
| Method | `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD` ou `OPTIONS`. |
| Body | Os dados a enviar. Não é enviado com `GET` nem `HEAD`. |
| Content type | O `Content-Type` do corpo, como `application/json`. |
| Timeout | Quantos segundos aguardar pela conexão e pela resposta. |
| Log response | Registra a resposta no log do jogo. |
| Response variable | Armazena a resposta nesta variável quando ela chegar. |
| Single-line response | Remove as quebras de linha da resposta antes de armazená-la. |
| Authentication | Nenhuma, Basic, Bearer ou chave de API. |
| Headers | Cabeçalhos adicionais da solicitação. |

A ação seguinte não espera pela resposta. Respostas de erro também são registradas e armazenadas. Não inclua senhas nem tokens de acesso na ação: qualquer pessoa com o layout pode lê-los.

### Enviar dados do FM ao servidor

**Identifier:** `send_fm_data_to_server`

Envia [dados do FM](/fm-data) ao servidor, que também precisa ter o FancyMenu.

**Value:** `data_identifier||data`

### Conectar a servidor remoto

**Identifier:** `connect_to_remote_server`

Conecta a um servidor remoto ou usa a conexão que já está aberta.

**Value:** o endereço do servidor, como `wss://example.com/ws`

Consulte [Comunicação com servidor remoto](/remote-server-communication#url-modes) para ver os endereços compatíveis.

### Enviar dados a servidor remoto

**Identifier:** `send_data_to_remote_server`

Envia texto a um servidor remoto e conecta-se primeiro, se necessário.

**Value:** `server_address||data`

### Fechar conexão com servidor remoto

**Identifier:** `close_remote_server_connection`

Fecha uma conexão com servidor remoto.

**Value:** o ID da solicitação, normalmente `$$request_id` de [**On Remote Server Connected**](/listeners#on-remote-server-connected)

### Fechar todas as conexões com servidores remotos

**Identifier:** `close_all_remote_server_connections`

Fecha todas as conexões com servidores remotos abertas pelo FancyMenu.

**Value:** nenhum

## Arquivos

### Criar arquivo na pasta do jogo

**Identifier:** `create_file_in_game_dir`

Cria um arquivo vazio. As pastas inexistentes também são criadas. Um arquivo existente permanece inalterado.

**Value:** o caminho do arquivo, como `config/mymodpack/first_start.txt`

Todas as ações de arquivo só funcionam dentro da pasta do jogo (pasta da instância). Caminhos que começam com `.minecraft/` usam a pasta `.minecraft` padrão, que pode ser diferente.

### Excluir arquivo/pasta na pasta do jogo

**Identifier:** `delete_file_in_game_dir`

Exclui um arquivo ou uma pasta com todo o seu conteúdo.

**Value:** o caminho, como `config/mymodpack/cache.txt`

Se o caminho terminar com `*`, como `config/downloads/*`, todos os arquivos diretamente nessa pasta serão excluídos, mas a pasta e suas subpastas serão mantidas.

### Copiar arquivo/pasta na pasta do jogo

**Identifier:** `copy_file_in_game_dir`

Copia um arquivo ou uma pasta com todo o seu conteúdo.

**Value:** `source||destination`, como `config/presets/default.json||config/mymod/settings.json`

- Se o caminho de origem terminar com `*`, como `config/presets/*||config/mymod/`, todos os arquivos diretamente nessa pasta serão copiados, mas nenhuma subpasta. Nesse caso, o destino será uma pasta e será criado se necessário.
- Nada é sobrescrito: se o destino já existir, a ação falhará.

### Mover arquivo/pasta na pasta do jogo

**Identifier:** `move_file_in_game_dir`

Move um arquivo ou uma pasta com todo o seu conteúdo.

**Value:** `source||destination`

O `*` no fim do caminho de origem funciona como em [**Copiar arquivo/pasta na pasta do jogo**](#copiar-arquivopasta-na-pasta-do-jogo). Nada é sobrescrito.

### Renomear arquivo/pasta na pasta do jogo

**Identifier:** `rename_file_in_game_dir`

Renomeia um arquivo ou uma pasta. A ação falha se já existir algo com o novo nome.

**Value:** `path||new_name`, como `config/mymod/old_name.txt||new_name.txt`

### Baixar arquivo para a pasta do jogo

**Identifier:** `download_file_to_game_dir`

Baixa um arquivo para uma pasta em segundo plano.

**Value:** `url||target_folder`, como `https://example.com/pack.zip||downloads`

- A segunda parte é uma pasta, não um nome de arquivo. O FancyMenu obtém o nome do download ou do link.
- Um arquivo com o mesmo nome será sobrescrito.
- [**On File Downloaded via Action**](/listeners#on-file-downloaded-via-action) é executado quando o download termina ou falha. Em caso de sucesso, `$$target_file_path` contém o caminho do arquivo salvo.

### Extrair arquivo ZIP na pasta do jogo

**Identifier:** `extract_zip_file_in_game_dir`

Extrai um arquivo ZIP para uma pasta em segundo plano.

**Value:** `zip_path||target_folder`, como `downloads/pack.zip||resourcepacks/MyPack`

Arquivos com os mesmos nomes serão substituídos, e nenhuma pasta adicional com o nome do ZIP será criada. [**On ZIP Extracted via Action**](/listeners#on-zip-extracted-via-action) é executado quando a extração termina. Extraia apenas arquivos ZIP em que você confia.

### Abrir arquivo/pasta na pasta do jogo

**Identifier:** `open_file_folder_in_game_dir`

Abre um arquivo ou uma pasta com o programa associado pelo sistema.

**Value:** o caminho, como `screenshots`

### Gravar arquivo na pasta do jogo

**Identifier:** `write_file_in_game_dir`

Grava texto em um arquivo. O arquivo e suas pastas são criados se necessário.

**Value:** `path|||text|||append`, como `config/mymodpack/log.txt|||Entrei no servidor\\n|||true`

`\\n` inicia uma nova linha. Se `append` estiver definido como `true`, o texto será adicionado ao final do arquivo; se estiver como `false`, o conteúdo existente será substituído.

### Selecionar arquivo do sistema

**Identifier:** `select_file_to_game_dir`

Abre o seletor de arquivos do sistema e copia o arquivo selecionado para a pasta do jogo.

**Value:** `target_path|||filter_name|||extensions|||overwrite`, como `config/fancymenu/assets/background.png|||Images|||png;jpg|||true`

- `target_path` é o caminho completo da cópia, incluindo o nome do arquivo.
- Separe as extensões com `;` ou `,`. Se não informar extensões, será possível selecionar qualquer arquivo.
- Se `overwrite` estiver definido como `false`, a ação falhará caso o arquivo já exista.

[**On File Selected**](/listeners#on-file-selected) é executado quando o arquivo é copiado, quando o seletor é cancelado ou quando ocorre uma falha.

## Jogo e FancyMenu

### Sair do Minecraft

**Identifier:** `quitgame`

Fecha o jogo.

**Value:** nenhum

### Definir opção do Minecraft

**Identifier:** `edit_minecraft_option`

Altera uma opção do Minecraft, como a distância de renderização ou a escala da GUI.

**Value:** `option_name:value`, como `renderDistance:12`

Consulte [Opções do Minecraft](/minecraft-options) para ver os nomes das opções.

### Simular tecla

**Identifier:** `mimic_keybind`

Pressiona uma tecla de atalho do Minecraft, como pular ou esgueirar-se, e pode mantê-la pressionada.

**Value:** `keybind|||hold|||duration_ms`, como `key.jump|||false|||1000`

| Parte | O que significa |
|---|---|
| `keybind` | O ID da tecla de atalho, como `key.jump` ou `key.sneak`. |
| `hold` | `true` mantém a tecla pressionada; `false` pressiona a tecla uma vez. |
| `duration_ms` | Por quanto tempo a tecla fica pressionada, em milissegundos. O padrão é `1000`. |

### Gerenciar pacote de recursos

**Identifier:** `manage_resource_pack`

Ativa ou desativa um pacote de recursos, conforme as opções configuradas na própria janela:

- **Target Resource Pack**: o nome do pacote, como aparece na tela Pacotes de Recursos. Letras maiúsculas e minúsculas não fazem diferença.
- **Action Mode**: **Enable**, **Disable** ou **Toggle**.
- **Reload Resources**: recarrega os pacotes de recursos logo após a alteração. Desative essa opção para recarregá-los mais tarde, por exemplo, com [**Recarregar pacotes de recursos**](#recarregar-pacotes-de-recursos).

Não é possível desativar pacotes necessários para o jogo.

### Recarregar pacotes de recursos

**Identifier:** `reload_resource_packs`

Recarrega os pacotes de recursos, como `F3 + T`. Durante cinco segundos após a recarga, a ação não faz nada, impedindo recargas repetidas.

**Value:** nenhum

### Recarregar o FancyMenu

**Identifier:** `reloadmenu`

Recarrega layouts, [GUIs personalizadas](/custom-guis), [panoramas](/panoramas), [apresentações de slides](/slideshows), configurações e arquivos do FancyMenu. Os pacotes de recursos não são recarregados.

**Value:** nenhum

> [!WARNING]
> A recarga leva alguns instantes. Use-a em um botão, nunca em um [Ticker](/elements#ticker) ou ouvinte que seja executado com frequência.

### Iniciar agendador

**Identifier:** `start_scheduler`

Inicia um [agendador](/schedulers).

**Value:** o identificador do agendador

### Parar agendador

**Identifier:** `stop_scheduler`

Interrompe um [agendador](/schedulers).

**Value:** o identificador do agendador

### Copiar texto para a área de transferência

**Identifier:** `copytoclipboard`

Copia texto para a área de transferência.

**Value:** o texto, como `play.example.net`

### Exibir no log do jogo

**Identifier:** `print_to_log`

Registra uma linha no log do jogo. É útil para descobrir o que um script está fazendo.

**Value:** o texto
