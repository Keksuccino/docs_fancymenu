---
title: Carregamento Contínuo do Mundo
description: >-
  Use uma visualização recente de um mundo como o próximo plano de fundo de
  carregamento.
---

# Carregamento Contínuo do Mundo

O Carregamento Contínuo do Mundo usa uma visualização recente de um mundo ou servidor como o próximo plano de fundo da tela de carregamento.

Ative-o em [**Customização -> Personalizações Globais**](./global-customizations) -> **Carregamento Contínuo do Mundo**.

# Como Funciona

- O FancyMenu captura periodicamente o quadro atual enquanto você está em um mundo ou servidor monitorado.
- A captura mais recente é salva quando você sai.
- Cada mundo e servidor tem seu próprio nome de arquivo PNG com hash.
- O FancyMenu pré-carrega até cinco capturas recentes de mundos e cinco capturas recentes de servidores.
- Nada é exibido para um destino até que sua primeira captura tenha sido salva.

As capturas são armazenadas em:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

As capturas de tela podem conter qualquer coisa visível no mundo no momento em que forem tiradas. Desativar o Carregamento Contínuo do Mundo interrompe a captura e o uso, mas não exclui os arquivos PNG existentes. Exclua as capturas indesejadas do diretório enquanto o jogo estiver fechado.
