---
title: Modelos de Botões e Sliders
description: >-
  Como usar modelos de botões/sliders para aplicar um design específico de
  botão/slider a TODOS os botões de uma vez.
---

# Usando Elementos de Botão como Modelos para Botões e Sliders

É possível usar um elemento de Botão como modelo para outros botões e até sliders. Ao fazer isso, você pode aplicar um design específico de botão/slider a TODOS os botões/sliders de um menu ou até mesmo a todos os menus de uma vez quando usar um layout universal.

> [!IMPORTANT]
> Desde o FancyMenu 3.9.0, é recomendado usar [Customizações Globais](/global-customizations) em vez de Modelos de Botão/Slider sempre que possível, pois elas podem substituir texturas nativas de botões e sliders globalmente sem usar um pacote de recursos. Use customizações globais para estilização ampla da interface nativa e use modelos apenas quando precisar de comportamento específico do layout.

# Importante Antes de Começar

Se você quiser apenas alterar a textura de um único botão ou slider, o mais fácil e recomendado é simplesmente **clicar com o botão direito** no botão ou slider (nativo e personalizado) no editor. Há uma opção para definir as **Texturas de Fundo** (e as texturas do controle do slider) para botões e sliders.

# O que é um Botão Modelo?

Um botão modelo é um tipo especial de botão personalizado no FancyMenu que permite controlar como outros botões e sliders se parecem e se comportam. É como criar um design mestre que muitos outros elementos seguirão.

Quando você cria um botão modelo, pode fazer com que vários botões ou sliders compartilhem o mesmo:
- Tamanho (largura e altura)
- Posição
- Visibilidade
- Opacidade (o quanto é transparente)
- Rótulos de texto
- **Texturas do botão** (compartilhadas automaticamente quando texturas personalizadas são definidas)

Isso é extremamente útil quando você quer deixar seu menu consistente ou quando precisa atualizar vários botões de uma vez!

# Quem Pode Usar Modelos?

Apenas **botões personalizados** podem funcionar como modelos. No entanto, esses modelos podem ser aplicados a:
- Botões nativos (os botões padrão do Minecraft)
- Botões personalizados (botões que você cria no FancyMenu)
- Sliders nativos (como controles de volume)
- Sliders personalizados (sliders que você cria no FancyMenu)

# Como Criar um Botão Modelo

1. Abra o editor do FancyMenu para a tela que você quer personalizar
2. Adicione um novo elemento de botão personalizado ao seu layout
3. Clique com o botão direito no seu novo botão
4. Selecione "Template Settings" no menu
5. Clique em "Is Template: ON" para ativar o modo de modelo

Seu botão agora estará pronto para funcionar como modelo para outros botões e sliders!

# Opções de Compartilhamento do Modelo

Você pode escolher quais tipos de elementos seu modelo afetará:
- **Buttons** - Seu modelo afetará apenas botões (nativos e personalizados)
- **Sliders** - Seu modelo afetará apenas sliders (nativos e personalizados)

Para definir essa opção:
1. Clique com o botão direito no seu botão modelo
2. Vá para "Template Settings"
3. Clique em "Share With: [Current Option]" para alternar entre as opções

> **Importante**: Você pode ter dois modelos ativos ao mesmo tempo - um para botões E um para sliders. Isso significa que você pode criar designs de modelo separados para diferentes tipos de elemento na mesma tela!
{.is-warning}


# O que Pode Ser Modelado

Você pode controlar exatamente quais propriedades seu modelo compartilhará com outros elementos:

## Propriedades que Podem Ser Ativadas/Desativadas:

1. Clique com o botão direito no seu botão modelo
2. Vá para "Template Settings" 
3. Ative ou desative qualquer uma destas opções:
   - **Width** - Faz com que todos os elementos afetados tenham a mesma largura do seu modelo
   - **Height** - Faz com que todos os elementos afetados tenham a mesma altura do seu modelo
   - **X Position** - Coloca todos os elementos afetados na mesma coordenada X do seu modelo
   - **Y Position** - Coloca todos os elementos afetados na mesma coordenada Y do seu modelo
   - **Opacity** - Dá a todos os elementos afetados a mesma transparência do seu modelo
   - **Visibility** - Controla se os elementos afetados serão mostrados ou ocultados
   - **Label** - Faz com que todos os elementos afetados usem o mesmo texto do seu modelo

## Propriedades que Sempre São Compartilhadas:

- **Texturas do botão** - Quando você define texturas personalizadas no seu modelo, elas serão aplicadas automaticamente a todos os elementos afetados
  - Diferentemente de outras propriedades, o compartilhamento de texturas não pode ser desativado
  - As texturas só são aplicadas quando texturas personalizadas realmente estão definidas no modelo
  - Se nenhuma textura personalizada estiver definida, serão usadas as texturas originais do elemento

# Personalizando a Aparência do Modelo

Seu botão modelo pode ser personalizado como qualquer outro botão:

1. Clique com o botão direito no seu botão modelo
2. Você pode definir:
   - Texturas do botão (estados normal, hover e inativo)
   - Rótulos (normal e hover)
   - Sons (hover e clique)
   - Tooltips

Para botões, você pode definir texturas personalizadas para diferentes estados:
- Fundo normal (quando não está interagindo)
- Fundo ao passar o mouse (quando o cursor está sobre ele)
- Fundo inativo (quando o botão está desativado)

Para sliders, você também pode definir:
- Texturas do controle do slider
- Texturas do fundo do slider

# Dicas Importantes

1. **Botões modelo não aparecerão no jogo** - Eles são visíveis apenas no editor, então coloque-os onde for mais conveniente.

2. **Você pode ter dois modelos ativos simultaneamente** - Um modelo para botões e um modelo para sliders podem estar ativos ao mesmo tempo.

3. **Apenas um modelo por tipo fica ativo** - Se você tiver vários modelos de botão, apenas o de cima na sua lista de elementos será usado para botões. O mesmo se aplica a modelos de sliders.

4. **As alterações no modelo são atualizadas instantaneamente** - Quando você edita seu modelo, todos os botões e sliders afetados serão atualizados imediatamente.

5. **Use o modo de compartilhamento correto** - Lembre-se de que o modo "Buttons" não afeta sliders, e o modo "Sliders" não afeta botões.

6. **Aplique propriedades seletivamente** - Você não precisa aplicar todas as propriedades. Por exemplo, talvez você queira usar um modelo apenas para as texturas e o tamanho, mas permitir que os elementos mantenham suas posições originais.

7. **As texturas sempre são compartilhadas quando definidas** - Diferentemente de outras propriedades, qualquer textura personalizada que você aplicar ao modelo será compartilhada automaticamente com os elementos correspondentes. Você não precisa ativar/desativar esse recurso.

# Exemplos de Uso

- Criar um estilo consistente para todos os botões de uma tela
- Fazer com que todos os sliders combinem com seu tema personalizado com um modelo separado
- Criar um "modo oculto" em que você pode mostrar/ocultar vários botões de uma vez
- Alterar o tamanho de muitos botões com apenas uma edição
- Dar a todos os botões do seu menu as mesmas texturas e sons personalizados
