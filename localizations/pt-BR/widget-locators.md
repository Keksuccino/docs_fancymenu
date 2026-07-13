---
title: Localizadores de Widgets
description: O que são localizadores de widgets e como encontrá-los.
---
# Localizadores de Widgets

Os localizadores de widgets são usados para apontar para um widget Vanilla/mod específico (botão, slider, campo de entrada de texto) em um menu, o que é necessário para alguns recursos do FancyMenu que precisam interagir com um widget de alguma forma.

# Obtendo o Localizador de um Widget

Há duas maneiras de obter o localizador de um widget Vanilla/mod.

A primeira é ativar a **sobreposição de depuração** no menu que contém o widget, pressionando **CTRL + ALT + D**, e então **clicar com o botão direito no widget**, o que abrirá um menu de contexto com uma opção para copiar o localizador para a área de transferência.

A segunda é abrir o **editor de layout** do menu que contém o widget e então **clicar com o botão direito no elemento do widget**, o que também abrirá um menu de contexto com uma opção para copiar o localizador para a área de transferência.

>[!WARNING]
>Se você **não conseguir clicar com o botão direito** no widget pela sobreposição de depuração, ou ele **não aparecer** no editor de layout, provavelmente ele não está visível para o FancyMenu, o que significa que nesse caso ele não possui um localizador. Isso acontece principalmente com botões de mods que são adicionados aos menus de maneiras incomuns.
