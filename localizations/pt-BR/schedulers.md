---
title: Agendadores
description: 'Execute scripts de ação do FancyMenu em um timer, até mesmo em segundo plano.'
---

# Agendadores

Os agendadores executam um script de ação em um timer.

Eles são globais (não vinculados a uma tela específica), então podem continuar funcionando mesmo quando nenhuma GUI estiver aberta.

Use agendadores quando quiser automação ao longo do tempo, em vez de uma ação única.
Eles são úteis para tarefas repetidas, tarefas com atraso e lógica em segundo plano.

Exemplos comuns:

- Atualizar variáveis ou elementos de texto a cada poucos segundos (por exemplo, um relógio/status personalizado).
- Executar verificações periódicas e disparar ações quando as condições forem atendidas.
- Iniciar efeitos de menu, sons ou outro comportamento scriptado em um loop temporizado.
- Atrasar uma ação e executá-la mais tarde sem precisar manter uma tela aberta.

# Onde Encontrá-los

Abra a **barra de menu** do FancyMenu enquanto **não** estiver no editor de layout e depois vá em **Customization -> Manage Schedulers**.

# Início Rápido

1. Abra **Customization -> Manage Schedulers**.
2. Clique em **Add Scheduler**.
3. Monte o **Action Script** do agendador (é isso que será executado uma vez a cada tick do agendador).
4. Selecione o agendador e clique em **Edit Settings**.
5. Configure:
   - **Scheduler ID** (nome único do agendador; usado pelas ações Start/Stop e pelos requisitos; permitido: `a-z`, `0-9`, `.`, `_`, `-`)
   - **Start Delay (ms)** (tempo de espera antes de o primeiro tick ser executado)
   - **Tick Delay (ms)** (tempo de espera entre ticks; `0` = a cada tick do jogo)
   - **Ticks to Run** (quantidade de ticks a executar antes de parar automaticamente; `0` = permanente)
   - **Start on Launch** (inicia automaticamente este agendador quando o FancyMenu carregar)
6. Use **Start Now** para executá-lo imediatamente.
7. Use **Stop Now** para interrompê-lo.

# Controlar e Observar Agendadores

Há ações e requisitos para controlar agendadores e verificar se eles estão em execução.

## Ações

- **Start Scheduler** recebe o ID do agendador e o inicia, se ainda não estiver em execução.
- **Stop Scheduler** também recebe o ID do agendador e o interrompe.

## Requisito

Para verificar se um agendador está em execução no momento, use o requisito **Scheduler Is Running**, que recebe o ID do agendador.

# Dicas

1. Use IDs claros como `hud_update`, `menu_animation`, `music_fade`.
2. Comece com um tick delay maior (por exemplo `200`-`1000` ms) e reduza-o apenas se necessário, para economizar desempenho.
3. Na lista de agendadores, clique com o botão direito em um agendador para editar rapidamente suas ações.
4. Na lista de agendadores, clique duas vezes no ID de um agendador para renomeá-lo.
