---
title: Obter Quadros de Vídeos
description: Como obter quadros de um arquivo de vídeo.
---

# Como Obter Quadros de um Vídeo Usando o FFmpeg

*Esta página foi parcialmente gerada pela IA ChatGPT.*

O FFmpeg é uma ferramenta gratuita que ajuda você a trabalhar com vídeos e arquivos de áudio. Uma coisa legal que você pode fazer com ele é extrair imagens (quadros) de um vídeo, como um arquivo MP4. Veja como fazer isso passo a passo.

MP4 será usado nos comandos a seguir, mas o FFmpeg também oferece suporte a outros formatos de vídeo, como AVI, MOV, MKV e MPEG.

# O Que Você Precisa

Antes de começar, verifique se você tem:

1. **FFmpeg Instalado**:

   - Baixe o FFmpeg no [site oficial do FFmpeg](https://ffmpeg.org/download.html). Certifique-se de baixar a versão "full".
   - Siga as instruções de instalação para o seu computador.

2. **Acesso à Linha de Comando**:

   - Use o terminal (Linux/macOS) ou o prompt de comando (Windows) para executar comandos do FFmpeg.

3. **Um Arquivo de Vídeo**:

    - Tenha um arquivo de vídeo MP4, AVI, MOV, MKV ou MPEG pronto para usar.

# Antes de Começar

Antes de executar qualquer comando, prepare o seguinte:

## Ativar Extensões de Arquivo

  - É importante ver extensões de arquivo como `.mp4` ou `.avi` ao renomear o seu vídeo.

    - **No Windows**:

      - Abra o Explorador de Arquivos.
      - Clique na aba "Exibir" na parte superior.
      - Marque a caixa que diz "Extensões de nome de arquivo."

    - **No macOS**:

      - Abra o Finder.
      - Clique em "Finder" na barra de menus e selecione "Preferências."
      - Vá para a aba "Avançado" e marque a opção "Mostrar todas as extensões de nome de arquivo."

## Criar uma Pasta de Saída

- Crie uma pasta chamada `output_frames` no diretório onde o executável do FFmpeg está localizado. É aqui que os quadros extraídos serão salvos.

## Preparar o Seu Arquivo de Vídeo

- Coloque o arquivo de vídeo do qual você quer extrair quadros no mesmo diretório do executável do FFmpeg.
- Renomeie o arquivo de vídeo para `input` seguido da sua extensão (por exemplo, `input.mp4`, `input.avi`, etc.). Isso garante que os comandos abaixo funcionem sem modificações.

<br>
<img width="579" alt="Screenshot_4" src="https://gist.github.com/user-attachments/assets/1cb4ddf9-a17a-4219-b7d4-aa344adaa87c" />

# Como Abrir o FFmpeg

Antes de usar o FFmpeg, você precisa abri-lo pela linha de comando. Veja como fazer isso passo a passo no Windows e no macOS.

## No Windows:

1. **Abra o Prompt de Comando**:
   - Pressione a tecla `Windows` e a tecla `R` ao mesmo tempo para abrir a janela Executar.
   - Digite `cmd` e pressione Enter. Isso abre o Prompt de Comando.

2. **Vá para a Pasta do FFmpeg**:
   - Você precisa informar ao computador onde o FFmpeg está localizado. Use o comando `cd` para ir até a pasta onde você salvou o FFmpeg.
   - Por exemplo, se o FFmpeg estiver em uma pasta chamada `ffmpeg-2024\bin` na sua área de trabalho, digite isto:
     ```bash
     cd C:\Users\SeuUsuario\Desktop\ffmpeg-2024\bin
     ```
     (Substitua "SeuUsuario" pelo seu nome de usuário real no computador.)

3. **Verifique se o FFmpeg Funciona**:
   - Para garantir que o FFmpeg está funcionando, digite este comando:
     ```bash
     ffmpeg -version
     ```
   - Se estiver funcionando, você verá informações sobre o FFmpeg aparecerem na tela.

## No macOS:

1. **Abra o Terminal**:
   - Pressione `Command` e `Espaço` ao mesmo tempo para abrir a Busca Spotlight.
   - Digite `Terminal` e pressione Enter para abri-lo.

2. **Vá para a Pasta do FFmpeg**:
   - Use o comando `cd` para ir até a pasta onde você salvou o FFmpeg.
   - Por exemplo, se o FFmpeg estiver na sua pasta `Downloads`, digite isto:
     ```bash
     cd ~/Downloads/ffmpeg-2024/bin
     ```

3. **Verifique se o FFmpeg Funciona**:
   - Para garantir que o FFmpeg está pronto, digite este comando:
     ```bash
     ./ffmpeg -version
     ```
   - Se o FFmpeg estiver funcionando, você verá detalhes sobre ele aparecerem na tela.

# Como Salvar Todos os Quadros

Para salvar todos os quadros de um vídeo, use este comando:

```bash
ffmpeg -i input.mp4 output_frames/%d.png
```

## O Que Isso Significa:

- `-i input.mp4`: Este é o seu arquivo de vídeo de entrada. Ele deve estar no mesmo diretório do executável do FFmpeg. Certifique-se de alterar `input.mp4` para o nome e a extensão corretos do arquivo.
- `output_frames/frame_%04d.png`: É assim que os quadros serão salvos:
- `output_frames/`: Salva todos os quadros em uma pasta chamada `output_frames`.
- `%d.png`: Os quadros serão nomeados usando números como `1.png`, `2.png` e assim por diante, mantendo a ordem.

# Salvar Quadros em Momentos Específicos

Se você não quiser todos os quadros, pode salvar um quadro por segundo (ou em outros intervalos). Use este comando:

```bash
ffmpeg -i input.mp4 -vf "fps=1" output_frames/%d.png
```

## O Que Isso Significa:

- `-i input.mp4`: Este é o seu arquivo de vídeo de entrada. Ele deve estar no mesmo diretório do executável do FFmpeg. Certifique-se de alterar `input.mp4` para o nome e a extensão corretos do arquivo.
- `-vf "fps=1"`: Salva um quadro por segundo. Altere o `1` para outro número se quiser quadros com mais ou menos frequência (por exemplo, `fps=0.5` salva um quadro a cada dois segundos, e `fps=2` salva dois quadros por segundo).
- `output_frames/%d.png`: Salva os quadros em uma pasta chamada `output_frames`, com nomes como `1.png`, `2.png` e assim por diante.

# Alterar o Tamanho e a Qualidade dos Quadros

Você também pode ajustar o tamanho e a qualidade dos quadros que salvar. Veja como:

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" -q:v 2 output_frames/%d.png
```

## O Que Isso Significa:

- `-i input.mp4`: Este é o seu arquivo de vídeo de entrada. Ele deve estar no mesmo diretório do executável do FFmpeg. Certifique-se de alterar `input.mp4` para o nome e a extensão corretos do arquivo.
- `-vf "scale=1280:720"`: Altera o tamanho do quadro para 1280x720 pixels.
- `-q:v 2`: Define a qualidade da imagem (1 é a melhor, números maiores significam qualidade menor).
- `output_frames/%d.png`: Salva os quadros em uma pasta chamada `output_frames`, com nomes como `1.png`, `2.png` e assim por diante.

# Dicas para Salvar Quadros

1. **Economize Espaço**:

   - Se o vídeo for longo, você pode salvar quadros em intervalos em vez de salvar cada quadro. Isso é especialmente útil quando você vai usá-los como quadros de animação FMA no FancyMenu.

2. **Saiba Mais**:

   - Execute `ffmpeg -h` no seu terminal para ver tudo o que o FFmpeg pode fazer.

<br>
Agora você está pronto para usar o FFmpeg para salvar quadros do seu vídeo!&#x20;

