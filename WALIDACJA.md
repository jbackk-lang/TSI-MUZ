# Walidacja — 16.10.2026

## Wyniki

- Pełny przebieg: **156 zaliczonych testów**, 0 błędów, 0 pominiętych.
- Dane testowe: syntetyczne. Nie używano prywatnych wyciągów ani profili.
- Przeglądarka: dodanie sprawy, zapis planu, dodanie wydatku, wykrycie przekroczenia 30 zł, włączenie automatu i ponowne wczytanie zapisanych danych.
- Układ: 1366 i 390 pikseli, bez poziomego przewijania i błędów JavaScript w sprawdzonym scenariuszu.
- Sprawdzono odtworzenie lokalnego repozytorium z Git: zgodność hashy vendora i zamrożonych polityk.

## Poprawione błędy

1. Identyczne próbki w kontroli statystycznej mogły dawać NaN. Jawny wybór istniejącego backendu numpy zachowuje protokół losowania i progi, a stałe tło daje p=1.
2. Szablon pisma przepuszczał puste wartości wymaganych pól. Teraz pismo jest blokowane, a propozycja działania może pozostać do uzupełnienia.
3. Długie pismo mogło wyjść poza stronę PDF. Dodano podział na strony i sprawdzono zachowanie treści, polskich znaków i marginesów.

## Ograniczenia dowodów

Pozostaje **387 ostrzeżeń RankWarning** w istniejącym dopasowaniu trendu META. Nie zostały wyciszone ani przedstawione jako rozwiązany problem.

Stałe tło w kontroli statystycznej sprawdza konkretny przypadek brzegowy; nie potwierdza częstości fałszywych alarmów na zmiennych danych.

Zaliczenie testów nie dowodzi opłacalności finansowej, niezawodności produkcyjnej ani zdolności rozumienia dowolnych poleceń. Nie przeprowadzono badania skuteczności na rzeczywistych budżetach użytkowników.
