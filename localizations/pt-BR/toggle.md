---
title: Alternar Partes de Layouts
description: Como alternar partes de layouts com base na entrada do usuário.
---

# Alternar Partes de Layouts

Às vezes é bom ter escolha! Talvez alguns dos seus usuários não gostem de ouvir Rick Astley o tempo todo como música de menu ou queiram uma garota anime diferente e fofinha como fundo do menu.

Bom, isso não é problema! Você pode fazer com que seus usuários ativem/desativem partes dos seus layouts ou alternem entre várias versões dessas partes.

# Ativar/Desativar

Para alternar, por exemplo, a visibilidade de um elemento ao clicar em um botão, você só precisa usar uma variável que seja definida no clique do botão, e o elemento que você quer alternar precisa verificar, em seus requisitos de carregamento, se essa variável tem o valor correto.

## A Variável

A primeira coisa é criar a variável que você vai usar para armazenar o estado de visibilidade do elemento que deseja alternar.

Para adicionar uma nova variável, vá até a aba **Customization** na barra de menu e clique em **Variables -> Manage Variables**, depois adicione uma nova variável com um nome **único**! Certifique-se de usar um nome realmente **único** que ainda não esteja em uso.

Depois de criar a variável, defina o valor dela como `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## O Elemento

O próximo passo é adicionar o elemento que você quer ativar/desativar.

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

Agora clique com o botão direito no elemento e clique em **Loading Requirements**.
Isso abrirá a tela de Manage Requirements. Clique em **Add Requirement**.

Procure pelo requisito **Is Variable Value**, selecione-o e clique em **Edit Requirement Value**.

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

Agora digite o nome da variável que você criou anteriormente e deixe o requisito verificar `true` como valor.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Pronto para essa parte. Agora seu elemento ficará visível quando o valor da variável for `true`.

## O Botão

Agora precisamos adicionar um novo elemento Button.

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

Depois de adicionar, clique com o botão direito nele e clique em **Edit Action Script**.
Isso abrirá a tela Manage Action Script do botão.

Clique em **Add IF Statement**, adicione o requisito **Is Variable Value** a ele e defina o modo do requisito como **OPPOSITE**.

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

Agora clique em **Edit Requirement Value**, assim como você fez com o elemento antes, e digite exatamente o mesmo nome de variável e o mesmo valor a serem verificados.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

Como definimos o modo do requisito como **OPPOSITE**, agora ele vai verificar se o valor da variável NÃO é `true`, que é exatamente o que queremos.

De volta à tela Edit Action Script, você verá agora a instrução IF que acabamos de adicionar.

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

Agora clique em **Add Action**, procure pela ação **Set Variable Value**, selecione-a e clique em **Edit Action Value**.

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

Como valor da ação, digite primeiro o nome da sua variável e depois o valor para o qual você quer defini-la. Separe o nome e o valor com `:`.
Neste caso, queremos definir nosso valor como `true`, porque essa ação será executada depois quando o valor NÃO for `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

Agora anexe a ação à instrução IF, arrastando-a e posicionando-a sobre a instrução IF, para que ela só seja executada quando o valor da nossa variável NÃO for `true`.

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

Depois disso, selecione a instrução IF e clique em **Append ELSE Statement**.

Agora adicione outra ação **Set Variable Value**, mas em vez de definir o valor da variável como `true`, defina-o como `false`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

Agora anexe a segunda ação à instrução ELSE, para que ela seja executada se o valor da variável FOR `true`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

E pronto! Parece muita etapa na primeira vez, mas na verdade é algo bem fácil e rápido de fazer depois que você se acostuma.

Agora você pode salvar seu layout, sair do editor e pressionar o botão para ver se funciona!

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

Fique à vontade para usar a mesma variável em outros elementos, assim você **alterna vários elementos ao mesmo tempo** ao pressionar o botão.

Você também pode alternar layouts inteiros usando os **Layout-Wide Loading Requirements**. Para configurar requisitos em todo o layout, clique com o botão direito no fundo do editor. Só lembre de adicionar o botão em outro layout, não naquele que você quer alternar.

# Alternar Entre

Além de alternar entre dois valores, alternar entre vários valores exige que o script de ação consiga ciclar entre mais de dois valores.

A lógica do script de ação é muito parecida com a usada para alternar, então vou manter esta parte bem curta. Certifique-se de ler também a parte sobre alternar.

Adicionei 3 imagens. A primeira imagem fica visível quando o valor da variável é `1`, a segunda quando o valor é `2` e a terceira quando o valor é `3`.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

Depois disso, adicionei o botão de ciclo e fiz com que ele alternasse o valor da variável de `1` para `2` para `3` para `1`.

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

E é isso. Agora salve o layout, saia do editor e confira se o botão de ciclo está funcionando corretamente.

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
