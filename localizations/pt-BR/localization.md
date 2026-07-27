---
title: Localizando Layouts
description: Localize textos e outros conteúdos do layout.
---

# Localizando Layouts

Use o [placeholder **Localize Text**](./placeholders#localize-text-local) para textos traduzíveis:

```text
{"placeholder":"local","values":{"key":"modpack.menu.play"}}
```

O FancyMenu primeiro verifica os dados de idioma ativos do Minecraft. Se a chave não estiver presente lá, ele verifica os arquivos de localização personalizados do FancyMenu. Se nenhuma das fontes contiver a chave, a própria chave será exibida.

# Arquivos de Localização Personalizados do FancyMenu

Coloque os arquivos abaixo:

```text
<game-directory>/config/fancymenu/custom_locals/
```

Crie um subdiretório para os seus arquivos de localização:

```text
custom_locals/
└── my_pack/
    └── text.json
```

Coloque os arquivos de localização dentro de pelo menos um subdiretório de `custom_locals`; arquivos colocados diretamente na raiz de `custom_locals` não são carregados. Subdiretórios aninhados são suportados.

Formatos UTF-8 suportados:

| Extensão | Formato |
|---|---|
| `.json` | Objeto JSON; objetos aninhados se tornam chaves separadas por ponto |
| `.lang` | Linhas `key=value` |
| `.properties` | Sintaxe de propriedades Java |

Exemplo em JSON:

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

O FancyMenu combina os arquivos suportados dessas subpastas em um único dicionário de localização personalizado. Use cada chave em apenas um arquivo. Os arquivos de localização personalizados não mudam com o idioma selecionado no Minecraft; use o método de pacote de recursos abaixo quando precisar de troca automática de idioma.

Reinicie o cliente após editar os arquivos de localização personalizados.

# Texto Específico por Idioma

Para alternância automática com o idioma selecionado no Minecraft, forneça arquivos de idioma normais do Minecraft por meio de um [pacote de recursos](./resources#minecraft-resources-resource-packs):

```text
assets/<namespace>/lang/en_us.json
assets/<namespace>/lang/de_de.json
```

Use as mesmas chaves em cada arquivo de idioma, ative o pacote de recursos e então leia-as com o [placeholder **Localize Text**](./placeholders#localize-text-local).

# Localizando Imagens e Elementos

Use a [requirement **Is Game Language**](./conditions#is-game-language-fancymenu_loading_requirement_is_language) para mostrar elementos ou layouts diferentes para códigos de idioma diferentes, como `en_us` e `de_de`.
