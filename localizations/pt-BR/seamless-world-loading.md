---
title: Carregamento Contínuo de Mundos
description: >-
  Use uma visualização recente de um mundo como próximo plano de fundo de
  carregamento.
sourceBlobSha: 2b8e960b11ea70fca33b317a7c14815ce5844e13
---

# Carregamento Contínuo de Mundos

O Carregamento Contínuo de Mundos usa uma visualização recente de um mundo ou servidor como próximo plano de fundo da tela de carregamento.

Ative-o em [**Personalização -> Personalizações Globais**](/global-customizations) -> **Carregamento Contínuo de Mundos**.

# Como funciona

- O FancyMenu captura periodicamente o quadro atual enquanto você está em um mundo ou servidor monitorado.
- A captura mais recente é salva quando você sai.
- Cada mundo e servidor tem seu próprio arquivo PNG com nome hash.
- O FancyMenu pré-carrega até cinco capturas recentes de mundos e cinco capturas recentes de servidores.
- Nada é exibido para um destino até que sua primeira captura seja salva.

As capturas são armazenadas em:

```text
<game-directory>/fancymenu_data/seamless_world_loading/
```

As capturas de tela podem conter qualquer coisa visível no mundo no momento da captura. Desativar o Carregamento Contínuo de Mundos interrompe as capturas e seu uso, mas não exclui os arquivos PNG existentes. Com o jogo fechado, exclua do diretório as capturas que não quiser manter.
