---
title: Espaços reservados
description: >-
  Exiba valores em tempo real, como o nome do jogador, o horário ou a quantidade
  de jogadores em um servidor, nos seus textos. Confira todos os espaços
  reservados do FancyMenu.
sourceBlobSha: 951d7772d640bc6b19d6f4dcc2fef4adcd1f13aa
---

# Espaços reservados

Espaços reservados são códigos curtos que o FancyMenu substitui por valores em tempo real, como o nome do jogador, o horário ou a quantidade de jogadores em um servidor. Eles funcionam nos textos dos elementos, nos rótulos de botões, nas dicas de ferramentas, nos valores de ações e requisitos e na maioria dos outros textos que você pode digitar.

<img width="800" alt="Adicionando o espaço reservado Nome do jogador a um elemento de texto no editor de layout: espaços reservados no editor de texto, a categoria Jogador e o texto cumprimentando o jogador pelo nome" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_add.gif?raw=true">

> [!TIP]
> Suas próprias [variáveis](/variables) também funcionam nesses textos, usando `$$` seguido do nome, como `$$coins`.

# Adicionar espaços reservados

1. Abra o texto no editor de texto, como **Conteúdo do texto** de um [elemento de texto](/text-in-menus). Campos de texto em janelas, como os valores de ações, têm um botão **Abrir no editor** ao lado.
2. Clique no local em que o espaço reservado deve aparecer.
3. Clique em **Espaços reservados**, no canto superior direito do editor de texto.
4. Clique em uma categoria ou pesquise pelo nome, identificador ou descrição. **VOLTAR** retorna às categorias. Os espaços reservados sem categoria são listados abaixo delas.
5. Passe o mouse sobre um espaço reservado para ver o que ele faz e clique nele para adicioná-lo.
6. Substitua os valores de exemplo, como o ID do mod em **Versão do mod**.

Textos cujo editor não tem o botão **Espaços reservados** não oferecem suporte a espaços reservados.

# Como os espaços reservados funcionam

Um espaço reservado tem esta aparência:

```
{"placeholder":"playername"}
```

Espaços reservados com configurações têm esses valores em `values`:

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

- O identificador, como `playername`, diferencia maiúsculas de minúsculas. Cada espaço reservado abaixo mostra seu identificador e seus valores.
- A ordem dos valores não importa. Valores marcados como opcionais podem ser omitidos.
- Um espaço reservado que o FancyMenu não consegue substituir, como um com erro de digitação, permanece no texto exatamente como você o escreveu.
- Espaços reservados sempre retornam texto. Quando não há nada para exibir, retornam um valor alternativo, como `0`, `0.0`, `---` ou nada.
- Os [códigos de formatação](/text-formatting) funcionam junto com os espaços reservados: `&6{"placeholder":"playername"}` exibe o nome em dourado.

> [!IMPORTANT]
> Espaços reservados parecem JSON, mas não são JSON. Não os passe por um formatador ou validador JSON, pois espaços reservados dentro de outros espaços reservados não são JSON válido.

## Espaços reservados dentro de espaços reservados

