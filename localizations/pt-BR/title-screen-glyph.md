---
title: Glifo da Tela de Título
description: >-
  Como ocultar/remover o pequeno diamante ou esmeralda (glifo/ícone verde ou
  azul) na tela de título.
---

# Ícone de Esmeralda/Diamante na Tela de Título

Se você está com dificuldade para esconder o pequeno ícone que continua aparecendo na sua Tela de Título e que parece um pequeno diamante ou uma esmeralda (um pequeno ícone verde ou azul), isso geralmente é a notificação de atualização do mod Menu Mod (mod Fabric) ou do Forge (recurso integrado do carregador de mods).

Em alguns casos, também pode fazer parte do botão de Reinos (Realms) do Minecraft Vanilla (para mostrar notificações).

# Ocultando o Ícone do Mod Menu

Para ocultar o glifo do Mod Menu, você precisa desativar o "indicador de atualização" nas configurações dele.

Clique no botão **Mods** -> Passe o mouse sobre o ícone do mod Mod Menu na lista de mods -> Clique nele -> Defina "Update Indicator" como "Hidden".

# Ocultando o Ícone do Forge

O Forge usa um verificador de versão embutido para mostrar esse ícone de esmeralda quando os mods estão desatualizados. Você pode desativá-lo:

1. Abra seu arquivo `config/fml.toml`.
2. Encontre a configuração `versionCheck`.
3. Defina-a como `false`: `versionCheck = false`
4. Salve e reinicie o Minecraft.

Isso desativa completamente a verificação de versão, o que também oculta o glifo de esmeralda na inicialização.

Outra forma de ocultar o ícone é simplesmente esconder o botão Mods inteiro usando o FancyMenu. Esconder o botão também esconderá o glifo.

# Ocultando os Ícones Padrão do Realms

Caso não seja nem o glifo do Mod Menu nem o do Forge, provavelmente são os ícones de notificação do Realms do próprio Minecraft. Esses ícones aparecem mais ou menos na posição do botão Realms e podem ser ocultados com o FancyMenu no editor de layout. Você precisa criar um layout "for the current screen" (Tela de Título, neste caso) e então verá os ícones do Realms como um elemento dedicado no editor. Para ocultá-los, basta **clicar com o botão direito** neles e clicar em **Delete**.

Os ícones do Realms podem ser um ícone de jornal, um glifo de diamante e outros, como um círculo vermelho com um contador de notificações.
