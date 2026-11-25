---
title: 호환성 문제 목록
description: FancyMenu에서 차단되는 화면과 커뮤니티에서 보고된 호환성 문제입니다.
sourceBlobSha: 2f89775eade27d0a90dd3805b5c58d779676bdbd
---
# 사용자 지정이 의도적으로 비활성화된 화면

FancyMenu는 충돌이나 비정상적인 동작을 방지하기 위해 특정 모드 패키지 경로와 일치하는 화면을 차단합니다. 일치하는 화면에서는 사용자 지정 토글, 오버레이, 레이아웃을 사용할 수 없습니다.

이 차단 규칙은 개별 화면을 하나씩 지정하는 대신 화면 클래스의 Java 패키지를 기준으로 적용됩니다. 따라서 하나의 규칙이 같은 모드나 관련 패키지에 속한 여러 화면에 영향을 줄 수 있습니다.

차단되는 화면 그룹은 다음과 같습니다.

- Create
- Panoramica
- Alex's Mobs
- Screenshot Viewer
- Twilight Forest
- Supplementaries
- OptiFine. [OptiFine 대안](/optifine-alternatives)을 사용하세요.
- SlimeKnights 및 Tinkers' Construct
- MidnightDust 모드
- SkinSwapper
- Immersive Engineering
- Dungeonz
- RPG-Hud
- Cobblemon 및 일부 Cobblemon 관련 화면
- Applied Energistics 2
- Xaero의 지도 모드

# 커뮤니티에서 보고된 호환성 문제

아래 항목은 커뮤니티에서 보고한 문제이며, FancyMenu 자체에서 차단하는 화면은 아닙니다. 호환성은 모드팩에 포함된 FancyMenu, Minecraft, 로더, 모드의 버전에 따라 달라질 수 있습니다.

