---
title: Niestandardowe GUI
description: Jak dodać do gry nowy ekran GUI.
---

# Niestandardowe GUI

FancyMenu pozwala dostosowywać istniejące ekrany GUI, ale umożliwia też dodawanie całkiem nowych i wypełnianie ich elementami.

# Dodawanie nowego ekranu

Aby dodać nowy ekran, przejdź do **Customization -> Custom GUIs -> Manage Custom GUIs**.

![custom_gui_1](https://github.com/Keksuccino/FancyMenu/assets/35544624/23e704ee-ccb5-434d-b75f-f4418399d9b7)

W następnym menu kliknij **New GUI**.

![custom_gui_2](https://github.com/Keksuccino/FancyMenu/assets/35544624/035454e8-b089-4b9a-9092-89a193c0eacd)

Tutaj musisz nadać swojemu nowemu GUI unikalny identyfikator oraz możesz dostosować inne aspekty podstawowego zachowania ekranu.
Gdy skończysz, naciśnij **Done**.

![custom_gui_3](https://github.com/Keksuccino/FancyMenu/assets/35544624/1fbed3f9-9c81-4c73-85c7-d152146c55d8)

Teraz masz nowe, puste GUI. Aby je otworzyć, wybierz GUI w menu **Manage Custom GUIs** i kliknij **Open GUI**.

![custom_gui_4](https://github.com/Keksuccino/FancyMenu/assets/35544624/b2e6a4b7-540d-4bf2-9dce-09bfff11ae7e)

Spowoduje to otwarcie nadal dość pustego ekranu GUI. Aby nie był tak pusty, po prostu utwórz dla niego nowy układ, tak jak zrobiłbyś to w przypadku każdego innego ekranu.

![custom_gui_5](https://github.com/Keksuccino/FancyMenu/assets/35544624/e7e06a5f-46b3-48f1-9ad9-96a7565c97a9)

# Otwieranie GUI przez akcję

Ostatnim krokiem jest umożliwienie zwykłym użytkownikom dostępu do Twojego GUI. Najprostszym sposobem jest użycie akcji **Open Screen or Custom GUI** za pomocą przycisku, suwaka lub ticker'a.

![custom_gui_6](https://github.com/Keksuccino/FancyMenu/assets/35544624/b5cc6518-3fc4-4715-96d4-44b65ab7831d)

# Otwieranie GUI przez komendę

Możesz również otworzyć swoje niestandardowe GUI za pomocą [komendy w grze](./commands#openguiscreen).
Pozwala to nawet zdalnie otwierać GUI dla innych użytkowników!

# Tryb popup

Począwszy od FancyMenu v3.8.0, niestandardowe GUI obsługują „Tryb popup”, który sprawia, że wyglądają jak wyskakujące okno otwierane na wierzchu innego ekranu (poprzedniego ekranu, z którego zostało otwarte niestandardowe GUI). To ustawienie można przełączać osobno dla każdego niestandardowego GUI w jego ustawieniach.

FancyMenu 3.9.0 dodaje także opcję przełączania nakładki tła ekranu dla niestandardowych GUI podczas przebywania w świecie. Użyj jej, gdy chcesz wyłączyć lub zachować rozmycie/przyciemnienie tła za niestandardowym GUI otwartym nad rozgrywką.
