---
title: Efeito de Paralaxe
description: Mova fundos e elementos com o cursor do mouse.
---

# Efeito de Paralaxe

A paralaxe desloca um fundo ou elemento com base no movimento do mouse para criar profundidade visual.

# Fundo de Menu com Imagem

1. Clique com o botão direito no fundo do editor de layout.
2. Abra [**Fundos de Menu**](./menu-backgrounds) -> **Imagem**.
3. Defina a origem da imagem.
4. Ative **Efeito de Paralaxe**.
5. Defina os valores de intensidade X e Y.
6. Opcionalmente, ative **Inverter Movimento de Paralaxe**.

Os valores X e Y controlam o movimento horizontal e vertical de forma independente. Use valores de `0.0` (nenhum) a `1.0` (máximo).

# Elementos

1. Clique com o botão direito em um [elemento](./elements).
2. Ative **Efeito de Paralaxe**.
3. Defina **Intensidade de Paralaxe X** e **Intensidade de Paralaxe Y**.
4. Opcionalmente, inverta o movimento.

Use menor intensidade para camadas distantes e maior intensidade para camadas em primeiro plano. Diferenças grandes ou camadas invertidas criam um efeito de profundidade mais forte.

# Solução de problemas

- Uma intensidade de `0` não produz movimento nesse eixo.
- **Deslizar Imagens Largas da Esquerda para a Direita** entra em conflito com a paralaxe do plano de fundo e deve ser desativado.
- Movimentos muito pequenos podem parecer em passos porque as posições da interface usam pixels inteiros.
