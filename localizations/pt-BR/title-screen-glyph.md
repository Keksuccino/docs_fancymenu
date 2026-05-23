---
title: Glyph da Tela de Título
description: >-
  Como ocultar/remover o pequeno ícone de diamante ou esmeralda (glyph/ícone
  verde ou azul) na tela de título.
---
# Ícone de Esmeralda/Diamante na Tela de Título

Se você está com dificuldade para esconder o pequeno ícone que continua aparecendo na sua Tela de Título e que parece um pequeno diamante ou esmeralda (um pequeno ícone verde ou azul), isso é, na maioria dos casos, a notificação de atualização do Mod Menu (mod Fabric) ou do Forge (recurso integrado do carregador de mods).

Em alguns casos, isso também pode fazer parte do botão Realms do Minecraft Vanilla (para exibir notificações).

# Ocultando o Ícone do Mod Menu

Para ocultar o glyph do Mod Menu, você precisa desativar o "indicador de atualização" nas configurações dele.

Clique no botão **Mods** -> Passe o mouse sobre o ícone do mod Mod Menu na lista de mods -> Clique nele -> Defina "Update Indicator" como "Hidden".

# Ocultando o Ícone do Forge

O Forge usa um verificador de versão integrado para mostrar esse ícone de esmeralda quando os mods estão desatualizados. Você pode desativá-lo:

1. Abra o arquivo `/config/fml.toml`.
2. Encontre a configuração `versionCheck`.
3. Defina-a como `false`: `versionCheck = false`
4. Salve e reinicie o Minecraft.

Isso desativa a verificação de versão por completo, o que também oculta o glyph de esmeralda na inicialização.

Outra forma de ocultar o ícone é simplesmente esconder o botão inteiro de Mods usando o FancyMenu. Ocultar o botão também ocultará o glyph.

# Ocultando o Ícone do NeoForge

No NeoForge, funciona exatamente da mesma forma que no Forge clássico.

1. Abra o arquivo `/config/fml.toml`.
2. Encontre a configuração `versionCheck`.
3. Defina-a como `false`: `versionCheck = false`
4. Salve e reinicie o Minecraft.

# Ocultando os Ícones do Realms do Vanilla

Caso não seja nem o glyph do Mod Menu nem o do Forge, provavelmente são os próprios ícones de notificação do Realms do Minecraft. Esses ícones aparecem aproximadamente na posição do botão Realms e podem ser ocultados com o FancyMenu no editor de layout. Você precisa criar um layout "para a tela atual" (no caso, a Tela de Título) e então verá os ícones do Realms como um elemento separado no editor. Para ocultá-los, basta clicar com o botão direito neles e clicar em **Delete**.

Os ícones do Realms podem ser um ícone de jornal, um glyph de diamante e outros, como um círculo vermelho com um contador de notificações.
