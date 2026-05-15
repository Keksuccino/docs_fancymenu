---
title: Layouts Universais
description: Como criar e usar layouts universais.
---

# O que são Layouts Universais?

Layouts Universais são um recurso poderoso no FancyMenu que permite criar layouts que podem ser aplicados a **várias telas** em vez de apenas a uma tela específica. Isso os torna extremamente úteis para criar elementos de interface consistentes que aparecem em todo o jogo.

Pense nos Layouts Universais como layouts "globais" que podem aparecer em qualquer lugar do seu jogo.

# Por que usar Layouts Universais?

Layouts Universais são muito úteis quando você quer:

- Adicionar o mesmo fundo a todas as telas
- Criar um logo ou texto que apareça em várias telas
- Fazer elementos de áudio continuarem tocando entre várias telas
- Construir uma aparência consistente em todo o jogo

# Como os Layouts Universais funcionam

Quando você cria um Layout Universal, ele é carregado por padrão com **todas as telas** do jogo. Isso significa que qualquer elemento que você adicionar a um Layout Universal (como botões, imagens ou texto) vai aparecer em todas as telas.

Mas não se preocupe! Também é possível fazer com que o layout universal seja carregado apenas em telas específicas! Para isso, role até as seções de **lista negra** e **lista branca**.

# Criando um Layout Universal

1. Abra qualquer tela no jogo
2. Pressione **Ctrl+Alt+C** para mostrar o menu de personalização
3. Vá para **Layouts → Novo → Para Todas as Telas [Universal]**
4. Crie o seu layout com elementos como imagens, texto ou botões
5. Salve seu layout com um nome descritivo

# Gerenciando quais telas recebem seu Layout Universal

## Usando a Lista Negra

A lista negra permite especificar telas nas quais você NÃO quer que seu Layout Universal apareça:

1. No Editor de Layout, clique com o botão direito no fundo
2. Selecione **Configurações do Layout → Opções de Layout Universal**
3. Clique em **Adicionar Tela à Lista Negra**
4. Digite o identificador da tela (como `title_screen` para a tela inicial)

Agora seu Layout Universal vai aparecer em todas as telas, EXCETO nas que estiverem na lista negra.

## Usando a Lista Branca

A lista branca é o oposto — ela mostra seu Layout Universal SOMENTE em telas específicas:

1. No Editor de Layout, clique com o botão direito no fundo
2. Selecione **Configurações do Layout → Opções de Layout Universal**
3. Clique em **Adicionar Tela à Lista Branca**
4. Digite o identificador de cada tela em que você quer que o layout apareça

Ao usar uma lista branca, seu Layout Universal vai aparecer SOMENTE nas telas que você सूचीou.

# Encontrando identificadores de telas

Para adicionar telas à lista branca ou à lista negra, você precisa saber os identificadores delas:

1. Vá até a tela que deseja identificar
2. Pressione **Ctrl+Alt+C** para abrir o menu de personalização
3. Clique em **Personalização → Copiar Identificador da Tela Atual**
4. O identificador agora foi copiado para a sua área de transferência

Você pode colar esse identificador na lista branca ou na lista negra.

# Ativando a personalização para todas as telas

Não é possível ativar a personalização para todas as telas de uma vez.
Isso é intencional e evita que as pessoas quebrem o jogo acidentalmente ao ativar a personalização para uma tela modificada que não é suportada.

# Dicas avançadas

## Gerenciando a ordem de carregamento

Quando você tem tanto Layouts Universais quanto layouts específicos de tela, os Layouts Universais são carregados PRIMEIRO. Isso significa que layouts específicos de tela podem sobrescrever elementos dos Layouts Universais.

## Requisitos de carregamento

Você pode adicionar requisitos de carregamento ao seu Layout Universal para que ele seja carregado apenas em certas condições:

1. Clique com o botão direito no editor
2. Escolha **Configurações do Layout → Requisitos de Todo o Layout**
3. Adicione condições como horário do dia, sistema operacional ou outros requisitos
