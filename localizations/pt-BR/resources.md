---
title: Recursos
description: >-
  Como os recursos funcionam no FancyMenu. Abrange localizações de recursos,
  recursos locais e recursos da web.
---

# Recursos

Campos de recursos podem carregar conteúdo de:

- **Minecraft:** uma localização de recurso fornecida pelo Minecraft ou por um pacote de recursos.
- **Local:** um arquivo na instância ativa do jogo.
- **Web:** uma URL direta de arquivo.

A maioria dos campos de imagem, áudio, vídeo e texto usa o mesmo seletor de recursos. O seletor inclui um navegador para conteúdo do Minecraft e de pacotes de recursos.

# Recursos do Minecraft (Pacotes de Recursos)

As localizações de recurso usam `namespace:path`. O namespace é o diretório imediatamente abaixo de `assets`, e o path é tudo abaixo desse namespace.

Por exemplo, considere uma imagem de pacote de recursos armazenada em `/assets/custom_resources/images/image.png`.
Sua localização de recurso é `custom_resources:images/image.png`.

> [!NOTE]
> Os recursos internos do Minecraft normalmente usam o namespace `minecraft`.

# Recursos Locais

Armazene recursos locais em `<game-directory>/config/fancymenu/assets/`. `<game-directory>` é a pasta da instância ativa, que pode ser diferente de `.minecraft`.

Campos de recurso podem mostrar o mesmo caminho como `/config/fancymenu/assets/example.png`. Nesses campos, a `/` inicial ainda significa `<game-directory>`; ela não é um caminho a partir da raiz do sistema de arquivos.

Esses arquivos podem ser [incluídos em um modpack](./modpacks) por meio da pasta de configuração dele.

Para um mapa completo dos caminhos de layout, recursos, configuração e estado gerado do FancyMenu, consulte [Locais de Armazenamento de Dados](./data-storage-locations).

# Recursos da Web

Use uma URL direta para o arquivo, por exemplo `https://example-domain.net/image.png`. Páginas e links de redirecionamento são mais lentos e têm mais chances de falhar do que URLs diretas que terminam no nome e na extensão do recurso.

# Placeholders nas Fontes de Recursos

Campos de recurso com seletor podem usar [placeholders](./placeholders) em caminhos locais, URLs e localizações de recurso do Minecraft. Selecione **Abrir no Editor** ao lado do campo de origem para editá-lo diretamente.

> [!WARNING]
> Entradas de recurso que não usam o seletor normal podem não oferecer suporte a placeholders ou a atualizações em tempo real da fonte.
