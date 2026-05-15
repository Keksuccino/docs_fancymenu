---
title: Condições (Requisitos)
description: Como usar requisitos de carregamento.
---

# Requisitos
Requisitos (também chamados de "requisitos de carregamento") permitem tornar partes dos seus layouts visíveis ou invisíveis com base em várias condições, como se um elemento está em hover, se a janela tem um tamanho específico ou se você está atualmente em um mundo.

Eles também podem ser usados em scripts de ação de botões, sliders, tickers e tudo mais que tenha uma entrada de script de ação.

# Adicionando Requisitos aos Elementos
Para adicionar um ou mais requisitos aos elementos, basta clicar com o botão direito no elemento e clicar em **Requisitos de Carregamento**.

# Requisitos para Todo o Layout
Você também pode alterar a visibilidade de layouts inteiros clicando com o botão direito no **fundo do editor** e depois clicando em **Requisitos de Carregamento [Todo o Layout]**.

# Scripts de Ação
Requisitos também podem ser usados em scripts de ação.
Você pode adicioná-los na tela do editor de scripts de ação e usá-los para executar ações específicas somente se a condição do requisito for atendida.

# Valores do Requisito
Alguns requisitos precisam que você defina valores para funcionar corretamente. Se for o caso, a tela do requisito deve informar que você precisa definir todos os valores primeiro, mas, se não, apenas verifique se o botão **Editar Valor do Requisito** fica clicável ao adicionar o requisito.
Sempre confira a descrição do requisito se não tiver certeza sobre o que definir como valor.
Alguns campos de valor até oferecem suporte a **autocompletar com TAB**.

O FancyMenu 3.9.0 reformula a janela Gerenciar Requisitos para usar um menu de contexto ao clicar com o botão direito, navegação por teclado, busca, desfazer/refazer (`CTRL + Z` / `CTRL + Y`) e `CTRL + S` como atalho de **Concluído**.

# Requisitos em Detalhe
A lista a seguir contém a maioria, se não todos, os requisitos disponíveis no FancyMenu. É possível que a lista às vezes fique um pouco desatualizada devido a atualizações do mod.

## O Elemento Está em Hover
Verifica se um elemento específico está em hover pelo cursor do mouse.  
**Valor necessário**: Sim - ID do elemento de destino (por exemplo, `some_element_ID`). Você pode obter o ID clicando com o botão direito em um elemento no editor.

## O Elemento Está Focado
Verifica se um elemento específico atualmente tem foco de teclado (por exemplo, um campo de texto ou um botão focado).
**Valor necessário**: Sim - ID do elemento de destino (o mesmo ID exibido no editor)

> Isso não é o mesmo que apenas estar em hover, embora pareça similar. Elementos focados continuam parecendo "em hover" mesmo quando já não estão mais em hover. Os elementos recebem foco ao serem clicados ou ao usar o teclado para navegar nos menus.
{.is-info}

## Algum Elemento Está em Hover
Verifica se algum elemento no layout está atualmente em hover pelo cursor do mouse.  
**Valor necessário**: Não

## Algum Botão Está em Hover
Verifica se algum botão (vanilla ou customizado) está atualmente em hover pelo cursor do mouse.  
**Valor necessário**: Não

## O Layout Está Habilitado
Verifica se um layout específico está atualmente habilitado.  
**Valor necessário**: Sim - O nome do layout (por exemplo, `my_cool_main_menu_layout`)

## O Agendador Está Rodando
Verifica se um agendador está atualmente em execução.
**Valor necessário**: Sim - ID do agendador (por exemplo, `my_scheduler`)

## É Escala da GUI
Verifica se a escala atual da GUI corresponde a determinadas condições.  
**Valor necessário**: Sim - Pode aceitar valores numéricos como `1`, `2`, etc.

## O Botão Está Ativo
Verifica se um botão específico está ativo (clicável).  
**Valor necessário**: Sim - ID do botão de destino (por exemplo, "some_element_ID")

## É Título da Tela
Verifica se o título de EXIBIÇÃO da tela corresponde a um texto específico ou chave de localização. Isso verificará apenas o nome/título exibido da tela, como "Opções" ou "Pausar". NÃO verificará o identificador do menu/tela (como `title_screen`)!

**Valor necessário**: Sim - O texto exato do título ou a chave de localização da tela

## Tecla Pressionada
Verifica se uma tecla específica do teclado está sendo pressionada no momento.  
**Valor necessário**: Sim - O código da tecla de destino. Selecionado por meio de uma interface ao editar o valor do requisito.

## Alguma Tela Está Aberta
Verifica se alguma tela/menu está aberta no momento (retorna falso se nenhuma tela estiver sendo exibida).  
**Valor necessário**: Não

