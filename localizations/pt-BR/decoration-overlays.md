---
title: Sobreposições de Decoração
description: >-
  Adicione sobreposições visuais em tela cheia aos menus no editor de layout do
  FancyMenu.
---

# Sobreposições de Decoração

As Sobreposições de Decoração são efeitos em tela cheia que são renderizados na frente dos elementos do seu menu.

Elas são úteis quando você quer adicionar atmosfera ou movimento a um menu sem construir esses efeitos manualmente.

Exemplos comuns:

- Adicione **Nevasca** para um menu de inverno com acúmulo de neve.
- Adicione **Chuva** para um visual de tempestade com poças e goteiras.
- Adicione **Vaga-lumes** para um menu calmo com estilo noturno.
- Adicione **Luzes de Cordão** para temas festivos ou decorativos de menu.
- Adicione **Folhas**, **Fogos de artifício** ou **Confete** para menus sazonais/de eventos.
- Adicione a sobreposição **Navegador** para mostrar uma camada em tela cheia de página da web/vídeo.

# Onde Encontrar

Abra um layout no editor de layout e, em seguida, clique com o botão direito no fundo do editor e abra **Sobreposições de Decoração**.

# Início Rápido

1. Abra um layout no editor de layout.
2. Clique com o botão direito no fundo (área vazia).
3. Abra **Sobreposições de Decoração**.
4. Selecione um tipo de sobreposição.
5. Defina **Mostrar Sobreposição** como **Ativado**.
6. Configure as definições da sobreposição.
7. Salve o layout e teste a tela.

# Como os Tipos de Sobreposição Funcionam

Cada tipo de sobreposição tem seu próprio submenu e seu próprio alternador **Mostrar Sobreposição**.

- Você pode ativar apenas os tipos que quiser.
- Você pode combinar vários tipos ativados em um único layout.
- As configurações são por tipo de sobreposição (por exemplo: cor, intensidade, velocidade, densidade, escala, comportamento especial).

> [!INFO]
> É possível empilhar várias instâncias do mesmo tipo de sobreposição usando vários layouts com o mesmo tipo ativado.

# Tipos de Sobreposição

- **Nevasca**: neve caindo com acúmulo opcional de neve em superfícies/botões.
- **Chuva**: chuva com poças, goteiras e flashes opcionais de trovão.
- **Vaga-lumes**: grupos de vaga-lumes em movimento com quantidade de grupos, densidade, tamanho e cor configuráveis.
- **Luzes de Cordão**: combinações de cordões configuráveis, cores das luzes, comportamento de vento/piscar e modo de cores festivas.
- **Folhas**: folhas caindo com cores, vento, velocidade, escala e densidade configuráveis.
- **Fogos de artifício**: fogos de artifício frequentes com quantidade, tamanho da explosão e escala configuráveis.
- **Confete**: chuva de confete com modo opcional de confete ao clicar com o mouse.
- **Navegador**: sobreposição de navegador em tela cheia com configurações de URL e mídia.
- **Shader GLSL**: sobreposição de shader personalizado em tela cheia (para visuais baseados em shader, animados ou estáticos).

# Sobreposição do Navegador: Interativa vs Passiva

A sobreposição de Navegador pode ser configurada como um navegador interativo ou como uma camada visual passiva.

- As configurações **Processar Mouse/Teclado** controlam se o próprio navegador lida com a entrada.
- As configurações **Consumir Mouse/Teclado** controlam se a entrada é bloqueada para o menu atrás dele.

Exemplos práticos de configuração:

- Navegador interativo na frente: ative **Processar** e **Consumir**.
- Camada de navegador apenas visual: desative **Processar** e desative **Consumir**.

> [!IMPORTANT]
> A sobreposição de decoração **Navegador** requer o mod **MCEF**.
