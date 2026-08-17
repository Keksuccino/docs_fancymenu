---
title: Variáveis
description: Como criar e usar variáveis.
---

# Variáveis no FancyMenu

As variáveis armazenam valores de texto que layouts, ações, placeholders, requisitos, listeners, agendadores e GUIs personalizadas podem reutilizar.

## Criando variáveis

Para criar uma variável no FancyMenu:

1. Certifique-se de que você não está no Editor de Layouts.
2. Clique na barra de menu na parte superior da tela.
3. Acesse **Customization -> Variables -> Manage Variables**.
4. Na tela "Manage Variables" exibida, clique no botão **Add Variable**.
5. Digite um nome para sua nova variável e clique em **OK**.

Pronto! Sua variável está pronta para ser usada. Você pode vê-la listada na tela "Manage Variables".

A janela Manage Variables oferece um menu de contexto acessível com o botão direito do mouse, navegação pelo teclado, copiar/colar, desfazer/refazer, pesquisa ao digitar, **Delete** para excluir e **Ctrl/Command + S** para salvar.

## Definindo valores de variáveis

Uma variável vazia não é muito útil por si só. Para fazer as variáveis trabalharem a seu favor, você precisa inserir dados nelas. No FancyMenu, isso é chamado de "definir o valor da variável".

Há duas maneiras principais de definir o valor de uma variável:

1. Na tela "Manage Variables", encontre a variável na lista, clique nela e depois clique em **Set Value**. Digite os dados que deseja armazenar.

2. Ao personalizar seu menu, use a [ação **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) em um elemento [Button](./elements#button), [Slider](./elements#slider) ou [Ticker](./elements#ticker).

Por exemplo, crie uma variável chamada `clicks` e adicione a [ação **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) a um botão:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Veja como isso funciona:
1. O [placeholder **Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) recupera o valor atual da variável `clicks`.
2. O placeholder [**Calculator**](./placeholders#calculator-calc) pega esse valor e adiciona 1 a ele.
3. O resultado é armazenado novamente em `clicks` usando a [ação **Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable).

Assim, cada vez que o botão é clicado, a variável `clicks` é incrementada em 1, contando efetivamente o número total de cliques.

## Usando variáveis

Agora que você tem variáveis armazenando dados, pode usar esses dados em diferentes partes da personalização do seu menu:

* [**Requisitos de carregamento**](./conditions): verifique o valor de uma variável para controlar quando os elementos aparecem. Por exemplo, mostre um elemento quando `clicks` for maior que 5 combinando [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) com o placeholder [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

* **Placeholders**: insira uma variável em um texto com o placeholder [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable), por exemplo `{"placeholder":"getvariable","values":{"name":"clicks"}}`.

* **Placeholders aninhados**: você pode usar o placeholder [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) dentro do placeholder [**Calculator**](./placeholders#calculator-calc).

* **Ações**: as variáveis podem criar comportamentos dinâmicos:
  - Use uma instrução **IF** em um [script de ação](./action-scripts#what-are-statements) com [**Is Number**](./conditions#is-number-fancymenu_visibility_requirement_is_number) e o placeholder [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).
  - Combine o placeholder [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) com [**Copy Text to Clipboard**](./action-scripts#copy-text-to-clipboard-copytoclipboard).
  - Use variáveis em [**Open Screen or Custom GUI**](./action-scripts#open-screen-or-custom-gui-opengui) para selecionar uma tela com base no progresso ou nas preferências armazenadas.

## Exemplos de variáveis

Aqui estão alguns exemplos para inspirar o uso das suas próprias variáveis:

1. **Pontuação máxima**: crie uma variável `highscore` e um botão que a defina como a pontuação atual do jogador caso ela seja maior que o valor existente. Exiba-a com o placeholder [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable).

2. **Seletor de dificuldade**: crie variáveis para diferentes níveis de dificuldade do jogo, como `easy`, `medium` e `hard`. Use botões para definir a variável de dificuldade e mostre/oculte elementos com base na dificuldade selecionada.

3. **Progresso do tutorial**: adicione variáveis para acompanhar o progresso do jogador em um tutorial, como `tutorial_step`. Incremente a variável conforme ele conclui cada etapa e use requisitos de carregamento para revelar gradualmente mais partes do menu.

## Persistência, escopo e armazenamento

As variáveis são compartilhadas em toda a instância atual do Minecraft. Elas não são separadas por layout, mundo, servidor ou jogador.

Os valores são salvos imediatamente em `<game-directory>/config/fancymenu/user_variables.db` e persistem após reinicializações.

- **Reset on Launch** esvazia essa variável na próxima vez que o jogo for iniciado.
- [**Clear All Variables**](./action-scripts#clear-all-variables-fm-variable-clear_variables) remove todos os valores de variáveis armazenados.
- Os nomes diferenciam maiúsculas de minúsculas. Use nomes simples e exclusivos, como `tutorial_step`.

O placeholder [**Get Stored Variable**](./placeholders#get-variable-value-fm-variable-getvariable) retorna `0` quando a variável nomeada não existe ou quando seu valor armazenado está vazio. Esse valor alternativo é importante em comparações e expressões de calculadora.

A ação [**Set Variable Value**](./action-scripts#set-variable-value-fm-variable-set_variable) usa `variable_name:variable_value` e divide o conteúdo no primeiro caractere de dois-pontos, portanto o valor pode conter outros dois-pontos.

Não armazene senhas, tokens ou outros segredos nas variáveis do FancyMenu. Elas são dados de configuração legíveis.
