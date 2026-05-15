---
title: Efeito Parallax
description: Como aplicar um efeito parallax ao plano de fundo do menu e aos elementos.
---

# O que é o Efeito Parallax?

O efeito parallax é um truque visual interessante que faz os fundos e elementos do seu menu parecerem ter profundidade. Quando você move o cursor do mouse, os elementos com parallax ativado se movem ligeiramente, criando a ilusão de um espaço 3D em um menu 2D.

Pense nisso como quando você está em um carro: coisas mais próximas de você (como placas de estrada) parecem se mover mais rápido do que coisas distantes (como montanhas). No FancyMenu, essa mesma ideia cria uma experiência mais dinâmica e interativa.

# Onde Você Pode Usar Parallax no FancyMenu?

No FancyMenu, você pode usar o efeito parallax em dois lugares principais:

1. **Fundos do Menu**: Faz com que todo o fundo do menu se mova levemente com o cursor do mouse
2. **Elementos**: Faz com que elementos individuais (como imagens, botões ou texto) se movam de forma independente

# Como Usar Parallax em Fundos de Menu

Adicionar um efeito parallax ao fundo do menu é super fácil:

1. Abra o editor de menu pressionando **CTRL+ALT+C** para mostrar a barra de menu, depois vá para **Customização**
2. Crie um novo layout ou edite um existente
3. Clique em **Layout → Propriedades** 
4. Abra **Fundos do Menu**
5. Escolha **Imagem** como tipo de fundo
6. Configure seu fundo de imagem:
   - Escolha uma imagem (local ou da web)
   - Ative **Efeito Parallax** clicando no botão de alternância
   - Defina a **Intensidade do Efeito Parallax X** e a **Intensidade do Efeito Parallax Y** (entre 0.0 e 1.0)
   - Opcionalmente, ative **Inverter Movimento Parallax** para mudar a direção

> **Dica**: Quanto maior o valor da intensidade, mais o seu fundo vai se mover. O FancyMenu 3.9.0 permite definir a intensidade de X e Y separadamente, então você pode deixar o movimento mais forte na horizontal do que na vertical, ou o contrário.
{.is-info}

# Como Usar Parallax em Elementos Individuais

Você também pode adicionar parallax a elementos individuais para criar efeitos em camadas:

1. Selecione qualquer elemento no editor clicando nele
2. Clique com o botão direito no elemento para abrir o menu de contexto
3. Role para baixo e encontre **Efeito Parallax: Ativado/Desativado**
4. Mude para **Ativado**
5. Ajuste os valores de **Intensidade Parallax X** e **Intensidade Parallax Y** (entre 0.0 e 1.0)
6. Opcionalmente, ative **Inverter Parallax** para mudar a direção do movimento

# Dicas para Criar Efeitos Parallax Incríveis

## Organize os Elementos em Camadas

Crie profundidade usando diferentes valores de intensidade parallax para diferentes elementos. Você pode ajustar X e Y separadamente:

- **Fundo**: Intensidade menor (0.1-0.3)
- **Elementos da camada intermediária**: Intensidade média (0.3-0.6)
- **Elementos em primeiro plano**: Intensidade maior (0.6-0.9)

Isso cria um efeito 3D convincente conforme você move o mouse!

## Combine Parallax Normal e Invertido

Tente definir alguns elementos como **Inverter Movimento Parallax: Ativado** e outros como **Desativado**. Isso faz com que os elementos se movam em direções opostas, aumentando o efeito de profundidade.

## Não Exagere

Movimento demais pode distrair. Use o efeito parallax com moderação, especialmente com valores de intensidade altos.

# Solução de Problemas

## O Parallax Não Está Funcionando?

1. Certifique-se de que o efeito parallax está ativado
2. Verifique se a intensidade do parallax não está definida como 0
4. Confirme que a opção "Slide Wide Images From Left To Right" está desativada (essa opção entra em conflito com o parallax)

## O Movimento do Parallax Está Muito Rápido/Lento?

Ajuste os valores de **Intensidade Parallax X/Y**:
- Valores mais baixos (mais próximos de 0) = movimento mais lento e sutil
- Valores mais altos (mais próximos de 1) = movimento mais rápido e mais dramático

# Considerações Finais

O efeito parallax é uma ótima maneira de fazer seus menus do Minecraft parecerem mais vivos e interativos. Experimente diferentes combinações de parallax para o fundo e para os elementos para criar layouts impressionantes e dinâmicos que respondem aos movimentos do seu mouse!

Lembre-se: os melhores efeitos costumam ser sutis — um pouco de movimento já faz muita diferença para criar uma experiência imersiva.