## A Sobreposição de Debug do MC Está Habilitada
Verifica se a sobreposição de debug do F3 está visível no momento.
**Valor necessário**: Não

## É Tipo de Cursor Ativo
Verifica se o tipo de cursor ativo no FancyMenu corresponde a um tipo de cursor padrão específico.
**Valor necessário**: Sim - Tipo de cursor: `normal`, `writing`, `crosshair`, `pointing_hand`, `resize_horizontal`, `resize_vertical`, `resize_nwse`, `resize_nesw`, `resize_all` ou `not_allowed`

## A Barra de Menu de Personalização Está Visível
Verifica se a barra de menu de personalização do FancyMenu está visível no momento.
**Valor necessário**: Não

## O Modo de Modpack Está Habilitado
Verifica se o Modo de Modpack do FancyMenu está habilitado.
**Valor necessário**: Não

## Clique do Mouse
Verifica se um botão específico do mouse está sendo pressionado.  
**Valor necessário**: Sim - `left` ou `right` para indicar qual botão do mouse verificar

## É Tela Cheia
Verifica se o jogo está atualmente em modo de tela cheia.  
**Valor necessário**: Não

## É Largura da Janela
Verifica se a largura da janela do jogo corresponde a valores específicos.  
**Valor necessário**: Sim - Largura da janela em pixels (por exemplo, "1920"). Vários valores podem ser fornecidos separados por vírgulas.

## É Altura da Janela
Verifica se a altura da janela do jogo corresponde a valores específicos.  
**Valor necessário**: Sim - Altura da janela em pixels (por exemplo, "1080"). Vários valores podem ser fornecidos separados por vírgulas.

## A Largura da Janela é Maior Que
Verifica se a largura da janela do jogo é maior que um valor específico.  
**Valor necessário**: Sim - Largura da janela em pixels (por exemplo, "1920")

## A Altura da Janela é Maior Que
Verifica se a altura da janela do jogo é maior que um valor específico.  
**Valor necessário**: Sim - Altura da janela em pixels (por exemplo, "1080")

## É Multijogador
Verifica se o jogador está atualmente em um mundo multijogador.  
**Valor necessário**: Não

## É Um Jogador
Verifica se o jogador está atualmente em um mundo de um jogador.  
**Valor necessário**: Não

## O Mundo Está Carregado
Verifica se algum mundo está carregado no momento.  
**Valor necessário**: Não

## É Aventura
Verifica se o jogador está atualmente no modo aventura.  
**Valor necessário**: Não

## É Criativo
Verifica se o jogador está atualmente no modo criativo.  
**Valor necessário**: Não

## É Espectador
Verifica se o jogador está atualmente no modo espectador.  
**Valor necessário**: Não

## É Sobrevivência
Verifica se o jogador está atualmente no modo sobrevivência.  
**Valor necessário**: Não

## É Modo de Jogo
Verifica se o jogador está em um modo de jogo específico.  
**Valor necessário**: Sim - Nome do modo de jogo (por exemplo, "creative", "survival", "adventure", "spectator")

## É Dificuldade
Verifica se a dificuldade atual do jogo corresponde a um valor específico.  
**Valor necessário**: Sim - Nome da dificuldade (por exemplo, "peaceful", "easy", "normal", "hard")

## É Hardcore
Verifica se o mundo carregado no momento está em modo hardcore.
**Valor necessário**: Não

## É Perspectiva da Câmera
Verifica se a perspectiva atual da câmera corresponde a uma perspectiva específica.
**Valor necessário**: Sim - `first_person`, `third_person_back` ou `third_person_front`

## Está Chovendo
Verifica se está chovendo atualmente na localização do jogador.  
**Valor necessário**: Não

## Está Trovejando
Verifica se há atualmente uma tempestade com trovões no mundo do jogador.  
**Valor necessário**: Não

## O Clima Está Limpo
Verifica se o clima está limpo no momento (sem chuva ou trovões).  
**Valor necessário**: Não

## Está Nevando
Verifica se está nevando atualmente na localização do jogador.  
**Valor necessário**: Não

## O Jogador Está Correndo
Verifica se o jogador está atualmente correndo em sprint.  
**Valor necessário**: Não

## O Jogador Está Agachado
Verifica se o jogador está atualmente agachado/abaixado.
**Valor necessário**: Não

## O Jogador Está Usando Item
Verifica se o jogador está usando um item no momento.
**Valor necessário**: Não

## O Jogador Está Nadando
Verifica se o jogador está nadando no momento.  
**Valor necessário**: Não

## O Jogador Está Pulando ou Caindo
Verifica se o jogador está pulando no momento.  
**Valor necessário**: Não

