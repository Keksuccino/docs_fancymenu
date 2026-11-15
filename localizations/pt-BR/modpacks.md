---
title: Modpacks
description: Como incluir layouts em um modpack.
sourceBlobSha: deb3c58e9536e0fe085820a2b9e463f5faaa7819
---

# FancyMenu em Modpacks

Incluir sua configuração do FancyMenu em um modpack é muito fácil e requer apenas alguns passos simples.

> [!CAUTION]
> As configurações do FancyMenu podem executar ações. Importe-as apenas de fontes confiáveis.

> [!WARNING]
> Esta página é **SOMENTE** para configurações do FancyMenu criadas completamente no **FancyMenu v3+**. Portanto, se você usa uma configuração legada (criada na v2 e convertida para a v3), alguns passos podem ser diferentes.

# Adicionando Sua Configuração ao Modpack

A maneira mais fácil de mover sua configuração da instância em que você a criou para a instância do seu modpack é usando um [perfil](./profiles):

1. Na instância que contém sua configuração, abra **barra de menus -> Personalização -> Perfis**, selecione sua configuração e [exporte](./profiles#exporting) como um arquivo `.fmp`.
2. Na instância do seu modpack, abra a janela de Perfis e [importe](./profiles#importing) o arquivo `.fmp`, por exemplo, arrastando-o para a janela.
3. Selecione o perfil importado e clique em **Carregar perfil**.

A configuração do FancyMenu que já existia na instância do modpack não é perdida. Ela continua disponível como um perfil próprio, permitindo que você volte a ela a qualquer momento.

# Distribuindo a Configuração com Seu Modpack

O perfil carregado corresponde ao conteúdo de `<game-directory>/config/fancymenu/`, portanto ele será incluído na pasta `config` do seu modpack, assim como as configurações de outros mods.

Todos os outros perfis da instância são armazenados em `<game-directory>/config/fancymenu/profiles/`. Exclua os perfis que os jogadores não devem receber antes de exportar seu modpack ou deixe a pasta `profiles` fora da exportação do modpack.

> [!CAUTION]
> Lembre-se de que configurações legadas antigas criadas no FancyMenu v2 (mesmo que convertidas para a v3) permitiam armazenar recursos de layout fora da pasta `<game-directory>/config/fancymenu/assets/` do FancyMenu. Os perfis contêm apenas a pasta de configuração do FancyMenu, portanto, nesse caso, você também precisa garantir que todos os seus recursos sejam incluídos no modpack.

## Como Encontrar a Pasta da Instância

A pasta da instância é a pasta principal do seu computador onde todos os arquivos de uma configuração específica do Minecraft são armazenados. Launchers como CurseForge e Modrinth chamam essas configurações de "instâncias" ou "perfis" (não confunda com os perfis do FancyMenu).

### Se você usa o aplicativo CurseForge

1. Abra o CurseForge.
2. Encontre seu perfil/instância do Minecraft na lista e abra-o.
3. Clique nos três pontos.
4. Escolha "Abrir pasta". Isso abrirá a pasta principal dessa instância do Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Se você usa o aplicativo Modrinth

1. Abra o aplicativo Modrinth.
2. Encontre seu perfil/instância do Minecraft na lista e abra-o.
3. Clique nos três pontos.
4. Escolha "Abrir pasta". Isso abrirá a pasta principal dessa instância do Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para outros launchers

Procure uma opção semelhante a "Abrir pasta", "Abrir pasta da instância" ou "Visualizar arquivos" para sua configuração específica do Minecraft.

# Desativando a Barra de Menus e as Teclas de Atalho

Você certamente não vai querer manter a barra de menus do FancyMenu visível no seu modpack, então deve desativá-la. Porém, como as pessoas ainda podem pressionar a tecla de atalho para torná-la visível novamente, vamos fazer algo um pouco mais *agressivo*.

Acesse `<game-directory>/config/fancymenu/options.txt` e abra o arquivo em um editor de texto.

Agora defina `modpack_mode` como `true` e salve o arquivo.
Isso desativará completamente todas as sobreposições e teclas de atalho.

Para poder editar seus layouts novamente, defina essa opção de configuração de volta para `false`.

# Desativando a Tela de Boas-vindas

Isso não deve ser necessário na maioria dos casos, mas, se você ainda não fechou a tela de Boas-vindas (a tela que informa que você deve ler a documentação), defina `show_welcome_screen` como `false` em `<game-directory>/config/fancymenu/options.txt`.

A tela é exibida apenas uma vez e se desativa quando você clica no botão **Abrir documentação**. Portanto, fazer isso manualmente também não deve ser necessário na maioria dos casos.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
