---
title: Modpacks
description: Como incluir layouts em um modpack.
---

# FancyMenu em Modpacks

Incluir sua configuração do FancyMenu em um modpack é muito fácil e leva apenas alguns passos simples.

> [!CAUTION]
> Configurações do FancyMenu podem executar ações. Importe-as apenas de fontes em que você confia.

> [!WARNING]
> Esta página é **APENAS** para configurações do FancyMenu feitas completamente no **FancyMenu v3+**. Então, se você usa uma configuração legada (feita no v2 e convertida para v3), alguns passos podem ser diferentes.

# Incluindo a Configuração do FancyMenu no Seu Modpack

A principal coisa que você precisa fazer é copiar uma pasta especial que o FancyMenu usa para salvar todos os seus designs.

## O que você vai precisar encontrar

1. **A pasta da sua "instância do Minecraft":** Esta é a pasta principal no seu computador onde ficam armazenados todos os arquivos de uma configuração específica do Minecraft (como aquela em que você criou seus menus). Launchers como CurseForge e Modrinth chamam isso de "instâncias" ou "perfis".
2. **A pasta `config`:** Dentro da pasta da sua instância do Minecraft, geralmente existe uma pasta chamada `config`. É aqui que muitos mods armazenam suas configurações.
3. **A pasta `fancymenu`:** Dentro dessa pasta `config`, o FancyMenu cria sua própria pasta chamada `fancymenu`. Essa é a pasta de ouro que precisamos!

## Como encontrar o local de salvamento da instância

### Se você usa o CurseForge App

1. Abra o CurseForge.
2. Encontre seu perfil/instância do Minecraft na lista e abra-o.
3. Clique nos três pontos.
4. Escolha "Open Folder". Isso abrirá a pasta principal dessa instância do Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Se você usa o Modrinth App

1. Abra o Modrinth App.
2. Encontre seu perfil/instância do Minecraft na lista e abra-o.
3. Clique nos três pontos.
4. Escolha "Open Folder". Isso abrirá a pasta principal dessa instância do Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para outros launchers

Procure uma opção semelhante como "Open Folder", "Open Instance Folder" ou "View Files" para a sua configuração específica do Minecraft.

## Copiando a Configuração do FancyMenu

1. Navegue até a pasta `config` da sua instância do MODPACK (aquela para a qual você quer copiar sua configuração).
2. Se houver uma pasta `fancymenu` dentro dela, EXCLUA-A.
3. Abra a pasta `config` da instância de ORIGEM (aquela de onde você quer usar a configuração).
4. Copie a pasta `fancymenu` dentro da pasta `config` da sua instância de ORIGEM para a pasta `config` da sua instância do MODPACK.
5. Pronto. É isso. Reinicie a instância do seu modpack agora e você deverá ver a configuração sendo carregada.

> [!CAUTION]
> Lembre-se de que configurações legadas antigas feitas no FancyMenu v2 (mesmo que convertidas para v3) permitiam armazenar assets de layout fora da pasta `<game-directory>/config/fancymenu/assets/` do FancyMenu. Nesse caso, você também precisa garantir que inclua todos os seus assets no modpack.

# Desativando a Barra de Menu e as Teclas de Atalho

Você certamente não quer manter a barra de menu do FancyMenu visível no seu modpack, então deve desativá-la. Mas, como as pessoas ainda podem pressionar a tecla de atalho para torná-la visível novamente, vamos fazer algo um pouco mais *agressivo*.

Navegue até `<game-directory>/config/fancymenu/options.txt` e abra o arquivo em um editor de texto.

Agora defina `modpack_mode` como `true` e salve o arquivo.
Isso desativará completamente todos os overlays e atalhos.

Para poder editar seus layouts novamente, altere a opção de configuração de volta para `false`.

# Desativando a Tela de Boas-Vindas

Isso não deve ser necessário na maioria dos casos, mas se você ainda não fechou a tela de Boas-Vindas (a tela que pede para você ler a documentação), certifique-se de definir `show_welcome_screen` como `false` em `<game-directory>/config/fancymenu/options.txt`.

A tela só aparece uma vez e se desativa quando você clica no botão **Open Documentation**, então, novamente, fazer isso manualmente geralmente não será necessário.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
