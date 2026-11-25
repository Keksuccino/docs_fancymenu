---
title: Localizando layouts
description: Localize textos e outros conteúdos de layout.
sourceBlobSha: f4883414b07e0c024de7bef4f131b878ca4f5f37
---

# Localizando layouts

Use o [espaço reservado **Localizar texto**](/placeholders#localize-text) para textos traduzíveis:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

O FancyMenu verifica primeiro os dados de idioma ativos do Minecraft. Se a chave não estiver presente, ele verifica os arquivos de localização personalizados do FancyMenu. Se a chave não estiver em nenhuma das fontes, ela será exibida como está.

# Arquivos de localização personalizados do FancyMenu

Coloque os arquivos em:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Crie um subdiretório para seus arquivos de localização:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Coloque os arquivos de localização em pelo menos um subdiretório de `custom_locals`; arquivos colocados diretamente na raiz de `custom_locals` não são carregados. Subdiretórios aninhados são aceitos.

Formatos UTF-8 compatíveis:

| Extensão | Formato |
|---|---|
| `.json` | Objeto JSON; objetos aninhados se tornam chaves separadas por pontos |
| `.lang` | Linhas no formato `chave=valor` |
| `.properties` | Sintaxe de propriedades do Java |

Exemplo de JSON:

```json
{
  "modpack": {
    "menu": {
      "play": "Jogar"
    }
  }
}
```

Isso define `modpack.menu.play`.

O FancyMenu combina os arquivos compatíveis desses subdiretórios em um único dicionário de localização personalizado. Use cada chave em apenas um arquivo. Os arquivos de localização personalizados não alternam de acordo com o idioma selecionado no Minecraft; use o método de pacote de recursos abaixo quando precisar de alternância automática de idioma.

Reinicie o cliente depois de editar os arquivos de localização personalizados.

# Texto específico por idioma

Para alternar automaticamente de acordo com o idioma selecionado no Minecraft, forneça arquivos de idioma padrão do Minecraft por meio de um [pacote de recursos](/resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Use as mesmas chaves em cada arquivo de idioma, ative o pacote de recursos e, em seguida, acesse-as com o [espaço reservado **Localizar texto**](/placeholders#localize-text).

# Localizando imagens e elementos

Use o [requisito **O idioma do jogo é**](/conditions#is-game-language) para exibir elementos ou layouts diferentes de acordo com o código do idioma, como `en_us` e `de_de`.
