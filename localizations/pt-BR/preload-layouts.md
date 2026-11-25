---
title: Pré-carregar recursos
description: >-
  Como pré-carregar recursos para que estejam prontos para uso assim que o jogo
  terminar de carregar.
sourceBlobSha: 8eca400e05987468c1fd0dc29faa5267083e38d0
---

# Pré-carregar recursos

O pré-carregamento prepara recursos selecionados antes que um menu precise deles. Use-o para recursos que, de outra forma, piscam, exibem um primeiro quadro preto ou demoram para iniciar.

# Adicionar recursos ao pré-carregador

Acesse **Personalização -> Pré-carregar recursos**.

<br>

<img width="350" alt="Screenshot_1" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/3265da80-1bbc-4634-bd94-ba2795d7e3f2">

A lista aceita recursos compatíveis de imagem, animação, áudio, vídeo e texto, provenientes de arquivos locais, URLs da web ou pacotes de recursos. Ela não pré-carrega uma página ativa do [Navegador](/elements#browser).

O pré-carregador é iniciado durante a inicialização do jogo e ao recarregar os recursos do Minecraft. Ele aguarda cada item terminar de carregar ou falhar antes de continuar, com um limite de dois minutos por item.

Os recursos carregados permanecem em cache até que o FancyMenu os libere durante uma recarga ou o encerramento do cliente. **Personalização -> Recarregar FancyMenu** libera o cache, mas não executa o pré-carregador novamente.

O pré-carregamento aumenta o tempo de carregamento e o uso de RAM/VRAM. Adicione apenas os recursos que precisam estar prontos imediatamente; remova itens grandes se o cliente ficar sem memória.

<br>

<img width="731" alt="Screenshot_2" src="https://github.com/Keksuccino/FancyMenu/assets/35544624/04632d52-c2a9-4f70-9d0a-e88c4cacc4c1">

# Pré-carregar apresentações de slides e panoramas

Adicionar uma [apresentação de slides](/slideshows) carrega todas as imagens e a sobreposição opcional. Adicionar um [panorama](/panoramas) carrega as seis faces e a sobreposição opcional.

**Personalização -> Recarregar FancyMenu** não executa o pré-carregador. Recarregue os recursos do Minecraft ou reinicie o jogo depois de alterar a lista de pré-carregamento.
