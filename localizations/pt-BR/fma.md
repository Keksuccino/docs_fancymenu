---
title: Animações (FMA/AFMA)
description: Como criar e usar arquivos de animação do FancyMenu.
---

# Animações

Arquivos AFMA/FMA são arquivos especiais de textura animada criados para o FancyMenu.
Eles são praticamente iguais aos APNGs, mas muito mais otimizados para o FancyMenu.

# Arquivos AFMA

O FancyMenu 3.9.0 adiciona o **AFMA** (Advanced FancyMenu Animation), o sucessor dos arquivos FMA clássicos.

Os arquivos AFMA não são mais arquivos ZIP. Eles usam o novo formato de animação do FancyMenu, com tamanhos de arquivo melhores, menor uso de memória e melhor desempenho.

Para novas texturas animadas grandes ou complexas, use **AFMA** em vez do FMA clássico.

Para criar um arquivo AFMA, faça o seguinte:

1. Abra a barra de menu do FancyMenu.
2. Vá em **Tools -> AFMA Creator**.
3. Importe/converta seus quadros com o criador.

> [!IMPORTANT]
> Arquivos AFMA não podem ser empacotados manualmente como arquivos FMA clássicos. Você precisa usar o **AFMA Creator** para empacotá-los/criá-los.

Os arquivos FMA clássicos ainda são compatíveis e foram otimizados no FancyMenu 3.9.0, então os layouts existentes não precisam ser convertidos imediatamente.

# Arquivos FMA Clássicos

## Criando um FMA

Criar um arquivo FMA é tão fácil quanto criar um arquivo ZIP! Bem, isso é principalmente porque ele _é_ um arquivo ZIP por baixo dos panos.

### Extensões de Arquivo

Você precisa ver as extensões de arquivo para conseguir acompanhar esta documentação, então certifique-se de **ATIVAR AS EXTENSÕES DE ARQUIVO** antes de começar.

No Windows, isso funciona abrindo uma pasta qualquer e clicando na seta no lado superior direito para expandir o menu abaixo.

Depois vá até a aba **Exibir** e ative **Extensões de nome de arquivo**.

<br>
<img width="764" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1f0a0864-1ad8-4f63-be3a-ab18385539e6"> 

### Preparação

Vamos começar criando uma nova pasta para o conteúdo do arquivo FMA.
Neste exemplo, vamos chamar a pasta de `fancymenu_animation`.

Dentro dessa pasta, crie mais duas pastas. A primeira **tem** que se chamar `frames` e a segunda **tem** que se chamar `intro_frames`.

Agora, na mesma pasta, crie um novo arquivo TXT e renomeie-o para `metadata.json`.
Certifique-se de que o arquivo não continue sendo um TXT. Você **precisa** alterar a extensão do arquivo para `json`.

Agora você deve ter uma pasta chamada `fancymenu_animation` e, dentro dela, uma pasta chamada `frames`, uma pasta chamada `intro_frames` e um arquivo JSON chamado `metadata.json`.

<br>
<img width="700" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/e29f6666-ee4a-4d79-b7e2-1b640f40ce78">

### O JSON de Metadados

Este é o arquivo que diz ao FancyMenu como ele deve lidar com a sua textura FMA.
Ele contém informações como o tempo de cada quadro (por quanto tempo um quadro fica visível) e a contagem de loops.

Abra o arquivo `metadata.json` com um editor de texto.

Copie este texto para o arquivo:

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

Este é o modelo básico de como o arquivo deve ficar.
Agora você pode personalizá-lo como quiser.

#### `loop_count`

Isso controla quantas vezes a textura deve repetir o loop (reiniciar sua animação).

Definir isso como `0` significa que ela vai repetir indefinidamente. Ela *nunca vai parar*.

Qualquer valor maior que `0` indica quantas vezes a textura será reproduzida. Por exemplo, definir o valor como `1` faz a textura tocar apenas uma vez e então parar no último quadro; `2` faz ela tocar duas vezes e então parar no último quadro, *e assim por diante*.

#### `frame_time`

Este é o tempo de quadro universal em **milissegundos** para os quadros da textura animada.
Tempo de quadro significa por quanto tempo o quadro fica visível antes de a animação ir para o próximo quadro.

#### `frame_time_intro`

Isso é basicamente o mesmo que `frame_time`, mas para os quadros de **introdução** da sua textura animada.
Os quadros de introdução são **opcionais** e você aprenderá mais sobre eles mais adiante.

#### `custom_frame_times`

Isso é **opcional** e pode ser usado para substituir o tempo de quadro de quadros específicos (que não sejam de introdução).
Por exemplo, você quer que todos os seus quadros sejam exibidos por `41` milissegundos, então define `frame_time` como `41`, mas quer que o primeiro e o segundo quadros sejam exibidos por `5000` milissegundos.

Nesse caso, você faria assim:

```json
{
  "loop_count": 0,
  "frame_time": 41,
  "frame_time_intro": 41,
  "custom_frame_times": {
    0: 5000,
    1: 5000
  },
  "custom_frame_times_intro": {
  }
}
```

