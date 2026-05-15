---
title: Variáveis
description: Como criar e usar variáveis.
---

# Variáveis no FancyMenu

Variáveis são um recurso poderoso no FancyMenu que permite armazenar e reutilizar informações ao longo das suas personalizações de menu. Elas funcionam como contêineres onde você pode colocar diferentes tipos de dados, dar um nome para cada contêiner e depois acessar esses dados mais tarde usando o nome da variável. As variáveis abrem um mundo de possibilidades para criar menus dinâmicos que mudam com base nas condições que você definir.

## Criando Variáveis

Para criar uma variável no FancyMenu:

1. Certifique-se de que você não está atualmente no Editor de Layout.
2. Clique na barra de menu na parte superior da tela.
3. Vá em **Customization -> Variables -> Manage Variables**.
4. Na tela "Manage Variables" que aparecer, clique no botão **Add Variable**.
5. Digite um nome para sua nova variável e clique em **OK**.

Pronto! Sua variável está pronta para uso. Você pode vê-la listada na tela "Manage Variables".

O FancyMenu 3.9.0 reformula a janela Manage Variables. Ações importantes estão disponíveis por meio de um menu de contexto acionado com o botão direito, a lista oferece suporte à navegação por teclado, variáveis podem ser copiadas/coladas, alterações podem ser desfeitas/refeitas, digitar inicia uma pesquisa, **DEL** exclui a variável selecionada e **CTRL + S** confirma a janela.

## Definindo Valores de Variáveis

Uma variável vazia não é muito útil por si só. Para fazer as variáveis funcionarem para você, é preciso colocar dados nelas. No FancyMenu, isso é chamado de "definir o valor da variável".

Existem duas maneiras principais de definir o valor de uma variável:

1. Na tela "Manage Variables", encontre a variável na lista, clique nela e depois clique em **Set Value**. Digite os dados que você quer armazenar.

2. أثناء personalizar seu menu, use a ação **Set Variable** em um elemento Button, Slider ou Ticker. Com essa ação, você especifica o nome da variável e o valor a ser armazenado nela. Quando alguém, por exemplo, clica em um botão com essa ação, a variável será atualizada com o novo valor.

Por exemplo, vamos supor que você crie uma variável chamada `clicks` para contar quantas vezes um botão é pressionado. Você adicionaria a ação **Set Variable** ao botão e usaria um placeholder no valor da ação para incrementar a contagem de cliques a cada vez, assim:

```
clicks:{"placeholder":"calc","values":{"expression":"{"placeholder":"getvariable","values":{"name":"clicks"}} + 1"}}
```

Veja como isso funciona:
1. O placeholder **Get Stored Variable** recupera o valor atual da variável `clicks`.
2. O placeholder **Calculator** pega esse valor e adiciona 1 a ele.
3. O resultado é então armazenado de volta na variável `clicks` usando a ação **Set Variable**.

Assim, toda vez que o botão é clicado, a variável `clicks` será incrementada em 1, contando efetivamente o total de cliques.

## Usando Variáveis

Agora que você tem variáveis armazenando dados, pode usar essas informações em diferentes partes da personalização do seu menu:

* **Requisitos de carregamento**: Você pode verificar o valor de uma variável em um requisito de carregamento para controlar quando certos عناصر do menu aparecem. Por exemplo, você pode fazer um elemento aparecer somente se a variável `clicks` for maior que 5 usando uma combinação do requisito **Is Number** e do placeholder **Get Stored Variable**.

* **Placeholders**: Variáveis podem ser inseridas em textos usando o placeholder **Get Stored Variable**. Se você tiver um elemento de texto, poderá usar `{"placeholder":"getvariable","values":{"name":"clicks"}}` para exibir o valor atual da variável "clicks".

* **Placeholders aninhados**: Você também pode usar variáveis dentro de outros placeholders! O exemplo de contagem de cliques acima demonstrou isso usando o placeholder **Get Stored Variable** dentro do placeholder **Calculator**.

* **Ações**: Variáveis podem ser usadas em ações para criar comportamentos dinâmicos com base nos valores das variáveis. Aqui estão alguns exemplos:
    - Use uma instrução **IF** em um script de ação para verificar o valor de uma variável usando uma combinação do requisito de carregamento **Is Number** e da ação **Get Stored Variable**, e execute ações diferentes com base no resultado. Por exemplo, você pode ter um botão que diga "Você me clicou X vezes!" e usar um bloco IF para mostrar uma mensagem especial se o número de cliques for maior que 10.
    - Combine o placeholder **Get Stored Variable** com a ação **Copy to Clipboard** para permitir que os usuários copiem o valor de uma variável para a área de transferência.
    - Use variáveis na ação **Open GUI** para carregar telas diferentes com base no progresso ou nas preferências do usuário, que você acompanha com variáveis.

## Exemplos de Variáveis

Aqui estão alguns exemplos para inspirar o uso das suas próprias variáveis:

1. **Pontuação máxima**: Crie uma variável `highscore` e um botão que a defina como a pontuação atual do jogador se ela for maior que o valor existente. Exiba a pontuação máxima no menu usando o placeholder **Get Stored Variable**.

2. **Seletor de dificuldade**: Crie variáveis para diferentes dificuldades do jogo, como `easy`, `medium` e `hard`. Use botões para definir a variável de dificuldade e mostre/oculte elementos com base na dificuldade selecionada.

3. **Progresso do tutorial**: Adicione variáveis para acompanhar o progresso do jogador em um tutorial, como `tutorial_step`. Incrementa a variável à medida que cada etapa é concluída e use requisitos de carregamento para revelar gradualmente mais partes do menu.

Variáveis combinadas com os outros recursos do FancyMenu oferecem uma flexibilidade incrível para criar menus adaptados às ações e preferências de cada jogador. Experimente diferentes configurações de variáveis para desbloquear todo o potencial das suas personalizações de menu!
