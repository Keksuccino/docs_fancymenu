---
title: Música de Fundo do Menu
description: Personalize a música tocada nos menus.
---
# Música de Fundo do Menu

O FancyMenu pode desativar a música de menu da Vanilla, reproduzir uma lista global de faixas ou usar [elementos de Áudio](./elements#audio) para música específica de cada layout.

# Música Global do Menu

Abra [**Personalizações Globais**](./global-customizations) em **Customização -> Personalizações Globais** fora do editor de layout.

Use estas configurações:

- **Reproduzir Música de Menu da Vanilla** ativa ou desativa globalmente a música de menu da Vanilla.
- **Faixas de Música Personalizada do Menu** gerencia a lista global de faixas substitutas.

> [!IMPORTANT]
> As faixas personalizadas globais do menu só tocam quando nenhum mundo está carregado, como na tela de título. Use um elemento [**Áudio**](./elements#audio) para áudio de menu dentro do mundo.

As faixas globais usam o canal de som Music. A primeira faixa começa após cerca de cinco segundos; as faixas seguintes usam um atraso aleatório de cerca de um a trinta segundos. A seleção é aleatória e evita repetir imediatamente a faixa anterior quando há mais de uma faixa configurada.

# Controle de Música por Tela

Adicione um elemento [**Controlador de Música**](./elements#music-controller) a um layout para controlar a música da Vanilla para aquela tela:

1. Clique com o botão direito no fundo do editor.
2. Selecione **Novo Elemento -> Controlador de Música**.
3. Configure separadamente Música do Menu e Música do Mundo.

O elemento suporta [requisitos de carregamento](./conditions).

Desativar a música do menu com um Controlador de Música também impede que a lista global de faixas personalizadas do menu toque naquela tela.

# Música Personalizada com Elementos de Áudio

Use um elemento [**Áudio**](./elements#audio) quando você precisar de:

- Música diferente em telas diferentes.
- Música em telas dentro do mundo.
- Requisitos de layout, playlists ordenadas, configurações de embaralhamento, volume ou controle de canal.

Coloque um elemento [Áudio](./elements#audio) em um [Layout Universal](./universal-layouts) para manter o mesmo player ativo entre as telas suportadas que carregam esse layout. A personalização de tela deve estar ativada em cada tela comum na qual o layout universal deve ser aplicado.