Os quadros começam em zero, o que significa que o primeiro quadro da animação é `0`, o segundo é `1` e assim por diante.

Precisa haver uma **vírgula** no final de cada entrada de tempo de quadro personalizado, **exceto** na última!

#### `custom_frame_times_intro`

Isso é exatamente igual a `custom_frame_times`, mas neste caso para os quadros de **introdução**. Os quadros de introdução são **opcionais** e você aprenderá mais sobre eles mais adiante.

É isso para o arquivo `metadata.json`. Salve-o agora e feche o editor de texto.

### Os Quadros

> É recomendável usar no máximo **200 quadros** com resolução máxima de **1080p** por animação, porque animações consomem muita memória e não são vídeos. Elas foram feitas para serem usadas em loops animados curtos, não para reproduzir vídeos completos a 24 FPS.
{.is-danger}

Os quadros da sua textura animada vão para a pasta `frames`.

Os quadros precisam ser **ARQUIVOS PNG**! **NÃO HÁ SUPORTE PARA JPEG E OUTROS FORMATOS**!

Cada quadro **tem que** ser chamado apenas pelo número do quadro e pela extensão do arquivo.
O primeiro quadro deve se chamar `0.png`, o segundo `1.png`, o terceiro `2.png` e assim por diante.
A textura **NÃO VAI FUNCIONAR** se os nomes dos arquivos estiverem inválidos!

Para **extrair quadros de vídeos**, consulte [esta página da documentação](/ffmpeg-frames).

<br>
<img width="574" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/eac54695-b57a-4919-8740-4e5c8aad649c">

### A Introdução

Este recurso é **OPCIONAL**.

O recurso de **introdução** dos arquivos FMA é uma forma especial de reproduzir alguns quadros **antes** de os quadros reais da pasta `frames` começarem a tocar. 

A introdução **nunca entra em loop** e só toca na primeira vez em que a animação é reproduzida, o que permite mostrar algo como uma animação de transição antes de a animação principal começar a tocar em loop.

Os quadros de introdução vão para a pasta `intro_frames` e funcionam da mesma forma que os quadros normais:

Os quadros precisam ser **ARQUIVOS PNG**! **NÃO HÁ SUPORTE PARA JPEG E OUTROS FORMATOS**!

Cada quadro **tem que** ser chamado apenas pelo número do quadro e pela extensão do arquivo.
O primeiro quadro deve se chamar `0.png`, o segundo `1.png`, o terceiro `2.png` e assim por diante.
A textura **NÃO VAI FUNCIONAR** se os nomes dos arquivos estiverem inválidos!

### Empacotando o Arquivo FMA

Agora tudo o que é importante está na pasta `fancymenu_animation`, então você já pode empacotar o seu arquivo FMA!

Empacotar o arquivo FMA basicamente significa compactar o conteúdo da pasta em um arquivo ZIP.
O conteúdo precisa estar na **RAIZ do arquivo ZIP**, então não pode estar dentro de uma pasta extra no ZIP.

No Windows, a maneira mais fácil de compactar o conteúdo do FMA em um arquivo ZIP é selecionando tudo na pasta `fancymenu_animation` e depois **clicando com o botão direito** no arquivo `metadata.json`. No menu de contexto que abrir, clique em **Enviar para -> Pasta compactada (zipada)**.

<br>
<img width="752" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/5b7e7670-5403-410e-943c-283bfe6d585c">

Agora deve existir um novo arquivo ZIP na pasta `fancymenu_animation` chamado `metadata.zip`, `frames.zip` ou `intro_frames.zip`.

<br>
<img width="700" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/987f7989-dff7-43b4-a54c-0898969827f5">

Quando você abrir esse arquivo, o conteúdo deve parecer com isto:

<img width="700" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/f1642a39-e14c-47a7-90f6-8a737e8ec75f">

Agora você precisa renomear o arquivo para `fancymenu_animation.fma`. Certifique-se de **SUBSTITUIR** o `.zip` por `.fma`, para que ele deixe de ser um ZIP.

Claro, você pode mudar a parte `fancymenu_animation` para o nome que quiser, mas certifique-se de que continue sendo um arquivo `.fma`!

Pronto! Agora você tem um arquivo FMA que, com sorte, está funcionando!

# Usando Arquivos AFMA e FMA no FancyMenu

> [!IMPORTANT]
> Arquivos AFMA/FMA são considerados **texturas animadas**, então você os adiciona por meio de entradas de **Imagem**. Quase tudo que aceita imagens (PNG, JPEG, GIF etc.) também aceitará arquivos FMA e AFMA.

Você pode usar arquivos AFMA/FMA como qualquer outro formato de imagem/textura animada. O FancyMenu os vê como uma imagem normal, então você pode usá-los em qualquer lugar onde seja possível definir uma textura, como em **elementos de Imagem** ou **fundos de menu de Imagem**.

Certifique-se de que o arquivo AFMA/FMA esteja na pasta `/config/fancymenu/assets/`, porque o FancyMenu só consegue carregar texturas e outros recursos da sua pasta `assets`.
