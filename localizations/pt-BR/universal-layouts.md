---
title: Layouts Universais
description: Aplique um layout a várias telas compatíveis.
sourceBlobSha: 2179fed92c6598b6e5c3ecfea354a4c853bc394b
---

# Layouts Universais

Um Layout Universal é considerado para todas as telas compatíveis que tenham a personalização de tela ativada. Ele não se aplica a telas [bloqueadas](/incompatibility-list#screens-where-customization-is-intentionally-disabled) nem a outras telas excluídas.

Use Layouts Universais para elementos compartilhados, como logotipos, navegação, sobreposições ou [elementos de áudio](/elements#audio) que devem aparecer em várias telas.

# Criar um layout

1. Abra uma tela compatível e exiba a barra de menus do FancyMenu.
2. Selecione **Layouts -> Novo -> Para todas as telas [Universal]**.
3. Adicione e configure elementos.
4. Salve o layout.

Ainda é necessário ativar a **Personalização da Tela Atual** nas telas comuns. Não há uma opção global para ativar tudo, pois a personalização pode causar problemas em telas de mods não compatíveis.

# Limitar telas

Abra as configurações do Layout Universal pelo menu de contexto do plano de fundo do editor.

- **Lista de permissões:** o layout é aplicado somente aos identificadores de tela listados.
- **Lista de bloqueio:** o layout é aplicado a todas as telas elegíveis, exceto aos identificadores listados.

Use **Personalização -> Copiar identificador da tela atual** para copiar um [identificador de tela](/screen-identifiers).

Você também pode adicionar [requisitos para todo o layout](/conditions#layout-wide-requirements) para controlar quando o layout é aplicado.

# Ordem dos layouts

Os Layouts Universais elegíveis e os layouts específicos de tela são combinados e empilhados de acordo com o **Índice do Layout**. Índices menores são aplicados primeiro; configurações empilháveis posteriores podem substituir as anteriores. Quando o índice é igual, os Layouts Universais são reunidos antes dos layouts específicos de tela.
