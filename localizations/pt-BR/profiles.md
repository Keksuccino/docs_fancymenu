---
title: Perfis
description: >-
  Como salvar, alternar e compartilhar configurações completas do FancyMenu com
  perfis.
sourceBlobSha: d0a07901ee271d802c7bc07ea6d787575f48d51c
---
# Perfis

Um perfil é uma configuração completa do FancyMenu: todos os layouts, recursos, variáveis e configurações do FancyMenu de uma instância. Os perfis permitem manter várias configurações em uma única instância do Minecraft, alternar entre elas em segundos e compartilhá-las com outras pessoas como um único arquivo.

<img width="800" alt="perfis" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/profiles_showcase.gif?raw=true">

# Abrindo a janela de Perfis

Abra a janela de Perfis em **barra de menus -> Personalização -> Perfis**.

A lista à esquerda mostra todos os seus perfis, e o lado direito exibe os detalhes do perfil selecionado. O perfil carregado é marcado como **Ativo**. Todas as alterações feitas no FancyMenu são aplicadas diretamente ao perfil carregado.

Sua configuração existente se torna automaticamente seu primeiro perfil, chamado **Meu Perfil**.

> [!TIP]
> Clique com o botão direito do mouse em um perfil na lista para ver todas as ações disponíveis para ele.

# Alternando entre perfis

Selecione um perfil e clique em **Carregar perfil**, ou clique duas vezes nele. O FancyMenu será recarregado com a configuração selecionada.

> [!NOTE]
> Alternar entre perfis nunca apaga nada. Sua configuração atual é salva como um perfil próprio antes que o outro seja carregado, então você sempre pode voltar para ela.

# Criando perfis

- **Novo perfil** (o botão **+** abaixo da lista) cria um perfil vazio e abre seu editor. Perfis vazios mantêm suas preferências pessoais do FancyMenu, como a escala da interface e o tema.
- **Duplicar** cria uma cópia do perfil selecionado, o que é útil para experimentar algo sem alterar o original.

# Editando perfis

Clique em **Editar** para alterar o título, a versão, os autores, a descrição, o ícone, o rastreador de problemas e os links de um perfil. A descrição é compatível com Markdown, e o ícone pode ser qualquer imagem PNG.

Nada é salvo até que você clique em **Concluído**.

# Compartilhando perfis

> [!CAUTION]
> Os perfis podem executar ações. Importe-os apenas de fontes confiáveis.

## Exportando

Selecione um perfil, clique em **Exportar** e escolha onde salvá-lo. Isso cria um arquivo `.fmp` que contém o perfil completo.

## Importando

Clique em **Importar**, abaixo da lista, e escolha um arquivo `.fmp`, ou simplesmente arraste e solte o arquivo sobre a janela de Perfis.

- Os perfis importados não são carregados automaticamente. Carregue-os como qualquer outro perfil.
- Se você já tiver o mesmo perfil (como uma versão mais antiga dele), poderá escolher **Substituir** ou **Manter ambos**. Ao substituir o perfil carregado, a versão importada é carregada imediatamente.
- Perfis criados com uma versão mais recente do FancyMenu exibem um aviso, pois algumas partes deles podem não funcionar.

## Adicionando pastas de configuração

Algumas configurações vêm como uma pasta `fancymenu` comum em vez de um arquivo `.fmp`. Para adicionar essa pasta como um perfil, renomeie-a com o nome de perfil desejado, mova-a para `<game-directory>/config/fancymenu/profiles/` (crie a pasta `profiles` caso ela ainda não exista) e abra a janela de Perfis. O FancyMenu a adicionará automaticamente aos seus perfis.

# Excluindo perfis

Selecione um perfil e clique em **Excluir**. A exclusão não pode ser desfeita, portanto exporte o perfil antes se quiser manter um backup.

O perfil carregado não pode ser excluído. Carregue outro perfil primeiro.

# Onde os perfis são armazenados

- O perfil carregado corresponde ao conteúdo de `<game-directory>/config/fancymenu/`, como qualquer configuração do FancyMenu.
- Todos os outros perfis são armazenados em `<game-directory>/config/fancymenu/profiles/`. Clique em **Abrir pasta** para abrir a pasta de um perfil.

`<game-directory>` é a pasta da instância ativa, que pode ser diferente de `.minecraft`. O estado de execução que o FancyMenu mantém fora de `config/fancymenu/` não faz parte dos perfis; consulte [Locais de armazenamento de dados](./data-storage-locations#persistent-runtime-state).
