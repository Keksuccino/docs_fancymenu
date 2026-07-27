---
title: Obter Quadros de Vídeos
description: Extraia quadros PNG de um vídeo com o FFmpeg.
---

# Extrair Quadros de Vídeo com FFmpeg

1. Instale o [FFmpeg](https://ffmpeg.org/download.html) e verifique se o comando `ffmpeg` está disponível.
2. Abra um terminal no diretório que contém seu vídeo.
3. Crie o diretório de saída:

   ```bash
   mkdir output_frames
   ```

4. Execute o comando que corresponde aos quadros de que você precisa. Substitua `input.mp4` pelo nome do arquivo do seu vídeo.

## Extrair Todos os Quadros

```bash
ffmpeg -i input.mp4 output_frames/frame_%04d.png
```

## Extrair em uma Taxa de Quadros Fixa

Este exemplo cria 10 quadros por segundo. Altere `10` conforme necessário.

```bash
ffmpeg -i input.mp4 -vf "fps=10" output_frames/frame_%04d.png
```

## Redimensionar Quadros Extraídos

Este exemplo ajusta cada quadro para `1280×720`.

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_frames/frame_%04d.png
```

Os arquivos PNG numerados em `output_frames` podem ser usados para criar uma [animação AFMA ou FMA clássica](./fma). Menos quadros e dimensões menores reduzem o tamanho do arquivo e o uso de memória.
