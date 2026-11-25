---
title: Modelos de Botões e Controles Deslizantes
description: >-
  Aplique a todos os botões ou controles deslizantes de uma tela as texturas, os
  sons e o estilo de rótulo de um botão modelo.
sourceBlobSha: 805a2ae3221a644c78cd5eafebc5579bc8d60815
---

# Modelos de Botões e Controles Deslizantes

Um modelo é um [elemento Botão](/elements#button) que aplica sua aparência a todos os outros botões ou controles deslizantes da tela, tanto os padrão quanto os criados por você. Altere o modelo e todos eles serão alterados junto com ele.

> [!TIP]
> Para manter a mesma aparência em todos os menus do jogo, use [Personalizações Globais](/global-customizations). Os modelos são para uma única tela ou para todas as telas carregadas por um [layout universal](/universal-layouts).

# Criar um Modelo

1. Adicione um elemento Botão ao layout.
2. Clique nele com o botão direito, abra **Configurações do Modelo** e ative **Modo de Modelo**.
3. Em **Compartilhar Configurações Com**, selecione **Botões** ou **Controles Deslizantes**.
4. Defina as texturas, os sons e as configurações de rótulo desejados para o modelo, como faria com qualquer outro botão. Quando **Controles Deslizantes** estiver selecionado, as configurações de textura serão as dos controles deslizantes.

O modelo não aparece fora do editor, então coloque-o onde não atrapalhe. No editor, um modelo para controles deslizantes tem a aparência de um controle deslizante.

# O Que os Modelos Compartilham

## Sempre

- As texturas do botão (ou as texturas dos controles deslizantes), com as configurações de [divisão em nove partes](/nine-slicing-and-tiling).
- Os sons de passar o cursor, tirar o cursor e clicar.

Enquanto um modelo estiver ativo, os botões usarão as texturas e os sons dele, em vez dos próprios. Se o modelo não tiver texturas, os botões também não usarão as próprias texturas.

## Ao Ativar

Ative estas opções em **Configurações do Modelo** do modelo:

| Configuração | O que os botões recebem do modelo |
|---|---|
| **Compartilhar Rótulo no Modo de Modelo** | O **Rótulo** e o **Rótulo ao Passar o Cursor** do modelo, além de todo o estilo do rótulo: **Alinhamento do Rótulo**, **Escala do Rótulo**, **Cor Base do Rótulo**, **Cor do Rótulo ao Passar o Cursor**, **Sombra do Rótulo** e **Sublinhar Rótulo ao Passar o Cursor**. |
| **Compartilhar Posição X no Modo de Modelo** e **Compartilhar Posição Y no Modo de Modelo** | A posição do modelo. Os botões padrão só se movem quando o **Ponto de Ancoragem** é diferente de **Padrão (Original)**. |
| **Compartilhar Opacidade no Modo de Modelo** | A opacidade do modelo. |

## Alinhamento de Rótulo para Todos os Botões

Com **Compartilhar Rótulo no Modo de Modelo**, todos os botões também recebem o texto do modelo. Portanto, essa opção serve para telas em que todos os botões devem ter o mesmo texto.

Para alinhar apenas os rótulos e manter os textos:

- Em uma tela, selecione os botões com `Ctrl` + clique (consulte [Selecionar](/layout-editor#selecting)), clique com o botão direito em um deles e defina **Alinhamento do Rótulo** uma única vez para todos.
- Para todos os menus, use **Alinhamento do Rótulo** em [Personalizações Globais](/global-customizations#labels).

# É Bom Saber

- Somente elementos Botão podem ser modelos, mas eles funcionam com botões e controles deslizantes padrão ou personalizados.
- Uma tela pode ter um modelo para botões e outro para controles deslizantes ao mesmo tempo. Se houver mais de um modelo do mesmo tipo, apenas um deles funcionará.
- Um modelo só funciona enquanto estiver visível. Com [requisitos](/element-visibility) no modelo, você pode ativá-lo e desativá-lo.
