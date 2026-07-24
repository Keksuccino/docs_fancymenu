---
title: Вступ до гри
description: >-
  Відтворюйте анімований контент перед тим, як гра вперше покаже екран
  заголовка.
---
# Вступи до гри

Вступи до гри відтворюють анімоване зображення або відео перед тим, як уперше з’явиться екран заголовка.

# Налаштування

Відкрийте [**Global Customizations**](./global-customizations) через **Customization -> Global Customizations**, а потім налаштуйте ці параметри:

| Параметр | Поведінка |
|---|---|
| Set Game Intro | Вибирає локальне, веб- або Minecraft-ресурсне анімоване зображення чи відео |
| Game Intro Skipping | Дозволяє пропускати вступ будь-якою клавішею або клацанням миші |
| Game Intro Fade-Out | Поступово затемнює вступ до цільового екрана |
| Custom Skip Text | Замінює стандартну підказку пропуску звичайним текстом або ключем локалізації |
| Game Intro Volume | Встановлює базову гучність від `0.0` до `1.0` |
| Game Intro Sound Channel | Вибирає категорію звуку Minecraft |
| Re-Trigger Game Intro | Відтворює налаштований вступ ще раз для тестування |

Для відеовступів потрібні **Watermedia V3**, **Watermedia Binaries V3** та рендерер OpenGL. Відтворення відео Watermedia недоступне з Vulkan. Коли відтворення недоступне, FancyMenu показує пояснення поверх екрана вступу. Див. [Відео](./video#requirements).

<br>
<img width="700" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/71cec75b-33f1-4a21-9f18-d0adc7ceebb6">
