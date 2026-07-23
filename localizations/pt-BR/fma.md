---
title: Animações (FMA/AFMA)
description: Como criar e usar arquivos de animação do FancyMenu.
---
# Animações

Arquivos AFMA e FMA são formatos de textura animada criados para o FancyMenu.

# Arquivos AFMA

**AFMA** (Advanced FancyMenu Animation) é o sucessor dos arquivos FMA clássicos.

AFMA usa um formato que não é ZIP, com arquivos menores, menor uso de memória e melhor desempenho do que o FMA clássico.

Para texturas animadas grandes ou complexas, use **AFMA** em vez do FMA clássico.

Crie arquivos AFMA com o criador integrado:

1. Abra a barra de menu do FancyMenu.
2. Vá em **Tools -> AFMA Creator**.
3. Importe/converta seus frames com o criador.

> [!IMPORTANT]
> Arquivos AFMA não podem ser empacotados manualmente. Use **Tools -> AFMA Creator**.

Arquivos FMA clássicos continuam compatíveis, então layouts existentes não precisam ser convertidos imediatamente.

# Arquivos FMA Clássicos

## Criando um FMA

Um arquivo FMA clássico é um arquivo ZIP com a extensão `.fma`.

### Extensões de Arquivo

Ative as extensões de arquivo no seu gerenciador de arquivos antes de criar ou renomear os arquivos abaixo.

No Windows, abra o Explorador de Arquivos e ative **Exibir -> Extensões de nome de arquivo**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Preparação

Crie uma pasta chamada `fancymenu_animation` para o conteúdo do arquivo.

Crie um diretório obrigatório `frames` e um diretório opcional `intro_frames` dentro dele.

Na mesma pasta, crie `metadata.json`. Verifique se a extensão do arquivo é `.json`, e não `.txt`.

A pasta agora deve conter `frames/`, `intro_frames/` e `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### O JSON de Metadados

Abra `metadata.json` em um editor de texto e use este modelo:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
  },
  "custom_frame_times_intro": {
  }
}
```

Edite os valores conforme necessário.

#### `loop_count`

Controla quantas vezes a animação é reproduzida. Use `0` para repetir indefinidamente. Um valor positivo reproduz essa quantidade de vezes e, depois, mantém o último frame.

#### `frame_time`

Define por quanto tempo cada frame normal fica visível, em milissegundos.

#### `frame_time_intro`

Define o tempo de exibição dos frames opcionais de **intro**.

#### `custom_frame_times`

Substitui opcionalmente a duração de frames individuais normais. Este exemplo mantém os frames `0` e `1` visíveis por `5000` milissegundos, enquanto os outros frames usam `frame_time`:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    "0": 5000,
    "1": 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Os índices dos frames começam em zero: o primeiro frame é `0`, o segundo é `1` e assim por diante.

Adicione uma vírgula após cada entrada de tempo personalizado, exceto a última.

#### `custom_frame_times_intro`

Usa o mesmo formato de `custom_frame_times`, mas se aplica aos frames opcionais de introdução.

Salve `metadata.json`.

### Os Frames

> [!CAUTION]
> Mantenha animações FMA clássicas com no máximo 200 frames e 1080p. Use [Vídeo](./video) para conteúdo longo ou com alta taxa de frames.

Coloque os frames normais em `frames/`. Eles devem ser arquivos PNG nomeados sequencialmente a partir de `0.png`, como `0.png`, `1.png` e `2.png`. Outros formatos e nomes não são suportados.

Para extrair frames de um vídeo, veja [Extraindo Frames com FFmpeg](./ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### A Intro

Coloque os frames opcionais de intro em `intro_frames/`. Eles seguem as mesmas regras de nomeação PNG dos frames normais, são reproduzidos uma vez antes da sequência normal e não entram em loop.

### Empacotando o Arquivo FMA

Crie um ZIP contendo o conteúdo da pasta. `metadata.json`, `frames/` e o diretório opcional `intro_frames/` devem estar na raiz do ZIP, não dentro de outro diretório.

No Windows, selecione o conteúdo de `fancymenu_animation`, clique com o botão direito na seleção e escolha **Enviar para -> Pasta compactada (zipada)**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Localize o arquivo ZIP resultante.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

O conteúdo da raiz deve parecer com isto:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Renomeie o arquivo para `fancymenu_animation.fma`, substituindo a extensão `.zip`. O nome base pode ser alterado, mas a extensão `.fma` é obrigatória.

O arquivo renomeado agora está pronto para ser usado como um arquivo FMA.

# Usando Arquivos AFMA e FMA no FancyMenu

> [!IMPORTANT]
> Arquivos AFMA/FMA são texturas animadas, então adicione-os por meio de entradas de [**Imagem**](./elements#image). Quase tudo que aceita imagens também aceita arquivos AFMA e FMA.

Use arquivos AFMA/FMA em qualquer lugar que aceite uma imagem, incluindo [elementos de imagem](./elements#image) e [planos de fundo de menu de imagem](./menu-backgrounds).

Armazene o arquivo AFMA/FMA em `<game-directory>/config/fancymenu/assets/` para que ele apareça no seletor de recursos locais do FancyMenu.