## O Jogador Está Sob a Água
Verifica se o jogador está completamente submerso na água.  
**Valor necessário**: Não

## O Jogador Está na Água
Verifica se o jogador está na água (pode estar parcialmente submerso).  
**Valor necessário**: Não

## O Jogador Está na Lava
Verifica se o jogador está na lava.  
**Valor necessário**: Não

## O Jogador Está em Fluido
Verifica se o jogador está em qualquer fluido (água, lava, etc.).  
**Valor necessário**: Não

## O Jogador Está Montado em Entidade/Veículo
Verifica se o jogador está montado em qualquer entidade.  
**Valor necessário**: Não

## O Jogador Está Montado em Entidade que Pula
Verifica se o jogador está montado em uma entidade que pode pular (como um cavalo).  
**Valor necessário**: Não

## O Jogador Está Montado em Entidade com Vida
Verifica se o jogador está montado em uma entidade viva com vida (como animais, não barcos).  
**Valor necessário**: Não

## O Jogador Está na Neve em Pó
Verifica se o jogador está atualmente na neve em pó.  
**Valor necessário**: Não

## O Jogador Estava na Neve em Pó
Verifica se o jogador estava na neve em pó (usado para efeitos que persistem após sair).  
**Valor necessário**: Não

## O Jogador Está Usando Abóbora
Verifica se o jogador está usando uma abóbora esculpida na cabeça.  
**Valor necessário**: Não

## O Jogador Está Voando com Elytra
Verifica se o jogador está voando com uma elytra no momento.  
**Valor necessário**: Não

## O Jogador Está Voando no Criativo
Verifica se o jogador está voando no modo criativo.  
**Valor necessário**: Não

## O Jogador Tem Corações de Absorção
Verifica se o jogador tem algum coração de absorção (corações dourados).  
**Valor necessário**: Não

## O Jogador Está Com o Efeito Wither
Verifica se o jogador está afetado pelo efeito wither.  
**Valor necessário**: Não

## O Jogador Está Totalmente Congelado
Verifica se o jogador está totalmente congelado (geralmente por neve em pó).  
**Valor necessário**: Não

## O Jogador Está Envenenado
Verifica se o jogador está afetado pelo efeito de veneno.  
**Valor necessário**: Não

## O Jogador Está em Bioma
Verifica se o jogador está em um bioma específico.  
**Valor necessário**: Sim - Identificador do bioma (por exemplo, `minecraft:birch_forest`)

## O Jogador Está em Dimensão
Verifica se o jogador está em uma dimensão específica.  
**Valor necessário**: Sim - Identificador da dimensão (por exemplo, `minecraft:overworld`, `minecraft:the_nether`, `minecraft:the_end`)

## O Jogador Está em Estrutura
Verifica se o jogador está atualmente dentro de uma estrutura específica. Requer o FancyMenu no servidor para mundos em servidor.
**Valor necessário**: Sim - Identificador da estrutura (por exemplo, `minecraft:village`)

## Entidade Próxima
Verifica se um tipo específico de entidade está dentro de um certo raio do jogador.  
**Valor necessário**: Sim - Formato: "raio:entity_id" (por exemplo, `10:minecraft:pig` - verifica por porcos dentro de 10 blocos)

## O Efeito Está Ativo
Verifica se um efeito de poção específico está ativo no jogador.  
**Valor necessário**: Sim - Identificador do efeito (por exemplo, `minecraft:speed`, `minecraft:strength`)

## Qualquer Efeito Está Ativo
Verifica se o jogador tem algum efeito de poção ativo.  
**Valor necessário**: Não

## O Jogador é Canhoto
Verifica se o jogador está configurado como canhoto nas opções do jogo.  
**Valor necessário**: Não

## O Slot do Inventário Está Preenchido
Verifica se um slot específico do inventário contém um item.  
**Valor necessário**: Sim - Número do slot (0-35 para o inventário principal, slots 0-8 são a hotbar)

## O Item Está em Hover no Inventário
Verifica se o cursor está sobre qualquer item em uma tela de inventário.
**Valor necessário**: Não

## O Cursor Está Segurando um Item do Inventário
Verifica se o cursor está atualmente segurando uma pilha de item do inventário.
**Valor necessário**: Não

## O Slot da Hotbar Está Selecionado
Verifica se um slot específico da hotbar está selecionado no momento.  
**Valor necessário**: Sim - Número do slot da hotbar (0-8)

## O Jogador Tem Nível de Permissão
Verifica se o jogador tem pelo menos o nível de permissão/OP especificado no mundo ou servidor atual.  
**Valor necessário**: Sim - Número do nível de permissão (0-4, onde 4 é operador do servidor)

## A Força de Ataque Está Reduzida
Verifica se a força de ataque do jogador está atualmente reduzida (não totalmente carregada).  
**Valor necessário**: Não

