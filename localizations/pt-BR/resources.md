---
title: Recursos
description: >-
  Como os recursos funcionam no FancyMenu. Abrange localizações de recursos,
  recursos locais e recursos da Web.
sourceBlobSha: eb783aaa0098ba295b3ebaf941bb4723e4d08970
---

# Recursos

Os campos de recursos podem carregar conteúdo de:

- **Minecraft:** uma localização de recurso fornecida pelo Minecraft ou por um pacote de recursos.
- **Local:** um arquivo na instância ativa do jogo.
- **Web:** um URL direto para um arquivo.

A maioria dos campos de imagem, áudio, vídeo e texto usa o mesmo seletor de recursos. O seletor inclui um navegador para conteúdo do Minecraft e de pacotes de recursos.

# Recursos do Minecraft (pacotes de recursos)

As localizações de recursos usam o formato `namespace:path`. O namespace é o diretório imediatamente abaixo de `assets`, e o caminho corresponde a tudo que está abaixo desse namespace.

Por exemplo, considere uma imagem de pacote de recursos armazenada em `/assets/custom_resources/images/image.png`.
A localização do recurso é `custom_resources:images/image.png`.

> [!NOTE]
> Os recursos integrados do Minecraft normalmente usam o namespace `minecraft`.

# Recursos locais

Armazene os recursos locais em `<game-directory>/config/fancymenu/assets/`. `<game-directory>` é a pasta da instância ativa, que pode ser diferente de `.minecraft`.

Os campos de recursos podem exibir o mesmo caminho como `/config/fancymenu/assets/example.png`. Nesses campos, o `/` inicial ainda significa `<game-directory>`; não é um caminho a partir da raiz do sistema de arquivos.

Esses arquivos podem ser [incluídos em um modpack](/modpacks) por meio da pasta de configuração dele.

Para ver um mapa completo dos caminhos de layout, recursos, configuração e estado gerado do FancyMenu, consulte [Locais de armazenamento de dados](/data-storage-locations).

# Recursos da Web

Use um URL direto para o arquivo, por exemplo, `https://example-domain.net/image.png`. Páginas e links com redirecionamento são mais lentos e têm mais chances de falhar do que URLs diretos que terminam com o nome e a extensão do recurso.

# Placeholders nas fontes de recursos

Os campos de recursos que usam um seletor podem usar [placeholders](/placeholders) em caminhos locais, URLs e localizações de recursos do Minecraft. Selecione **Abrir no editor** ao lado do campo de origem para editá-lo diretamente.

> [!WARNING]
> Entradas de recursos que não usam o seletor normal podem não oferecer suporte a placeholders ou à atualização da origem em tempo real.
