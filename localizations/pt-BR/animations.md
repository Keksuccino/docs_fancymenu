---
title: Animações
description: Como usar imagens animadas no FancyMenu e como criá-las.
sourceBlobSha: 76227b0d592e15bf10929c35d6a78e1eea6ee85a
---
# Animações

O FancyMenu reproduz imagens animadas em quase todos os lugares onde você pode usar uma imagem: em [elementos de imagem](/elements#image), [planos de fundo de menu com imagem](/menu-backgrounds#image), texturas de botões e controles deslizantes, na [introdução do jogo](/game-intro) e muito mais.

Use arquivos **APNG** ou **GIF** para suas animações:

- **APNG** (PNG animado) oferece melhor qualidade: todas as cores de um PNG normal e transparência adequada com bordas suaves. É a melhor opção para logotipos, planos de fundo e tudo que tenha transparência.
- **GIF** é mais comum, então há mais ferramentas para criar e editar GIFs. Porém, um GIF tem apenas 256 cores por quadro, e seus pixels são totalmente transparentes ou totalmente opacos.

> [!NOTE]
> Os formatos de animação próprios do FancyMenu, FMA e AFMA, foram descontinuados. Seus arquivos existentes continuam funcionando, mas use APNG ou GIF para novas animações. Consulte [FMA e AFMA](#fma-and-afma).

# Usar animações

1. Coloque o arquivo em `<game-directory>/config/fancymenu/assets/` para que ele apareça no seletor de arquivos do FancyMenu. URLs da Web e arquivos de pacotes de recursos também funcionam; consulte [Recursos](/resources).
2. Selecione-o como qualquer outra imagem, por exemplo, em **Origem da imagem** de um elemento de imagem.

> [!WARNING]
> Os arquivos APNG precisam terminar em `.apng`. Muitas ferramentas salvam APNGs com a extensão `.png`, então renomeie o arquivo; caso contrário, o FancyMenu o exibirá como uma imagem estática. O mesmo vale para URLs da Web: elas precisam terminar em `.apng`.

## Como as animações são reproduzidas

- Uma animação é reproduzida o número de vezes especificado no arquivo e, em seguida, permanece no último quadro. Você define o número de repetições ao criar o arquivo.
- As animações só são reproduzidas enquanto estão na tela. Quando aparecem novamente, continuam de onde pararam.
- **Reiniciar texturas animadas ao abrir a tela** faz com que as animações de elementos de imagem e planos de fundo de menu com imagem recomecem sempre que a tela é aberta.
- **Reiniciar texturas animadas ao passar o cursor** faz com que as texturas de botões e controles deslizantes recomecem sempre que o cursor do mouse passa sobre eles.
- Os listeners [**Animação de textura iniciada**](/listeners#animated-texture-started-playing) e [**Animação de textura concluída**](/listeners#animated-texture-finished-playing) executam ações quando uma animação começa ou termina.

## Desempenho

O FancyMenu decodifica APNGs e GIFs durante a reprodução, apenas alguns quadros à frente. Assim, até animações longas exigem pouca memória.

Quadros grandes e altas taxas de quadros ainda podem afetar o desempenho. Faça com que seus quadros tenham aproximadamente o tamanho em que serão exibidos na tela; consulte [Otimização de texturas](/optimizing-textures). Para clipes longos com áudio, use um [vídeo](/video).

# Criar animações

Estas ferramentas gratuitas criam APNGs e GIFs a partir de quadros individuais ou vídeos:

- [ScreenToGif](https://www.screentogif.com/) (Windows): clique em **Editor**, arraste seus quadros PNG para ele, defina o intervalo entre os quadros e salve a animação como APNG ou GIF. Você pode definir a repetição no menu de salvamento.
- [ezgif](https://ezgif.com/) (online, sem precisar baixar): crie um [GIF](https://ezgif.com/maker) ou um [APNG](https://ezgif.com/apng-maker) a partir de imagens, converta um vídeo em [GIF](https://ezgif.com/video-to-gif) ou [APNG](https://ezgif.com/video-to-apng), ou converta [GIF para APNG](https://ezgif.com/gif-to-apng) e [APNG para GIF](https://ezgif.com/apng-to-gif).
- [FFmpeg](https://ffmpeg.org/download.html) (linha de comando): veja abaixo.

## Com FFmpeg

Converta quadros PNG numerados, como `frame_0001.png`, `frame_0002.png` e assim por diante, em um APNG que se repete indefinidamente. `-framerate 20` reproduz 20 quadros por segundo:

```bash
ffmpeg -framerate 20 -i frame_%04d.png -plays 0 animation.apng
```

Converta um vídeo em APNG. `fps=20` mantém 20 quadros por segundo, e `scale=960:-1` define a largura como 960 pixels:

```bash
ffmpeg -i trailer.mp4 -vf "fps=20,scale=960:-1" -plays 0 trailer.apng
```

Converta um vídeo em GIF que se repete indefinidamente. A parte `palettegen` seleciona as 256 melhores cores para ele:

```bash
ffmpeg -i trailer.mp4 -vf "fps=15,scale=640:-1:flags=lanczos,split[a][b];[a]palettegen[p];[b][p]paletteuse" -loop 0 trailer.gif
```

Converta um GIF em APNG:

```bash
ffmpeg -i logo.gif -plays 0 logo.apng
```

# FMA e AFMA

FMA e AFMA são formatos de animação próprios do FancyMenu. Ambos foram descontinuados: ainda são reproduzidos, mas APNG e GIF são opções melhores para novas animações.

Para criar um AFMA mesmo assim:

1. Coloque seus quadros como arquivos PNG em uma pasta. Eles serão reproduzidos na ordem dos nomes, como `frame_1.png`, `frame_2.png`, ..., `frame_10.png`.
2. Abra **barra de menus -> Ferramentas -> Criador de AFMA**.
3. Defina **Diretório principal dos quadros** como a pasta. Os quadros em **Diretório dos quadros de introdução** são reproduzidos uma vez antes dos quadros principais.
4. Defina **Duração do quadro principal (ms)** e **Número de repetições**. Um número de repetições igual a `0` repete a animação indefinidamente.
5. Defina **Arquivo AFMA de saída** e clique em **Exportar**.
