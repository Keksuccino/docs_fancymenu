---
title: APNGs
description: Como criar imagens APNG compatíveis com o FancyMenu.
---

# Imagens PNG Animadas

> Para novas animações grandes ou complexas, prefira [arquivos AFMA/FMA](/fma). O FancyMenu 3.9.0 pode usar Watermedia V3 + Watermedia Binaries V3 para uma decodificação de APNG/GIF mais rápida quando disponível, mas o AFMA ainda é o formato de animação preferido do FancyMenu.
{.is-info}


APNGs são uma versão animada de imagens PNG, permitindo ter os mesmos recursos de um GIF, mas com qualidade PNG total e sem perdas!

O FancyMenu tem suporte integrado a APNG, mas ele é um pouco exigente quanto aos APNGs aceitos.
Ele precisa de APNGs **sem compactação** e **não entrelaçados**.

# Criando Animações APNG

Você vai se surpreender com a dificuldade de encontrar um bom editor de APNG, especialmente com opções para desativar a compactação e o entrelaçamento.

Uma ótima opção de editor é o [ScreenToGif](https://www.screentogif.com/), que na verdade é uma ferramenta para gravar GIFs e APNGs da sua tela, mas também é excelente para criar APNGs normais, pulando a parte da gravação e carregando diretamente no editor!

## Abra o Editor

A primeira coisa que você vê ao abrir o [ScreenToGif](https://www.screentogif.com/) é esta tela. Clique em **Editor** aqui.

![screentogif_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/a8d34313-b841-4fb6-bf3a-ff02c39792cb)

## Carregue os Quadros

Agora você precisa dos seus quadros PNG. Arraste e solte-os no editor.

![screentogif_dragndrop](https://github.com/Keksuccino/FancyMenu/assets/35544624/ba4ad4a5-484e-46f1-8efd-90ba764462d8)

## Tempo de Quadro

Para configurar o atraso entre os quadros, selecione o(s) quadro(s) que deseja editar, vá para a aba **Edit** e, na seção **Delay (Duration)**, clique em **Override**.

![screentogif_delay](https://github.com/Keksuccino/FancyMenu/assets/35544624/a5d93139-3192-4090-b243-e5c0fe299963)

## Loop

O comportamento do loop pode ser configurado no menu **Save As**. Veja a próxima etapa para saber como abrir esse menu.

## Exportando o APNG

Agora você está pronto para voltar para a aba **File** e clicar em **Save As**.

No menu de salvamento, certifique-se de:
- Definir o tipo de arquivo como **APNG** (primeira opção; talvez você precise rolar até o topo do menu primeiro)
- Desativar **Detect Unchanged Pixels**

> Você também pode configurar o **comportamento de loop** nesse menu! Desativar **Looped Apng** fará com que o APNG não repita, e ao ativá-lo você pode escolher entre um número específico de repetições ou loop infinito.
{.is-info}

![screentogif_save](https://github.com/Keksuccino/FancyMenu/assets/35544624/954353da-45ed-4df8-9f06-c78a0a469fc8)

## Usando o APNG no FancyMenu

Agora você pode copiar seu arquivo APNG para `/config/fancymenu/assets/`. Depois disso, você poderá usá-lo em quase tudo que aceite imagens.

> É **muito importante** que o nome do arquivo APNG termine com `.apng`!
> O FancyMenu não conseguirá identificar a imagem como APNG se ela não terminar com `.apng`.
{.is-warning}

![screentogif_use_apng](https://github.com/Keksuccino/FancyMenu/assets/35544624/2322da62-4013-451e-9a8b-3df0bf92df54)