* [Animated Loading Screen](https://modrinth.com/mod/animated-loading-screen) (메뉴가 오류가 난 것처럼 보이게 함)
* [Animated Mojang Logo](https://www.curseforge.com/minecraft/mc-mods/animated-mojang-logo) (레이아웃이 간혹 로드되지 않으며 Drippy Loading Screen도 작동하지 않게 함)
* [Bedrockify](https://www.curseforge.com/minecraft/mc-mods/bedrockify) (사용자 지정하려는 메뉴에서 이 모드의 메뉴 수정 기능을 모두 비활성화하면 호환됨)
* [BetterFPS](https://www.curseforge.com/minecraft/mc-mods/betterfps) (이 모드가 추가하는 버튼과 메뉴는 사용자 지정할 수 없음)
* [Chat Colors](https://www.curseforge.com/minecraft/mc-mods/chat-colours) (시작 시 충돌)
* [Chloride](https://modrinth.com/mod/chloride) (이 모드를 설치하면 FPS 자리 표시자가 작동하지 않음)
* [Colormatic](https://www.curseforge.com/minecraft/mc-mods/colormatic) (Minecraft 시작 시 심한 렉을 유발하고 FM의 오디오 기능을 작동하지 않게 함)
* [Controllable](https://www.curseforge.com/minecraft/mc-mods/controllable) (FancyMenu로 메뉴에 추가한 사용자 지정 버튼을 Controllable의 “가상 마우스” 기능으로 클릭할 수 없음)
* [Controlify](https://modrinth.com/mod/controlify) (충돌이 보고됨. [이슈 #1144](https://github.com/Keksuccino/FancyMenu/issues/1144) 참고)
* [Crash To Main Menu](https://www.curseforge.com/minecraft/mc-mods/crash-to-main-menu)
* [Custom Loading Screen](https://www.curseforge.com/minecraft/mc-mods/better-loading-screen)
* [Custom Main Menu](https://www.curseforge.com/minecraft/mc-mods/custom-main-menu)
* [Debugify](https://www.curseforge.com/minecraft/mc-mods/debugify) (대신 [Modern Debugify](https://www.curseforge.com/minecraft/mc-mods/modern-debugify)를 사용하세요)
* [Dynamic Surroundings](https://www.curseforge.com/minecraft/mc-mods/dynamic-surroundings) (오디오 요소를 작동하지 않게 한다는 보고가 있음)
* [EnhancedVisuals](https://www.curseforge.com/minecraft/mc-mods/enhancedvisuals) (애니메이션 및 반투명 배경 문제가 보고됨)
* [Entity Model Features](https://modrinth.com/mod/entity-model-features) (충돌이 보고됨. [이슈 #1115](https://github.com/Keksuccino/FancyMenu/issues/1115) 참고)
* [Fossils and Archeology Revival](https://www.curseforge.com/minecraft/mc-mods/fossils) (게임 내에서는 작동하지만 사용자 지정 메인 메뉴는 지원되지 않음. 모드 설정에서 비활성화할 수 있음)
* [Holographic Renderers](https://www.curseforge.com/minecraft/mc-mods/holographic-renderers) (시작 시 충돌)
* [Ice and Fire](https://www.curseforge.com/minecraft/mc-mods/ice-and-fire-dragons) (모드 설정에서 사용자 지정 메인 메뉴를 비활성화하면 작동함)
* [Jurassicraft](https://www.curseforge.com/minecraft/mc-mods/jurassicraft) (GUI 사용자 지정을 활성화하면 시작 시 충돌함. `<game-directory>/config/fancymenu/customizablemenus.txt`에서 해당 GUI를 삭제하세요)
* [Legacy4J](https://www.curseforge.com/minecraft/mc-mods/legacy-minecraft) (게임 충돌)
* [MalisisCore](https://www.curseforge.com/minecraft/mc-mods/malisiscore) (메인 메뉴 사용자 지정 기능을 작동하지 않게 함)
* [Main Menu Scale Mod](https://www.curseforge.com/minecraft/mc-mods/main-menu-scale)
* [MCA Reborn](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-reborn) (작동하지만, 일부 메뉴가 FM 메뉴 바를 망가뜨리거나 사용자 지정할 수 없음)
* [Minecraft Comes Alive](https://www.curseforge.com/minecraft/mc-mods/minecraft-comes-alive-mca) (호환된다는 보고가 있지만, 해당 모드의 메뉴는 사용자 지정할 수 없음)
* [MineTogether](https://www.curseforge.com/minecraft/mc-mods/creeperhost-minetogether) (GUI 배율이 2보다 높을 때 레이아웃 문제가 보고됨)
* [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (대체로 호환됨. Mods 버튼이 중복 표시되거나 사용자 지정할 수 없는 경우 **메인 메뉴 -> Mods -> Mod Menu -> Mods Button**을 **Adjacent**로 설정하세요.)
* [Modern Online Picture Frames](https://www.curseforge.com/minecraft/mc-mods/online-picture-frame) (충돌. [이 이슈](https://github.com/Keksuccino/FancyMenu/issues/776) 참고)
* [Not Enough Animations](https://www.curseforge.com/minecraft/mc-mods/not-enough-animations) (1.16 이상에서는 호환되고 1.12에서는 호환되지 않는다는 보고가 있음)
* [Optiscale](https://www.curseforge.com/minecraft/mc-mods/optiscale) (FancyMenu UI를 망가뜨려 버튼을 클릭할 수 없게 함)
* [Pack Menu](https://www.curseforge.com/minecraft/mc-mods/packmenu)
* [Panorama Screens](https://modrinth.com/mod/panorama-screens) (메뉴 사용자 지정 시스템 간 충돌이 보고됨)
* [QuestCraft](https://github.com/QuestCraftPlusPlus/QuestCraft) (게임이 로드되지 않음)
* [RandomPatches](https://www.curseforge.com/minecraft/mc-mods/randompatches-forge) (모드 설정에서 `patchMinecraftClass = false`로 설정하면 작동함)
* [Remove Reloading Screen](https://www.curseforge.com/minecraft/mc-mods/rrls) (FancyMenu와 Drippy Loading Screen을 작동하지 않게 한다는 보고가 있음)
* [Replay Mod](https://www.replaymod.com/download/) (`<game-directory>/config/replaymod.json`에서 `mainMenuButton`을 **BIG**로 설정하면 작동함)
* [Seamless Loading Screen](https://www.curseforge.com/minecraft/mc-mods/seamless-loading-screen) (게임 충돌)
* [Slight Gui Modifications](https://www.curseforge.com/minecraft/mc-mods/slight-gui-modifications)
* [Skin Layers 3D](https://www.curseforge.com/minecraft/mc-mods/skin-layers-3d) (1.16 이상에서는 호환되고 1.12에서는 호환되지 않는다는 보고가 있음)
* [Smooth Scrolling Everywhere](https://www.curseforge.com/minecraft/mc-mods/smooth-scrolling-everywhere)
* [Sound Filters](https://www.curseforge.com/minecraft/mc-mods/sound-filters) (설치되어 있으면 오디오 확장 기능이 작동하지 않음)
* [Sound Physics Remastered](https://www.curseforge.com/minecraft/mc-mods/sound-physics-remastered) (설치되어 있으면 오디오 확장 기능이 작동하지 않음)
* [Stylish Effects](https://www.curseforge.com/minecraft/mc-mods/stylish-effects) (메인 메뉴가 처음 표시될 때 레이아웃을 로드하지 못함)
* [Supplementaries](https://www.curseforge.com/minecraft/mc-mods/supplementaries) (설정 화면을 사용자 지정할 때 간헐적으로 충돌함. 문제가 있는 레이아웃을 `<game-directory>/config/fancymenu/customization/`에서 삭제하세요)
* [Terraria Craft](https://www.curseforge.com/minecraft/mc-mods/terraria-craft)
* [The Dalek Mod](https://www.curseforge.com/minecraft/mc-mods/the-dalek-mod) (설정에서 사용자 지정 메인 메뉴를 비활성화하면 작동함)
* [ThonkUtil](https://www.curseforge.com/minecraft/mc-mods/thonkutil) (작동하지만 현재 메인 메뉴에 제거할 수 없는 텍스트를 추가함)
* [Trade Uses](https://modrinth.com/mod/trade-uses) (주민 거래 메뉴에서 충돌을 일으킴. “Easy Villagers”도 설치된 경우에만 발생할 수 있음)
* [VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix) (사용할 수 있지만 일부 사용자가 VanillaFix 충돌 화면에 문제가 있다고 보고함)
* [FireplaceMode](https://www.curseforge.com/minecraft/mc-mods/fireplacemode) (이 모드를 설치하면 일시 정지 화면의 사용자 지정 내용이 간혹 초기화됨)
* [Respackopts](https://www.curseforge.com/minecraft/mc-mods/respackopts) (작동하지만 리소스 팩 화면의 사용자 지정을 비활성화해야 함)
* [Bind Pizzeria](https://modrinth.com/mod/jjpizza) (FancyMenu의 컨텍스트 메뉴에서 텍스트 렌더링을 망가뜨림)
* [EnhancedTooltips](https://www.curseforge.com/minecraft/mc-mods/enhancedtooltips) (FancyMenu의 툴팁을 작동하지 않게 함)
* [Skin Shuffle](https://modrinth.com/mod/skinshuffle) (이 모드가 메뉴에 추가하는 플레이어 엔티티는 FancyMenu로 사용자 지정할 수 없음)
* [Wakes](https://modrinth.com/mod/wakes) (`IncompatibleClassChangeError`로 인해 게임 시작 시 충돌함. `AbstractSliderButton.getSprite()` 최종 메서드를 재정의하려고 하지만, Wakes가 메서드의 가시성을 수정하기 때문에 해당 메서드가 최종 메서드가 됨. 자세한 내용은 GitHub 이슈를 참고하세요: [Goby56/wakes #215](https://github.com/Goby56/wakes/issues/215), [Keksuccino/FancyMenu #1733](https://github.com/Keksuccino/FancyMenu/issues/1733))
* [Essential](https://www.curseforge.com/minecraft/mc-mods/essential-mod) (자세한 내용은 [이 페이지](/essential)를 참고하세요)
