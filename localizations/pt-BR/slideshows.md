---
title: Apresentações de Slides
description: Como criar e usar apresentações de slides.
---

# Apresentações de Slides

O FancyMenu permite que você adicione apresentações de slides e as exiba em menus e como fundos de menu.

> **IMPORTANTE**: Se você estiver no Windows, não se esqueça de ativar as [extensões de arquivo](https://vtcri.kayako.com/article/296-view-file-extensions-windows-10), porque, caso contrário, você não conseguirá ver partes importantes dos nomes dos arquivos depois!
{.is-warning}

# Criando uma Apresentação de Slides

Cada apresentação de slides precisa estar em sua própria pasta **dentro** do diretório de apresentações localizado em `/config/fancymenu/slideshows/`.

![1](https://user-images.githubusercontent.com/35544624/105209961-b823e600-5b4a-11eb-8ed2-1016d3b05815.png)

Para que o sistema reconheça uma apresentação de slides como tal, ela precisa ter um arquivo de propriedades localizado na pasta da apresentação. Então, se você nomeou a pasta da sua apresentação como `myslideshow`, o arquivo de propriedades deve estar localizado em `/config/fancymenu/slideshows/myslideshow/properties.txt`.

**Esse arquivo sempre precisa se chamar `properties.txt`!**
Por enquanto, crie apenas o arquivo de propriedades **vazio** e siga para a próxima etapa.

![2](https://user-images.githubusercontent.com/35544624/105210016-cbcf4c80-5b4a-11eb-84ad-9aa735340287.png)

## Adicionando Imagens

Uma apresentação de slides precisa de imagens (óbvio), então vamos adicionar algumas!

> As imagens da sua apresentação precisam ser arquivos **PNG**! Nada de JPEG, GIF, APNG ou FMA!
{.is-danger}

Todas as imagens da sua apresentação vão para uma pasta extra **dentro** da pasta da apresentação (`myslideshow` no exemplo acima).
O nome dessa pasta precisa ser `images`.

![3](https://user-images.githubusercontent.com/35544624/105210833-d9d19d00-5b4b-11eb-8ae7-528ad156e27a.png)

Agora coloque todas as imagens da sua apresentação na pasta `images`.
Elas são organizadas em ordem alfabética (respeitando números), então basta nomeá-las como `image_1.png`, `image_2.png` e assim por diante.
No meu exemplo, `image_1.png` seria exibida primeiro e `image_2.png` depois.

<br>
<img width="548" alt="Screenshot_2" src="https://github.com/user-attachments/assets/f58ecbfa-affa-4071-8a84-18ed27a6cfee">

## Adicionando Conteúdo ao Arquivo de Propriedades

No início, você criou um arquivo `properties.txt` vazio na pasta da sua apresentação.
Agora esse arquivo precisa ser preenchido com algumas informações importantes.

Todo arquivo de propriedades de apresentação de slides deve se parecer com isto:

```
type = slideshow

slideshow-meta {
   name = cool_slideshow
   width = 1920
   height = 1080
   x = 0
   y = 0
   duration = 5.0
   fadespeed = 12.0
   randomize = false
}
```
Somente as variáveis dentro da seção `slideshow-meta` podem ser alteradas!

### name

Este é o nome, ou melhor, o identificador da sua apresentação de slides.
Os nomes das apresentações precisam ser **únicos**, então não é possível ter duas apresentações com o mesmo nome!

### width | height

A `width` (largura) e a `height` (altura) base da sua apresentação.
Usadas pelo FancyMenu para calcular a proporção da tela.

### x | y

A posição `x` e `y` da sua apresentação.
Mais para fins de depuração, então basta definir ambas como `0`.

### duration

A duração em **segundos** de quanto tempo cada imagem é exibida antes de mudar para a próxima.
Suporta valores decimais!

### fadespeed

A velocidade da animação de fade ao trocar para a próxima imagem.
Este valor é um multiplicador de velocidade. Por exemplo, `1.0` é a velocidade padrão, `2.0` dobra a velocidade e `0.5` fará com que seja metade da velocidade padrão.
Valores negativos não são suportados.

### randomize

Se as imagens da apresentação devem ser exibidas em ordem aleatória (`true`) ou não (`false`).

# Usando a Apresentação de Slides

Todos os passos importantes foram concluídos e sua apresentação já deve estar pronta, então vamos testá-la!

Para carregar sua apresentação nova (ou editada) no FancyMenu, recarregue o mod em **Customization -> Reload FancyMenu**.

Agora você pode usar sua apresentação no elemento **Slideshow** ou como fundo do menu (clique com o botão direito no fundo do editor de layout -> **Menu Background**).
