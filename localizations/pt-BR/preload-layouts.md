---
title: Pré-Carregar Recursos
description: >-
  Como pré-carregar recursos para que estejam prontos para uso assim que o jogo
  terminar de carregar.
---

# Pré-Carregar Recursos

O pré-carregamento prepara recursos selecionados antes que um menu precise deles. Use isso para recursos que, de outra forma, piscam, mostram um primeiro quadro preto ou demoram para iniciar.

# Adicionar Recursos ao Pré-Carregador

Abra **Personalização -> Pré-Carregar Recursos**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

A lista aceita recursos suportados de imagem, animação, áudio, vídeo e texto de arquivos locais, URLs da web ou pacotes de recursos. Ela não pré-carrega uma página do [Browser](./elements#browser) ao vivo.

O pré-carregador inicia durante a inicialização do jogo e nos recarregamentos de recursos do Minecraft. Ele aguarda cada entrada concluir ou falhar antes de continuar, com um limite de dois minutos por entrada.

Os recursos carregados permanecem em cache até o FancyMenu liberar os recursos durante um recarregamento ou ao encerrar o cliente. **Personalização -> Recarregar FancyMenu** libera o cache, mas não executa o pré-carregador novamente.

O pré-carregamento aumenta o tempo de carregamento e o uso de RAM/VRAM. Adicione apenas os recursos que precisam estar prontos imediatamente; remova entradas grandes se o cliente ficar sem memória.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Pré-Carregando Slideshows e Panoramas

Adicionar um [slideshow](./slideshows) carrega todas as suas imagens e a sobreposição opcional. Adicionar um [panorama](./panoramas) carrega todas as seis faces e a sobreposição opcional.

**Personalização -> Recarregar FancyMenu** não executa o pré-carregador. Use um recarregamento de recursos do Minecraft ou reinicie o jogo depois de alterar a lista de pré-carregamento.
