---
title: Lista de Incompatibilidades
description: >-
  Telas bloqueadas pelo FancyMenu e incompatibilidades relatadas pela
  comunidade.
---
# Incompatibilidades

# Telas em Que a Personalização é Desativada Intencionalmente

O FancyMenu bloqueia telas que correspondem a certos caminhos de pacote de mods para evitar crashes ou comportamentos quebrados. O botão de ativação de personalização, a sobreposição e os layouts ficam indisponíveis nessas telas correspondentes.

Esses bloqueios usam o pacote Java da classe da tela, em vez de uma lista selecionada manualmente de telas individuais. Portanto, uma única regra pode afetar várias telas do mesmo mod ou de pacotes relacionados.

Os grupos de telas bloqueados incluem:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; use [Alternativas ao OptiFine](./optifine-alternatives)
- SlimeKnights e Tinkers' Construct
- mods do MidnightDust
- SkinSwapper
- As telas de configuração do próprio FancyMenu; [GUIs Personalizadas](./custom-guis) estão excluídas
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon e algumas telas relacionadas ao Cobblemon
- Applied Energistics 2
- mods de mapa do Xaero

# Incompatibilidades Relatadas pela Comunidade

As entradas abaixo são relatos da comunidade, não telas bloqueadas pelo próprio FancyMenu. A compatibilidade pode mudar conforme as versões do FancyMenu, Minecraft, carregador e dos mods no pacote.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (Faz os menus parecerem bugados)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (Os layouts às vezes não carregam; também quebra o Drippy Loading Screen)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (Compatível quando você desativa todas as modificações de menu do mod, pelo menos para os menus que deseja personalizar)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (Os botões e menus deste mod não podem ser personalizados)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (Crash na inicialização)
* [Chloride](https://modrinth.com/mod/chloride) (O placeholder de FPS não funciona quando este mod está instalado)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Grande lag ao iniciar o Minecraft e quebra os recursos de áudio do FM)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (Botões personalizados adicionados aos menus com o FancyMenu não podem ser clicados pelo recurso “Virtual Mouse” do Controllable)
* [Controlify](https://modrinth.com/mod/controlify) (Crash relatado; veja [issue #1144](https://github.com/Keksuccino/FancyMenu/issues/1144))
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (Use [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify) em vez disso)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (Relatado que quebra elementos de áudio)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (Problemas relatados de animação e de fundo translúcido)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (Crash relatado; veja [issue #1115](https://github.com/Keksuccino/FancyMenu/issues/1115))
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (Funciona no jogo, mas o menu principal personalizado não é suportado — pode ser desativado na configuração)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (Crash na inicialização)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (Funciona se o menu principal personalizado for desativado na configuração)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (Crasha ao iniciar quando as personalizações são ativadas para suas GUIs — apague-as de `<game-directory>/config/fancymenu/customizablemenus.txt`)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (Crash no jogo)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (Quebra a personalização do menu principal)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (Funciona, mas alguns de seus menus quebram a barra de menus do FM e/ou não podem ser personalizados)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (Relatado como compatível, mas seus menus não podem ser personalizados)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (Problemas de layout relatados acima da escala de GUI 2)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (Geralmente compatível; para um botão Mods duplicado ou não personalizável, defina **Main Menu -> Mods -> Mod Menu -> Mods Button** como **Adjacent**)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (Crash — veja [este issue](https://github.com/Keksuccino/FancyMenu/issues/776))
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (Relatado como compatível na 1.16+ e incompatível na 1.12)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (Quebra a interface do FancyMenu; os botões não podem ser clicados)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (Conflito relatado entre sistemas de personalização de menu)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (O jogo não consegue carregar)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (Funciona se `patchMinecraftClass = false` estiver na configuração)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (Relatado que quebra o FancyMenu e o Drippy Loading Screen)
* [Replay Mod](https://www.replaymod.com/download/) (Funciona quando você define `mainMenuButton` como **BIG** em `<game-directory>/config/replaymod.json`)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (Crasha o jogo)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (Relatado como compatível na 1.16+ e incompatível na 1.12)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (A extensão de áudio não funcionará com isto instalado)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (A extensão de áudio não funcionará com isto instalado)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (O menu principal falha ao carregar os layouts na primeira vez que é exibido)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (Crasha aleatoriamente ao personalizar sua tela de configuração; exclua o layout problemático de `<game-directory>/config/fancymenu/customization/`)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (Funciona se o menu principal personalizado estiver desativado na configuração)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (Funciona, mas atualmente adiciona um texto que não pode ser removido ao menu principal)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (Causa crashes no menu de trocas do aldeão — possivelmente apenas quando “Easy Villagers” também está instalado)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (Usável, mas alguns usuários relatam problemas com a tela de crash do VanillaFix)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (A tela de pausa às vezes redefine suas personalizações com este mod instalado)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (Funciona, mas apenas se você desativar as personalizações da tela de Pacotes de Recursos)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (Quebra a renderização de texto nos menus de contexto do FancyMenu)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (Quebra as tooltips do FancyMenu)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (A entidade do jogador adicionada aos menus por esse mod não pode ser personalizada via FancyMenu)
