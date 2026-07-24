---
title: Cursor Personalizado
description: Como fazer menus usarem um cursor de mouse personalizado.
---
# Cursor Personalizado

Adicione um elemento [**Cursor**](./elements#cursor) a um layout para substituir o cursor do sistema nessa tela:

1. Selecione **Novo Elemento -> Cursor**.
2. Defina uma textura PNG com cor RGBA.
3. Defina **Hotspot X** e **Hotspot Y** para o pixel da textura onde os cliques devem ocorrer.
4. Ative a pré-visualização no editor quando quiser verificar o cursor أثناء edição.
5. Use um [Layout Universal](./universal-layouts) quando o mesmo cursor deva aparecer em várias telas compatíveis.

Texturas de cursor pequenas, como `32×32` ou `64×64`, são recomendadas. A aparência e o comportamento do cursor podem variar de acordo com o sistema operacional.
