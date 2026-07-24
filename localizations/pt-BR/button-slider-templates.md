---
title: Modelos de Botão e Slider
description: >-
  Como usar modelos de botão/slider para aplicar um design específico de
  botão/slider a TODOS os botões de uma vez.
---
# Usando Elementos de Botão como Modelos para Botões e Sliders

É possível usar um elemento de Botão como modelo para outros botões e até sliders. Fazendo isso, você pode aplicar um design específico de botão/slider a TODOS os botões/sliders em um menu ou até mesmo a todos os menus de uma vez ao usar um layout universal.

> [!IMPORTANT]
> Prefira [Global Customizations](./global-customizations) para estilização ampla de botões e sliders Vanilla. Use Modelos de Botão/Slider quando o comportamento precisar ser específico do layout.

# Importante Antes de Começar

Para um único botão ou slider, **clique com o botão direito** nele no editor e edite diretamente as **Background Textures** ou as texturas do controle deslizante.

# O que é um Botão de Modelo?

Um botão de modelo é um tipo especial de botão personalizado no FancyMenu que permite controlar como outros botões e sliders parecem e se comportam. É como criar um design mestre que muitos outros elementos seguirão.

Quando você cria um botão de modelo, pode fazer com que muitos botões ou sliders compartilhem o mesmo:
- Tamanho (largura e altura)
- Posição
- Visibilidade
- Opacidade (o quanto são transparentes)
- Rótulos de texto
- **Texturas do botão** (compartilhadas automaticamente quando texturas personalizadas são definidas)

Isso é muito útil quando você quer deixar seu menu consistente ou quando precisa atualizar vários botões de uma vez!

# Quem Pode Usar Modelos?

Apenas **botões personalizados** podem funcionar como modelos. No entanto, esses modelos podem ser aplicados a:
- Botões Vanilla (os botões padrão do Minecraft)
- Botões personalizados (botões que você cria no FancyMenu)
- Sliders Vanilla (como controles de volume)
- Sliders personalizados (sliders que você cria no FancyMenu)

# Como Criar um Botão de Modelo

1. Abra o editor do FancyMenu para a tela que você deseja personalizar
2. Adicione um novo elemento de botão personalizado ao seu layout
3. Clique com o botão direito no seu novo botão
4. Selecione "Template Settings" no menu
5. Clique em "Is Template: ON" para ativar o modo de modelo

Seu botão agora estará pronto para funcionar como modelo para outros botões e sliders!

# Opções de Compartilhamento do Modelo

Você pode escolher quais tipos de elementos serão afetados pelo seu modelo:
- **Buttons** - Seu modelo afetará apenas botões (tanto Vanilla quanto personalizados)
- **Sliders** - Seu modelo afetará apenas sliders (tanto Vanilla quanto personalizados)

Para definir essa opção:
1. Clique com o botão direito no seu botão de modelo
2. Vá para "Template Settings"
3. Clique em "Share With: [Current Option]" para alternar entre as opções

> [!WARNING]
> **Importante**: Você pode ter dois modelos ativos ao mesmo tempo - um para botões E um para sliders. Isso significa que você pode criar designs de modelo separados para diferentes tipos de elementos na mesma tela!


# O que Pode Ser Modelado

Você pode controlar exatamente quais propriedades o seu modelo compartilhará com outros elementos:

## Propriedades que Podem Ser Ativadas/Desativadas:

1. Clique com o botão direito no seu botão de modelo
2. Vá para "Template Settings" 
3. Ative ou desative qualquer uma destas opções:
   - **Width** - Faz com que todos os elementos afetados tenham a mesma largura do seu modelo
   - **Height** - Faz com que todos os elementos afetados tenham a mesma altura do seu modelo
   - **X Position** - Coloca todos os elementos afetados na mesma coordenada X do seu modelo
   - **Y Position** - Coloca todos os elementos afetados na mesma coordenada Y do seu modelo
   - **Opacity** - Faz com que todos os elementos afetados tenham a mesma transparência do seu modelo
   - **Visibility** - Controla se os elementos afetados serão mostrados ou ocultados
   - **Label** - Faz com que todos os elementos afetados usem o mesmo texto do seu modelo

## Propriedades que São Sempre Compartilhadas:

- **Texturas do botão** - Quando você define texturas personalizadas no seu modelo, elas serão aplicadas automaticamente a todos os elementos afetados
  - Diferentemente de outras propriedades, o compartilhamento de texturas não pode ser desativado
  - As texturas só são aplicadas quando texturas personalizadas são realmente definidas no modelo
  - Se nenhuma textura personalizada for definida, as texturas originais do elemento serão usadas

# Personalizando a Aparência do Modelo

Seu botão de modelo pode ser personalizado como qualquer outro botão:

1. Clique com o botão direito no seu botão de modelo
2. Você pode definir:
   - Texturas do botão (estados normal, ao passar o mouse e inativo)
   - Rótulos (normal e ao passar o mouse)
   - Sons (ao passar o mouse e ao clicar)
   - Tooltips

Para botões, você pode definir texturas personalizadas para diferentes estados:
- Fundo normal (quando não estiver interagindo)
- Fundo ao passar o mouse (quando o mouse estiver sobre ele)
- Fundo inativo (quando o botão estiver desativado)

Para sliders, você também pode definir:
- Texturas do controle do slider
- Texturas do fundo do slider

# Dicas Importantes

1. **Botões de modelo não aparecerão no jogo** - Eles só ficam visíveis no editor, então coloque-os onde for mais conveniente.

2. **Você pode ter dois modelos ativos simultaneamente** - Um modelo para botões e um modelo para sliders podem ficar ativos ao mesmo tempo.

3. **Apenas um modelo por tipo fica ativo** - Se você tiver vários modelos de botão, apenas o que estiver no topo da sua lista de elementos será usado para botões. O mesmo se aplica aos modelos de slider.

4. **As alterações no modelo são atualizadas instantaneamente** - Quando você editar seu modelo, todos os botões e sliders afetados serão atualizados imediatamente.

5. **Use o modo de compartilhamento correto** - Lembre-se de que o modo "Buttons" não afetará sliders, e o modo "Sliders" não afetará botões.

6. **Aplique propriedades de forma seletiva** - Você não precisa aplicar todas as propriedades. Por exemplo, talvez você queira modelar apenas as texturas e o tamanho, mas permitir que os elementos mantenham suas posições originais.

7. **Texturas são sempre compartilhadas quando definidas** - Diferentemente de outras propriedades, quaisquer texturas personalizadas que você aplicar ao modelo serão compartilhadas automaticamente com os elementos correspondentes. Você não precisa ativar ou desativar esse recurso.

# Exemplos de Uso

- Criar um estilo consistente para todos os botões de uma tela
- Fazer com que todos os sliders combinem com seu tema personalizado usando um modelo separado
- Criar um "modo oculto" em que você pode mostrar/ocultar vários botões de uma vez
- Alterar o tamanho de vários botões com apenas uma edição
- Dar a todos os botões do seu menu as mesmas texturas e sons personalizados
