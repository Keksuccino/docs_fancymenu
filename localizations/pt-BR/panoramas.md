---
title: Panoramas
description: Como criar e usar panoramas personalizados de fundo.
---

# Panoramas Cúbicos

O FancyMenu oferece suporte ao carregamento de cubos panorâmicos personalizados com 6 imagens como fundo para menus.

Esses panoramas são um formato especial de panorama cúbico usado pelo Minecraft como fundo na tela de título e são compostos por 6 imagens (faces) que são renderizadas como um cubo (ou skybox, para ser mais específico).

> **IMPORTANTE**: Se você estiver no Windows, não esqueça de ativar as [extensões de arquivo](https://cdn.discordapp.com/attachments/795308330746511390/801561308012347482/unknown.png), porque, caso contrário, você não conseguirá ver partes importantes dos nomes dos arquivos mais tarde!
{.is-warning}

# Criando um Panorama

Se você não sabe como o Minecraft lida com seus panoramas de fundo e como criá-los, confira [este vídeo](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t).
Ele vai te dar uma ótima compreensão de como os panoramas do Minecraft funcionam e como fazer um!

Depois de assistir ao vídeo, você vai perceber que criar esses panoramas pode levar um certo tempo.
Para economizar tempo, talvez valha a pena usar um mod que os cria para você.
Você pode encontrar alguns pesquisando por `minecraft panorama mod`, mas um deles é o [Panoramica](https://www.curseforge.com/minecraft/mc-mods/panoramica) (feito por mim).

# Preparando o Panorama

Depois de obter suas 6 imagens do panorama, você precisará movê-las para o lugar certo!

O diretório de panoramas do FancyMenu fica em `.minecraft/config/fancymenu/panoramas`.
Este é o diretório de todos os panoramas que você deseja usar no mod.

## A Pasta do Panorama

Cada panorama tem sua própria pasta.
Você precisará criar uma nova pasta em `.minecraft/config/fancymenu/panoramas` se quiser adicionar um novo panorama.
No meu exemplo, vou nomear a pasta como `mypanorama`.

![1](https://user-images.githubusercontent.com/35544624/100791916-2802d380-341a-11eb-8e32-f9913e93a38c.png)

## Conteúdo da Pasta

Depois de criar a pasta, você precisará preenchê-la.

### Arquivo de Propriedades
Todo panorama precisa de um arquivo de propriedades para funcionar.
Esse arquivo sempre precisa se chamar `properties.txt` e precisa ter algumas informações importantes escritas nele.

O conteúdo de um arquivo de propriedades de panorama deve sempre ser assim:
```
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```
Apenas as variáveis dentro da seção `panorama-meta` podem ser alteradas!

#### name
Este precisa ser o nome **único** do seu panorama.
Não é possível carregar dois panoramas com o mesmo nome!
Você usará esse nome mais tarde para identificar seu panorama.

#### speed
A velocidade com que seu panorama gira.
Este valor é um multiplicador de velocidade. Por exemplo, `1.0` é a velocidade padrão, `2.0` dobra a velocidade e `0.5` a reduz pela metade.
Valores negativos não são suportados; use valores decimais para diminuir a velocidade.

#### fov
O campo de visão.
O FOV padrão é `85.0`.
Usar valores muito altos ou muito baixos aqui quebrará o panorama. Basta testar para encontrar o FOV desejado.

#### angle
O ângulo vertical sob o qual o panorama é visualizado.
O ângulo padrão é `25.0`.

#### start_rotation
O ângulo de rotação (horizontal) em que o panorama deve começar. Valor entre 0 e 360.

<br>

### Pasta de Imagens do Panorama

A segunda coisa obrigatória que a pasta do seu panorama precisa é a pasta de imagens real contendo as imagens do panorama.

O nome dessa pasta precisa ser `panorama`.

Coloque todas as imagens do seu panorama nela, mas não esqueça de nomeá-las corretamente, como mostrado no [vídeo](https://www.youtube.com/watch?v=F7jMd3zsjZQ&t) acima!

![3](https://user-images.githubusercontent.com/35544624/100791922-29340080-341a-11eb-8174-874a180d0485.png)

> Apenas PNGs são समर्थidos como imagens de panorama!
{.is-warning}

### Overlay do Panorama

A última etapa é **opcional** e pode ser ignorada se você não quiser um overlay sobre o seu panorama.

Se quiser adicionar uma vinheta ou outros tipos de overlay ao seu panorama, você pode adicionar um arquivo chamado 'overlay.png'.
Lembre-se de que apenas PNG é suportado para o overlay e que o nome do arquivo sempre precisa ser 'overlay.png'!

### Conferindo Tudo Novamente

Agora você deve ter uma pasta localizada em `.minecraft/config/fancymenu/panoramas`, contendo um arquivo `properties.txt`, outra pasta chamada `panorama` e talvez um overlay chamado `overlay.png`.

![2](https://user-images.githubusercontent.com/35544624/100791920-29340080-341a-11eb-8e26-98a7fd2ad7eb.png)

# Usando o Panorama

Depois de iniciar (ou reiniciar) o jogo ou recarregar o FancyMenu por meio de **Customization -> Reload FancyMenu**, você já deverá conseguir definir seu panorama como fundo do menu. Para fazer isso, clique com o botão direito no fundo do editor de layout e clique em **Menu Background**.
