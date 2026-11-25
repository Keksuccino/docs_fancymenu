---
title: Układy uniwersalne
description: Stosuj jeden układ na wielu obsługiwanych ekranach.
sourceBlobSha: 2179fed92c6598b6e5c3ecfea354a4c853bc394b
---

# Układy uniwersalne

Układ uniwersalny jest brany pod uwagę na każdym obsługiwanym ekranie, dla którego włączono dostosowywanie. Nie dotyczy ekranów [zablokowanych](/incompatibility-list#screens-where-customization-is-intentionally-disabled) ani ekranów wykluczonych w inny sposób.

Używaj układów uniwersalnych do wspólnych elementów, takich jak logo, nawigacja, nakładki czy [elementy audio](/elements#audio), które mają być widoczne na wielu ekranach.

# Tworzenie układu

1. Otwórz obsługiwany ekran i wyświetl pasek menu FancyMenu.
2. Wybierz **Układy -> Nowy -> Dla wszystkich ekranów [Uniwersalny]**.
3. Dodaj elementy i skonfiguruj je.
4. Zapisz układ.

Na zwykłych ekranach nadal trzeba włączyć **Dostosowywanie bieżącego ekranu**. Nie ma globalnego przełącznika włączającego dostosowywanie na wszystkich ekranach, ponieważ dostosowanie ekranów nieobsługiwanych przez mody może powodować problemy.

# Ograniczanie ekranów

Otwórz ustawienia układu uniwersalnego z menu kontekstowego tła edytora.

- **Biała lista:** układ dotyczy tylko wymienionych identyfikatorów ekranów.
- **Czarna lista:** układ dotyczy wszystkich kwalifikujących się ekranów z wyjątkiem wymienionych identyfikatorów.

Użyj opcji **Dostosowywanie -> Kopiuj identyfikator bieżącego ekranu**, aby skopiować [identyfikator ekranu](/screen-identifiers).

Możesz też dodać [wymagania obowiązujące dla całego układu](/conditions#layout-wide-requirements), aby określić, kiedy układ ma być stosowany.

# Kolejność układów

Kwalifikujące się układy uniwersalne i układy przypisane do konkretnych ekranów są łączone i układane w stos według **Indeksu układu**. Niższe indeksy są stosowane jako pierwsze; późniejsze ustawienia układów warstwowych mogą zastępować wcześniejsze. Przy tym samym indeksie układy uniwersalne są uwzględniane przed układami przypisanymi do konkretnych ekranów.
