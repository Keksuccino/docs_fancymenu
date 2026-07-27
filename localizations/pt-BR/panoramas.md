---
title: Panoramas
description: Crie e use panoramas cúbicos de seis imagens.
---

# Panoramas Cúbicos

Cada panorama tem seu próprio diretório abaixo:

```text
<game-directory>/config/fancymenu/panoramas/
```

`<game-directory>` é a instância ativa do launcher, que pode ser diferente do diretório convencional `.minecraft`.

# Estrutura de Diretórios

```text
<game-directory>/config/fancymenu/panoramas/
└── mypanorama/
    ├── properties.txt
    ├── overlay.png          # opcional
    └── panorama/
        ├── panorama_0.png
        ├── panorama_1.png
        ├── panorama_2.png
        ├── panorama_3.png
        ├── panorama_4.png
        └── panorama_5.png
```

As seis imagens das faces devem ser arquivos PNG com os nomes exatos mostrados acima, e todas as seis devem ter dimensões idênticas. A diferença entre maiúsculas e minúsculas no nome do arquivo pode importar em alguns sistemas operacionais.

Adicione um `overlay.png` opcional ao lado de `properties.txt` para uma vinheta ou outra sobreposição para o panorama completo.

# `properties.txt`

```text
type = panorama

panorama-meta {
  name = name_of_your_panorama
  speed = 1.0
  fov = 85.0
  angle = 25.0
  start_rotation = 0
}
```

| Propriedade | Significado |
|---|---|
| `name` | Obrigatório, identificador em tempo de execução sensível a maiúsculas e minúsculas; mantenha-o único |
| `speed` | Multiplicador da velocidade de rotação; `1.0` é o padrão |
| `fov` | Campo de visão em graus |
| `angle` | Ângulo de visão vertical em graus |
| `start_rotation` | Rotação horizontal inicial em graus |

Somente `name` é obrigatório. Valores opcionais ausentes usam os padrões mostrados no exemplo. Mantenha `type = panorama` e `panorama-meta` inalterados; escreva um `key = value` por linha e use ponto para decimais.

Nomes duplicados não são rejeitados, e a ordem de varredura do diretório decide qual panorama permanece disponível. Mantenha os nomes únicos dentro do diretório de panoramas. Os nomes de panorama e slideshow usam listas separadas.

# Usando um Panorama

Recarregue o FancyMenu por meio de **Customization -> Reload FancyMenu**, ou reinicie o cliente. Depois, clique com o botão direito no fundo do editor de layout e selecione [**Menu Backgrounds**](./menu-backgrounds) -> **Cubic Panorama**.
