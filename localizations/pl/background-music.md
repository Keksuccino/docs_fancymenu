---
title: Muzyka w tle menu
description: Dostosuj muzykę odtwarzaną w menu.
sourceBlobSha: 46d219f5573b915991f23082cfbc42e6ed11d132
---

# Muzyka w tle menu

FancyMenu może wyłączyć muzykę menu z wersji Vanilla, odtwarzać globalną listę utworów lub używać [elementów audio](/elements#audio) do odtwarzania muzyki zależnej od układu.

# Globalna muzyka menu

Otwórz [**Globalne ustawienia**](/global-customizations), wybierając **Dostosowywanie -> Globalne ustawienia** poza edytorem układu.

Użyj tych ustawień:

- **Odtwarzaj muzykę menu z wersji Vanilla** globalnie włącza lub wyłącza muzykę menu z wersji Vanilla.
- **Niestandardowe utwory muzyki menu** pozwalają zarządzać globalną listą utworów zastępczych.

> [!IMPORTANT]
> Globalne niestandardowe utwory są odtwarzane tylko wtedy, gdy żaden świat nie jest wczytany, na przykład na ekranie tytułowym. Aby odtwarzać dźwięk w menu w świecie, użyj elementu [**Audio**](/elements#audio).

Globalne utwory korzystają z kanału dźwiękowego Muzyka. Pierwszy utwór rozpoczyna się po około pięciu sekundach, a kolejne są odtwarzane po losowym opóźnieniu wynoszącym od około jednej do trzydziestu sekund. Utwory są wybierane losowo; jeśli skonfigurowano więcej niż jeden, poprzedni utwór nie zostanie odtworzony ponownie bezpośrednio po sobie.

# Sterowanie muzyką na poszczególnych ekranach

Dodaj do układu element [**Kontroler muzyki**](/elements#music-controller), aby sterować muzyką z wersji Vanilla na tym ekranie:

1. Kliknij prawym przyciskiem myszy tło edytora.
2. Wybierz **Nowy element -> Kontroler muzyki**.
3. Skonfiguruj osobno muzykę menu i muzykę świata.

Element obsługuje [wymagania wczytywania](/conditions).

Wyłączenie muzyki menu za pomocą Kontrolera muzyki uniemożliwia również odtwarzanie globalnej listy niestandardowych utworów menu na tym ekranie.

# Własna muzyka z elementami Audio

Użyj elementu [**Audio**](/elements#audio), jeśli potrzebujesz:

- Innej muzyki na różnych ekranach.
- Muzyki na ekranach wyświetlanych w świecie.
- Wymagań układu, list odtwarzania z ustaloną kolejnością, ustawień odtwarzania losowego, głośności lub sterowania kanałem.

Umieść element [Audio](/elements#audio) w [układzie uniwersalnym](/universal-layouts), aby zachować aktywny ten sam odtwarzacz na obsługiwanych ekranach, które wczytują ten układ. Dostosowywanie ekranu musi być włączone na każdym zwykłym ekranie, na którym ma być stosowany układ uniwersalny.
