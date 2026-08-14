---
title: Layouts Universais
description: Aplique um layout a várias telas compatíveis.
---
# Layouts Universais

Um Layout Universal é considerado para toda tela compatível que tenha a personalização de tela ativada. Ele não se aplica a telas [bloqueadas](./incompatibility-list#screens-where-customization-is-intentionally-disabled) ou excluídas de outra forma.

Use Layouts Universais para elementos compartilhados, como logos, navegação, sobreposições ou [elementos de Áudio](./elements#audio) que devam permanecer em várias telas.

# Criando um

1. Abra uma tela compatível e exiba a barra de menu do FancyMenu.
2. Selecione **Layouts -> Novo -> Para Todas as Telas [Universal]**.
3. Adicione e configure os elementos.
4. Salve o layout.

As telas comuns ainda exigem que **Personalização da Tela Atual** esteja ativada. Não existe um botão global para ativar tudo porque telas de mods não compatíveis podem quebrar quando personalizadas.

# Limitando Telas

Abra as configurações do Layout Universal no menu de contexto do fundo do editor.

- **Whitelist:** o layout se aplica somente aos identificadores de tela listados.
- **Blacklist:** o layout se aplica a toda tela elegível, exceto aos identificadores listados.

Use **Personalização -> Copiar Identificador da Tela Atual** para copiar um [identificador de tela](./screen-identifiers).

Você também pode adicionar [requisitos para todo o layout](./conditions#layout-wide-requirements) para controlar quando o layout se aplica.

# Ordem dos Layouts

Layouts Universais elegíveis e layouts específicos da tela são combinados e empilhados por **Índice do Layout**. Índices mais baixos são aplicados primeiro; configurações empilháveis posteriores podem substituir as anteriores. No mesmo índice, Layouts Universais são coletados antes dos layouts específicos da tela.
