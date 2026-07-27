---
title: Menu Principal de Ice & Fire
description: Como desativar o menu principal personalizado de Ice and Fire.
---

# Menu Principal de Ice & Fire

Para desativar a tela de título personalizada no mod Ice and Fire, você precisa alterar a configuração dele. Veja como fazer isso:

## 1. Localize o Arquivo de Configuração
- **Nome do arquivo:** A configuração fica no arquivo chamado **`iceandfire-client.toml`**.
- **Local da pasta:** Esse arquivo geralmente está em **`<game-directory>/config/`**, onde `<game-directory>` é o diretório da instância/perfil ativo do launcher.

## 2. Edite o Arquivo de Configuração
- **Abra o arquivo:** Use qualquer editor de texto simples (como o Bloco de Notas no Windows ou o TextEdit no macOS) para abrir `iceandfire-client.toml`.
- **Encontre a configuração:** Role para baixo até encontrar uma opção relacionada ao menu principal personalizado. Ela pode estar comentada e parecer com isto:
  ```toml
  # Whether to display the dragon on the main menu or not [default: true]
  B:"Custom main menu"=true
  ```
- **Altere o valor:** Defina essa opção como **false** alterando a linha para:
  ```toml
  B:"Custom main menu"=false
  ```
  Essa alteração informa ao mod para não renderizar seu menu principal personalizado (geralmente com o dragão ou outros visuais temáticos).

## 3. Salve e Reinicie
- **Salve o arquivo:** Depois de fazer a alteração, salve o arquivo.
- **Reinicie o Minecraft:** Feche e abra o Minecraft novamente para que as mudanças tenham efeito. Quando o jogo carregar, ele deverá usar o menu principal padrão em vez do personalizado do mod.

## Dicas Adicionais
- **Verifique se está editando o arquivo correto:** Pode existir um arquivo de configuração comum separado, então certifique-se de estar editando **`iceandfire-client.toml`** (esta é a configuração específica do cliente, não a comum).
- **Faça um backup antes:** É sempre uma boa ideia fazer uma cópia de segurança do arquivo de configuração original antes de modificá-lo.
- **Modpacks:** Se você estiver usando um modpack, o arquivo de configuração pode estar dentro da estrutura de pastas do pacote, mas o princípio continua o mesmo.

Seguindo esses passos, você deverá desativar o menu principal personalizado fornecido pelo mod, permitindo usar o próprio plano de fundo do menu principal do seu pacote de texturas.
