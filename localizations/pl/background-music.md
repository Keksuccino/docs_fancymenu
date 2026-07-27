---
title: Muzyka w tle menu
description: Dostosuj muzykę odtwarzaną w menu.
---

# Muzyka w tle menu

FancyMenu może wyłączyć domyślną muzykę menu Vanilla, odtwarzać globalną listę utworów albo używać elementów [Audio](./elements#audio) do muzyki zależnej od układu.

# Globalna muzyka menu

Otwórz [**Global Customizations**](./global-customizations) przez **Customization -> Global Customizations** poza edytorem układu.

Użyj tych ustawień:

- **Play Vanilla Menu Music** włącza lub wyłącza globalnie domyślną muzykę menu Vanilla.
- **Custom Menu Music Tracks** zarządza globalną listą zastępczych utworów.

> [!IMPORTANT]
> Globalne niestandardowe utwory menu odtwarzają się tylko wtedy, gdy nie jest załadowany żaden świat, na przykład na ekranie tytułowym. Użyj elementu [**Audio**](./elements#audio) dla muzyki menu podczas przebywania w świecie.

Globalne utwory używają kanału dźwiękowego Music. Pierwszy utwór startuje po około pięciu sekundach; kolejne utwory używają losowego opóźnienia od około jednej do trzydziestu sekund. Wybór jest losowy i unika natychmiastowego powtórzenia poprzedniego utworu, gdy skonfigurowano więcej niż jeden utwór.

# Sterowanie muzyką dla konkretnego ekranu

Dodaj element [**Music Controller**](./elements#music-controller) do układu, aby sterować domyślną muzyką Vanilla dla tego ekranu:

1. Kliknij prawym przyciskiem myszy tło edytora.
2. Wybierz **New Element -> Music Controller**.
3. Skonfiguruj osobno Menu Music i World Music.

Ten element obsługuje [wymagania ładowania](./conditions).

Wyłączenie muzyki menu za pomocą Music Controllera zapobiega również odtwarzaniu globalnej, niestandardowej listy utworów menu na tym ekranie.

# Własna muzyka z elementami Audio

Użyj elementu [**Audio**](./elements#audio), gdy potrzebujesz:

- Innej muzyki na różnych ekranach.
- Muzyki na ekranach w świecie.
- Wymagań układu, list odtwarzania w kolejności, ustawień losowania, głośności lub kontroli kanału.

Umieść element [Audio](./elements#audio) w [Universal Layout](./universal-layouts), aby ten sam odtwarzacz pozostał aktywny na obsługiwanych ekranach, które ładują ten układ. Dostosowanie ekranu musi być włączone na każdym zwykłym ekranie, na którym ma obowiązywać układ uniwersalny.
