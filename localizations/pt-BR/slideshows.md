---
title: Apresentações de slides
description: Crie e use apresentações de imagens.
---

# Apresentações de slides

Cada apresentação de slides tem seu próprio diretório abaixo:

```text
<game-directory>/config/fancymenu/slideshows/
```

`<game-directory>` é a instância ativa do launcher, que pode ser diferente do diretório `.minecraft` convencional.

# Estrutura de diretórios

```text
<game-directory>/config/fancymenu/slideshows/
└── myslideshow/
    ├── properties.txt
    ├── overlay.png          # opcional
    └── images/
        ├── image_01.png
        └── image_02.jpg
```

As imagens devem usar `.png` ou `.jpg`; outras extensões, incluindo `.jpeg`, são ignoradas.

Quando `randomize = false`, as imagens são exibidas em ordem alfabética pelo nome do arquivo, sem diferenciar maiúsculas de minúsculas. Use nomes com zeros à esquerda, como `image_01.png`, `image_02.png` e `image_10.png`.

# `properties.txt`

```text
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

| Propriedade | Significado |
|---|---|
| `name` | Obrigatório, identificador em tempo de execução sensível a maiúsculas e minúsculas; mantenha-o exclusivo |
| `width`, `height` | Tamanho base em pixels com escala da GUI e a proporção da imagem de origem |
| `x`, `y` | Posição base no canto superior esquerdo; elementos normais e fundos usam sua própria posição, então mantenha estes em `0` |
| `duration` | Mínimo de segundos entre o início das transições; inclui o tempo de fade e deve ser maior que `0` |
| `fadespeed` | Multiplicador da velocidade do fade; `1.0` é o padrão, valores mais altos fazem o fade acontecer mais rápido, e o valor deve ser maior que `0` |
| `randomize` | `true` para seleção aleatória ou `false` para ordem por nome de arquivo |

Apenas `name` é obrigatório. Os padrões são `width = 50`, `height = 50`, `x = 0`, `y = 0`, `duration = 10.0`, `fadespeed = 1.0` e `randomize = false`. Mantenha `type = slideshow` e `slideshow-meta` inalterados; escreva um `key = value` por linha e use ponto para decimais.

Os layouts selecionam o valor de `name`, não o nome do diretório. Nomes duplicados não são rejeitados, e a ordem da varredura dos diretórios determina qual apresentação de slides permanece disponível. Mantenha os nomes exclusivos dentro do diretório de apresentações de slides.

O modo aleatório escolhe de forma independente a cada transição e evita repetir imediatamente quando há várias imagens disponíveis. O tempo usa tempo real; um fade que demora mais que `duration` atrasa a próxima transição, e voltar para uma apresentação de slides depois que ela foi ocultada pode avançá-la imediatamente.

# Usando uma apresentação de slides

Recarregue o FancyMenu em **Customização -> Recarregar FancyMenu** ou reinicie o cliente. Use o elemento [**Slideshow**](./elements#slideshow), ou clique com o botão direito no fundo do editor de layout e selecione [**Fundos do menu**](./menu-backgrounds) -> **Slideshow**.
