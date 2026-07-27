---
title: Sobreposições de Decoração
description: >-
  Adicione sobreposições visuais em tela cheia aos menus no editor de layout do
  FancyMenu.
---
# Sobreposições de Decoração

As Sobreposições de Decoração são efeitos em tela cheia que são renderizados na frente dos elementos do seu menu.

Elas são úteis quando você quer adicionar atmosfera ou movimento a um menu sem construir esses efeitos manualmente.

# Onde Encontrar

Abra um layout no editor de layout, depois clique com o botão direito no fundo do editor e abra **Sobreposições de Decoração**.

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
- **Chuva**: chuva com poças, gotas e flashes de trovão opcionais.
- **Vagalumes**: grupos de vagalumes em movimento com quantidade de grupos, densidade, tamanho e cor configuráveis.
- **Luzes de Cordão**: combinações de cordões configuráveis, cores das luzes, comportamento de vento/piscar e modo de cores festivas.
- **Folhas**: folhas caindo com cores, vento, velocidade, escala e densidade configuráveis.
- **Fogos de Artifício**: fogos frequentes com quantidade, tamanho da explosão e escala configuráveis.
- **Confete**: chuva de confete com modo opcional de confete ao clicar com o mouse.
- **Buddy**: um bichinho virtual interativo com fome, felicidade, energia, diversão, atividades, níveis, conquistas e estado persistente.
- **Navegador**: sobreposição de navegador em tela cheia com URL e configurações de mídia.
- **Shader GLSL**: sobreposição de shader personalizada em tela cheia (para visuais animados ou estáticos baseados em shader).

# Bichinho Virtual Buddy

A sobreposição **Buddy** é um bichinho virtual no estilo Tamagotchi, não apenas um personagem visual. Ele anda pela parte inferior da tela, mostra balões de pensamento para suas necessidades, reage à interação e mantém seu estado entre sessões de jogo.

## Necessidades e Controles

Buddy acompanha quatro valores de `0` a `100`:

- **Fome** diminui com o tempo e é restaurada com comida.
- **Felicidade** diminui com o tempo e aumenta com cuidado, incluindo carinho e brincadeiras.
- **Energia** diminui enquanto acordado e durante atividades, e depois se regenera enquanto dorme.
- **Diversão** diminui com o tempo e aumenta enquanto brinca.

Use estes controles do mouse e a tela de status para cuidar dele:

- **Clique esquerdo no Buddy** para fazer carinho. Clicar com o botão esquerdo enquanto ele dorme o acorda e aplica uma pequena penalidade de felicidade.
- **Clique direito no Buddy** para abrir a tela de status. A aba Estatísticas mostra as quatro necessidades, nível e XP; a aba Conquistas mostra o progresso das conquistas.
- Selecione **Alimentar** na tela de status e depois arraste a comida até o Buddy. A comida restaura fome e felicidade.
- Selecione **Brincar** na tela de status e depois arraste e solte a bola. A bola usa o movimento do mouse para calcular a velocidade do arremesso, e o Buddy pode perseguir, pegar, segurar e brincar com ela.
- Selecione **Dormir** quando o botão estiver disponível para restaurar energia. Buddy também adormece automaticamente quando sua energia fica criticamente baixa.
- Buddy ocasionalmente deixa cocô para trás. **Clique esquerdo no cocô** para limpá-lo. Deixar pelo menos três cocôs na tela reduz continuamente a felicidade até que restem menos de três; o número máximo de cocôs é configurável.

## XP, Níveis e Conquistas

Cuidar do Buddy, limpar cocô, manter boas necessidades e completar outras metas concede XP. Buddy começa no nível 1 e pode chegar ao nível 30. Níveis mais altos reduzem gradualmente a perda de fome, felicidade e energia (até 50% no nível 30) e melhoram vários efeitos de cuidado e XP.

As conquistas acompanham marcos de interação, atributos, nível, sessão e especiais. Abra a tela de status com um clique direito para verificar ambos os sistemas de progressão.

## Morte e Redefinição do Salvamento

**Buddy Pode Morrer** vem ativado por padrão. Se fome ou felicidade permanecerem continuamente em `0` por **10 horas reais**, Buddy morre e é substituído por uma lápide. Aumentar a necessidade zerada antes que o temporizador expire redefine o temporizador dessa necessidade; desativar **Buddy Pode Morrer** limpa os dois temporizadores.

Para recomeçar após a morte, clique com o botão esquerdo na lápide. Você também pode usar **Redefinir Salvamento do Buddy** nas configurações da sobreposição Buddy a qualquer momento. A redefinição remove tanto o salvamento do estado do bichinho quanto o salvamento separado de níveis/conquistas dessa instância da sobreposição.

> [!WARNING]
> Redefinir um salvamento do Buddy remove permanentemente suas necessidades, nível, XP, conquistas, contadores de atividades e estado de cocô salvo.

## Persistência e Personalização

O estado do Buddy é salvo automaticamente aproximadamente a cada dois minutos e quando a tela dele é fechada. O estado do bichinho e o estado de progressão usam arquivos JSON separados para cada instância da sobreposição dentro de `<game-directory>/fancymenu_data/buddy/`. Consulte [Locais de Armazenamento de Dados](./data-storage-locations) para ver a referência completa do caminho do FancyMenu.

As configurações da sobreposição também permitem substituir o atlas de sprites do Buddy, itens de interação, ícones de necessidade, texturas da tela de status e a lápide. As configurações avançadas de atributos controlam a perda, os custos e ganhos de atividades, a eficácia do cuidado, o número máximo de cocôs e se a morte está habilitada.

# Sobreposição do Navegador: Interativo vs Passivo

A sobreposição de Navegador pode ser configurada como um navegador interativo ou como uma camada visual passiva.

- As configurações **Processar Mouse/Teclado** controlam se o próprio navegador lida com a entrada.
- As configurações **Consumir Mouse/Teclado** controlam se a entrada é bloqueada para o menu atrás dele.

Exemplos práticos de configuração:

- Navegador interativo em primeiro plano: ative **Processar** e **Consumir**.
- Camada de navegador apenas visual: desative **Processar** e desative **Consumir**.

> [!IMPORTANT]
> A sobreposição de decoração Browser requer o mod **MCEF**.
