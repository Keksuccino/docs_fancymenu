---
title: Sobreposições de Decoração
description: >-
  Adicione sobreposições visuais em tela cheia aos menus no editor de layout do
  FancyMenu.
---
# Sobreposições de Decoração

As Sobreposições de Decoração são efeitos em tela cheia que são renderizados na frente dos elementos do seu menu.

Elas são úteis quando você quer adicionar atmosfera ou movimento a um menu sem criar esses efeitos manualmente.

# Onde Encontrar

Abra um layout no editor de layout, depois clique com o botão direito no fundo do editor e abra **Sobreposições de Decoração**.

# Início Rápido

1. Abra um layout no editor de layout.
2. Clique com o botão direito no fundo (área vazia).
3. Abra **Sobreposições de Decoração**.
4. Selecione um tipo de sobreposição.
5. Defina **Show Overlay** como **Enabled**.
6. Configure as opções da sobreposição.
7. Salve o layout e teste a tela.

# Como os Tipos de Sobreposição Funcionam

Cada tipo de sobreposição tem seu próprio submenu e seu próprio alternador **Show Overlay**.

- Você pode ativar apenas os tipos que quiser.
- Você pode combinar vários tipos ativados em um único layout.
- As configurações são por tipo de sobreposição (por exemplo: cor, intensidade, velocidade, densidade, escala, comportamento especial).

> [!INFO]
> É possível empilhar várias instâncias do mesmo tipo de sobreposição usando vários layouts com o mesmo tipo ativado.

# Tipos de Sobreposição

- **Snowfall**: neve com acúmulo opcional em superfícies/botões.
- **Rainfall**: chuva com poças, pingos e flashes de trovão opcionais.
- **Fireflies**: grupos de vagalumes em movimento com quantidade de grupos, densidade, tamanho e cor configuráveis.
- **String Lights**: combinações de luzes em cordão configuráveis, cores das luzes, comportamento de vento/piscar e modo de cores natalinas.
- **Leaves**: folhas caindo com cores, vento, velocidade, escala e densidade configuráveis.
- **Fireworks**: fogos de artifício frequentes com quantidade, tamanho da explosão e escala configuráveis.
- **Confetti**: chuva de confete com modo opcional de confete ao clicar com o mouse.
- **Buddy**: um animal de estimação virtual interativo com fome, felicidade, energia, diversão, atividades, níveis, conquistas e estado persistente.
- **Browser**: sobreposição de navegador em tela cheia com URL e configurações de mídia.
- **GLSL Shader**: sobreposição de shader personalizado em tela cheia (para visuais animados ou estáticos baseados em shader).

# Animal de Estimação Virtual Buddy

A sobreposição **Buddy** é um animal de estimação virtual no estilo Tamagotchi, não apenas um personagem visual. Ele anda pela parte inferior da tela, exibe balões de pensamento para suas necessidades, reage à interação e mantém seu estado entre sessões do jogo.

## Necessidades e Controles

Buddy acompanha quatro valores de `0` a `100`:

- **Hunger** diminui com o tempo e é restaurado com comida.
- **Happiness** diminui com o tempo e aumenta com cuidados, incluindo carinho e brincadeiras.
- **Energy** diminui enquanto acordado e durante atividades, depois se regenera enquanto dorme.
- **Fun** diminui com o tempo e aumenta ao brincar.

Use estes controles do mouse e a tela de status para cuidar dele:

- **Clique com o botão esquerdo no Buddy** para fazer carinho. Clicar com o botão esquerdo enquanto ele dorme o acorda e aplica uma pequena penalidade de felicidade.
- **Clique com o botão direito no Buddy** para abrir a tela de status. A aba Stats mostra todas as quatro necessidades, nível e XP; a aba Achievements mostra o progresso das conquistas.
- Selecione **Feed** na tela de status e arraste a comida até o Buddy. A comida restaura fome e felicidade.
- Selecione **Play** na tela de status e depois arraste e solte a bola. A bola usa o movimento do mouse para calcular a velocidade do arremesso, e o Buddy pode correr atrás, pegar, segurar e brincar com ela.
- Selecione **Sleep** quando o botão estiver disponível para restaurar energia. O Buddy também adormece automaticamente quando sua energia fica criticamente baixa.
- Às vezes o Buddy deixa cocô para trás. **Clique com o botão esquerdo no cocô** para limpá-lo. Deixar pelo menos três cocôs na tela reduz continuamente a felicidade até restarem menos de três; a quantidade máxima de cocôs é configurável.

## XP, Níveis e Conquistas

Cuidar do Buddy, limpar cocô, manter boas necessidades e concluir outros marcos concede XP. O Buddy começa no nível 1 e pode chegar ao nível 30. Níveis mais altos reduzem gradualmente a perda de fome, felicidade e energia (até 50% no nível 30) e melhoram vários efeitos de cuidado e XP.

As conquistas acompanham marcos de interação, status, nível, sessão e especiais. Abra a tela de status com um clique com o botão direito para inspecionar ambos os sistemas de progresso.

## Morte e Redefinição do Save

**Buddy Can Die** vem ativado por padrão. Se fome ou felicidade permanecerem continuamente em `0` por **10 horas reais**, o Buddy morre e é substituído por uma lápide. Aumentar a necessidade que chegou a zero antes que o temporizador expire redefine o temporizador dessa necessidade; desativar **Buddy Can Die** limpa ambos os temporizadores.

Para recomeçar após a morte, clique com o botão esquerdo na lápide. Você também pode usar **Reset Buddy Save** nas configurações da sobreposição Buddy a qualquer momento. Redefinir remove tanto o save do estado do pet quanto o save separado de nível/conquistas para essa instância da sobreposição.

> [!WARNING]
> Redefinir um save do Buddy remove permanentemente suas necessidades, nível, XP, conquistas, contadores de atividade e estado salvo do cocô.

## Persistência e Personalização

O estado do Buddy é salvo automaticamente a cada cerca de dois minutos e quando a tela dele é fechada. O estado do pet e o estado de nível usam arquivos JSON separados para cada instância da sobreposição dentro de `<game-directory>/fancymenu_data/buddy/`. Consulte [Locais de Armazenamento de Dados](./data-storage-locations) para a referência completa dos caminhos do FancyMenu.

As configurações da sobreposição também permitem substituir o atlas de sprites do Buddy, itens de interação, ícones de necessidade, texturas da tela de status e a lápide. As configurações avançadas de status controlam a perda gradual, os custos e ganhos de atividade, a eficácia dos cuidados, a quantidade máxima de cocôs e se a morte está ativada.

# Sobreposição do Navegador: Interativa vs. Passiva

A sobreposição Browser pode ser configurada tanto como um navegador interativo quanto como uma camada visual passiva.

- As configurações **Process Mouse/Keyboard** controlam se o próprio navegador processa a entrada.
- As configurações **Consume Mouse/Keyboard** controlam se a entrada é bloqueada para o menu atrás dele.

Exemplos práticos de configuração:

- Navegador interativo em primeiro plano: ative **Process** e **Consume**.
- Camada visual בלבד do navegador: desative **Process** e desative **Consume**.

> [!IMPORTANT]
> A sobreposição de decoração Browser requer o mod **[Rinku](https://modrinth.com/mod/rinku)**.
