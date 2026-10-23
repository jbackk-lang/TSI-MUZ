# Integracja TSI — 23 października 2026

Walidator i MUZ korzystają ze wspólnego interfejsu TSI. W instalacji roboczej moduł matematyczny znajduje się wewnątrz TSI. W portable jego samodzielna kopia jest w `tsi_runtime`; odnośniki do kodu i modułu MUZ są względne.

Czytnik i narzędzia matematyczne pozostają w jednym procesie roboczym. Żądania mają limit czasu; błąd danych nie zatruwa następnego poprawnego żądania. Dokładne obliczenia nadal wykonują solvery. Nie scalono wszystkich modułów w jeden checkpoint.

Sprawdzenia lokalne: 7/7 obliczeń matematycznych i 5/5 kontroli budżetu; dodatkowo sprawdzono drogi HTTP obu aplikacji. Saldo testowe jest liczbą całkowitych groszy. Zadanie o sumie 13 i iloczynie 40 daje pierwiastki 5 i 8, sprawdzone podstawieniem.

Pierwszy odczyt nadal może trwać kilkadziesiąt sekund, kolejne korzystają z załadowanych bibliotek. Nowy generator swobodnej rozmowy pozostaje niewdrożony; jego trening jest oddzielony od aktywnych wag.

Szczegóły budowy i weryfikacji konkretnego archiwum znajdują się w jego `PACKAGE_INFO.json` oraz pliku `PORTABLE_VERIFICATION.json`. Tylko raport z wynikiem `passed` potwierdza wykonanie prób danej paczki.
