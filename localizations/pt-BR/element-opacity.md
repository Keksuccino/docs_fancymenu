---
title: Opacidade de Elementos
description: Como controlar a opacidade dos elementos.
---

# Opacidade de Elementos

A maioria dos elementos no FancyMenu (com algumas exceções) suporta a configuração da opacidade por meio do menu de clique com o botão direito.

O valor de opacidade dos elementos suporta placeholders, o que torna possível atualizar dinamicamente sua opacidade com base no placeholder.

Isso torna possível criar uma lógica personalizada de desaparecimento/aparecimento ao usar em combinação com elementos Ticker para atualizar valores de variáveis e, então, aplicá-los como opacidade via placeholders.

Para definir a opacidade dos elementos, **clique com o botão direito no elemento -> Opacidade -> Definir**.

# Aparição/Desaparecimento dos Elementos

Se você quiser apenas fazer elementos aparecerem ou desaparecerem gradualmente, provavelmente é mais fácil usar o recurso de transição gradual integrado dos elementos. Você pode ativar a transição gradual no menu de clique com o botão direito dos elementos.

Esse recurso faz com que os elementos apareçam gradualmente toda vez que carregam, seja no carregamento inicial ao abrir um menu ou quando os requisitos de carregamento do elemento fazem com que ele seja carregado. Eles desaparecerão gradualmente sempre que seus requisitos de carregamento fizerem com que sejam descarregados/invisíveis.

O recurso de transição gradual permite definir uma velocidade de transição para controlar o quão rápido um elemento deve aparecer ou desaparecer gradualmente.
