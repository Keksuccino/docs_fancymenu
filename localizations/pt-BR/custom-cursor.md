---
title: Cursor personalizado
description: Como fazer com que os menus usem um cursor de mouse personalizado.
sourceBlobSha: 6ccd4932bed99ab10c094adffd503bd0a44d9edd
---

# Cursor de mouse personalizado

Adicione um [elemento **Cursor**](/elements#cursor) a um layout para substituir o cursor do sistema nessa tela:

1. Selecione **Novo elemento -> Cursor**.
2. Defina uma textura PNG com cor RGBA.
3. Defina **Ponto ativo X** e **Ponto ativo Y** para indicar o pixel da textura em que os cliques devem ocorrer.
4. Ative a prévia do editor quando quiser conferir o cursor durante a edição.
5. Use um [Layout universal](/universal-layouts) quando quiser que o mesmo cursor apareça em várias telas compatíveis.

Recomendamos usar texturas pequenas para o cursor, como `32×32` ou `64×64`. A aparência e o comportamento do cursor podem variar de acordo com o sistema operacional.