Os valores podem conter outros espaços reservados e [variáveis](/variables#showing-variables-in-text). O FancyMenu substitui primeiro os espaços reservados internos. Não é necessário escapar aspas dentro dos valores.

Este exemplo converte o valor máximo de RAM de MB para GB:

```
{"placeholder":"calc","values":{"decimal":"true","expression":"{"placeholder":"maxram"} / 1024"}}
```

Este exemplo exibe a variável `rank` em letras maiúsculas:

```
{"placeholder":"uppercase_text","values":{"text":"$$rank"}}
```

Quando um espaço reservado retorna um texto que contém espaços reservados, como um arquivo lido com [**Texto do arquivo**](#texto-do-arquivo), o FancyMenu também os substitui.

# Informações úteis

- Os espaços reservados são atualizados automaticamente. O FancyMenu mantém um texto substituído por 30 milissegundos antes de substituir os espaços reservados novamente. Altere esse intervalo em **Duração do cache de espaços reservados [MS]**, em **barra de menu -> Personalização -> Configurações**. O valor `0` faz com que sejam substituídos a cada quadro, o que consome mais desempenho.
- Espaços reservados que leem sites, arquivos ou servidores, como **Texto da Web** ou **Status do servidor**, carregam em segundo plano. Até isso acontecer, eles não retornam nada ou exibem um valor alternativo.
- Em [ações](/action-scripts), os espaços reservados recebem seu valor atual no momento em que a ação é executada.
- Espaços reservados sobre o mundo, a tela e os elementos só funcionam na thread principal do jogo. Em um [Ticker](/elements#ticker) executado em segundo plano (de forma assíncrona), o FancyMenu exibe um erro.
- **Número aleatório** gera um número novo sempre que o texto é atualizado. Para manter um número, salve-o em uma [variável](/variables) com [**Definir valor da variável (FM Variable)**](/action-scripts#set-variable-value-fm-variable).

> [!CAUTION]
> Espaços reservados como **Analisador JSON**, **Texto do arquivo** e **Conteúdo da área de transferência** podem ler arquivos da pasta do jogo e o conteúdo da sua área de transferência. Junto com ações que acessam sites, um layout poderia enviar esses dados para terceiros. Use apenas layouts em que você confia.

# Exemplos

## Painel de boas-vindas

<img width="800" alt="Um elemento de texto cumprimenta o jogador pelo nome e exibe a versão do Minecraft, a quantidade de mods e o horário" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/placeholders_welcome.png?raw=true">

```
### Boas-vindas, {"placeholder":"playername"}!
Minecraft {"placeholder":"mcversion"} com {"placeholder":"loadedmods"} mods
Agora são {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Status do servidor e jogadores

```
Sobrevivência: {"placeholder":"serverstatus","values":{"ip":"play.example.net"}}&r, {"placeholder":"serverplayercount","values":{"ip":"play.example.net"}} jogadores
```

## Data e horário

```
{"placeholder":"realtimeday"}.{"placeholder":"realtimemonth"}.{"placeholder":"realtimeyear"}, {"placeholder":"realtimehour"}:{"placeholder":"realtimeminute"}
```

## Uso de RAM

```
RAM: {"placeholder":"usedram"} / {"placeholder":"maxram"} MB ({"placeholder":"percentram"}%)
```

# Todos os espaços reservados

Confira todos os espaços reservados disponíveis no FancyMenu. As categorias **Avançado** e **Mundo** do menu de espaços reservados são divididas em grupos menores aqui.

## Variáveis e listas

Estes espaços reservados estão na categoria **Avançado**. Consulte [Variáveis](/variables) para saber como criar variáveis e listas.

### Obter valor da variável (FM Variable)

**Identificador:** `getvariable`

O valor de uma das suas variáveis. Retorna `0` quando a variável está vazia ou não existe, o que é útil para números. Uma lista retorna todas as entradas como uma matriz JSON, por exemplo `["Steve","Alex"]`.

- `name`: o nome da variável, sem `$$`

```
{"placeholder":"getvariable","values":{"name":"clicks"}}
```

### Obter entrada da lista (FM Variable)

**Identificador:** `list_get`

Uma entrada de uma variável de lista.

- `name`: o nome da lista
- `index`: a posição da entrada. A primeira é `0`; números negativos contam a partir do final, então `-1` é a última entrada.
- `fallback` (opcional): o valor retornado quando não há entrada nesse índice ou uma lista com esse nome. Por padrão, fica vazio.

```
{"placeholder":"list_get","values":{"name":"tips","index":"0","fallback":"No tips yet"}}
```

### Tamanho da lista (FM Variable)

**Identificador:** `list_size`

A quantidade de entradas de uma lista. Retorna `0` quando não existe uma lista com esse nome.

- `name`: o nome da lista

```
{"placeholder":"list_size","values":{"name":"tips"}}
```

### Índice da entrada da lista (FM Variable)

**Identificador:** `list_index_of`

O índice da primeira entrada que corresponde ao `value` completo, ou `-1` quando a lista não contém esse valor.

- `name`: o nome da lista
- `value`: a entrada a ser procurada
- `ignore_case` (opcional): `true` faz com que `Apple` corresponda a `apple`. O padrão é `false`.

```
{"placeholder":"list_index_of","values":{"name":"read_news","value":"news_42","ignore_case":"false"}}
```

### Juntar entradas da lista (FM Variable)

**Identificador:** `list_join`

Todas as entradas de uma lista em um único texto. Retorna vazio quando não existe uma lista com esse nome.

- `name`: o nome da lista
- `separator` (opcional): o texto entre as entradas. `\n` representa uma quebra de linha. O padrão é `, `.

```
{"placeholder":"list_join","values":{"name":"tips","separator":"\n"}}
```

## Matemática

Estes espaços reservados estão na categoria **Avançado**. Números decimais usam ponto, como em `2.5`.

### Calculadora

**Identificador:** `calc`

Resolve uma expressão matemática, como `2 + 3 * 4`.

- `expression`: a expressão a resolver
- `decimal` (opcional): `false` arredonda o resultado para um número inteiro. O padrão é `true`, que pode retornar resultados como `14.0`.

```
{"placeholder":"calc","values":{"decimal":"false","expression":"{"placeholder":"usedram"} * 100 / {"placeholder":"maxram"}"}}
```

| Em expressões | O que faz |
|---|---|
| `+` `-` `*` `/` | Somar, subtrair, multiplicar e dividir |
| `^` | Potência, como `2 ^ 3` para obter 8 |
| `%` | Resto, como `7 % 3` para obter 1 |
| `( )` | Agrupa partes, como `(2 + 3) * 4` |
| `pi`, `e` | Os números π e e |
| `abs(x)` | Número sem o sinal de menos |
| `sqrt(x)`, `cbrt(x)` | Raiz quadrada e raiz cúbica |
| `pow(x, y)` | x elevado a y |
| `floor(x)`, `ceil(x)` | Arredonda para baixo e para cima |
| `sin(x)`, `cos(x)`, `tan(x)`, `cot(x)` | Funções trigonométricas, com ângulos em radianos |
| `asin(x)`, `acos(x)`, `atan(x)` | Funções trigonométricas inversas |
| `sinh(x)`, `cosh(x)`, `tanh(x)` | Funções hiperbólicas |
| `log(x)`, `log2(x)`, `log10(x)` | Logaritmos nas bases e, 2 e 10 |
| `exp(x)` | e elevado a x |
| `signum(x)` | `1`, `-1` ou `0`, como em [**Sinal (matemática)**](#sinal-matemática) |

### Número aleatório

**Identificador:** `random_number`

Um número inteiro aleatório entre `min` e `max`. Ele muda sempre que o texto é atualizado.

- `min`, `max`: os números mínimo e máximo

```
{"placeholder":"random_number","values":{"min":"1","max":"6"}}
```

### Número máximo

**Identificador:** `maxnum`

O maior entre dois números.

- `first`, `second`: os números

```
{"placeholder":"maxnum","values":{"first":"$$score","second":"$$best_score"}}
```

### Número mínimo

**Identificador:** `minnum`

O menor entre dois números.

- `first`, `second`: os números

```
{"placeholder":"minnum","values":{"first":"10","second":"15"}}
```

### Valor absoluto

**Identificador:** `absnum`

O número sem o sinal de menos: `-10.5` retorna `10.5`.

- `num`: o número

```
{"placeholder":"absnum","values":{"num":"-10.5"}}
```

### Negar número

**Identificador:** `negnum`

Transforma um número positivo em negativo: `10.5` retorna `-10.5`. Zero e números negativos permanecem como estão.

- `num`: o número

```
{"placeholder":"negnum","values":{"num":"10.5"}}
```

### Arredondar (matemática)

**Identificador:** `math_round`

Arredonda um número. `2.5` é arredondado para cima, resultando em `3`.

- `num`: o número
- `decimals` (opcional): quantas casas decimais manter. Por exemplo, `2` transforma `3.14159` em `3.14`. `0`, `-1` ou a ausência do valor arredondam para um número inteiro.

```
{"placeholder":"math_round","values":{"num":"3.14159","decimals":"2"}}
```

### Piso (matemática)

**Identificador:** `math_floor`

Arredonda um número para baixo até um número inteiro: `3.7` retorna `3` e `-3.2` retorna `-4`.

- `num`: o número

```
{"placeholder":"math_floor","values":{"num":"3.7"}}
```

### Teto (matemática)

**Identificador:** `math_ceil`

Arredonda um número para cima até um número inteiro: `3.2` retorna `4` e `-3.7` retorna `-3`.

- `num`: o número

```
{"placeholder":"math_ceil","values":{"num":"3.2"}}
```

### Sinal (matemática)

**Identificador:** `math_sign`

Retorna `1` para números positivos, `-1` para negativos e `0` para zero.

- `num`: o número

```
{"placeholder":"math_sign","values":{"num":"-3.14"}}
```

### *pi* (matemática)

**Identificador:** `math_pi`

O número π: `3.141592653589793`.

```
{"placeholder":"math_pi"}
```

### Seno trigonométrico (matemática)

**Identificador:** `math_sin`

O seno de um ângulo em radianos. Para usar graus, primeiro multiplique-os por π / 180 com a Calculadora.

- `angle`: o ângulo em radianos

```
{"placeholder":"math_sin","values":{"angle":"1.5707963267948966"}}
```

### Cosseno trigonométrico (matemática)

**Identificador:** `math_cos`

O cosseno de um ângulo em radianos.

- `angle`: o ângulo em radianos

```
{"placeholder":"math_cos","values":{"angle":"0"}}
```

### Tangente trigonométrica (matemática)

**Identificador:** `math_tan`

A tangente de um ângulo em radianos.

- `angle`: o ângulo em radianos

```
{"placeholder":"math_tan","values":{"angle":"0.7853981633974483"}}
```

### Seno hiperbólico (matemática)

**Identificador:** `math_sinh`

O seno hiperbólico de um número.

- `num`: o número

```
{"placeholder":"math_sinh","values":{"num":"1"}}
```

### Cosseno hiperbólico (matemática)

**Identificador:** `math_cosh`

O cosseno hiperbólico de um número.

- `num`: o número

```
{"placeholder":"math_cosh","values":{"num":"1"}}
```

### Tangente hiperbólica (matemática)

**Identificador:** `math_tanh`

A tangente hiperbólica de um número.

- `num`: o número

```
{"placeholder":"math_tanh","values":{"num":"1"}}
```

### Conversor de base numérica

**Identificador:** `number_base_convert`

Converte um número para outra base, por exemplo, de decimal para binário ou hexadecimal. Também aceita decimais, com até 16 dígitos após o ponto. As letras do resultado são maiúsculas, como em `FF`.

- `input`: o número
- `from_base` (opcional): a base de `input`, de `2` a `36`. O padrão é `10`.
- `to_base` (opcional): a base do resultado, de `2` a `36`. O padrão é `10`.

```
{"placeholder":"number_base_convert","values":{"input":"255","from_base":"10","to_base":"16"}}
```

## Texto

Estes espaços reservados estão na categoria **Avançado**.

### Texto em maiúsculas

**Identificador:** `uppercase_text`

Converte o texto para letras maiúsculas: `Hello World` retorna `HELLO WORLD`. Os [códigos de formatação](/text-formatting), como `&a`, permanecem inalterados.

- `text`: o texto

```
{"placeholder":"uppercase_text","values":{"text":"Hello World"}}
```

### Texto em minúsculas

**Identificador:** `lowercase_text`

Converte o texto para letras minúsculas: `HELLO WORLD` retorna `hello world`. Os códigos de formatação permanecem inalterados.

- `text`: o texto

```
{"placeholder":"lowercase_text","values":{"text":"HELLO WORLD"}}
```

### Texto em formato de título

**Identificador:** `title_case_text`

A primeira letra de cada palavra fica maiúscula: `hello world` retorna `Hello World`. Os códigos de formatação permanecem inalterados.

- `text`: o texto

```
{"placeholder":"title_case_text","values":{"text":"hello world"}}
```

### Texto em formato de frase

**Identificador:** `sentence_case_text`

A primeira letra de cada frase fica maiúscula: `hello world. this is fancymenu!` retorna `Hello world. This is fancymenu!`. Os códigos de formatação permanecem inalterados.

- `text`: o texto

```
{"placeholder":"sentence_case_text","values":{"text":"hello world. this is fancymenu!"}}
```

### Texto em snake_case

**Identificador:** `snake_case_text`

Converte para minúsculas e separa as palavras com `_`: `Hello World` retorna `hello_world`. Os códigos de formatação são removidos.

- `text`: o texto

```
{"placeholder":"snake_case_text","values":{"text":"Hello World"}}
```

### Texto em kebab-case

**Identificador:** `kebab_case_text`

Converte para minúsculas e separa as palavras com `-`: `Hello World` retorna `hello-world`. Os códigos de formatação são removidos.

- `text`: o texto

```
{"placeholder":"kebab_case_text","values":{"text":"Hello World"}}
```

### Texto com maiúsculas alternadas

**Identificador:** `alternating_case_text`

Alterna entre letras minúsculas e maiúsculas: `alternating case` retorna `aLtErNaTiNg CaSe`.

- `text`: o texto

```
{"placeholder":"alternating_case_text","values":{"text":"alternating case"}}
```

### Inverter maiúsculas e minúsculas

**Identificador:** `toggle_case_text`

Transforma letras minúsculas em maiúsculas e vice-versa: `Toggle Case` retorna `tOGGLE cASE`.

- `text`: o texto

```
{"placeholder":"toggle_case_text","values":{"text":"Toggle Case"}}
```

### Remover espaços das extremidades

**Identificador:** `trim_text`

Remove os espaços no começo e no final do texto. Os espaços internos permanecem.

- `text`: o texto

```
{"placeholder":"trim_text","values":{"text":"  Welcome!  "}}
```

### Cortar texto

**Identificador:** `crop_text`

Remove uma quantidade de caracteres do começo e do final do texto. Remover 1 caractere de cada lado de `hello world` retorna `ello worl`.

- `text`: o texto
- `remove_from_start`: quantos caracteres remover do começo
- `remove_from_end`: quantos caracteres remover do final

```
{"placeholder":"crop_text","values":{"text":"hello world","remove_from_start":"1","remove_from_end":"1"}}
```

### Dividir texto

**Identificador:** `split_text`

Divide um texto e retorna uma das partes. Dividir `Steve,Alex,Notch` em `,` retorna `Alex` como parte de índice `1`.

- `input`: o texto
- `regex`: onde dividir, usando uma expressão regular. Caracteres como `.`, `|` e `?` precisam de um `\` antes deles, como em `\.`.
- `max_parts` (opcional): o número máximo de partes. `-1` (padrão) divide em todas as correspondências.
- `split_index`: a parte retornada. A primeira parte tem índice `0`.

```
{"placeholder":"split_text","values":{"input":"Steve,Alex,Notch","regex":",","max_parts":"-1","split_index":"1"}}
```

### Substituir texto

**Identificador:** `replace_text`

Substitui partes de um texto: em `Hello World!`, substituir `World` por `FancyMenu` retorna `Hello FancyMenu!`.

- `text`: o texto
- `search`: o que procurar
- `replacement` (opcional): o que colocar no lugar. Por padrão, fica vazio, removendo o trecho encontrado.
- `use_regex` (opcional): `true` faz com que `search` seja uma expressão regular. Nesse caso, `$1`, `$2` e assim por diante em `replacement` correspondem aos grupos encontrados. O padrão é `false`.
- `replace_all` (opcional): `false` substitui apenas a primeira correspondência. O padrão é `true`.

```
{"placeholder":"replace_text","values":{"text":"Hello World!","search":"World","replacement":"FancyMenu","use_regex":"false","replace_all":"true"}}
```

### Alternar caso

**Identificador:** `switch_case`

Retorna o resultado do caso correspondente a um valor. Se a variável `difficulty_level` for `2`, o exemplo retorna `Hard Mode`.

- `value`: o valor a verificar
- `cases`: pares de valor e resultado, como `1:Easy Mode,2:Hard Mode`. Os valores e resultados não podem conter `,` ou `:`.
- `default` (opcional): o resultado quando nenhum caso corresponder. Sem um valor padrão, o espaço reservado permanece como está.

```
{"placeholder":"switch_case","values":{"value":"$$difficulty_level","cases":"1:Easy Mode,2:Hard Mode","default":"Normal Mode"}}
```

### Localizar texto

**Identificador:** `local`

O texto de uma chave de localização no idioma atual do jogo, como `Singleplayer` para `menu.singleplayer`. Funciona com chaves do Minecraft, de mods e suas próprias chaves (consulte [Localização](/localization)).

- `key`: a chave de localização

```
{"placeholder":"local","values":{"key":"menu.singleplayer"}}
```

### Converter em texto literal

**Identificador:** `stringify`

Substitui os espaços reservados no texto e, em seguida, coloca `\` antes de cada `"`, `{` e `}`. Assim, textos externos, como os de um site, não podem ser interpretados como espaços reservados.

- `text`: o texto

```
{"placeholder":"stringify","values":{"text":"{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}"}}
```

## Dados e arquivos

Estes espaços reservados estão na categoria **Avançado**. Caminhos locais começam na pasta do jogo, como `/config/fancymenu/assets/news.txt`, e não podem sair dela (consulte [Recursos](/resources#local-resources)).

### Analisador JSON

**Identificador:** `json`

Lê um valor de JSON. Se houver vários resultados, exibe um por linha.

- `source`: texto JSON, um arquivo JSON na pasta do jogo ou o URL de um arquivo JSON
- `json_path`: o caminho até o valor, como `$.name` ou `$.players[0].name`. Consulte [json.fancymenu.net](https://json.fancymenu.net) para saber mais sobre caminhos JSON.

```
{"placeholder":"json","values":{"source":"https://example.com/server_info.json","json_path":"$.news.title"}}
```

O JSON da Web é carregado uma vez e novamente quando o FancyMenu é recarregado. Alterações em arquivos aparecem imediatamente.

| Caminho | O que retorna |
|---|---|
| `$.name` | O `name` do nível superior |
| `$.player.level` | `level` dentro de `player` |
| `$.items[0].id` | O `id` da primeira entrada de `items` |
| `$.scores.*` | Todos os valores de `scores` |

### Texto do arquivo

**Identificador:** `file_text`

O texto de um arquivo ou URL. Os arquivos são lidos novamente a cada segundo; os URLs, a cada 10 segundos. Retorna vazio enquanto o texto está carregando ou quando não pode ser lido.

- `path_or_url`: um arquivo na pasta do jogo ou um URL. Caminhos iniciados por `.minecraft/` apontam para a pasta padrão do Minecraft.
- `mode` (opcional): `all` para o texto inteiro ou `last` para as últimas linhas. O padrão é `all`.
- `separator` (opcional): o texto entre as linhas. O padrão é `\n` (quebra de linha).
- `last_lines` (opcional): quantas linhas `last` retorna. O padrão é `1`.

```
{"placeholder":"file_text","values":{"path_or_url":"/config/fancymenu/assets/changelog.txt","mode":"all","separator":"\n","last_lines":"1"}}
```

### Tamanho do arquivo

**Identificador:** `file_size`

O tamanho de um arquivo em bytes. Retorna `0` se o arquivo não existir. Caminhos iniciados por `.minecraft/` apontam para a pasta padrão do Minecraft.

- `path`: o arquivo

```
{"placeholder":"file_size","values":{"path":"/config/fancymenu/assets/news.txt"}}
```

### MD5 do arquivo

**Identificador:** `file_md5`

O hash MD5 de um arquivo, como `d41d8cd98f00b204e9800998ecf8427e`. Retorna vazio se o arquivo não existir. Caminhos iniciados por `.minecraft/` apontam para a pasta padrão do Minecraft.

- `path`: o arquivo

```
{"placeholder":"file_md5","values":{"path":"/config/fancymenu/assets/menu_music.ogg"}}
```

### Codificar em Base64

**Identificador:** `base64_encode`

O texto codificado em Base64: `Hello World` retorna `SGVsbG8gV29ybGQ=`.

- `text`: o texto

```
{"placeholder":"base64_encode","values":{"text":"Hello World"}}
```

### Decodificar de Base64

**Identificador:** `base64_decode`

Converte Base64 novamente em texto: `SGVsbG8gV29ybGQ=` retorna `Hello World`.

- `text`: o texto em Base64

```
{"placeholder":"base64_decode","values":{"text":"SGVsbG8gV29ybGQ="}}
```

### Obter dados NBT (lado do cliente)

**Identificador:** `nbt_data_get`

Lê dados NBT, como `/data get`, a partir das informações que o jogo tem sobre o mundo. Isso é rápido, mas os servidores não enviam todas as informações aos jogadores.

- `source_type`: `entity` ou `block`
- `entity_selector`: para `entity`, um seletor como `@s` (você), `@p`, `@e[type=minecraft:horse,limit=1,sort=nearest]`, ou o nome ou UUID de uma entidade. Os seletores podem usar `type`, `name`, `tag`, `limit`, `sort`, `distance`, `x`, `y`, `z`, `dx`, `dy` e `dz`. A primeira correspondência é usada.
- `block_pos`: para `block`, a posição de uma entidade de bloco, como um baú: `120 64 -35`
- `nbt_path`: o caminho NBT, como `foodLevel` ou `Inventory[0].id`
- `scale` (opcional): multiplica os números. O padrão é `1.0`.
- `return_type` (opcional): `value` (números e textos como estão), `string`, `snbt` ou `json`. O padrão é `value`.

```
{"placeholder":"nbt_data_get","values":{"source_type":"entity","entity_selector":"@s","nbt_path":"foodLevel","scale":"1.0","return_type":"value"}}
```

### Obter dados NBT (lado do servidor)

**Identificador:** `nbt_data_get_server`

Lê dados NBT do servidor, exatamente como `/data get`. Requer o FancyMenu no servidor. No modo para um jogador, sempre funciona. Não retorna nada até o servidor responder; depois, atualiza aproximadamente a cada 100 milissegundos.

- `source_type`: `entity`, `block` ou `storage`
- `entity_selector`: para `entity`, qualquer seletor de `/data get` que encontre uma entidade, como `@s` ou `@e[type=minecraft:villager,limit=1,sort=nearest]`
- `block_pos`: para `block`, uma posição como `120 64 -35`, `~ ~-1 ~` ou `^ ^ ^1`
- `storage_id`: para `storage`, o ID de um armazenamento de comandos, como `mypack:quests`
- `nbt_path` (opcional): o caminho NBT. Sem ele, retorna todos os dados.
- `scale` (opcional): multiplica os números. O padrão é `1.0`.
- `return_type` (opcional): `value`, `string`, `snbt` ou `json`. O padrão é `value`.

```
{"placeholder":"nbt_data_get_server","values":{"source_type":"storage","storage_id":"mypack:quests","nbt_path":"completed","return_type":"value"}}
```

## Áudio

Estes espaços reservados leem [elementos de áudio](/elements#audio) do menu aberto. No editor de layout, clique com o botão direito em um elemento de áudio e clique em **Copiar ID do elemento** para obter seu ID.

### Volume do elemento de áudio

**Identificador:** `audio_element_vol`

O volume do elemento de áudio, de `0.0` (0%) a `1.0` (100%).

- `element_identifier`: o ID do elemento de áudio

```
{"placeholder":"audio_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Faixa de áudio atual

**Identificador:** `audio_element_current_track`

O nome do arquivo da faixa que está sendo reproduzida, como `menu_theme.ogg`. Retorna `---` quando nenhuma faixa está tocando.

- `element_identifier`: o ID do elemento de áudio
- `display_name_mappings` (opcional): nomes a serem exibidos no lugar dos nomes dos arquivos. `=>` separa o nome do arquivo do nome de exibição; `%:%` separa os pares.

```
{"placeholder":"audio_element_current_track","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","display_name_mappings":"menu_theme.ogg=>Menu Theme%:%credits.ogg=>Credits Theme"}}
```

### Duração do áudio

**Identificador:** `audio_duration`

A duração da faixa atual, como `03:45`. Retorna `00:00` enquanto ela carrega.

- `element_identifier`: o ID do elemento de áudio

```
{"placeholder":"audio_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Tempo de reprodução do áudio

**Identificador:** `audio_playtime`

O ponto atual da faixa, como `01:30`. Retorna `00:00` (ou `0`) quando a reprodução está parada.

- `element_identifier`: o ID do elemento de áudio
- `show_percentage` (opcional): `true` retorna o progresso de `0` a `100`. O padrão é `false`.

```
{"placeholder":"audio_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false"}}
```

### Estado de reprodução do áudio

**Identificador:** `audio_playing_state`

Retorna `true` enquanto o elemento de áudio estiver tocando e `false` enquanto estiver pausado ou parado.

- `element_identifier`: o ID do elemento de áudio

```
{"placeholder":"audio_playing_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

## Cliente

Estes espaços reservados são sobre o jogo e seus mods.

### Versão do Minecraft

**Identificador:** `mcversion`

A versão do Minecraft, como `1.21.1`.

```
{"placeholder":"mcversion"}
```

### Nome do carregador de mods

**Identificador:** `loadername`

O nome do carregador de mods, como `Fabric` ou `NeoForge`.

```
{"placeholder":"loadername"}
```

### Versão do carregador de mods

**Identificador:** `loaderver`

A versão do carregador de mods, como `0.16.14`.

```
{"placeholder":"loaderver"}
```

### Versão do mod

**Identificador:** `modversion`

A versão de um mod instalado, como `3.11.0`. Retorna `0.0.0` quando o mod não está instalado.

- `modid`: o ID do mod, como `fancymenu`

```
{"placeholder":"modversion","values":{"modid":"fancymenu"}}
```

### Quantidade de mods ativos

**Identificador:** `loadedmods`

A quantidade de mods carregados. Bibliotecas e mods incluídos em outros mods também são contabilizados; por isso, o total costuma ser maior que o número de arquivos de mod.

```
{"placeholder":"loadedmods"}
```

### Quantidade total de mods

**Identificador:** `totalmods`

Uma estimativa da quantidade de mods instalados, contados a partir dos arquivos `.jar` na pasta `mods` uma vez a cada inicialização do jogo. O valor nunca é menor que o de **Quantidade de mods ativos**.

```
{"placeholder":"totalmods"}
```

### Progresso do carregamento do mundo

**Identificador:** `world_load_progress`

O progresso do carregamento de um mundo, de `0` a `100`, enquanto a tela de carregamento está aberta. Útil para barras de carregamento. Retorna `0` nas demais telas.

```
{"placeholder":"world_load_progress"}
```

### Valor de opção do Minecraft

**Identificador:** `minecraft_option_value`

O valor de uma opção do Minecraft, conforme salvo no arquivo `options.txt` da pasta do jogo, como `12` para `renderDistance`. Retorna vazio quando não existe uma opção com esse nome.

- `name`: o nome da opção em `options.txt`

```
{"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}}
```

### Tecla de atalho

**Identificador:** `keybind_key`

A tecla usada atualmente por um atalho, como na tela de Controles: `Space` para pular. Retorna vazio quando não existe um atalho com esse nome.

- `keybind`: o nome do atalho, como `key.jump` ou `key.inventory`. Os nomes estão em `options.txt`, sem o prefixo `key_`: `key_key.jump` corresponde a `key.jump`.

```
Pressione {"placeholder":"keybind_key","values":{"keybind":"key.inventory"}} para abrir seu inventário!
```

### Último mundo ou servidor

**Identificador:** `last_world_server`

O último mundo ou servidor em que o jogador entrou. Servidores são exibidos como `play.example.net:25565`.

- `type`: `both` para mundos e servidores, `world` somente para mundos ou `server` somente para servidores. Com `world` ou `server`, retorna vazio se o último destino era do outro tipo.
- `full_world_path` (opcional): `false` retorna apenas o nome do mundo, como `New World`. `true` retorna o caminho da pasta. O padrão é `true`.

```
{"placeholder":"last_world_server","values":{"type":"world","full_world_path":"false"}}
```

## Interface gráfica

Estes espaços reservados são sobre a tela aberta e seus elementos. Os espaços reservados de elementos usam o ID de um elemento: no editor de layout, clique nele com o botão direito e selecione **Copiar ID do elemento**.

### Largura da tela

**Identificador:** `guiwidth`

A largura da tela em pixels da interface gráfica. Esse é o tamanho usado pelos elementos, não a quantidade de pixels do monitor.

```
{"placeholder":"guiwidth"}
```

### Altura da tela

**Identificador:** `guiheight`

A altura da tela em pixels da interface gráfica.

```
{"placeholder":"guiheight"}
```

### Escala da interface gráfica

**Identificador:** `guiscale`

A escala da interface gráfica do jogo, como `2`.

```
{"placeholder":"guiscale"}
```

### Identificador da tela atual

**Identificador:** `screenid`

O [identificador](/screen-identifiers) da tela aberta, como `title_screen`. Retorna vazio quando nenhuma tela está aberta.

```
{"placeholder":"screenid"}
```

### Largura do elemento

**Identificador:** `elementwidth`

A largura de um elemento em pixels da interface gráfica. Retorna `1` quando não existe um elemento com esse ID.

- `id`: o ID do elemento

```
{"placeholder":"elementwidth","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Altura do elemento

**Identificador:** `elementheight`

A altura de um elemento em pixels da interface gráfica. Retorna `1` quando não existe um elemento com esse ID.

- `id`: o ID do elemento

```
{"placeholder":"elementheight","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posição X do elemento

**Identificador:** `elementposx`

A posição da borda esquerda de um elemento em pixels da interface gráfica, contada a partir da esquerda da tela. Retorna `1` quando não existe um elemento com esse ID.

- `id`: o ID do elemento

```
{"placeholder":"elementposx","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posição Y do elemento

**Identificador:** `elementposy`

A posição da borda superior de um elemento em pixels da interface gráfica, contada a partir do topo da tela. Retorna `1` quando não existe um elemento com esse ID.

- `id`: o ID do elemento

```
{"placeholder":"elementposy","values":{"id":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Altura do conteúdo de um elemento de texto

**Identificador:** `text_element_content_height`

A altura necessária para um [elemento de texto](/text-in-menus) exibir todo o seu texto sem rolagem, em pixels da interface gráfica. Considera linhas quebradas automaticamente, escala do texto e espaçamento entre linhas, sendo útil para ajustar fundos ao texto. Retorna `0` quando o elemento não é um elemento de texto.

- `element_identifier`: o ID do elemento de texto

```
{"placeholder":"text_element_content_height","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Posição de rolagem do elemento

**Identificador:** `scroll_area_scroll_position`

O quanto o conteúdo de uma [área rolável](/scrollable-areas) ou de um elemento de texto foi rolado, em pixels da interface gráfica a partir do início. Retorna `0` para outros elementos.

- `element_identifier`: o ID do elemento
- `axis`: `vertical` ou `horizontal`. Qualquer outro valor indica a direção em que o elemento rola.

```
{"placeholder":"scroll_area_scroll_position","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Percentual de rolagem do elemento

**Identificador:** `scroll_area_scroll_percent`

O quanto o conteúdo de uma área rolável ou de um elemento de texto foi rolado, de `0` (início) a `100` (fim). Retorna `0` para outros elementos e quando não há conteúdo para rolar.

- `element_identifier`: o ID do elemento
- `axis`: `vertical` ou `horizontal`. Qualquer outro valor indica a direção em que o elemento rola.

```
{"placeholder":"scroll_area_scroll_percent","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Tamanho do conteúdo rolável do elemento

**Identificador:** `scroll_area_content_size`

O tamanho do conteúdo de uma área rolável ou de um elemento de texto: a altura para `vertical` e a largura para `horizontal`. Retorna `0` para outros elementos.

- `element_identifier`: o ID do elemento
- `axis`: `vertical` ou `horizontal`. Qualquer outro valor indica a direção em que o elemento rola.

```
{"placeholder":"scroll_area_content_size","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","axis":"vertical"}}
```

### Valor do campo de entrada de texto

**Identificador:** `text_input_field_value`

O texto digitado em um [campo de entrada de texto](/elements#text-input-field) ou em um campo de texto da tela original. Retorna vazio quando o elemento não é um campo de texto.

- `element_identifier`: o ID do elemento

```
{"placeholder":"text_input_field_value","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Rótulo/texto de widget original

**Identificador:** `vanillabuttonlabel`

O rótulo de um botão ou outro widget da tela original, como `Opções...`. No editor de layout, clique com o botão direito no widget e selecione **Copiar localizador do widget** para obter seu localizador.

- `locator`: o localizador do widget

```
{"placeholder":"vanillabuttonlabel","values":{"locator":"title_screen:mc_titlescreen_options_button"}}
```

### Posição X do mouse

**Identificador:** `mouseposx`

A posição do mouse em pixels da interface gráfica, contada a partir da esquerda da tela. No editor de layout, é sempre `10`, para que os elementos que seguem o mouse permaneçam em uma posição editável.

```
{"placeholder":"mouseposx"}
```

### Posição Y do mouse

**Identificador:** `mouseposy`

A posição do mouse em pixels da interface gráfica, contada a partir do topo da tela. No editor de layout, é sempre `10`.

```
{"placeholder":"mouseposy"}
```

### Cliques por segundo

**Identificador:** `clicks_per_second`

A quantidade de cliques em um botão do mouse durante o último segundo.

- `mouse_button` (opcional): `left` ou `right`. O padrão é `left`.

```
{"placeholder":"clicks_per_second","values":{"mouse_button":"left"}}
```

## Jogador

### Nome do jogador

**Identificador:** `playername`

O nome do jogador, como `Steve`.

```
{"placeholder":"playername"}
```

### UUID do jogador

**Identificador:** `playeruuid`

O UUID do jogador, como `c8cde7fe-7ced-11eb-9439-0242ac130002`.

```
{"placeholder":"playeruuid"}
```

### Mensagem da última morte

**Identificador:** `lastdeathmessage`

A última mensagem de morte do jogador desde que o jogo foi iniciado, como `Steve foi morto por Zumbi`. Retorna vazio antes da primeira morte.

- `as_json_component` (opcional): `true` retorna a mensagem como um componente de texto JSON, com suas cores. O padrão é `false`.

```
{"placeholder":"lastdeathmessage","values":{"as_json_component":"false"}}
```

## Tempo atual

Estes espaços reservados são sobre o horário do seu computador. Os que se referem à data e ao horário aceitam o valor opcional `timezone`: `system` usa o fuso horário do computador (padrão), ou você pode indicar um ID, como `UTC`, `Europe/Berlin` ou `America/New_York`. Consulte [nodatime.org/TimeZones](https://nodatime.org/TimeZones) para ver todos os IDs.

### Ano atual

**Identificador:** `realtimeyear`

O ano, como `2026`.

```
{"placeholder":"realtimeyear","values":{"timezone":"system"}}
```

### Mês atual

**Identificador:** `realtimemonth`

O mês, de `01` a `12`.

```
{"placeholder":"realtimemonth","values":{"timezone":"system"}}
```

### Dia atual

**Identificador:** `realtimeday`

O dia do mês, de `01` a `31`.

```
{"placeholder":"realtimeday","values":{"timezone":"system"}}
```

### Hora atual

**Identificador:** `realtimehour`

A hora, de `00` a `23`.

- `twelve_hour_format` (opcional): `true` retorna valores de `01` a `12`. O padrão é `false`.

```
{"placeholder":"realtimehour","values":{"twelve_hour_format":"false","timezone":"Europe/Berlin"}}
```

### Minuto atual

**Identificador:** `realtimeminute`

O minuto, de `00` a `59`.

```
{"placeholder":"realtimeminute","values":{"timezone":"system"}}
```

### Segundo atual

**Identificador:** `realtimesecond`

O segundo, de `00` a `59`.

```
{"placeholder":"realtimesecond","values":{"timezone":"system"}}
```

### Horário atual em milissegundos (Unix timestamp)

**Identificador:** `unix_time`

Os milissegundos decorridos desde 1º de janeiro de 1970 (UTC), como `1732456789012`. É útil para cronômetros: salve o valor em uma variável e subtraia-o de um valor posterior usando a Calculadora.

```
{"placeholder":"unix_time"}
```

## Servidor

Estes espaços reservados consultam o status de um servidor, como a lista de servidores. Enquanto uma tela personalizada está aberta, o FancyMenu consulta o servidor a cada 30 segundos. Até a primeira resposta, o servidor é considerado offline.

- `ip`: o endereço do servidor, incluindo a porta quando ela não for a padrão, como `play.example.net` ou `play.example.net:25566`

### Status do servidor

**Identificador:** `serverstatus`

Retorna `Online` em verde ou `Offline` em vermelho.

```
{"placeholder":"serverstatus","values":{"ip":"play.example.net"}}
```

### Quantidade de jogadores no servidor

**Identificador:** `serverplayercount`

A quantidade de jogadores online e o limite máximo, como `12/100`. Retorna `0/0` até o servidor responder.

```
{"placeholder":"serverplayercount","values":{"ip":"play.example.net"}}
```

### MOTD do servidor

**Identificador:** `servermotd`

Uma linha da mensagem do dia do servidor.

- `line`: `1` ou `2`

```
{"placeholder":"servermotd","values":{"ip":"play.example.net","line":"1"}}
```

### Ping do servidor

**Identificador:** `serverping`

O ping do servidor em milissegundos, como `54`. Retorna `-1` enquanto o servidor estiver offline.

```
{"placeholder":"serverping","values":{"ip":"play.example.net"}}
```

### Versão do servidor

**Identificador:** `serverversion`

A versão do Minecraft do servidor, como `1.21.1`. Alguns servidores exibem um texto próprio aqui. Retorna `---` até o servidor responder.

```
{"placeholder":"serverversion","values":{"ip":"play.example.net"}}
```

## Vídeo

Estes espaços reservados leem [elementos de vídeo e planos de fundo de vídeo dos menus](/video) do menu aberto. Para elementos de vídeo, clique com o botão direito em um deles no editor de layout e selecione **Copiar ID do elemento**. Para planos de fundo, clique com o botão direito no plano de fundo do editor e selecione **Copiar identificador do plano de fundo**.

### Volume do elemento de vídeo

**Identificador:** `video_element_vol`

O volume de um elemento de vídeo, de `0.0` (0%) a `1.0` (100%).

- `element_identifier`: o ID do elemento de vídeo

```
{"placeholder":"video_element_vol","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Duração do elemento de vídeo

**Identificador:** `video_element_duration`

A duração do vídeo de um elemento de vídeo, como `02:00`. Retorna `00:00` (ou `0`) enquanto ele carrega.

- `element_identifier`: o ID do elemento de vídeo
- `output_as_timestamp` (opcional): `true` retorna milissegundos, como `120000`. O padrão é `false`.

```
{"placeholder":"video_element_duration","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","output_as_timestamp":"false"}}
```

### Tempo de reprodução do elemento de vídeo

**Identificador:** `video_element_playtime`

O ponto atual do vídeo de um elemento de vídeo, como `00:45`. Retorna `00:00` (ou `0`) enquanto ele carrega.

- `element_identifier`: o ID do elemento de vídeo
- `show_percentage` (opcional): `true` retorna o progresso de `0` a `100`. O padrão é `false`.
- `output_as_timestamp` (opcional): `true` retorna milissegundos. Se ambos forem `true`, `show_percentage` prevalece. O padrão é `false`.

```
{"placeholder":"video_element_playtime","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012","show_percentage":"false","output_as_timestamp":"false"}}
```

### Estado de pausa do elemento de vídeo

**Identificador:** `video_element_paused_state`

Retorna `true` enquanto um elemento de vídeo estiver pausado e `false` nos demais casos.

- `element_identifier`: o ID do elemento de vídeo

```
{"placeholder":"video_element_paused_state","values":{"element_identifier":"5f1c2a9e-7b3d-4c8e-9a21-6d0f4e8b3c17-1732456789012"}}
```

### Volume do plano de fundo de vídeo

**Identificador:** `video_background_vol`

O volume de um plano de fundo de vídeo do menu, de `0.0` (0%) a `1.0` (100%).

- `background_identifier`: o identificador do plano de fundo do menu

```
{"placeholder":"video_background_vol","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

### Duração do plano de fundo de vídeo

**Identificador:** `video_background_duration`

A duração do vídeo de um plano de fundo do menu, como `03:00`. Retorna `00:00` (ou `0`) enquanto ele carrega.

- `background_identifier`: o identificador do plano de fundo do menu
- `output_as_timestamp` (opcional): `true` retorna milissegundos. O padrão é `false`.

```
{"placeholder":"video_background_duration","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","output_as_timestamp":"false"}}
```

### Tempo de reprodução do plano de fundo de vídeo

**Identificador:** `video_background_playtime`

O ponto atual do vídeo de um plano de fundo do menu, como `01:00`. Retorna `00:00` (ou `0`) enquanto ele carrega.

- `background_identifier`: o identificador do plano de fundo do menu
- `show_percentage` (opcional): `true` retorna o progresso de `0` a `100`. O padrão é `false`.
- `output_as_timestamp` (opcional): `true` retorna milissegundos. Se ambos forem `true`, `show_percentage` prevalece. O padrão é `false`.

```
{"placeholder":"video_background_playtime","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012","show_percentage":"true","output_as_timestamp":"false"}}
```

### Estado de pausa do plano de fundo de vídeo

**Identificador:** `video_background_paused_state`

Retorna `true` enquanto um plano de fundo de vídeo do menu estiver pausado e `false` nos demais casos.

- `background_identifier`: o identificador do plano de fundo do menu

```
{"placeholder":"video_background_paused_state","values":{"background_identifier":"8c2e4f6a-1b3d-4e5f-8a7b-9c0d1e2f3a4b-1732456789012"}}
```

## Mundo: estatísticas do jogador

A categoria **Mundo** se refere ao mundo em que você está jogando. A maioria desses espaços reservados precisa de um mundo carregado. Fora de um mundo, retornam `0`, `0.0` ou nada.

### Vida atual do jogador

**Identificador:** `current_player_health`

A vida do jogador, como `20.0`. Cada coração vale `2.0`.

```
{"placeholder":"current_player_health"}
```

### Vida máxima do jogador

**Identificador:** `max_player_health`

A vida máxima do jogador, como `20.0`.

```
{"placeholder":"max_player_health"}
```

### Vida atual do jogador (percentual)

**Identificador:** `current_player_health_percent`

A vida do jogador em percentual, de `0` a `100`.

```
{"placeholder":"current_player_health_percent"}
```

### Vida atual de absorção do jogador

**Identificador:** `current_player_absorption_health`

A vida de absorção do jogador (os corações dourados), como `4.0`.

```
{"placeholder":"current_player_absorption_health"}
```

### Vida máxima de absorção do jogador

**Identificador:** `max_player_absorption_health`

A vida máxima de absorção do jogador, como `4.0`.

```
{"placeholder":"max_player_absorption_health"}
```

### Vida atual de absorção do jogador (percentual)

**Identificador:** `current_player_absorption_health_percent`

A vida de absorção do jogador em percentual, de `0` a `100`.

```
{"placeholder":"current_player_absorption_health_percent"}
```

### Nível de comida atual do jogador

**Identificador:** `current_player_hunger`

O nível de comida do jogador, de `0.0` a `20.0`.

```
{"placeholder":"current_player_hunger"}
```

### Nível máximo de comida do jogador

**Identificador:** `max_player_hunger`

O nível máximo de comida dos jogadores: sempre `20.0`.

```
{"placeholder":"max_player_hunger"}
```

### Nível de comida atual do jogador (percentual)

**Identificador:** `current_player_hunger_percent`

O nível de comida do jogador em percentual, de `0` a `100`.

```
{"placeholder":"current_player_hunger_percent"}
```

### Saturação atual de fome do jogador

**Identificador:** `current_player_hunger_saturation`

A saturação do jogador, como `5.0`. A barra de comida só diminui depois que a saturação acaba.

```
{"placeholder":"current_player_hunger_saturation"}
```

### Armadura atual do jogador

**Identificador:** `current_player_armor`

Os pontos de armadura do jogador, de `0.0` a `20.0`.

```
{"placeholder":"current_player_armor"}
```

### Armadura máxima do jogador

**Identificador:** `max_player_armor`

O máximo de pontos da barra de armadura: sempre `20.0`.

```
{"placeholder":"max_player_armor"}
```

### Armadura atual do jogador (percentual)

**Identificador:** `current_player_armor_percent`

Os pontos de armadura do jogador em percentual, de `0` a `100`.

```
{"placeholder":"current_player_armor_percent"}
```

### Resistência da armadura do jogador

**Identificador:** `player_armor_toughness`

A resistência da armadura do jogador, como `8.0` com uma armadura de diamante completa.

```
{"placeholder":"player_armor_toughness"}
```

### Nível atual de oxigênio do jogador

**Identificador:** `current_player_oxygen`

O ar do jogador debaixo d'água, de `0.0` a `300.0`.

```
{"placeholder":"current_player_oxygen"}
```

### Nível máximo de oxigênio do jogador

**Identificador:** `max_player_oxygen`

O ar máximo do jogador, como `300.0`.

```
{"placeholder":"max_player_oxygen"}
```

### Nível atual de oxigênio do jogador (percentual)

**Identificador:** `current_player_oxygen_percent`

O ar do jogador em percentual, de `0` a `100`.

```
{"placeholder":"current_player_oxygen_percent"}
```

### Nível atual do jogador

**Identificador:** `current_player_level`

O nível de experiência do jogador, como `30`.

```
{"placeholder":"current_player_level"}
```

### Experiência atual do jogador

**Identificador:** `current_player_exp`

O total de pontos de experiência do jogador, como `1395.0`. Não é o nível.

```
{"placeholder":"current_player_exp"}
```

### Progresso de experiência do jogador (percentual)

**Identificador:** `current_player_exp_progress`

O quanto a barra de experiência está cheia, de `0` a `100`.

```
{"placeholder":"current_player_exp_progress"}
```

### Força de ataque do jogador (percentual)

**Identificador:** `player_attack_strength`

O quanto o próximo ataque está carregado, de `0` a `100`, como o indicador de ataque.

```
{"placeholder":"player_attack_strength"}
```

### Modo de jogo do jogador

**Identificador:** `player_gamemode`

`survival`, `creative`, `adventure` ou `spectator`.

```
{"placeholder":"player_gamemode"}
```

### Progresso de uso de item do jogador (FM)

**Identificador:** `player_item_use_progress_fm`

O progresso do jogador ao usar um item, como comer, beber ou puxar um arco, de `0.0` a `1.0`.

```
{"placeholder":"player_item_use_progress_fm"}
```

### Vida atual da montaria

**Identificador:** `current_mount_health`

A vida da criatura montada pelo jogador, como um cavalo, por exemplo `30.0`.

```
{"placeholder":"current_mount_health"}
```

### Vida máxima da montaria

**Identificador:** `max_mount_health`

A vida máxima da criatura montada pelo jogador.

```
{"placeholder":"max_mount_health"}
```

### Vida atual da montaria (percentual)

**Identificador:** `current_mount_health_percent`

A vida da criatura montada pelo jogador em percentual, de `0` a `100`.

```
{"placeholder":"current_mount_health_percent"}
```

### Indicador atual de salto da montaria (percentual)

**Identificador:** `current_mount_jump_meter`

O quanto o salto de um cavalo está carregado, de `0` a `100`.

```
{"placeholder":"current_mount_jump_meter"}
```

### Quantidade de efeitos ativos

**Identificador:** `effects_count`

A quantidade de efeitos que o jogador tem no momento.

```
{"placeholder":"effects_count"}
```

### Efeito ativo

**Identificador:** `active_effect`

O ID de um efeito do jogador, como `minecraft:speed`, na ordem dos ícones de efeito no canto superior direito. Retorna vazio quando não há efeito nesse índice.

- `effect_index`: a posição do efeito. O primeiro tem índice `0`.

```
{"placeholder":"active_effect","values":{"effect_index":"0"}}
```

## Mundo: inventário e itens

Estes espaços reservados estão na categoria **Mundo**. Números dos espaços: `0` a `8` correspondem à barra rápida, `9` a `35` ao restante do inventário, `36` a `39` à armadura, das botas ao capacete, e `40` à mão secundária.

### Espaço selecionado da barra rápida

**Identificador:** `active_hotbar_slot`

O espaço selecionado da barra rápida, de `0` a `8`.

```
{"placeholder":"active_hotbar_slot"}
```

### Item do espaço

**Identificador:** `slot_item`

O ID do item em um espaço, como `minecraft:diamond_sword`. Espaços vazios retornam `minecraft:air`.

- `slot`: o número do espaço

```
{"placeholder":"slot_item","values":{"slot":"0"}}
```

### Quantidade de itens no espaço

**Identificador:** `slot_item_count`

A quantidade de itens em um espaço, como `64`.

- `slot`: o número do espaço

```
{"placeholder":"slot_item_count","values":{"slot":"0"}}
```

### Durabilidade do item no espaço

**Identificador:** `slot_item_durability`

A durabilidade do item em um espaço. Retorna `0` para itens sem durabilidade.

- `slot`: o número do espaço
- `format` (opcional): `current` (durabilidade restante), `max`, `damage` (durabilidade perdida) ou `percentage` (restante, de `0` a `100`). O padrão é `current`.

```
{"placeholder":"slot_item_durability","values":{"slot":"39","format":"percentage"}}
```

### Nome de exibição do item no espaço (FM)

**Identificador:** `slot_item_display_name_fm`

O nome do item em um espaço como componente de texto JSON, com a cor da raridade, como `{"text":"Diamond Sword","color":"aqua"}`. No modo espectador, os espaços da barra rápida retornam os nomes do menu de espectador.

- `slot`: o número do espaço
- `ignore_spectator` (opcional): `true` também retorna os nomes dos itens no modo espectador. O padrão é `false`.

```
{"placeholder":"slot_item_display_name_fm","values":{"slot":"0","ignore_spectator":"false"}}
```

### Quantidade de itens no inventário

**Identificador:** `inventory_item_count`

A quantidade de um item que o jogador tem em todo o inventário.

- `item`: o ID do item, como `minecraft:diamond`. Se ficar vazio, conta todos os itens.

```
{"placeholder":"inventory_item_count","values":{"item":"minecraft:diamond"}}
```

### Pontos de comida restaurados pelo item do espaço

**Identificador:** `inventory_slot_food_point_restore_amount`

A quantidade de pontos de comida restaurados ao comer o item em um espaço, como `4.0` para uma maçã. Retorna `0.0` para itens que não são comida.

- `slot`: o número do espaço

```
{"placeholder":"inventory_slot_food_point_restore_amount","values":{"slot":"0"}}
```

### Categoria do item

**Identificador:** `item_category`

A aba do inventário criativo à qual um item pertence, como `Combat`. Retorna `UNKNOWN` para itens sem uma aba.

- `item`: o ID do item
- `as_key` (opcional): `true` retorna o ID da aba, como `minecraft:combat`. O padrão é `false`.

```
{"placeholder":"item_category","values":{"item":"minecraft:diamond_sword","as_key":"false"}}
```

### Item do inventário sob o cursor

**Identificador:** `hovered_inventory_item`

O ID do item sobre o qual o mouse está em uma tela de inventário, como `minecraft:apple`. Retorna vazio quando não há nenhum.

```
{"placeholder":"hovered_inventory_item"}
```

## Mundo: HUD e chefes

Estes espaços reservados estão na categoria **Mundo**. Os espaços reservados de invasão leem a invasão correspondente à barra exibida na parte superior da tela e requerem o FancyMenu no servidor. No modo para um jogador, sempre funcionam. Sem uma invasão, retornam `0` ou nada.

### Mensagem da barra de ação (FM)

**Identificador:** `action_bar_message_fm`

A mensagem acima da barra rápida como componente de texto JSON, por exemplo `{"text":"You may not rest now","color":"red"}`. Retorna vazio quando não há mensagem.

```
{"placeholder":"action_bar_message_fm"}
```

### Tempo da mensagem da barra de ação (FM)

**Identificador:** `action_bar_message_time_fm`

Quantos ticks a mensagem acima da barra rápida ainda será exibida. 20 ticks equivalem a um segundo.

```
{"placeholder":"action_bar_message_time_fm"}
```

### Tempo de exibição do item destacado (FM)

**Identificador:** `highlighted_item_time_fm`

Quantos ticks o nome do item selecionado ainda será exibido acima da barra rápida.

```
{"placeholder":"highlighted_item_time_fm"}
```

### Título/subtítulo atual do HUD

**Identificador:** `current_title`

O título ou subtítulo exibido no momento, como o de `/title`. Retorna vazio quando não há nenhum.

- `is_subtitle` (opcional): `true` retorna o subtítulo. O padrão é `false`.
- `as_json` (opcional): `true` retorna um componente de texto JSON. O padrão é `false`.

```
{"placeholder":"current_title","values":{"is_subtitle":"false","as_json":"false"}}
```

### Quantidade de barras de chefe

**Identificador:** `boss_count`

A quantidade de barras de chefe exibidas no momento.

```
{"placeholder":"boss_count"}
```

### Nome do chefe

**Identificador:** `boss_name`

O nome de uma barra de chefe, como `Ender Dragon`. Retorna vazio quando não há uma barra nesse índice.

- `boss_index`: a posição da barra de chefe. A primeira tem índice `0`.
- `as_json` (opcional): `true` retorna um componente de texto JSON. O padrão é `false`.

```
{"placeholder":"boss_name","values":{"boss_index":"0","as_json":"false"}}
```

### Vida atual do chefe (percentual)

**Identificador:** `current_boss_health`

O quanto uma barra de chefe está cheia, de `0` a `100`.

- `boss_index`: a posição da barra de chefe. A primeira tem índice `0`.

```
{"placeholder":"current_boss_health","values":{"boss_index":"0"}}
```

### Total de ondas da invasão ativa

**Identificador:** `active_raid_total_waves`

A quantidade total de ondas da invasão, incluindo a onda bônus.

```
{"placeholder":"active_raid_total_waves"}
```

### Ondas restantes da invasão ativa

**Identificador:** `active_raid_remaining_waves`

A quantidade de ondas da invasão que ainda estão por vir.

```
{"placeholder":"active_raid_remaining_waves"}
```

### Onda atual da invasão ativa

**Identificador:** `active_raid_current_wave`

O número da onda mais recente: retorna `1` enquanto a primeira onda ataca e `0` antes dela.

```
Onda {"placeholder":"active_raid_current_wave"} de {"placeholder":"active_raid_total_waves"}
```

### Quantidade de invasores vivos na invasão ativa

**Identificador:** `active_raid_alive_raiders_count`

A quantidade de invasores da invasão que ainda estão vivos.

```
{"placeholder":"active_raid_alive_raiders_count"}
```

### Lista de invasores vivos na invasão ativa

**Identificador:** `active_raid_alive_raiders_list`

Todos os invasores ainda vivos, separados por vírgulas. Cada entrada contém o ID da criatura e o UUID do invasor, como `minecraft:pillager#0d9a4b2e-5f1c-4a8e-9b3d-6c2f1e7a8b90`.

```
{"placeholder":"active_raid_alive_raiders_list"}
```

## Mundo: posição e câmera

Estes espaços reservados estão na categoria **Mundo**.

### Coordenada X do jogador

**Identificador:** `player_x_coordinate`

A coordenada X do bloco em que o jogador está, como `125`.

```
{"placeholder":"player_x_coordinate"}
```

### Coordenada Y do jogador

**Identificador:** `player_y_coordinate`

A coordenada Y do bloco em que o jogador está, como `64`.

```
{"placeholder":"player_y_coordinate"}
```

### Coordenada Z do jogador

**Identificador:** `player_z_coordinate`

A coordenada Z do bloco em que o jogador está, como `-250`.

```
{"placeholder":"player_z_coordinate"}
```

### Direção para a qual o jogador está olhando

**Identificador:** `player_view_direction`

A direção para a qual o jogador está olhando: `north`, `east`, `south` ou `west`.

```
{"placeholder":"player_view_direction"}
```

### Variação da posição X do jogador (FM)

**Identificador:** `player_position_delta_x_fm`

O quanto o jogador se moveu no eixo X desde o último tick, em blocos, como `0.12`. O valor é negativo quando o movimento ocorre na direção oposta.

```
{"placeholder":"player_position_delta_x_fm"}
```

### Variação da posição Y do jogador (FM)

**Identificador:** `player_position_delta_y_fm`

O quanto o jogador se moveu no eixo Y desde o último tick, como `-0.08` ao cair.

```
{"placeholder":"player_position_delta_y_fm"}
```

### Variação da posição Z do jogador (FM)

**Identificador:** `player_position_delta_z_fm`

O quanto o jogador se moveu no eixo Z desde o último tick.

```
{"placeholder":"player_position_delta_z_fm"}
```

### Rotação X da câmera (FM)

**Identificador:** `camera_rotation_x_fm`

O quanto a câmera está voltada para cima ou para baixo, em graus, de `-90.0` (direto para cima) a `90.0` (direto para baixo).

```
{"placeholder":"camera_rotation_x_fm"}
```

### Rotação Y da câmera (FM)

**Identificador:** `camera_rotation_y_fm`

A direção para a qual a câmera está voltada, em graus, de `-180.0` a `180.0`. `0.0` corresponde ao sul.

```
{"placeholder":"camera_rotation_y_fm"}
```

### Variação da rotação X da câmera (FM)

**Identificador:** `camera_rotation_delta_x_fm`

O quanto a câmera girou para cima ou para baixo desde o último tick, em graus.

```
{"placeholder":"camera_rotation_delta_x_fm"}
```

### Variação da rotação Y da câmera (FM)

**Identificador:** `camera_rotation_delta_y_fm`

O quanto a câmera girou para a esquerda ou para a direita desde o último tick, em graus.

```
{"placeholder":"camera_rotation_delta_y_fm"}
```

## Mundo: informações do mundo

Estes espaços reservados estão na categoria **Mundo**.

### Horário do dia no mundo

**Identificador:** `world_daytime`

O horário do dia no mundo em ticks. Um dia tem 24000 ticks e começa às 6h da manhã. A contagem continua de um dia para o outro; por isso, `{"placeholder":"world_daytime"} % 24000` em uma Calculadora retorna o horário do dia atual.

```
{"placeholder":"world_daytime"}
```

### Hora do dia no mundo

**Identificador:** `world_daytime_hour`

A hora do dia no mundo, de `00` a `23`.

- `twelve_hour_format` (opcional): `true` retorna valores de `01` a `12`. O padrão é `false`.

```
{"placeholder":"world_daytime_hour","values":{"twelve_hour_format":"false"}}
```

### Minuto do dia no mundo

**Identificador:** `world_daytime_minute`

O minuto do dia no mundo, de `00` a `59`.

```
{"placeholder":"world_daytime_hour"}:{"placeholder":"world_daytime_minute"}
```

### Tempo total do mundo

**Identificador:** `game_time`

A quantidade total de ticks transcorridos no mundo. Diferentemente do horário do dia, comandos como `/time set` não alteram esse valor.

```
{"placeholder":"game_time"}
```

### Dificuldade do mundo

**Identificador:** `world_difficulty`

`peaceful`, `easy`, `normal` ou `hard`.

```
{"placeholder":"world_difficulty"}
```

### Dimensão atual

**Identificador:** `current_dimension`

A dimensão em que o jogador está, como `minecraft:overworld`.

- `as_key` (opcional): `false` retorna o nome, como `Overworld`. Dimensões sem nome retornam o ID. O padrão é `true`.

```
{"placeholder":"current_dimension","values":{"as_key":"false"}}
```

### Bioma atual

**Identificador:** `current_biome`

O bioma em que o jogador está, como `minecraft:plains`.

- `as_key` (opcional): `false` retorna o nome, como `Plains`. O padrão é `true`.

```
{"placeholder":"current_biome","values":{"as_key":"false"}}
```

### Semente do mundo atual

**Identificador:** `current_world_seed`

A semente do mundo para um jogador, como `-4172144997902289642`. Retorna vazio em servidores.

```
{"placeholder":"current_world_seed"}
```

### Valor da regra do jogo

**Identificador:** `gamerule_value`

O valor de uma regra do jogo, como `true` ou `3`. No modo para um jogador, sempre funciona. Em servidores, requer o FancyMenu no servidor. Retorna vazio quando não existe uma regra com esse nome.

- `name`: o nome da regra do jogo, como `keep_inventory`. No Minecraft 1.21.10 e anteriores, as regras têm nomes como `keepInventory`; esses nomes antigos também funcionam nas versões mais recentes.

```
{"placeholder":"gamerule_value","values":{"name":"keep_inventory"}}
```

### IP do servidor atual

**Identificador:** `current_server_ip`

O endereço do servidor em que o jogador está, como `play.example.net`. Retorna vazio no modo para um jogador.

```
{"placeholder":"current_server_ip"}
```

### Lista de jogadores do mundo

**Identificador:** `world_players_list`

Os nomes dos jogadores que o jogo conhece no mundo, em ordem alfabética, como `Alex, Notch, Steve`.

- `separator` (opcional): o texto entre os nomes. O padrão é `, `.

```
{"placeholder":"world_players_list","values":{"separator":", "}}
```

## Mundo: salvamentos de mundos

Estes espaços reservados estão na categoria **Mundo** e funcionam em qualquer menu, mesmo sem um mundo carregado.

### Quantidade de mundos salvos

**Identificador:** `level_save_count`

A quantidade de mundos para um jogador.

```
{"placeholder":"level_save_count"}
```

### Nomes dos mundos salvos

**Identificador:** `level_save_names`

Os nomes de todos os mundos para um jogador, na ordem da lista de mundos, como `Survival World, Creative Test`.

- `separator` (opcional): o texto entre os nomes. O padrão é `, `.

```
{"placeholder":"level_save_names","values":{"separator":", "}}
```

### Dados do mundo salvo

**Identificador:** `level_save_data`

Todos os dados de um mundo para um jogador em formato JSON, como `{"file_name":"Survival World","game_type":"survival","difficulty":"normal",...}`. Inclui `file_name`, `display_name`, `game_type`, `difficulty`, `allow_commands`, `last_played` (como Unix timestamp), `minecraft_version_name` e outros. Leia valores individuais com o [**Analisador JSON**](#analisador-json).

- `level_name`: o nome do mundo, exatamente como aparece na lista de mundos

```
{"placeholder":"json","values":{"source":"{"placeholder":"level_save_data","values":{"level_name":"Survival World"}}","json_path":"$.game_type"}}
```

## Outros

Estes espaços reservados não têm categoria, então o menu os lista abaixo das categorias.

### FPS (quadros por segundo)

**Identificador:** `fps`

Os quadros por segundo, como `120`.

```
{"placeholder":"fps"}
```

### RAM usada em MB

**Identificador:** `usedram`

A quantidade de RAM usada pelo jogo no momento, em MB, como `4096`.

```
{"placeholder":"usedram"}
```

### RAM máxima em MB

**Identificador:** `maxram`

A quantidade máxima de RAM que o jogo pode usar, em MB, como `8192`.

```
{"placeholder":"maxram"}
```

### RAM usada em %

**Identificador:** `percentram`

A RAM usada pelo jogo como percentual da RAM máxima, como `50`.

```
{"placeholder":"percentram"}
```

### Uso de CPU (JVM)

**Identificador:** `jvmcpu`

O uso de CPU pelo jogo, em percentual, como `25.5`.

```
{"placeholder":"jvmcpu"}
```

### Uso de CPU (sistema operacional)

**Identificador:** `oscpu`

O uso de CPU pelo computador inteiro, em percentual, como `42.8`.

```
{"placeholder":"oscpu"}
```

### Informações da CPU

**Identificador:** `cpuinfo`

O nome da CPU, como `Intel(R) Core(TM) i7-10700K CPU @ 3.80GHz`.

```
{"placeholder":"cpuinfo"}
```

### Informações da GPU

**Identificador:** `gpuinfo`

O nome do dispositivo gráfico usado pelo jogo, como `NVIDIA GeForce RTX 3080`.

```
{"placeholder":"gpuinfo"}
```

### Versão do OpenGL

**Identificador:** `glver`

As informações do driver do dispositivo gráfico usado pelo jogo, como `4.6.0 NVIDIA 566.36`.

```
{"placeholder":"glver"}
```

### Versão do Java

**Identificador:** `javaver`

A versão do Java em que o jogo está sendo executado, como `21.0.5`.

```
{"placeholder":"javaver"}
```

### Máquina virtual Java

**Identificador:** `jvmname`

O nome da máquina virtual Java, como `OpenJDK 64-Bit Server VM`.

```
{"placeholder":"jvmname"}
```

### Nome do sistema operacional

**Identificador:** `osname`

O nome do sistema operacional, como `Windows 11`.

```
{"placeholder":"osname"}
```

### Tempo de execução

**Identificador:** `uptime_duration`

Há quanto tempo o jogo está em execução, em segundos, como `742`.

- `output_as_millis` (opcional): `true` retorna milissegundos. O padrão é `false`.

```
{"placeholder":"uptime_duration","values":{"output_as_millis":"false"}}
```

### Texto aleatório

**Identificador:** `randomtext`

Uma linha aleatória de um arquivo de texto, de um URL ou de um texto digitado por você, como uma dica aleatória. Arquivos e URLs são lidos novamente a cada 30 segundos.

- `source`: um arquivo `.txt` na pasta do jogo, um URL ou linhas separadas por `\n`, como `Tip 1\nTip 2\nTip 3`
- `interval` (opcional): após quantos segundos escolher uma nova linha. `0` escolhe uma linha por sessão de jogo. O padrão é `10`.

```
{"placeholder":"randomtext","values":{"source":"/config/fancymenu/assets/tips.txt","interval":"10"}}
```

### Texto da Web

**Identificador:** `webtext`

A primeira linha do texto de uma página da Web, como um arquivo de texto no seu site. É carregada uma vez e novamente quando o FancyMenu é recarregado. Retorna vazio enquanto carrega.

- `link`: o URL da página

```
{"placeholder":"webtext","values":{"link":"https://example.com/motd.txt"}}
```

### Caminho absoluto de arquivo/pasta

**Identificador:** `absolute_path`

O caminho completo de um arquivo ou pasta na pasta do jogo, como `C:/Users/Steve/AppData/Roaming/.minecraft/config/fancymenu`.

- `short_path`: o caminho dentro da pasta do jogo

```
{"placeholder":"absolute_path","values":{"short_path":"config/fancymenu"}}
```

### Quantidade de caracteres do texto

**Identificador:** `text_character_count`

A quantidade de caracteres de um texto: `Hello World!` tem `12`.

- `text`: o texto

```
{"placeholder":"text_character_count","values":{"text":"$$player_nickname"}}
```

### Largura do texto

**Identificador:** `text_width`

A largura de um texto em pixels da interface gráfica: `Hello World!` tem largura `57`. Os códigos de formatação, como `&l`, são considerados como no jogo; por isso, textos em negrito são mais largos.

- `text`: o texto

```
{"placeholder":"text_width","values":{"text":"Hello World!"}}
```

### Altura do texto

**Identificador:** `text_height`

A altura de um texto em pixels da interface gráfica, incluindo todas as linhas. Quebras de linha são representadas por `\n`. Para ajustar algo a um elemento de texto, use [**Altura do conteúdo de um elemento de texto**](#altura-do-conteúdo-de-um-elemento-de-texto), que também considera a escala do texto, o espaçamento entre linhas e as linhas quebradas automaticamente.

- `text`: o texto

```
{"placeholder":"text_height","values":{"text":"First line\nSecond line"}}
```

### Conteúdo da área de transferência

**Identificador:** `clipboard_content`

O texto na área de transferência do seu computador. Retorna vazio quando ela não contém texto.

```
{"placeholder":"clipboard_content"}
```
