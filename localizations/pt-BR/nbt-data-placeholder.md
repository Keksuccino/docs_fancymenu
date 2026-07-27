---
title: Placeholder de Dados NBT
description: 'Lê dados NBT de entidades, blocos e storage.'
---

# Placeholders de Dados NBT

O FancyMenu fornece dois placeholders de NBT:

| Placeholder | Executa em | Dados disponíveis |
|---|---|---|
| `nbt_data_get` | Cliente | Entidades e block entities visíveis no cliente |
| `nbt_data_get_server` | Servidor | Alvos do `/data get` vanilla; requer FancyMenu no servidor |

# Placeholder do Lado do Cliente

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Valores

| Valor | Obrigatório | Descrição |
|---|---|---|
| `source_type` | Sim | `entity` ou `block` |
| `entity_selector` | Para entidades | Seletor do lado do cliente, UUID ou nome exato da entidade |
| `block_pos` | Para blocos | Três coordenadas inteiras absolutas, como `100 64 -200` |
| `nbt_path` | Sim | Caminho NBT, como `Health`, `Pos[0]` ou `Inventory[0].id` |
| `scale` | Não | Multiplica resultados numéricos de `value`; padrão `1.0` |
| `return_type` | Não | `value`, `string`, `snbt` ou `json`; padrão `value` |

As posições de bloco no lado do cliente não suportam coordenadas `~` ou `^`.

## Seletores de Entidade do Cliente

| Seletor | Alvos iniciais | Ordem padrão |
|---|---|---|
| `@s` | Jogador local | O próprio |
| `@p` | Jogadores | Mais próximo |
| `@a` | Jogadores | Ordem de iteração do cliente |
| `@r` | Jogadores | Aleatório |
| `@e` | Todas as entidades visíveis no cliente | Ordem de iteração do cliente |

`@e` não seleciona a entidade mais próxima, a menos que você adicione `sort=nearest`. A busca direta por UUID e por nome exato da entidade também é suportada.

Opções de seletor suportadas:

| Opção | Descrição |
|---|---|
| `type` | ID da entidade; use `!` no prefixo para excluir |
| `name` | Nome de exibição exato; use `!` no prefixo para excluir |
| `tag` | Tag da entidade; use `!` no prefixo para excluir |
| `limit` | Limite positivo de resultados |
| `sort` | `nearest`, `furthest`, `random` ou `arbitrary` |
| `distance` | Faixa de distância vanilla, como `..10` ou `5..20` |
| `x`, `y`, `z` | Origem da busca; aceita valores absolutos e deslocamentos `~` |
| `dx`, `dy`, `dz` | Tamanho da caixa de busca a partir da origem |

Coordenadas locais `^` e outras opções vanilla de seletor não são suportadas pelo placeholder do cliente.

Exemplo:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@e[type=minecraft:zombie,sort=nearest,limit=1,distance=..20]","nbt_path":"Health"}}
```

## Tipos de Retorno

| Tipo | Resultado |
|---|---|
| `value` | Tags numéricas são formatadas numericamente e aplicam `scale`; tags de string retornam seu texto; outras tags retornam texto no estilo SNBT |
| `string` | Retorna o valor de string da tag, ou uma string vazia quando a tag não tem valor de string |
| `snbt` | Retorna a representação SNBT da tag |
| `json` | Apenas para tags compostas: retorna um componente de texto do Minecraft serializado contendo a saída NBT formatada |

O modo `json` no lado do cliente não é uma conversão direta de NBT para JSON.

## Exemplos

Fome do jogador:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

ID do primeiro item da hotbar:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

Quantidade de item da block entity:

```text
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].count"}}
```

# Placeholder do Lado do Servidor

`nbt_data_get_server` segue o comportamento de `/data get` do servidor e suporta:

- Seletores de entidade completos do lado do servidor.
- Alvos de bloco com coordenadas absolutas, relativas (`~`) ou locais (`^`).
- Storage de comando por meio de `source_type:"storage"`.

```text
{"placeholder":"nbt_data_get_server","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","return_type":"value"}}
```

O placeholder retorna um valor vazio até a resposta do servidor chegar. As respostas são armazenadas em cache por um curto período para evitar excesso de requisições.

# Encontrando Caminhos NBT

Use o comando correspondente sem um caminho NBT para inspecionar os dados disponíveis:

```text
/data get entity @s
/data get block 100 64 -200
```

Os resultados do lado do cliente são limitados aos dados sincronizados com o cliente. Alvos ou caminhos inválidos retornam uma string vazia e gravam detalhes em `logs/latest.log`.
