---
title: Perfis
description: >-
  Salve, alterne e compartilhe configurações completas do FancyMenu com perfis e
  instale modelos de layout da comunidade.
sourceBlobSha: 52348efde29798073477e572b59a7630f96013ad
---

# Perfis

Um perfil é uma configuração completa do FancyMenu: layouts, recursos, variáveis, configurações e tudo mais em `config/fancymenu/` (consulte [Locais de armazenamento de dados](/data-storage-locations#your-setup)). Com os perfis, você mantém várias configurações em uma única instância do Minecraft, alterna entre elas em segundos e as compartilha em um único arquivo.

<img width="800" alt="Criação do perfil My Menu Pack, importação do perfil Wind Chimes ao arrastar o arquivo .fmp para a janela Perfis, exclusão de My Menu Pack e carregamento de Wind Chimes, que altera a tela de título" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# A janela Perfis

Abra-a em **barra de menus -> Personalização -> Perfis**.

- A lista à esquerda mostra todos os perfis. O perfil carregado aparece primeiro e é marcado como **Ativo**. Todas as alterações feitas no FancyMenu são aplicadas diretamente a ele.
- O lado direito mostra o perfil selecionado: ícone, título, versão, autores, número de layouts, tamanho, links e descrição.
- Os botões abaixo da lista e dos detalhes exibem seus nomes quando você passa o cursor sobre eles. Clique com o botão direito em um perfil para ver também as ações disponíveis.

Sua configuração se torna automaticamente seu primeiro perfil, chamado **Meu Perfil**.

# Carregando um perfil

Selecione um perfil e clique em **Carregar perfil**, clique duas vezes nele ou pressione `Enter`.

O FancyMenu será reiniciado com o perfil, como acontece ao iniciar o jogo. Todas as outras janelas do FancyMenu serão fechadas e, se você não estiver em um mundo, a tela de título será aberta.

> [!NOTE]
> Carregar um perfil nunca exclui nada. Primeiro, sua configuração atual é salva como um perfil próprio, para que você sempre possa voltar a ela.

# Criando perfis

- **Novo perfil** (o botão `+` abaixo da lista) cria um perfil vazio e abre seus detalhes imediatamente para que você possa dar um nome a ele. O perfil mantém suas preferências do FancyMenu, como a escala da interface e o tema, mas não tem layouts nem outras personalizações. Ele não é carregado automaticamente.
- **Duplicar** copia o perfil selecionado. É uma opção útil para experimentar algo sem alterar o original.

# Editando os detalhes do perfil

Selecione um perfil e clique em **Editar** para alterar seus detalhes:

- **Título**, a única informação obrigatória de um perfil.
- **Versão** e **Autores**. Separe vários autores com vírgulas.
- **Descrição**, com recursos de [Markdown](/text-formatting#markdown), como texto em negrito, títulos e listas.
- **Rastreador de problemas**, um site onde as pessoas podem relatar problemas com o perfil. Ele aparece como **Relatar um problema**.
- **Links** para seu servidor do Discord, canal do YouTube, site e muito mais. Clique em **Adicionar link** e cole o link: o FancyMenu identifica a plataforma automaticamente.
- Um ícone: **Escolher ícone** aceita uma imagem PNG, e **Remover ícone** a remove. Imagens que não forem quadradas serão cortadas pelo centro.

Nada será salvo até você clicar em **Concluir**.

# Compartilhando perfis

> [!CAUTION]
> Os perfis podem executar ações, como abrir links ou executar comandos. Importe-os somente de fontes confiáveis.

## Exportando

Selecione um perfil, clique em **Exportar** e escolha onde salvá-lo. Isso cria um arquivo `.fmp` com o perfil completo, pronto para ser compartilhado.

## Importando

Clique em **Importar**, abaixo da lista, e escolha um arquivo `.fmp`, ou arraste o arquivo para a janela Perfis.

- Os perfis importados não são carregados automaticamente. Carregue-os como qualquer outro perfil.
- Se você já tiver o perfil, por exemplo, uma versão mais antiga, escolha **Substituir** ou **Manter ambos**. Ao substituir o perfil carregado, o perfil importado será carregado imediatamente e suas alterações no perfil antigo serão perdidas.
- Perfis criados com uma versão mais recente do FancyMenu exibem um aviso antes da importação, pois algumas partes podem não funcionar.
- Só funcionam arquivos `.fmp` exportados pelo FancyMenu. Para uma pasta comum, consulte a próxima seção.

## Adicionando pastas de configurações

Algumas configurações são fornecidas como uma pasta `fancymenu` comum (uma cópia de `config/fancymenu/` de alguém), em vez de um arquivo `.fmp`. Para adicioná-la como perfil:

1. Descompacte-a, se ela vier como arquivo `.zip`.
2. Mova a pasta para `<game-directory>/config/fancymenu/profiles/`. Crie a pasta `profiles` se ela ainda não existir.
3. Abra a janela Perfis ou feche-a e abra-a novamente. O FancyMenu adicionará a pasta aos seus perfis.

A pasta deve conter diretamente os arquivos, como `customization/` e `options.txt`, e não outra pasta `fancymenu`. O perfil receberá o nome da pasta como título, a menos que ela contenha detalhes próprios do perfil. Altere o título em **Editar**.

## Modelos de layout

O canal [`#layout-templates`](https://discord.com/channels/704163135787106365/1234093433795383316) do [servidor do Discord Kekscord](https://discord.gg/rhayah27GC) (servidor oficial de suporte a mods do Keksuccino) contém configurações completas criadas pela comunidade para o FancyMenu e seus complementos, como SpiffyHUD e Drippy Loading Screen. Cada publicação inclui um link para download, seja de um arquivo `.fmp` ou de uma pasta `fancymenu`.

Os modelos são complexos, então não tente mesclá-los com sua própria configuração. Adicione cada um como um perfil separado:

1. [Importe](#importando) o arquivo `.fmp` ou [adicione a pasta](#adicionando-pastas-de-configurações).
2. Selecione o modelo na janela Perfis e clique em **Carregar perfil**.

Sua própria configuração continua disponível como um perfil separado, então você sempre pode voltar a ela.

A maioria dos modelos permite que você os edite e use em seus próprios projetos, como modpacks, mas nem todos. Sempre confira a publicação do modelo para saber o que você tem permissão para fazer com ele.

# Excluindo perfis

Selecione um perfil e clique em **Excluir**, ou pressione `Delete` (`Fn + Delete` no macOS). A exclusão não pode ser desfeita, então exporte o perfil antes se quiser ter um backup.

O perfil carregado não pode ser excluído. Carregue outro perfil primeiro.

# Onde os perfis são armazenados

- O perfil carregado corresponde ao conteúdo de `<game-directory>/config/fancymenu/`.
- Todos os outros perfis ficam em `<game-directory>/config/fancymenu/profiles/`, cada um em sua própria pasta. **Abrir pasta** abre a pasta do perfil selecionado.

`<game-directory>` é a pasta da sua instância, que pode ser diferente de `.minecraft`. Os dados em `<game-directory>/fancymenu_data/` não fazem parte dos perfis. Consulte [Locais de armazenamento de dados](/data-storage-locations#instance-data).

# Quando algo dá errado

- **Alguns arquivos ainda estão em uso:** muitas vezes, o próprio jogo ainda está carregando algo, como áudio. Aguarde alguns segundos e tente novamente. Se continuar acontecendo, feche programas que possam estar usando os arquivos, como seu antivírus, um serviço de sincronização na nuvem ou uma janela do explorador de arquivos.
- **A última troca de perfil ainda não terminou:** nada foi perdido. Carregue um perfil novamente ou reinicie o jogo para concluir a troca.
- **Não há espaço suficiente em disco:** a mensagem informa quanto espaço o perfil precisa. Libere espaço e tente novamente.
- As ações dos perfis são executadas uma de cada vez. Exportar, importar e duplicar perfis grandes pode demorar um pouco, então um botão **Cancelar** será exibido enquanto essas ações estiverem em andamento.
