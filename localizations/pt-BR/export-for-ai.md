---
title: Exportar para IA
description: >-
  Transforme partes da sua configuração do FancyMenu em texto para assistentes
  de IA, como a Alice, e receba ajuda mais rapidamente.
sourceBlobSha: 37ce2fdd6cf8d770ca3f6f31528ac6076fe46922
---
# Exportar para IA

**Exportar para IA** transforma uma parte da sua configuração do FancyMenu em texto preparado para assistentes de IA, como a Alice, o bot de ajuda do [Discord do FancyMenu](https://discord.gg/rhayah27GC). Cole o texto no seu chat para que a IA veja exatamente como tudo está configurado, em vez de tentar adivinhar.

<img width="800" alt="Uma publicação de suporte no Discord em que a Alice pede uma exportação, encontra o problema e ajuda o jogador a corrigir o botão" src="https://raw.githubusercontent.com/Keksuccino/docs_fancymenu/refs/heads/wiki-2026/assets/export_for_ai_chat.gif?raw=true">

# Por que esse recurso existe

Uma captura de tela mostra a aparência de algo, mas não como está configurado. Descrever um script de ação ou um requisito manualmente leva tempo, e o detalhe mais importante muitas vezes acaba se perdendo no caminho.

Uma exportação contém tudo de que a IA precisa:

- Cada configuração, ação, requisito e valor do que você exportou.
- As versões do FancyMenu, do Minecraft, do carregador de mods, do Java e do sistema.
- Breves explicações sobre como o FancyMenu funciona, para que a IA interprete tudo corretamente.

As exportações são sempre em inglês, independentemente do idioma em que você joga. O nome da sua conta nos caminhos dos arquivos é substituído por `<user>`, para que você possa compartilhar exportações em chats públicos.

# Quando usar

- Algo não funciona como deveria, como um botão que não faz nada ou um elemento que nunca aparece.
- O FancyMenu exibe um erro ou aviso.
- Você quer ajuda para criar algo, como um script de ação, um requisito ou um menu inteiro.
- Você quer saber o que é possível fazer no seu jogo. **Tudo o que o FancyMenu pode fazer** lista todos os elementos, planos de fundo, ações, requisitos, espaços reservados e ouvintes que você tem, inclusive os de complementos.

Exporte apenas o que tem a ver com sua dúvida, como o botão que não funciona. Exportações menores ajudam a IA a manter o foco. Depois, diga o que você esperava que acontecesse e o que aconteceu de fato.

# Como exportar

Cada opção abaixo abre um pequeno menu:

- **Copiar para a área de transferência** copia a exportação para que você possa colá-la no chat com `Ctrl + V` (`Cmd + V` no macOS).
- **Salvar como arquivo** salva a exportação como um arquivo Markdown em `<game-directory>/fancymenu_data/ai_exports/` e abre essa pasta para que você possa arrastar o arquivo para o chat. Use essa opção para exportações grandes demais para uma mensagem de chat.

As exportações do editor de layouts e das janelas de ouvintes e agendadores incluem as alterações que você ainda não salvou.

# Onde exportar

## Barra de menu

| O que é exportado | Onde encontrar |
|---|---|
| A tela atual, com seus componentes e o que o FancyMenu faz nela | **barra de menu -> Personalização -> Exportar tela atual para IA** |
| Um layout | **barra de menu -> Personalização -> Layouts**, escolha o layout e depois **Exportar layout para IA** |
| Informações do jogo, do hardware e dos mods, além dos recursos que o FancyMenu pode usar, como suporte a vídeo e navegador | **barra de menu -> Ajuda -> Exportar para IA -> Informações do sistema** |
| Todas as configurações do FancyMenu, incluindo as [personalizações globais](/global-customizations) | **barra de menu -> Ajuda -> Exportar para IA -> Configurações do FancyMenu** |
| Todas as [variáveis](/variables) | **barra de menu -> Ajuda -> Exportar para IA -> Todas as variáveis** |
| Todos os [ouvintes](/listeners) | **barra de menu -> Ajuda -> Exportar para IA -> Todos os ouvintes** |
| Todos os [agendadores](/schedulers) | **barra de menu -> Ajuda -> Exportar para IA -> Todos os agendadores** |
| Todas as [GUIs personalizadas](/custom-guis) | **barra de menu -> Ajuda -> Exportar para IA -> GUIs personalizadas** |
| Todos os [perfis](/profiles) | **barra de menu -> Ajuda -> Exportar para IA -> Perfis** |
| Todos os elementos, planos de fundo, ações, requisitos, espaços reservados e ouvintes do seu jogo | **barra de menu -> Ajuda -> Exportar para IA -> Tudo o que o FancyMenu pode fazer** |

## Editor de layouts

| O que é exportado | Onde encontrar |
|---|---|
| O layout que você está editando | **Layout -> Exportar layout para IA** na barra de menu do editor |
| Outro layout da tela | **Layout -> Abrir** na barra de menu do editor, escolha o layout e depois **Exportar layout para IA** |
| Um elemento | Clique com o botão direito no elemento e depois em **Exportar para IA** |
| Todos os elementos selecionados | **Editar -> Exportar elementos selecionados para IA** na barra de menu do editor |
| Um [plano de fundo de menu](/menu-backgrounds) | Clique com o botão direito no plano de fundo do editor, depois em **Planos de fundo de menu**, escolha o plano de fundo e, em seguida, **Exportar para IA** |
| Uma [sobreposição decorativa](/decoration-overlays) | Clique com o botão direito no plano de fundo do editor, depois em **Sobreposições decorativas**, escolha a sobreposição e, em seguida, **Exportar para IA** |

## Editores e janelas

| O que é exportado | Onde encontrar |
|---|---|
| Um [script de ação](/action-scripts) | Clique com o botão direito no editor de scripts de ação e depois em **Exportar script de ação para IA** |
| [Requisitos](/conditions) | Clique com o botão direito na janela **Gerenciar requisitos** e depois em **Exportar requisitos para IA** |
| Um texto, como o conteúdo de um elemento de texto | Clique com o botão direito no editor de texto e depois em **Exportar texto para IA** |
| Uma variável ou todas as variáveis | Abra **barra de menu -> Personalização -> Gerenciar variáveis**, clique com o botão direito e depois em **Exportar variável para IA** ou **Exportar todas as variáveis para IA** |
| Um ouvinte ou todos os ouvintes | Abra **barra de menu -> Personalização -> Gerenciar ouvintes**, clique em **Exportar para IA** e depois em **Ouvinte selecionado** ou **Todos os ouvintes** |
| Um agendador ou todos os agendadores | Abra **barra de menu -> Personalização -> Gerenciar agendadores**, clique em **Exportar para IA** e depois em **Agendador selecionado** ou **Todos os agendadores** |

## Erros e avisos

Quando o FancyMenu exibir um erro ou aviso, clique em **Exportar para IA**, ao lado de **OK**, para exportar a mensagem.

## Servidores

A configuração de [FMData](/fm-data) de um servidor, com os ouvintes do servidor e os dados de boas-vindas, pode ser exportada com um comando. É necessário ter nível de permissão 2, assim como para todos os comandos `/fmdata`.

```mcfunction
/fmdata export_for_ai copy
/fmdata export_for_ai file
```

- `copy` envia uma mensagem no chat. Clique nela para copiar a exportação. No console do servidor, a exportação inteira é exibida.
- `file` salva a exportação no servidor, em `fancymenu_data/ai_exports/`. Use essa opção quando a exportação for grande demais para o chat.
