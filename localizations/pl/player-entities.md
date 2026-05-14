---
title: Encje gracza
description: Jak działa element „Encja gracza” w FancyMenu i jak używać go poprawnie.
---

# Encje gracza

FancyMenu pozwala dodawać encje gracza do ekranów, dzięki czemu możesz wyświetlać gracza klienta lub innych graczy, a także niestandardowe encje, które w ogóle nie reprezentują prawdziwego gracza, z własną skórką, nazwą, peleryną i tak dalej.

# Gracz klienta

Aby wyświetlić „lustrzane odbicie” gracza klienta, po prostu kliknij prawym przyciskiem myszy element Encja gracza i włącz **Kopiuj gracza klienta**. Spowoduje to skopiowanie skórki, peleryny i nazwy gracza klienta.

# Inni gracze

Jeśli chcesz wyświetlić innego, istniejącego gracza, po prostu kliknij prawym przyciskiem myszy element i ustaw **Nazwa gracza** na nazwę istniejącego gracza. Automatycznie wyświetli to skórkę, pelerynę i nazwę tego gracza, o ile nie masz ustawionej własnej skórki lub peleryny oraz **Kopiuj gracza klienta** jest **wyłączone**.

# Niestandardowe encje gracza

Jeśli nie chcesz wyświetlać prawdziwego gracza, a zamiast tego chcesz w pełni dostosować skórkę, pelerynę i nazwę encji, możesz kliknąć element prawym przyciskiem myszy. Dostępne są opcje ustawienia niestandardowej tekstury skórki i peleryny. Jeśli niestandardowa skórka i peleryna są aktywne, możesz również ustawić dowolną nazwę gracza, a nie spowoduje to skopiowania skórki tej nazwy, nawet jeśli gracz istnieje.

# Pozowanie encji

Element Encja gracza w pełni obsługuje dostosowywanie pozy, więc innymi słowy możesz swobodnie poruszać wszystkimi kończynami, częściami ciała itp.

Aby to zrobić, kliknij element prawym przyciskiem myszy i wybierz **Poza gracza**. Otworzy się ekran z suwakami do konfiguracji obrotu X/Y/Z wszystkich części ciała.

Ustawienia pozy gracza mają normalny tryb, w którym możesz dostosowywać obroty za pomocą suwaków, a także tryb zaawansowany, który umożliwia wprowadzanie tekstu dla wszystkich obrotów z pełną obsługą placeholderów, co pozwala nawet animować encję za pomocą elementu Ticker ustawiającego zmienne obrotu!

# Zmiana rozmiaru encji

W Minecraft 1.21.1+ możesz po prostu użyć zwykłych uchwytów zmiany rozmiaru elementu, aby skalować encję.

W starszych wersjach (1.21.0 i starszych) elementy Encja gracza nie obsługują bezpośredniej zmiany rozmiaru za pomocą uchwytów. Zamiast tego musisz kliknąć element prawym przyciskiem myszy i wybrać **Skala**. Pozwala to ustawić skalę elementu. Domyślna wartość powinna wynosić `30`, więc ustawienie jej na przykład na `60` sprawia, że gracz jest dwa razy większy niż normalnie, ustawienie `15` pokazuje go w połowie rozmiaru i tak dalej.

# Zależność: Fancy Entity Renderer (FER)

W Minecraft 1.21.1+ potrzebny jest dodatkowy mod, aby elementy Encja gracza działały. Mod nazywa się „Fancy Entity Renderer” i jest dostępny na CurseForge oraz Modrinth.

Jeśli nie ma jeszcze dostępnej kompilacji dla używanej przez ciebie wersji Minecrafta, najprawdopodobniej zostanie ona wydana później.

Pamiętaj, że FER nie jest tworzony przez Keksuccino, więc nie ma on kontroli nad tym, kiedy kolejne kompilacje zostaną opublikowane.
