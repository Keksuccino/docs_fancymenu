---
title: Variáveis
description: >-
  Como armazenar textos e listas em variáveis e usá-los em textos, ações e
  requisitos.
sourceBlobSha: 2f0d48fd6cc100f976d4fdf1bceb28fe1a540a52
---

# Variáveis

As variáveis são valores que o FancyMenu guarda, mesmo depois que o jogo é fechado. Use-as para contar cliques, guardar escolhas, acompanhar o progresso ou manter listas, como dicas de carregamento. Textos, ações, requisitos, listeners e alguns elementos podem ler e alterar variáveis.

> [!TIP]
> As ações para variáveis estão listadas em [Scripts de Ação](/action-scripts), os requisitos em [Requisitos](/conditions) e o listener em [Listeners](/listeners#on-variable-updated-fm-variable).

# Variáveis de Texto e de Lista

Há dois tipos de variáveis:

- Variáveis de texto armazenam um texto, como `dark`, `5` ou `true`.
- Variáveis de lista armazenam uma lista de itens, como dicas de carregamento ou nomes de servidores. Cada item é um texto independente.

A posição de um item em uma lista é o índice dele. O primeiro item tem índice `0`, o segundo tem índice `1` e assim por diante. Índices negativos contam a partir do fim, então `-1` é o último item.

Recursos que só reconhecem texto, como `$$name` ou **Is Variable Value (FM Variable)**, recebem uma lista como um array JSON com seus itens, por exemplo `["Craft a bed before your first night.","Torches keep most mobs away."]`.

# Gerenciar Variáveis

Abra **barra de menus -> Personalização -> Gerenciar Variáveis**. Essa opção só aparece na barra de menus fora do editor de layout.

<img width="800" alt="Adicionando a variável de texto menu_theme com o valor dark e a variável de lista tips com três dicas em Gerenciar Variáveis" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_manage.gif?raw=true">

## Adicionar Variáveis

1. Clique com o botão direito na lista e clique em **Adicionar Variável de Texto** ou **Adicionar Variável de Lista**.
2. Digite um nome e clique em **Concluído**.

Os nomes podem conter letras minúsculas, números, `.`, `_` e `-`, e cada nome só pode existir uma vez.

## Alterar Variáveis

Clique com o botão direito em uma variável para ver estas opções:

| Opção | O que faz |
|---|---|
| **Definir Valor** | Define o texto de uma variável de texto. |
| **Editar Lista** | Abre o editor de lista de uma variável de lista (veja abaixo). |
| **Converter em Lista…** | Transforma uma variável de texto em uma lista. Um **Separador** divide o texto em itens: digite `\n` para dividir nas quebras de linha. **Remover Espaços dos Itens** remove os espaços ao redor de cada item, e **Ignorar Itens Vazios** exclui os itens vazios. Textos que já são um array JSON, como `["a","b"]`, são interpretados como um único item (**Ler como Array JSON**). |
| **Converter em Texto…** | Transforma uma lista em uma variável de texto. O **Separador** é colocado entre os itens, ou **Manter Texto JSON** mantém a lista como um array JSON. |
| **Limpar Variável ao Iniciar o Jogo** | Esvazia a variável toda vez que o jogo é iniciado. Útil para valores que devem durar apenas uma sessão. |
| **Excluir Variável** | Exclui a variável. |
| **Copiar** e **Colar** | Cria uma cópia de uma variável. |
| **Exportar Variável para IA** | Exporta a variável para [conversas com IA](/export-for-ai). |

As alterações são aplicadas imediatamente. Desfaça-as com `Ctrl + Z` e refaça-as com `Ctrl + Y` (`Cmd` no macOS). Comece a digitar para pesquisar, pressione `Enter` para editar a variável selecionada ou `Delete` para excluí-la.

## Editar Listas

O editor de lista mostra cada item com seu índice.

- Para adicionar itens, clique em **Adicionar Item** abaixo da lista, digite o item e pressione `Enter`. O próximo item novo começa a ser adicionado imediatamente. Pressione `Enter` em um item vazio ou `Esc` para parar de adicionar.
- Para editar um item, clique duas vezes nele. `Shift + Enter` abre o item no editor de texto, onde ele pode ter quebras de linha.
- Para reordenar os itens, arraste-os ou pressione `Alt + Up` e `Alt + Down`.
- Clique com o botão direito em um item para acessar **Duplicar Item** (`Ctrl + D`), **Excluir Item** (`Delete`), **Copiar**, **Colar**, **Mover para Cima** e **Mover para Baixo**.
- **Editar como Texto** permite editar todos os itens de uma vez, um por linha.

**Concluído** salva a lista. **Cancelar** descarta todas as alterações feitas no editor de lista.

# Exibir Variáveis em Textos

Digite `$$` seguido do nome de uma variável para exibir o valor dela: uma variável chamada `menu_theme` é acessada com `$$menu_theme`. Isso funciona em qualquer texto que aceite [espaços reservados](/placeholders), como [elementos de texto](/text-in-menus), rótulos de botões, dicas de ferramentas e valores de ações e requisitos. O texto é atualizado automaticamente quando a variável muda.

```
Tema atual: $$menu_theme
```

- `$$name` de uma variável inexistente permanece como está.
- Quando os nomes começam da mesma forma, como `coins` e `coins_record`, `$$coins_record` sempre corresponde ao nome mais longo.
- Uma lista é exibida como um array JSON. Estes espaços reservados exibem listas de uma forma mais prática:

| Espaço reservado | Exemplo | Resultado |
|---|---|---|
| **Obter Valor da Variável (FM Variable)** | `{"placeholder":"getvariable","values":{"name":"clicks"}}` | O valor ou `0` quando a variável está vazia ou não existe. Ideal para números. |
| **Obter Item da Lista (FM Variable)** | `{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}` | O item no índice indicado ou o valor de `fallback` quando não há nenhum. |
| **Tamanho da Lista (FM Variable)** | `{"placeholder":"list_size","values":{"name":"tips"}}` | Quantos itens há na lista. |
| **Índice do Item da Lista (FM Variable)** | `{"placeholder":"list_index_of","values":{"name":"tips","value":"Torches keep most mobs away.","ignore_case":"false"}}` | O índice do primeiro item que corresponde ao `value` completo ou `-1`. |
| **Juntar Itens da Lista (FM Variable)** | `{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}` | Todos os itens em um único texto, com o `separator` entre eles (`, ` se não for informado). `\n` representa uma quebra de linha. |

# Alterar Variáveis com Ações

Os [scripts de ação](/action-scripts) alteram variáveis quando um botão é clicado, um ticker é executado, um listener é acionado e assim por diante.

## Variáveis de Texto

[**Definir Valor da Variável (FM Variable)**](/action-scripts#set-variable-value-fm-variable) recebe o nome e o novo valor, separados por `:`. Se a variável ainda não existir, ela será criada.

```
menu_theme:dark
```

Somente o primeiro `:` separa o nome, então o valor pode conter outros, como em `last_server:play.example.net:25565`.

Para contar os cliques em um botão, some 1 ao valor anterior:

```
clicks:{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

**Obter Valor da Variável (FM Variable)** retorna `0` enquanto `clicks` estiver vazia, então o primeiro clique define o valor como `1`.

Definir Valor da Variável nunca transforma uma lista em texto. Um array JSON se torna os itens da lista, um texto vazio esvazia a lista e qualquer outro texto se torna o único item dela.

[**Excluir Variável (FM Variable)**](/action-scripts#delete-variable-fm-variable) exclui uma variável, e [**Limpar Todas as Variáveis (FM Variable)**](/action-scripts#clear-all-variables-fm-variable) exclui todas elas.

## Ações de Lista

Cada ação de lista tem sua própria janela. Todos os campos aceitam espaços reservados.

| Ação | O que faz |
|---|---|
| [**Adicionar à Lista (FM Variable)**](/action-scripts#add-to-list-fm-variable) | Adiciona um item ao final ou em um índice. **Ignorar se Já Estiver na Lista** não adiciona o item se ele já estiver na lista. |
| [**Definir Item da Lista (FM Variable)**](/action-scripts#set-list-entry-fm-variable) | Substitui o item em um índice. |
| [**Remover da Lista (FM Variable)**](/action-scripts#remove-from-list-fm-variable) | Remove o **Item no Índice**, a **Primeira Correspondência** de um valor ou **Todas as Correspondências**. |
| [**Limpar Lista (FM Variable)**](/action-scripts#clear-list-fm-variable) | Remove todos os itens. A lista continua existindo, mas fica vazia. |
| [**Definir Lista (FM Variable)**](/action-scripts#set-list-fm-variable) | Substitui todos os itens pelas partes de um **Texto Dividido** ou pelos itens de um **Array JSON**. `$$other_list` como Array JSON copia outra lista. |
| [**Organizar Lista (FM Variable)**](/action-scripts#arrange-list-fm-variable) | **Ordenar de A–Z**, **Ordenar de Z–A**, **Números, do Menor para o Maior**, **Números, do Maior para o Menor**, **Inverter Ordem**, **Embaralhar** ou **Remover Duplicatas**. |

- As ações de lista criam listas que ainda não existem e transformam variáveis de texto vazias em listas. Elas nunca alteram uma variável de texto que tenha um valor: [converta-a](#changing-variables) primeiro.
- Digite o nome da lista sem `$$`. Com `$$`, a ação usa o valor dessa variável como nome.

Por exemplo, um elemento de texto exibe o primeiro item da lista `tips`:

```
{"placeholder":"list_get","values":{"name":"tips","index":"0"}}
```

Um botão Próxima Dica abaixo dele usa **Organizar Lista (FM Variable)** com a opção **Embaralhar** no script de ação:

<img width="800" alt="Adicionando Organizar Lista com a lista tips e a opção Embaralhar ao script de ação de um botão Próxima Dica no editor de layout" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_script.gif?raw=true">

A cada clique, a lista é embaralhada, então o texto exibe uma dica aleatória:

<img width="800" alt="Clicar no botão Próxima Dica exibe uma dica do dia diferente" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/variables_next_tip_result.gif?raw=true">

## Percorrer uma Lista

O loop [FOR EACH](/action-scripts#for-each-loop) executa as ações dentro dele uma vez para cada item de uma lista, do primeiro ao último.

1. Clique com o botão direito na área de script do editor de scripts de ação e clique em **Adicionar Loop FOR EACH**.
2. Digite o nome da variável de lista, sem `$$`, e clique em **Concluído**.
3. Adicione ações dentro do loop. Nos valores delas, `$$list_entry` corresponde ao item atual e `$$list_index`, ao índice dele.

Por exemplo, uma lista `starter_commands` com os itens `/time set day` e `/weather clear` e uma ação [**Enviar Mensagem/Comando no Chat**](/action-scripts#send-chat-messagecommand) dentro do loop, com este valor, executa os dois comandos:

```
$$list_entry
```

- O loop lê a lista uma vez ao iniciar. As ações dentro dele podem alterar a lista sem mudar quais itens o loop percorre.
- Se for uma variável de texto ou uma lista inexistente, o loop será executado zero vezes.
- Assim como os loops WHILE, ele para após 3 segundos para não travar o jogo.

# Verificar Variáveis

Os [requisitos](/conditions) exibem elementos ou executam partes de scripts de ação somente quando uma variável tem determinado valor.

- [**O Valor da Variável É (FM Variable)**](/conditions#is-variable-value-fm-variable) verifica o valor completo. Para listas, compara o array JSON de todos os itens.
- [**A Lista Contém o Item (FM Variable)**](/conditions#list-contains-entry-fm-variable) verifica se uma lista contém um item. A correspondência precisa ser com o item completo. **Ignorar Maiúsculas e Minúsculas** faz com que `Apple` corresponda a `apple`.
- [**É Número**](/conditions#is-number) compara números, como verificar se `$$clicks` é maior que `5`.

Por exemplo, um botão abre a publicação de notícias mais recente e adiciona `news_42` à lista `read_news` com **Adicionar à Lista (FM Variable)**. Um selo "Novo!" ao lado do botão tem o requisito **A Lista Contém o Item (FM Variable)** para `news_42`, com o **Modo do Requisito** definido como Oposto. Assim, o selo desaparece quando o jogador lê a publicação.

# Vincular Variáveis a Elementos

- [Campo de Entrada de Texto](/elements#text-input-field): **Vincular à Variável** grava na variável o que o jogador digita, e o campo exibe o valor da variável. Se estiver vinculado a uma lista, o texto digitado substituirá a lista inteira.
- [Caixa de Seleção](/elements#checkbox): ative **Modo de Variável** e defina **Vincular à Variável**. A caixa de seleção grava `true` ou `false` na variável.
- [Controle deslizante](/elements#slider) do tipo **Lista de Valores**: **Valores de Variável de Lista** obtém os valores do controle deslizante de uma lista. Os itens adicionados ou removidos da lista aparecem imediatamente.

# Reagir a Alterações

- O listener [**Ao Atualizar Variável [FM Variable]**](/listeners#on-variable-updated-fm-variable) executa um script de ação sempre que uma variável é definida.
- O comando [`/fmvariable`](/commands#fmvariable) define e lê variáveis pelo chat, por blocos de comando e por outros mods.

# Onde as Variáveis São Salvas

O FancyMenu salva as variáveis imediatamente em `<game-directory>/config/fancymenu/user_variables.db`, para que elas sejam mantidas após reiniciar o jogo.

- As variáveis pertencem à instância inteira do Minecraft e ao [perfil](/profiles) ativo. Elas não são separadas por layout, mundo, servidor ou jogador.
- Os nomes diferenciam maiúsculas de minúsculas.
- Não armazene senhas, tokens ou outros segredos em variáveis. Qualquer pessoa com acesso à pasta do jogo pode lê-los.
