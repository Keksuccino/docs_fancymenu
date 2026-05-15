---
title: Placeholder de Dados NBT
description: Como usar o placeholder de Dados NBT.
---


# Obtendo Dados NBT

Esses placeholders estão disponíveis no FancyMenu v3.8.0+.

Os placeholders **Client NBT Data Get** e **Server NBT Data Get** permitem que você recupere dados NBT (Named Binary Tag) de entidades e blocos no Minecraft, de forma semelhante ao comando `/data get`. Isso é extremamente útil para criar layouts dinâmicos que respondem ao estado do jogo, às estatísticas do jogador ou às condições do mundo.

> Este placeholder é particularmente poderoso para jogabilidade com mods, pois pode acessar dados NBT personalizados que os mods adicionam a entidades e jogadores. Seja em mods de magia que adicionam sistemas de mana, mods de RPG com atributos personalizados ou mods de tecnologia com valores de energia, você pode exibir esses valores modificados nos seus layouts de interface.
{.is-info}

## Visão Geral

Esses placeholders extraem valores específicos de estruturas de dados NBT usando caminhos NBT. Você pode recuperar a saúde do jogador, fome, itens do inventário, estados de blocos, atributos modificados como mana ou energia e muito mais.

A versão do lado do cliente do placeholder tem a grande vantagem de funcionar puramente no cliente, então você não precisa do FancyMenu no servidor, mas isso também a torna muito mais limitada, porque nem tudo relacionado a dados NBT fica visível para todos os clientes o tempo todo.

A versão do lado do servidor exige que o FancyMenu esteja instalado no servidor, mas isso lhe dá **suporte completo** para praticamente **tudo** o que é armazenado como NBT.

Esta página vai focar na versão do lado do cliente (`nbt_data_get`), mas tudo funciona de forma muito semelhante para a versão do lado do servidor (`nbt_data_get_server`) também.

## Sintaxe do Placeholder

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

## Valores Obrigatórios

| Valor | Descrição | Opções |
|-------|-------------|---------|
| `source_type` | O tipo de fonte de dados | `entity` ou `block` |
| `nbt_path` | O caminho NBT a ser consultado | por exemplo `Health`, `foodLevel`, `Pos[0]`, `Inventory[0].id` |

## Valores Condicionais

Dependendo do seu `source_type`, você precisará de um destes:

| Valor | Obrigatório Quando | Descrição | Formato |
|-------|-------------------|-------------|--------|
| `entity_selector` | `source_type` é `entity` | Seleciona qual entidade consultar | `@s` (self), `@p` (jogador mais próximo), `@e` (entidade mais próxima), UUID ou nome da entidade |
| `block_pos` | `source_type` é `block` | As coordenadas do bloco | `x y z` (ex.: `100 64 -200`) |

## Valores Opcionais

| Valor | Descrição | Padrão | Opções |
|-------|-------------|--------|---------|
| `scale` | Fator de escala para valores numéricos | `1.0` | Qualquer número decimal |
| `return_type` | Como formatar os dados retornados | `value` | `value` (numérico/tamanho), `string` (texto), `snbt` (NBT formatado), `json` (formato JSON) |

## Explicação dos Tipos de Retorno

- **`value`** - Retorna valores numéricos ou tamanhos (padrão)
  - Para números: retorna o número (opcionalmente escalado)
  - Para strings: retorna o comprimento da string
  - Para listas/arrays: retorna a contagem de itens
  - Para compounds: retorna o número de tags

- **`string`** - Retorna o valor de string real dos dados NBT

- **`snbt`** - Retorna os dados no formato SNBT (Stringified NBT)

- **`json`** - Retorna os dados no formato JSON (somente para tags compound)

## Exemplos

### Obter a Saúde do Jogador
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}
```

### Obter o Nível de Fome do Jogador
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel"}}
```

### Obter a Coordenada X do Jogador
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Pos[0]"}}
```

### Obter o Item no Primeiro Slot da Barra de Acesso
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Inventory[{Slot:0b}].id","return_type":"string"}}
```

### Obter Dados de um Bloco em uma Posição Específica
```json
{"placeholder":"nbt_data_get","values":{"source_type":"block","block_pos":"100 64 -200","nbt_path":"Items[0].Count"}}
```

### Obter a Porcentagem de Vida Escalada (Health * 5)
```json
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health","scale":"5"}}
```

## Encontrando Caminhos NBT Disponíveis

### Método 1: Usando o comando `/data get` (Recomendado)

A maneira mais fácil de descobrir caminhos NBT disponíveis é usar o comando `/data get` no jogo sem especificar um caminho:

