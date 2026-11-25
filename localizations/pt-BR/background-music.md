---
title: Música de fundo dos menus
description: Personalize a música que toca nos menus.
sourceBlobSha: 46d219f5573b915991f23082cfbc42e6ed11d132
---

# Música de fundo dos menus

O FancyMenu pode desativar a música dos menus do Vanilla, reproduzir uma lista global de faixas ou usar [elementos de áudio](/elements#audio) para reproduzir músicas específicas de cada layout.

# Música global dos menus

Abra [**Personalizações globais**](/global-customizations) em **Personalização -> Personalizações globais**, fora do editor de layout.

Use estas opções:

- **Reproduzir música dos menus do Vanilla** ativa ou desativa globalmente a música dos menus do Vanilla.
- **Faixas de música personalizadas dos menus** gerencia a lista global de faixas substitutas.

> [!IMPORTANT]
> As faixas personalizadas globais só tocam quando nenhum mundo está carregado, como na tela inicial. Para reproduzir áudio nos menus dentro de um mundo, use um elemento [**Áudio**](/elements#audio).

As faixas globais usam o canal de som Música. A primeira faixa começa a tocar após cerca de cinco segundos; as seguintes começam após um intervalo aleatório de aproximadamente um a trinta segundos. A seleção é aleatória e evita repetir imediatamente a faixa anterior quando há mais de uma faixa configurada.

# Controle de música por tela

Adicione um elemento [**Controlador de música**](/elements#music-controller) a um layout para controlar a música do Vanilla naquela tela:

1. Clique com o botão direito no plano de fundo do editor.
2. Selecione **Novo elemento -> Controlador de música**.
3. Configure separadamente a música dos menus e a música do mundo.

O elemento oferece suporte a [requisitos de carregamento](/conditions).

Desativar a música dos menus com um Controlador de música também impede que a lista global de faixas personalizadas toque nessa tela.

# Música personalizada com elementos de áudio

Use um elemento [**Áudio**](/elements#audio) quando precisar de:

- Músicas diferentes em telas diferentes.
- Música em telas dentro de um mundo.
- Requisitos de layout, listas de reprodução ordenadas, opções de reprodução aleatória, controle de volume ou de canal.

Coloque um [elemento Áudio](/elements#audio) em um [Layout universal](/universal-layouts) para manter o mesmo reprodutor ativo nas telas compatíveis que carregam esse layout. A personalização de tela precisa estar ativada em cada tela comum em que o layout universal deve ser aplicado.
