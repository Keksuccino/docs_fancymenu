---
title: Recursos
description: >-
  Como os recursos funcionam no FancyMenu. Aborda locais de recursos, recursos
  locais e recursos da web.
---

# Recursos

O sistema de recursos do FancyMenu permite usar recursos do próprio carregador de recursos do Minecraft (**Pacotes de Recursos**), recursos **Locais** (arquivos do sistema do cliente) e recursos da **Web** (arquivos armazenados online).

Quase todas as entradas de recursos, sejam imagens, áudio, vídeo ou texto, são configuradas por meio do seletor de recursos do FancyMenu. Existem algumas exceções, como ao definir um caminho de origem para um placeholder ou ação, mas, na maioria dos casos, os recursos são definidos pela mesma interface do seletor de recursos.

Quando você define uma entrada de recurso pela interface do seletor de recursos, você basicamente escolhe uma chamada "fonte de recurso" (é assim que o FancyMenu as chama), que pode ser um caminho, um link ou um local de recurso, dependendo do tipo de fonte.

O FancyMenu 3.9.0 adiciona um navegador de recursos do Minecraft ao seletor de recursos. Isso permite navegar pelos recursos carregados por pacotes de recursos como se fossem um diretório, em vez de digitar manualmente cada local de recurso.

# Recursos do Minecraft (Pacotes de Recursos)

O Minecraft usa os chamados "locais de recurso" para "apontar" para um recurso.

Os locais de recurso escritos em texto consistem em duas partes, separadas por dois-pontos (`:`).
A primeira parte é o **namespace** e o segundo caminho é o restante do **caminho até o recurso**, incluindo o nome do recurso com a extensão do arquivo.

O **namespace** de um local de recurso é sempre apenas o **diretório/pasta de nível superior** do caminho completo até o recurso.

Então, digamos que você carregue um pacote de recursos com um recurso chamado `image.png` armazenado em `/assets/custom_resources/images/image.png`.
Nesse caso, o **namespace** do local de recurso seria `custom_resources`, porque `/assets/` é apenas de onde o Minecraft carrega todos os recursos, então `custom_resources` é o **diretório de nível superior** do recurso.
Isso significa que `images/image.png` é o **restante do caminho** até o recurso.

Então, o local de recurso correto para o recurso `image.png` seria:
`custom_resources:images/image.png`

> **Curiosidade**: Como o Minecraft armazena a maioria de seus recursos em `/assets/minecraft/`, o **namespace** da maioria dos recursos do Minecraft é `minecraft`.
{.is-info}

# Recursos Locais

A maneira mais fácil de carregar recursos é simplesmente usar arquivos locais armazenados no cliente (e, na maioria dos casos, incluídos com os modpacks).

O FancyMenu só permite carregar recursos locais armazenados em `/config/fancymenu/assets/`, então certifique-se de guardar todos os seus recursos lá!

Isso também torna muito fácil [incluir recursos locais com seus modpacks](./modpacks), já que a maioria dos sistemas de modpack (CurseForge, Modrinth etc.) oferece suporte padrão para incluir pastas de configuração de mods.

# Recursos da Web

Quando você precisa alterar recursos dinamicamente sem precisar atualizar o modpack, recursos da **web** seriam a melhor opção.

Um recurso da web é basicamente apenas a **URL** de um arquivo armazenado em um servidor, então imagine `https://example-domain.net/image.png`.

Certifique-se de sempre usar **URLs DIRETAS**, ou seja, URLs que terminem com o **nome e a extensão do arquivo** do recurso, assim como no exemplo acima.
Usar URLs não diretas prejudica o desempenho e tem mais chances de falhar.

# Placeholders em Fontes de Recursos

É possível usar os placeholders do FancyMenu em fontes de recursos, como o caminho para uma fonte local, a URL de uma fonte web ou o local de recurso de um recurso do Minecraft.

Isso torna possível atualizar fontes dinamicamente, como alterar a origem da imagem de um fundo de menu ao definir uma variável do FancyMenu, para mostrar um plano de fundo diferente com base no valor da variável.

Você pode editar manualmente a fonte clicando no botão **Abrir no Editor** no lado direito do campo de entrada da fonte de recurso.

> Lembre-se de que isso vale apenas para entradas de recursos que usam a interface normal do seletor de recursos. É possível que *algumas* entradas de recursos que não usam o seletor **NÃO** ofereçam suporte a placeholders ou não sejam atualizadas dinamicamente quando o placeholder mudar.
{.is-warning}