1. **Para entidades:** `/data get entity @p`
2. **Para blocos:** `/data get block <x> <y> <z>`

Isso exibirá todos os dados NBT disponíveis para esse alvo, mostrando os caminhos exatos que você pode usar.

#### Entendendo a Saída

Quando você executa `/data get entity @p`, verá uma saída semelhante a esta:

```
Player616 has the following entity data: {Brain: {memories: {}}, 
HurtByTimestamp: 0, SleepTimer: 0s, Invulnerable: 0b, FallFlying: 
0b, PortalCooldown: 0, AbsorptionAmount: 0.0f, abilities: 
{invulnerable: 1b, mayfly: 1b, instabuild: 1b, walkSpeed: 0.1f, 
mayBuild: 1b, flying: 1b, flySpeed: 0.05f}, FallDistance: 0.0f, 
recipeBook: {recipes: ["minecraft:crafting_table"]}, 
DeathTime: 0s, XpSeed: -380875747, XpTotal: 0, UUID: [I; 1379890089, -1732753738, 
-2135065633, -718799804], playerGameType: 1, seenCredits: 
0b, Motion: [0.0d, 0.0d, 0.0d], Health: 20.0f, foodSaturationLevel: 
5.0f, ...}
```

Para extrair um caminho válido dessa saída:

1. **Valores simples** - Use o nome da chave diretamente:
   - `Health: 20.0f` → Caminho: `Health`
   - Exemplo: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Health"}}`

2. **Valores aninhados** - Use notação com ponto para acessar dados aninhados:
   - `abilities: {walkSpeed: 0.1f}` → Caminho: `abilities.walkSpeed`
   - Exemplo: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"abilities.walkSpeed"}}`

3. **Valores em array** - Use colchetes com números de índice:
   - `Motion: [0.0d, 0.0d, 0.0d]` → Caminho para o movimento Y: `Motion[1]`
   - Exemplo: `{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"Motion[1]"}}`

### Método 2: Mod de Autocompletar NBT

Para facilitar a descoberta de caminhos NBT, considere instalar o mod **NBT Autocomplete**:
- Disponível para Fabric e Forge (Minecraft 1.21.x)
- Fornece sugestões de autocompletar no jogo enquanto você digita comandos
- Mostra os nomes e tipos das tags disponíveis
- [Modrinth](https://modrinth.com/mod/nbt-autocomplete) | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/nbt-autocomplete)

## Caminhos NBT Comuns

### Entidade do Jogador
- `Health` - Saúde atual (float)
- `foodLevel` - Nível de fome (int, 0-20)
- `foodSaturationLevel` - Nível de saturação (float)
- `XpLevel` - Nível de experiência (int)
- `XpP` - Progresso de experiência (float, 0.0-1.0)
- `Pos[0]`, `Pos[1]`, `Pos[2]` - Coordenadas X, Y, Z
- `Inventory` - Array do inventário do jogador
- `SelectedItemSlot` - Slot da barra de acesso atualmente selecionado (int, 0-8)

### NBT Comum de Blocos
- `Items` - Conteúdo do contêiner (baús, fornalhas, etc.)
- `CustomName` - Nome personalizado do bloco
- `Lock` - String de bloqueio para contêineres

### Exemplos Comuns de NBT Modificado
- **Mods de magia**: muitas vezes armazenam mana como `playerMana`, `mana.current` ou similar
- **Mods de tecnologia**: valores de energia como `energy`, `forgeEnergy` ou `energyStorage.energy`
- **Mods de RPG**: atributos personalizados como `customStats.strength`, `rpgAttributes.level`

Para encontrar caminhos NBT modificados, use `/data get entity @p` enquanto o mod estiver ativo e procure pelas tags personalizadas adicionadas pelo mod.

## Limitações

- **Sem acesso a storage no cliente** - A fonte de dados storage não é suportada no lado do cliente (somente no servidor)
- **Desempenho** - Acessar dados NBT com frequência pode afetar o desempenho
- Retorna uma string vazia se o caminho for inválido ou se os dados não puderem ser acessados

## Dicas

1. Sempre teste seus caminhos NBT no jogo primeiro usando `/data get`
2. Use o parâmetro `scale` para converter valores em porcentagens ou outros formatos úteis
3. Lembre-se de que alguns dados NBT podem não estar sincronizados com o cliente
4. Os seletores de entidade são limitados a entidades dentro da distância de renderização
5. Para conteúdo modificado, consulte a documentação do mod ou use `/data get` para descobrir caminhos NBT personalizados
