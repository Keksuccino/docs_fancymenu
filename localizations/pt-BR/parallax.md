---
title: Efeito Parallax
description: Como aplicar um efeito parallax ao plano de fundo do menu e aos elementos.
---
# O que é o Efeito Parallax?

O efeito parallax é um truque visual interessante que faz os planos de fundo e elementos do seu menu parecerem ter profundidade. Quando você move o cursor do mouse, os elementos com parallax ativado se movem ligeiramente, criando a ilusão de um espaço 3D em um menu 2D.

Pense nisso como quando você está andando de carro — coisas mais próximas de você (como placas na estrada) parecem se mover mais rápido do que coisas distantes (como montanhas). No FancyMenu, essa mesma ideia cria uma experiência mais dinâmica e interativa.

# Onde Você Pode Usar Parallax no FancyMenu?

No FancyMenu, você pode usar o efeito parallax em dois lugares principais:

1. **Planos de fundo do menu**: faz o fundo inteiro do menu se mover levemente com o cursor do mouse
2. **Elementos**: faz elementos individuais (como imagens, botões ou texto) se moverem de forma independente

# Como Usar Parallax nos Planos de Fundo do Menu

Adicionar um efeito parallax ao plano de fundo do menu é muito fácil:

1. Abra o editor de menus pressionando **CTRL+ALT+C** para exibir a barra de menu e depois vá para **Personalização**
2. Crie um novo layout ou edite um existente
3. Clique em **Layout → Propriedades**
4. Abra **Planos de Fundo do Menu**
5. Escolha **Imagem** como tipo de plano de fundo
6. Configure o plano de fundo com imagem:
   - Escolha uma imagem (local ou da web)
   - Ative **Efeito Parallax** clicando no botão de alternância
   - Defina a **Intensidade do Efeito Parallax X** e a **Intensidade do Efeito Parallax Y** (entre 0.0 e 1.0)
   - Opcionalmente, ative **Inverter Movimento Parallax** para alterar a direção

> **Dica**: quanto maior o valor da intensidade, mais o seu plano de fundo se moverá. O FancyMenu 3.9.0 permite definir as intensidades de X e Y separadamente, então você pode tornar o movimento mais forte na horizontal do que na vertical, ou o contrário.
{.is-info}

# Como Usar Parallax em Elementos Individuais

Você também pode adicionar parallax a elementos individuais para criar efeitos em camadas:

1. Selecione qualquer elemento no editor clicando nele
2. Clique com o botão direito no elemento para abrir o menu de contexto
3. Role para baixo e encontre **Efeito Parallax: Ativado/Desativado**
4. Altere para **Ativado**
5. Ajuste os valores de **Intensidade Parallax X** e **Intensidade Parallax Y** (entre 0.0 e 1.0)
6. Opcionalmente, ative **Inverter Parallax** para alterar a direção do movimento

# Dicas para Criar Efeitos Parallax Incríveis

## Organize seus Elementos em Camadas

Crie profundidade usando diferentes valores de intensidade parallax para elementos diferentes. Você pode ajustar X e Y separadamente:

- **Plano de fundo**: intensidade menor (0.1-0.3)
- **Elementos da camada do meio**: intensidade média (0.3-0.6)
- **Elementos do primeiro plano**: intensidade maior (0.6-0.9)

Isso cria um efeito 3D convincente conforme você move o mouse!

## Combine Parallax Normal e Invertido

Tente definir alguns elementos como **Inverter Movimento Parallax: Ativado** e outros como **Desativado**. Isso faz com que os elementos se movam em direções opostas, reforçando o efeito de profundidade.

## Não Exagere

Movimento demais pode distrair. Use o efeito parallax com moderação, especialmente com valores de intensidade altos.

# Solução de Problemas

## O Parallax Não Está Funcionando?

1. Verifique se você ativou o efeito parallax
2. Confirme se a intensidade do parallax não está definida como 0
4. Confirme que a opção "Slide Wide Images From Left To Right" está desativada (essa opção entra em conflito com o parallax)

## O Movimento do Parallax Está Muito Rápido/Lento?

Ajuste os valores de **Intensidade Parallax X/Y**:
- Valores menores (mais próximos de 0) = movimento mais lento e sutil
- Valores maiores (mais próximos de 1) = movimento mais rápido e mais dramático

## O Parallax Parece Impróprio ou Com Lag?

Essa é uma limitação do efeito parallax, já que o Minecraft usa coordenadas baseadas em inteiros (números inteiros). Então, é possível que o efeito pareça um pouco como se os elementos estivessem "pulando", mas isso não deve ser muito perceptível se você usar intensidades de parallax "normais" e não valores muito pequenos ou muito altos.
