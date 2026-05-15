---
title: Localizando Layouts
description: Como localizar o conteúdo de layouts.
---

# Localizando Layouts

O FancyMenu permite localizar conteúdo de texto e até elementos inteiros ou layouts!

# Conteúdo de Texto

O FancyMenu permite adicionar suas próprias localizações ao jogo.
Depois, elas podem ser usadas com o placeholder **Localize Text** para localizar o texto para o idioma atual do jogo.

## Usando Chaves de Localização do Minecraft Vanilla

Antes de criar localizações personalizadas, talvez você queira usar chaves de localização já existentes do Minecraft. Isso economiza tempo e garante consistência com o texto do Minecraft vanilla.

### Encontrando Chaves de Localização do Vanilla

A maneira mais fácil de encontrar as chaves de localização do Minecraft é navegar pelos arquivos de assets do jogo online:

1. **Acesse o MCAsset.cloud:**  
   Vá para [https://mcasset.cloud/](https://mcasset.cloud/) - este site permite navegar pelos assets do Minecraft sem extraí-los do jogo.

2. **Navegue até os Arquivos de Idioma:**  
   - Selecione sua versão do Minecraft no menu suspenso
   - Vá para: `assets` → `minecraft` → `lang`
   - Abra `en_us.json` para ver todas as localizações em inglês

3. **Encontre a Chave de que Você Precisa:**  
   - Use a função de busca do navegador (Ctrl+F ou Cmd+F) para encontrar um texto específico
   - O formato é `"key": "text"` - a primeira parte entre aspas antes dos dois-pontos (`:`) é a chave
   - Por exemplo: `"menu.singleplayer": "Singleplayer"` - a chave é `menu.singleplayer`

### Usando Chaves de Localização de Mods

Se você tiver outros mods instalados, também pode usar as chaves de localização deles:

1. Verifique a documentação do mod para ver as chaves disponíveis
2. Navegue pelos arquivos de idioma do mod, se eles forem de código aberto

## Arquivos de Localização Personalizados

Arquivos de localização são arquivos de texto com todo o conteúdo que deve estar disponível em vários idiomas. Cada texto traduzível tem uma chave única, para que o Minecraft encontre o texto traduzível correto nos arquivos de localização.

- **Arquivo Padrão (en_us.json):**  
  Inglês (EUA). Este arquivo é usado quando nenhum outro arquivo de idioma é escolhido. Ele funciona como o arquivo de idioma de backup.

- **Outros Arquivos de Idioma:**  
  Por exemplo, você pode criar um arquivo em alemão chamado `de_de.json` para jogadores que usam alemão.

### Como Criar um Arquivo de Localização Personalizado

Você sempre precisa de um arquivo `en_us.json`! Sem ele, o jogo não tem um fallback quando algo dá errado ou quando um idioma não suportado é definido.

1. **Abra um Editor de Texto:**  
   Use o Bloco de Notas (Windows), TextEdit (Mac) ou qualquer editor de texto simples.

2. **Escreva Seu Código JSON:**  
   Crie seu arquivo com suas chaves personalizadas. Uma chave é um nome único que o Minecraft usa para encontrar o texto. Por exemplo:
   
   ```json
   {
     "modpack_name.custom.localization.key": "Seu texto personalizado aqui",
     "modpack_name.another.key": "Outra mensagem"
   }
   ```

3. **Salve o Arquivo:**  
   Salve o arquivo como `en_us.json` para o texto padrão em inglês.

Se você agora quiser adicionar versões traduzidas, como alemão, copie o conteúdo do arquivo `en_us.json` para o novo arquivo e traduza apenas o texto real, NÃO as chaves! As chaves precisam permanecer iguais, para que o jogo ainda consiga encontrar o texto.

Para alemão, você salvaria o arquivo como `de_de.json`. Para outros idiomas, consulte [esta página da wiki do Minecraft](https://minecraft.wiki/w/Language) para encontrar o código de idioma correto e nomeie o arquivo de acordo com ele. Procure pelo **"in-game locale code"** do seu idioma.

## Criando um Resource Pack do Minecraft para o MC 1.21.4

Agora que seus arquivos de localização estão prontos, precisamos de uma forma de carregá-los no Minecraft. Para isso, vamos usar um resource pack. Faremos com que o pack seja ativado por padrão e até possamos escondê-lo se não quisermos que os usuários do modpack mexam nele.

Um **resource pack** é um arquivo ZIP que contém arquivos que alteram a aparência e o estilo do jogo.

### Passos para Criar Seu Resource Pack

1. **Crie uma Nova Pasta:**  
   Crie uma pasta com um nome como `my_custom_pack`, onde você adicionará seus arquivos de localização personalizados.

2. **Crie o Arquivo do Pack (`pack.mcmeta`):**  
   Dentro da sua pasta, crie um arquivo chamado `pack.mcmeta` com o seguinte conteúdo:
   
   ```json
   {
     "pack": {
       "pack_format": 16,
       "description": "Meu Pack Personalizado com Localizações"
     }
   }
   ```
   
   *Observação: `pack_format` 16 é para o Minecraft 1.21.4.*

3. **Adicione Seus Arquivos de Localização:**  
   Dentro da pasta do resource pack, crie a seguinte estrutura de pastas:
   
   ```
   my_custom_pack/
   ├── assets/
   │   └── minecraft/
   │       └── lang/
   │           ├── en_us.json
   │           └── de_de.json
   └── pack.mcmeta
   ```
   
   Coloque seu `en_us.json` personalizado (e quaisquer outros arquivos de idioma, como `de_de.json`) na pasta `lang`.

4. **Compacte o Resource Pack em ZIP:**  
   Quando a pasta estiver pronta, **compacte a pasta inteira em um arquivo ZIP**. Nomeie o ZIP como **my_custom_pack.zip**. Este é o nome de exemplo usado ao longo do guia.

## Onde Colocar o Resource Pack

Coloque o arquivo **my_custom_pack.zip** na pasta **resourcepacks** do Minecraft. Essa pasta geralmente fica em:

- **Windows:** `%appdata%\.minecraft\resourcepacks`
- **Mac:** `~/Library/Application Support/minecraft/resourcepacks`
- **Linux:** `~/.minecraft/resourcepacks`

> Para modpacks, a pasta `resourcepacks` fica no diretório da instância do seu pack.
{.is-warning}

## Carregando Automaticamente o Pack com "Resource Pack Overrides"

O mod **Resource Pack Overrides** permite ativar resource packs por padrão.

### Passos para Carregar Seu Pack Automaticamente

1. **Instale o Mod:**  
   Baixe e instale o mod no [CurseForge](https://www.curseforge.com/minecraft/mc-mods/resource-pack-overrides) ou no [Modrinth](https://modrinth.com/mod/resource-pack-overrides).

2. **Localize o Arquivo de Configuração:**  
   Encontre o arquivo em `.minecraft/config/resourcepackoverrides.json`.  
   *Se o arquivo não existir, crie-o manualmente.*

3. **Edite o Arquivo de Configuração:**  
   Abra o arquivo e adicione seu resource pack à lista `default_packs` usando o nome do arquivo:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ]
   }
   ```
   
   Isso diz ao Minecraft para carregar seu resource pack automaticamente quando você iniciar o jogo.

   **É importante adicionar o prefixo `file/`!**


*Observação: Os resource packs na lista são aplicados em ordem reversa. Isso significa que o pack no topo da lista aparecerá abaixo dos outros no menu de resource packs do jogo.*

## Escondendo o Resource Pack na Tela de Seleção

Você pode esconder seu resource pack para que os jogadores não o vejam na tela de seleção de resource packs.

### Como Escondê-lo

1. **Edite o Arquivo de Configuração Novamente:**  
   No mesmo arquivo `.minecraft/config/resourcepackoverrides.json`, adicione uma substituição para o seu pack:
   
   ```json
   {
     "schema_version": 2,
     "default_packs": [
       "file/my_custom_pack.zip"
     ],
     "pack_overrides": {
       "file/my_custom_pack.zip": {
         "hidden": true
       }
     }
   }
   ```
   
   Essa configuração vai ocultar **my_custom_pack.zip** da tela de seleção, enquanto ainda o carrega automaticamente.

## Usando Suas Novas Chaves de Localização com o FancyMenu

Agora que seus arquivos de localização personalizados foram carregados, você pode usar suas novas chaves nos layouts do FancyMenu.

1. **Edite um Elemento Baseado em Texto:**  
   Abra o FancyMenu e escolha um elemento como um Button ou um elemento de texto.

2. **Clique no Botão de Placeholders:**  
   Procure o botão Placeholders no canto superior direito do editor de texto. (Se você não o vir, talvez o elemento não suporte placeholders.)

3. **Insira o Placeholder Localize Text:**  
   O placeholder Localize Text aparece como um trecho JSON. Ele se parece com isto:
   
   ```json
   {"placeholder":"local","values":{"key":"localization.key"}}
   ```
   
   Substitua `localization.key` pela sua própria chave personalizada. Por exemplo, se você quiser usar a chave do seu arquivo de localização, altere para:
   
   ```json
   {"placeholder":"local","values":{"key":"modpack_name.custom.localization.key"}}
   ```

Bem, e basicamente é isso! O placeholder deve ser substituído pelo conteúdo localizado real quando você não estiver editando-o no editor de texto.

Lembre-se de que o placeholder sempre localizará o conteúdo de texto para o idioma atual do jogo.

# Conteúdo Não Textual (Imagens, etc.)

O FancyMenu também permite localizar imagens e praticamente qualquer elemento que você quiser.

Para isso, você precisará usar **requisitos de carregamento**.
Mais especificamente, o requisito **Is Game Language**.

O requisito **Is Game Language** permite mostrar elementos ou layouts apenas se um idioma específico do jogo estiver definido, então você pode, por exemplo, criar dois elementos de imagem que contenham texto e localizar essa imagem para uma versão com texto em japonês quando o idioma estiver definido como japonês, ou uma versão com texto em inglês, se o idioma estiver definido como inglês.

Para definir requisitos de carregamento para um **elemento**, clique com o botão direito nele e clique em **Loading Requirements**.

Para definir requisitos de carregamento para **layouts inteiros**, clique com o botão direito no fundo do editor de layout e clique em **Loading Requirements [Layout-Wide]**.
