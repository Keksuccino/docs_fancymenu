---
title: 비호환 목록
description: FancyMenu에 의해 차단되는 화면과 커뮤니티가 보고한 비호환성입니다.
---
# 비호환성

# 사용자 지정이 의도적으로 비활성화되는 화면

FancyMenu는 충돌이나 잘못된 동작을 방지하기 위해 특정 모드 패키지 경로와 일치하는 화면을 차단합니다. 일치하는 화면에서는 사용자 지정 토글, 오버레이, 레이아웃을 사용할 수 없습니다.

이 차단은 개별 화면을 하나하나 고른 목록이 아니라 화면 클래스의 Java 패키지를 기준으로 합니다. 따라서 하나의 규칙이 같은 모드 또는 관련 패키지의 여러 화면에 영향을 줄 수 있습니다.

차단되는 화면 그룹에는 다음이 포함됩니다:

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine; [OptiFine 대안](./optifine-alternatives) 사용
- SlimeKnights 및 Tinkers' Construct
- MidnightDust 모드
- SkinSwapper
- FancyMenu 자체의 설정 화면; [Custom GUIs](./custom-guis)는 제외됨
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon 및 일부 Cobblemon 관련 화면
- Applied Energistics 2
- Xaero의 지도 모드들

# 커뮤니티가 보고한 비호환성

아래 항목은 FancyMenu 자체가 차단하는 화면이 아니라 커뮤니티의 보고입니다. 호환성은 팩에 포함된 FancyMenu, Minecraft, 로더, 모드 버전에 따라 달라질 수 있습니다.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (메뉴가 버그가 있는 것처럼 보이게 함)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (레이아웃이 가끔 로드되지 않음; Drippy Loading Screen도 망가뜨림)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (모드의 모든 메뉴 수정을 끄면 호환됨, 최소한 사용자 지정하려는 메뉴에 대해서는)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (이 모드의 버튼과 메뉴는 사용자 지정할 수 없음)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (시작 시 충돌)
* [Chloride](https://modrinth.com/mod/chloride) (이 모드가 설치되어 있으면 FPS 자리표시자가 작동하지 않음)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (MC 시작 시 심한 렉이 발생하고 FM의 오디오 기능을 망가뜨림)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (FancyMenu로 추가한 커스텀 버튼은 Controllable의 “Virtual Mouse” 기능으로 클릭할 수 없음)
* [Controlify](https://modrinth.com/mod/controlify) (충돌 보고됨; [이슈 #1144](https://github.com/Keksuccino/FancyMenu/issues/1144) 참조)
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) ([Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify)를 대신 사용하세요)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (오디오 요소를 망가뜨린다는 보고가 있음)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (애니메이션 및 반투명 배경 문제 보고됨)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (충돌 보고됨; [이슈 #1115](https://github.com/Keksuccino/FancyMenu/issues/1115) 참조)
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (게임 내에서는 작동하지만, 커스텀 메인 메뉴는 지원되지 않음—설정에서 비활성화 가능)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (시작 시 충돌)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (설정에서 커스텀 메인 메뉴를 비활성화하면 작동함)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (해당 GUI에 대한 사용자 지정을 켜면 시작 시 충돌함—`<game-directory>/config/fancymenu/customizablemenus.txt`에서 삭제하세요)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (게임이 충돌함)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (메인 메뉴 사용자 지정을 망가뜨림)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (작동하지만 일부 메뉴가 FM의 메뉴 바를 망가뜨리거나/또는 사용자 지정할 수 없음)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (호환된다고 보고되었지만 메뉴는 사용자 지정할 수 없음)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (GUI 크기 2 초과에서 레이아웃 문제 보고됨)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (대체로 호환됨; 중복되거나 사용자 지정할 수 없는 Mods 버튼이 보이면 **Main Menu -> Mods -> Mod Menu -> Mods Button**을 **Adjacent**로 설정하세요)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (충돌—[이 이슈](https://github.com/Keksuccino/FancyMenu/issues/776) 참조)
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (1.16+에서는 호환, 1.12에서는 비호환으로 보고됨)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (FancyMenu의 UI를 망가뜨림; 버튼을 클릭할 수 없음)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (메뉴 사용자 지정 시스템 간 충돌이 보고됨)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (게임 로드 실패)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (설정에서 `patchMinecraftClass = false`로 하면 작동함)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (FancyMenu와 Drippy Loading Screen을 망가뜨린다는 보고가 있음)
* [Replay Mod](https://www.replaymod.com/download/) (`<game-directory>/config/replaymod.json`에서 `mainMenuButton`을 **BIG**로 설정하면 작동함)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (게임이 충돌함)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (1.16+에서는 호환, 1.12에서는 비호환으로 보고됨)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (이 모드가 설치되어 있으면 오디오 확장 기능이 작동하지 않음)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (이 모드가 설치되어 있으면 오디오 확장 기능이 작동하지 않음)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (처음 표시될 때 메인 메뉴가 레이아웃을 로드하지 못함)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (설정 화면 사용자 지정 중 무작위로 충돌함; `<game-directory>/config/fancymenu/customization/`에서 문제되는 레이아웃을 삭제하세요)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (설정에서 커스텀 메인 메뉴를 비활성화하면 작동함)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (작동하지만, 현재 메인 메뉴에 제거할 수 없는 텍스트를 추가함)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (주민 거래 메뉴에서 충돌을 일으킴—아마 “Easy Villagers”도 함께 설치된 경우에만 해당)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (사용 가능하지만, 일부 사용자는 VanillaFix 충돌 화면에 문제가 있다고 보고함)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (이 모드가 설치되어 있으면 일시정지 화면의 사용자 지정이 가끔 초기화됨)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (리소스 팩 화면 사용자 지정을 비활성화하면 작동함)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (FancyMenu의 컨텍스트 메뉴에서 텍스트 렌더링을 망가뜨림)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (FancyMenu의 툴팁을 망가뜨림)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (이 모드가 메뉴에 추가한 플레이어 엔티티는 FancyMenu로 사용자 지정할 수 없음)
