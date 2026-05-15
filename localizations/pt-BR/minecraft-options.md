---
title: Definir/Obter Opções do Minecraft
description: >-
  Como definir e obter opções do Minecraft como volume, FOV, distância de
  renderização etc.
---

# Trabalhando com Opções do Minecraft no FancyMenu

O FancyMenu permite que você obtenha e defina configurações do jogo Minecraft (opções) usando diferentes عناصر de interface. Este guia mostrará como usar botões, sliders e tickers para trabalhar com opções do Minecraft nos seus layouts de menu personalizados.

# Entendendo as Opções do Minecraft

O Minecraft tem muitas opções nativas que controlam tudo, desde configurações gráficas até o volume do som. O FancyMenu permite que você acesse essas opções pelos nomes delas.

Alguns nomes comuns de opções incluem:
- `soundCategory_master` - Volume principal
- `soundCategory_music` - Volume da música
- `soundCategory_ambient` - Volume dos sons ambientes
- `soundCategory_players` - Volume dos sons dos jogadores
- `soundCategory_blocks` - Volume dos sons dos blocos
- `fov` - Campo de visão
- `gamma` - Brilho
- `renderDistance` - Distância de renderização

# Exibindo Valores das Opções

Você pode exibir o valor atual de qualquer opção do Minecraft usando um placeholder especial.

O placeholder é assim:
```
{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}
```

Substitua `option_name` pelo nome real da opção que você quer exibir.

# Definindo Opções com Botões

Botões podem ser usados para definir valores específicos para opções do Minecraft.

## Como configurar um botão:

1. Crie um novo elemento Button
2. Defina o rótulo do botão (o que aparece nele)
3. Adicione uma ação: clique com o botão direito no botão → Edit Action Script → Add Action → Set Minecraft Option Value
4. Na janela "Set Minecraft Option Value":
   - Name: digite o nome da opção (como `renderDistance`)
   - Value: digite o valor a ser definido (como `16`)

## Exemplo: 

Criando um botão que define a distância de renderização para 16 chunks:
- Option Name: `renderDistance`
- Value: `16`
- Label: "Definir Distância de Renderização para 16 chunks"

# Definindo Opções com Sliders

Sliders são perfeitos para opções com intervalo de valores, como configurações de volume ou brilho.

## Como configurar um slider:

1. Crie um novo elemento Slider
2. Defina o tipo do slider:
   - Para números inteiros (como distância de renderização): escolha "Integer Range"
   - Para números decimais (como volume): escolha "Decimal Range"
3. Defina os valores mínimo e máximo
4. Adicione uma ação para definir a opção do Minecraft:
   - Clique com o botão direito → Edit Action Script → Add Action → Set Minecraft Option Value
   - Name: o nome da opção
   - Value: `$$value` (essa variável especial contém o valor atual do slider)
5. Defina o valor pré-selecionado como o valor atual da opção:
   - Defina "Pre-Selected Value" como `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

## Exemplos de formatos de rótulo do slider:

Para mostrar o valor atual da opção no rótulo do slider, use:
```
Volume: {"placeholder":"minecraft_option_value","values":{"name":"soundCategory_master"}}
```

Para mostrar uma porcentagem (útil para volume):
```
Volume: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
```

# Definindo Opções com Tickers

Tickers são elementos invisíveis que podem alterar opções automaticamente em uma programação.

## Como configurar um ticker:

1. Crie um novo elemento Ticker
2. Configure as opções de tick:
   - Tick Mode: escolha quando a opção deve ser atualizada
   - Tick Delay: defina com que frequência ela é atualizada (em milissegundos)
3. Adicione a ação para definir uma opção do Minecraft:
   - Clique com o botão direito → Edit Action Script → Add Action → Set Minecraft Option Value
   - Defina o nome e o valor da opção

## Exemplo:

Definindo gamma (brilho) como máximo quando o menu carrega:
- Tick Mode: On Load Screen
- Name: `gamma`
- Value: `1.0`

# Casos de Uso Comuns

Aqui estão alguns casos comuns do que você pode fazer ao usar o FancyMenu para definir e obter opções do Minecraft.

## Criando Sliders de Volume Personalizados

Sliders de volume são um uso comum da integração com opções do Minecraft. Veja como criar um slider personalizado de volume da música:

1. Crie um novo elemento Slider
2. Defina "Slider Type" como "Decimal Range"
3. Defina "Minimum Range Value" como "0.0"
4. Defina "Maximum Range Value" como "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Defina Name como `soundCategory_music`
   - Defina Value como `$$value`
6. Defina "Pre-Selected Value" como `{"placeholder":"minecraft_option_value","values":{"name":"soundCategory_music"}}`
7. Para exibir o volume como porcentagem, defina o rótulo como: 
   ```
   Music: {"placeholder":"calc","values":{"expression":"$$value * 100.0","decimal":"false"}}%
   ```

Você pode criar sliders semelhantes para outras categorias de som:
- Volume Principal: `soundCategory_master`
- Música: `soundCategory_music`
- Ambiente: `soundCategory_ambient`
- Blocos: `soundCategory_blocks`
- Jogadores: `soundCategory_players`
- Clima: `soundCategory_weather`

## Criando um Slider de FOV Personalizado

Field of View (FOV) é uma configuração gráfica importante que determina o quão amplo é o seu campo de visão no jogo. A opção FOV usa internamente valores de -1.0 a 1.0, mas é exibida como 30 a 110 na interface.

### Entendendo o Mapeamento do Valor de FOV
- Faixa de valor interno: -1.0 a 1.0
- Faixa de valor exibida: 30 a 110
- Fórmula de mapeamento: `(internal_value + 1) * 40 + 30`

### Etapa 1: Criar um Elemento Ticker para Atualizar o Texto do FOV

Primeiro, precisamos de um ticker que verifique o valor atual do FOV e defina uma variável com a descrição apropriada:

1. Crie um novo elemento Ticker
2. Defina "Tick Mode" como "Normal" (para que ele seja atualizado continuamente)
3. Defina "Tick Delay" para cerca de "10" (milissegundos) para evitar verificações excessivas

Agora precisamos configurar as ações para os rótulos do FOV. Veja como a estrutura do seu action script deve ficar:

```
▶ Action Script
│
├─▶ IF (FOV mapeado = 70)
│  └─■ Set Variable Value: fov_text:Normal
│
├─▶ ELSE-IF (FOV mapeado = 110)
│  └─■ Set Variable Value: fov_text:Quake Pro
│
└─▶ ELSE
   └─■ Set Variable Value: fov_text:[valor numérico calculado]