## É Hora do Tempo Real
Verifica se o dia atual do mês no mundo real corresponde a um valor específico.  
**Valor necessário**: Sim - Número do dia (1-31). Vários valores podem ser fornecidos separados por vírgulas.

## É Hora do Tempo Real
Verifica se a hora atual no mundo real corresponde a um valor específico.  
**Valor necessário**: Sim - Hora no formato de 24 horas (0-23). Vários valores podem ser fornecidos separados por vírgulas.

## É Minuto do Tempo Real
Verifica se o minuto atual no mundo real corresponde a um valor específico.  
**Valor necessário**: Sim - Minuto (0-59). Vários valores podem ser fornecidos separados por vírgulas.

## É Mês do Tempo Real
Verifica se o mês atual no mundo real corresponde a um valor específico.  
**Valor necessário**: Sim - Número do mês (1-12, onde 1 é janeiro). Vários valores podem ser fornecidos separados por vírgulas.

## É Segundo do Tempo Real
Verifica se o segundo atual no mundo real corresponde a um valor específico.  
**Valor necessário**: Sim - Segundo (0-59). Vários valores podem ser fornecidos separados por vírgulas.

## É Dia da Semana do Tempo Real
Verifica se o dia atual da semana no mundo real corresponde a um valor específico.  
**Valor necessário**: Sim - Dia da semana como número (1-7, onde 1 é domingo). Vários valores podem ser fornecidos separados por vírgulas.

## É Ano do Tempo Real
Verifica se o ano atual no mundo real corresponde a um valor específico.  
**Valor necessário**: Sim - Ano completo (por exemplo, "2023"). Vários valores podem ser fornecidos separados por vírgulas.

## Arquivo/Pasta Existe
Verifica se um arquivo ou pasta específica existe no sistema.  
**Valor necessário**: Sim - Caminho para o arquivo ou pasta (absoluto ou relativo ao diretório do jogo)

## O SO é Linux
Verifica se o sistema operacional é Linux.  
**Valor necessário**: Não

## O SO é macOS
Verifica se o sistema operacional é macOS.  
**Valor necessário**: Não

## O SO é Windows
Verifica se o sistema operacional é Windows.  
**Valor necessário**: Não

## A Conexão com a Internet Está Disponível
Verifica se uma conexão ativa com a internet está disponível.  
**Valor necessário**: Não

## É Idioma do Jogo
Verifica se o idioma atual do jogo corresponde a um valor específico.  
**Valor necessário**: Sim - Código do idioma (por exemplo, `en_us` para inglês)

## O Mod Está Carregado
Verifica se um mod específico está carregado.  
**Valor necessário**: Sim - ID do mod (por exemplo, `fancymenu`, `jei`). Você também pode verificar o Optifine com `optifine`. Vários IDs de mods podem ser fornecidos separados por vírgulas.

## O MCEF Está Carregado
Verifica se o MCEF (Minecraft Chromium Embedded Framework) está instalado e inicializado.  
**Valor necessário**: Não

## É Número
Fornece comparação avançada de números com diferentes modos de comparação.  
**Valor necessário**: Sim - Formato complexo: `["mode":"comparison_mode","number":"valor1","compare_with":"valor2"]$` onde `comparison_mode` pode ser `equals`, `bigger-than`, `smaller-than`, `bigger-than-or-equals` ou `smaller-than-or-equals`

## É Texto
Fornece comparação avançada de texto com diferentes modos de comparação.  
**Valor necessário**: Sim - Formato complexo: `["mode":"comparison_mode","text":"texto1","compare_with":"texto2"]$` onde `comparison_mode` pode ser `equals`, `contains`, `starts-with` ou `ends-with`

## É IP do Servidor
Verifica se o IP do servidor atual corresponde a um valor específico.  
**Valor necessário**: Sim - Endereço IP do servidor (com ou sem porta)

## O Servidor Está Online
Verifica se um servidor específico está online e acessível.  
**Valor necessário**: Sim - Endereço IP do servidor (com ou sem porta)

## O Pacote de Recursos Está Habilitado
Verifica se um pacote de recursos específico está atualmente selecionado/ativo.  
**Valor necessário**: Sim - Título do pacote de recursos ou ID do pacote (por exemplo, `Programmer Art` ou o ID do pacote)

## É Valor de Variável (Variável FM)
Verifica se uma variável do FancyMenu tem um valor específico.  
**Valor necessário**: Sim - Formato: "nome_da_variável:valor_esperado"

## Apenas Uma Vez por Sessão
Retorna verdadeiro apenas uma vez por sessão de jogo. Útil para anúncios ou ações únicas.  
**Valor necessário**: Não
