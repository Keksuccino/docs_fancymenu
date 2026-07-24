---
title: GUIs Personalizadas
description: Crie e configure novas telas de GUI.
---
# GUIs Personalizadas

GUIs Personalizadas são novas telas que você pode preencher com [elementos](./elements) do FancyMenu.

> [!CAUTION]
> GUIs Personalizadas podem executar ações. Importe-as apenas de fontes em que você confia.

# Criando uma GUI Personalizada

1. Abra **Personalização -> GUIs Personalizadas -> Gerenciar GUIs Personalizadas**.
2. Selecione **Nova GUI**.
3. Insira um identificador e configure as opções da tela.
4. Selecione **Concluído** e, em seguida, abra a nova GUI pelo gerenciador.
5. Crie e edite seu layout como qualquer outra tela.

Os identificadores podem usar letras minúsculas, números, `.`, `_` e `-`. Eles não podem conter espaços e devem ser exclusivos. Identificadores vazios, inválidos ou duplicados não podem ser salvos.

As GUIs Personalizadas sempre têm a personalização de tela ativada; a opção de alternância de personalização não pode ser desativada.

# Configurações da Tela

| Configuração | Comportamento |
|---|---|
| Permitir ESC | Permite que a tecla Escape feche a GUI e retorne à tela pai |
| Pausar Jogo/Mundo | Pausa o modo singleplayer enquanto a GUI estiver aberta |
| Renderizar Fundo do Mundo | Mostra o mundo carregado atrás da GUI |
| Sobreposição do Fundo do Mundo | Adiciona a sobreposição padrão de blur/escurecimento sobre o mundo |
| Modo Pop-up | Mantém a tela pai visível atrás da GUI Personalizada |
| Sobreposição do Fundo do Pop-up | Adiciona blur/tintura sobre a tela pai no Modo Pop-up |

O Modo Pop-up não mescla as duas telas. A GUI Personalizada continua sendo a tela ativa enquanto sua tela pai é renderizada atrás dela. Fechar a GUI Personalizada retorna a essa tela pai quando houver uma.

# Abrindo uma GUI Personalizada

Use o identificador exato da GUI Personalizada com uma destas opções:

- A ação [**Abrir Tela ou GUI Personalizada**](./action-scripts#open-screen-or-custom-gui-opengui).
- O comando [`/openguiscreen`](./commands#openguiscreen).

# Substituindo uma Tela Existente

Uma GUI Personalizada pode substituir uma tela Vanilla ou de mod sempre que essa tela for aberta.

1. Crie a GUI Personalizada de substituição.
2. Abra a tela que você deseja substituir.
3. Ative **Personalização -> Configurações -> Modo Avançado de Personalização**.
4. Selecione **Personalização -> GUIs Personalizadas -> Substituir Atual por GUI Personalizada**.
5. Escolha a GUI Personalizada de substituição.

Gerencie as substituições salvas em **Personalização -> GUIs Personalizadas -> Gerenciar Telas Substituídas**.

Uma substituição ignora a tela original, então teste a navegação dela e quaisquer recursos que dependam do comportamento da tela original.
