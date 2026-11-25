---
title: Modpacks
description: Como incluir layouts em um modpack.
sourceBlobSha: c19df01d8e726bbff6c9d1d147287ada5d1773eb
---

# FancyMenu em modpacks

Incluir sua configuração do FancyMenu em um modpack é muito fácil e exige apenas alguns passos simples.

> [!CAUTION]
> As configurações do FancyMenu podem executar ações. Importe-as apenas de fontes confiáveis.

> [!WARNING]
> Esta página é **SOMENTE** para configurações do FancyMenu feitas inteiramente no **FancyMenu v3+**. Portanto, se você usa uma configuração legada (feita na v2 e convertida para a v3), alguns passos podem ser diferentes.

# Importando sua configuração para o modpack

A maneira mais fácil de transferir sua configuração da instância em que você a criou para a instância do seu modpack é usando um [perfil](/profiles):

1. Na instância que contém sua configuração, abra **barra de menus -> Personalização -> Perfis**, selecione sua configuração e [exporte-a](/profiles#exporting) como um arquivo `.fmp`.
2. Na instância do seu modpack, abra a janela Perfis e [importe](/profiles#importing) o arquivo `.fmp`, por exemplo, arrastando-o para a janela.
3. Selecione o perfil importado e clique em **Carregar perfil**.

A configuração do FancyMenu que já existia na instância do modpack não será perdida. Ela continuará disponível como um perfil separado, então você poderá voltar a ela quando quiser.

# Distribuindo a configuração com seu modpack

O perfil carregado corresponde ao conteúdo de `<game-directory>/config/fancymenu/`, então ele será distribuído com a pasta `config` do seu modpack, assim como as configurações de outros mods.

Todos os outros perfis da instância ficam em `<game-directory>/config/fancymenu/profiles/`. Exclua os perfis que os jogadores não devem receber antes de exportar seu modpack ou deixe a pasta `profiles` de fora da exportação do modpack.

> [!CAUTION]
> Lembre-se de que configurações legadas criadas no FancyMenu v2 (mesmo que convertidas para a v3) permitiam armazenar recursos de layout fora da pasta `<game-directory>/config/fancymenu/assets/` do FancyMenu. Os perfis contêm apenas a pasta de configuração do FancyMenu. Portanto, nesse caso, você também precisa incluir todos os seus recursos no modpack.

## Redefinindo caixas de seleção antes da exportação

Os [elementos de caixa de seleção](/elements#checkbox) lembram se estão marcados no arquivo `config/fancymenu/checkbox_states.json`. Assim, as caixas de seleção em que você clicou durante os testes também aparecerão marcadas para seus jogadores.

Para que os jogadores comecem do zero, feche o jogo e exclua `checkbox_states.json` antes de exportar seu modpack ou perfil. Sem esse arquivo, todas as caixas de seleção começam desmarcadas. As caixas de seleção que usam uma [variável](/variables) armazenam o estado na própria variável.

O mesmo vale para coisas que foram alteradas por ações durante os testes, como o volume dos [elementos de vídeo](/video): consulte [Locais de armazenamento de dados](/data-storage-locations#your-setup) para encontrar esses arquivos.

## Como encontrar a pasta da instância

A pasta da instância é a pasta principal do seu computador onde ficam armazenados todos os arquivos de uma configuração específica do Minecraft. Launchers como CurseForge e Modrinth chamam essas configurações de "instâncias" ou "perfis" (não confunda com os perfis do FancyMenu).

### Se você usa o CurseForge App

1. Abra o CurseForge.
2. Encontre seu perfil/instância do Minecraft na lista e abra-o.
3. Clique nos três pontos.
4. Escolha "Abrir pasta". Isso abrirá a pasta principal dessa instância do Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/curseforge_launcher_instance.png">

### Se você usa o Modrinth App

1. Abra o Modrinth App.
2. Encontre seu perfil/instância do Minecraft na lista e abra-o.
3. Clique nos três pontos.
4. Escolha "Abrir pasta". Isso abrirá a pasta principal dessa instância do Minecraft.

<img width="630" alt="Screenshot_1" src="https://raw.githubusercontent.com/Keksuccino/FancyMenu/refs/heads/master/assets/docs/modrinth_launcher_instance.png">

### Para outros launchers

Procure uma opção semelhante a "Abrir pasta", "Abrir pasta da instância" ou "Exibir arquivos" para sua configuração específica do Minecraft.

# Desativando a barra de menus e os atalhos de teclado

Você provavelmente não vai querer deixar a barra de menus do FancyMenu visível no seu modpack, então é melhor desativá-la. Mas, como ainda será possível pressionar o atalho de teclado para exibi-la novamente, vamos fazer algo um pouco mais *agressivo*.

Acesse `<game-directory>/config/fancymenu/options.txt` e abra o arquivo em um editor de texto.

Agora defina `modpack_mode` como `true` e salve o arquivo.
Isso desativará completamente todas as sobreposições e os atalhos de teclado.

Para poder editar seus layouts novamente, defina a opção de configuração como `false`.

# Desativando a tela de boas-vindas

Na maioria dos casos, isso não será necessário. Mas, se você ainda não fechou a tela de boas-vindas (a tela que pede para você ler a documentação), defina `show_welcome_screen` como `false` em `<game-directory>/config/fancymenu/options.txt`.

A tela aparece apenas uma vez e é desativada quando você clica no botão **Abrir documentação**. Portanto, na maioria dos casos, não será necessário fazer isso manualmente.

<br>
<img width="630" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4383b39f-f55a-4eb8-8142-34a425474bb3">
