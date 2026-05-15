---
title: Menu Principal do Ice & Fire
description: Como desativar o menu principal personalizado do Ice and Fire.
---

Para desativar a tela de título personalizada no mod Ice and Fire, você precisa alterar a configuração dele. Veja como fazer isso:

## 1. Localize o Arquivo de Configuração
- **Nome do arquivo:** A configuração está no arquivo chamado **`iceandfire-client.toml`**.
- **Local da pasta:** Esse arquivo geralmente fica na pasta **`.minecraft/config`** (ou no diretório de configuração equivalente, se você estiver usando um launcher personalizado ou um modpack).

## 2. Edite o Arquivo de Configuração
- **Abra o arquivo:** Use qualquer editor de texto simples (como o Bloco de Notas no Windows ou o TextEdit no macOS) para abrir `iceandfire-client.toml`.
- **Encontre a configuração:** Role até encontrar uma opção relacionada ao menu principal personalizado. Ela pode estar comentada e parecer algo assim:
  ```toml
  # Se deve exibir o dragão no menu principal ou não [padrão: true]
  B:"Custom main menu"=true
  ```
- **Altere o valor:** Defina essa opção como **false** alterando a linha para:
  ```toml
  B:"Custom main menu"=false
  ```
  Essa alteração instrui o mod a não renderizar seu menu principal personalizado (geralmente com o dragão ou outros visuais temáticos).

## 3. Salve e Reinicie
- **Salve o arquivo:** Depois de fazer a alteração, salve o arquivo.
- **Reinicie o Minecraft:** Feche e abra o Minecraft novamente para que as mudanças tenham efeito. Quando o jogo carregar, ele deve usar o menu principal padrão em vez do personalizado do mod.

## Dicas adicionais
- **Confirme que está editando o arquivo correto:** Pode haver um arquivo de configuração comum separado, então certifique-se de estar editando **`iceandfire-client.toml`** (a configuração específica do cliente, e não a comum).
- **Faça um backup antes:** É sempre uma boa ideia fazer uma cópia de segurança do arquivo de configuração original antes de modificá-lo.
- **Modpacks:** Se você estiver usando um modpack, o arquivo de configuração pode estar dentro da estrutura de pastas do pacote, mas o princípio continua o mesmo.

Esse método foi confirmado por usuários da comunidade — por exemplo, vários usuários nos fóruns do Feed The Beast mencionaram que encontrar e alterar a opção `"Custom main menu"` em **`iceandfire-client.toml`** resolveu o problema. (Veja a discussão em que um usuário observou: “defina o config do ice and fire para não exibi-lo em iceandfire-client.toml” e que o arquivo fica na pasta config.) citeturn0search1

Seguindo esses passos, você deve desativar o menu principal personalizado fornecido pelo mod, permitindo usar o fundo do menu principal do seu pacote de texturas.