```

Vamos configurar cada parte:

#### Configurando o rótulo "Normal" do FOV:
1. Clique com o botão direito → Edit Action Script → Add Action
2. Clique em "IF Statement" para adicionar um bloco condicional
3. Defina o requisito como "Is Number" com:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "70"
4. Dentro deste bloco IF, adicione a ação "Set Variable Value (FM Variable)" com:
   - Value: `fov_text:Normal`

#### Configurando o rótulo "Quake Pro" do FOV:
1. Dentro do Action Script, adicione "ELSE-IF Statement"
2. Defina o requisito como "Is Number" com:
   - Compare Mode: "equals"
   - Number: `{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`
   - Compare With: "110"
3. Dentro deste bloco ELSE-IF, adicione a ação "Set Variable Value (FM Variable)" com:
   - Value: `fov_text:Quake Pro`

#### Configurando o rótulo numérico do FOV:
1. Adicione um bloco "ELSE Statement"
2. Dentro deste bloco ELSE, adicione a ação "Set Variable Value (FM Variable)" com:
   - Value: `fov_text:{"placeholder":"calc","values":{"decimal":"false","expression":"({"placeholder":"minecraft_option_value","values":{"name":"fov"}} + 1) * 40 + 30"}}`

<img src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/fov_slider_action_script.png" alt="Script de Ação do Slider de FOV" style="max-width: 600px; height: auto;">

### Etapa 2: Criar o Slider de FOV

1. Crie um novo elemento Slider
2. Defina "Slider Type" como "Decimal Range"
3. Defina "Minimum Range Value" como "-1.0"
4. Defina "Maximum Range Value" como "1.0"
5. Edit Action Script → Add Action → Set Minecraft Option Value
   - Defina Name como `fov`
   - Defina Value como `$$value`
6. Defina "Pre-Selected Value" como `{"placeholder":"minecraft_option_value","values":{"name":"fov"}}`

### Etapa 3: Definir o Rótulo do Slider

Defina o rótulo do slider para simplesmente exibir a variável de texto do FOV:

```
FOV: {"placeholder":"getvariable","values":{"name":"fov_text"}}
```

Esse rótulo mostrará:
- "FOV: Normal" quando o valor for 70
- "FOV: Quake Pro" quando o valor for 110  
- "FOV: 85" (ou qualquer outro número) para todos os outros valores

### Dicas para Sliders de FOV

- A faixa interna de valor do slider é de -1.0 a 1.0, e precisa ser mapeada para 30 a 110 para exibição
- A fórmula de conversão é: `(internal_value + 1) * 40 + 30`
- Apenas dois valores têm rótulos especiais: 70 (Normal) e 110 (Quake Pro)
- O FOV padrão no Minecraft é 70 (o que corresponde ao valor interno 0.0)
- A variável `fov_text` contém automaticamente o rótulo especial ou o valor numérico

## Exibindo Valores das Opções em Elementos de Texto

Você também pode exibir os valores atuais das opções em elementos de Texto:

1. Crie um elemento Text
2. Para o conteúdo do texto, use o placeholder: `{"placeholder":"minecraft_option_value","values":{"name":"option_name"}}`

Por exemplo, para mostrar a distância de renderização atual:
```
Distância de renderização atual: {"placeholder":"minecraft_option_value","values":{"name":"renderDistance"}} chunks
```

# Encontrando Nomes de Opções

Você pode encontrar os nomes de todas as opções disponíveis assim:

  1. Criando um botão
  2. Clicando com o botão direito nele
  3. Clicando em "Edit Action Script"
  4. Adicionando a ação "Set Minecraft Option Value"
  5. Ao editar o valor da ação, observe as sugestões do menu suspenso quando você começar a digitar no campo "Name"
  
# Dicas Importantes

- **Valores Válidos**: Nem todas as opções aceitam todos os valores. Por exemplo:
  - Opções de volume aceitam valores de 0.0 a 1.0
  - A distância de renderização normalmente aceita números inteiros de 2 a 32
  - Opções booleanas (true/false), como `pauseOnLostFocus`, aceitam "true" ou "false"

- **Teste**: Sempre teste suas configurações para garantir que funcionem como esperado!

- **Feedback Visual**: Dê aos usuários um feedback visual sobre o valor atual usando os placeholders descritos acima.
