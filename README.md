# TSI-MUZ

**Stan: 23 października 2026.** Lokalny zarządca budżetu, dokumentów, spraw i terminów.

## Co działa

- Dashboard spraw i planów oraz osobna tabela budżetu z wykresami i podsumowaniem kategorii.
- Import wyciągów PDF z tekstem, CSV i MT940/STA: do 10 plików i 100 MB, status każdego pliku, propozycje kategorii i kontrola ponownego importu. Skan może wymagać OCR; nie każdy układ dokumentu jest obsługiwany.
- Ręczne wpływy i wydatki, edycja, usuwanie oraz cofanie korekty; kwoty są przechowywane w całkowitych groszach.
- Analiza dostępnego salda, historii wydatków i stałych opłat; plan rezerwy i przydziału środków oraz projekty pism w zakresie silnika MUZ.
- Automat sprawdzający terminy i zmiany co 30 sekund, gdy serwer działa. Dane i historia spraw są zapisywane lokalnie w SQLite.
- Wspólna obsługa zadań przez TSI, walidacja przekazywanych rekordów i wskazywanie brakujących danych zamiast wymyślania salda.

MUZ nie wykonuje przelewów ani nie wysyła pism. Nie pobiera sam transakcji z banku. Projekty wymagają oceny użytkownika; bez kompletnego salda i historii plan może pozostać niepełny.

## Uruchomienie

Instalacja robocza: `Uruchom_TSI_MUZ.bat`; panel `http://127.0.0.1:8796/`. Menu umożliwia otwarcie, restart i zamknięcie własnego serwera.

Portable: rozpakuj ZIP i użyj `START.bat`. Wybierany jest osobny wolny port od 8820. Zamykanie własnej instancji: `ZATRZYMAJ.bat`. Automat działa przy uruchomionym serwerze; zamknięcie karty przeglądarki nie zatrzymuje serwera.

## Ostatnie sprawdzenia

**5/5 kontroli budżetu**: pełny plan zgodny z dotychczasowym silnikiem, dokładne saldo **2950,00 zł**, odrzucenie niecałkowitych groszy, niewłaściwej waluty i przyszłej daty oraz poprawny wynik po odrzuconych żądaniach.

Próba HTTP z dodanym wydatkiem potwierdziła wskazanie brakującego salda i historii potrzebnej do planu. Dane sprawdzianu były syntetyczne. Wyniki nie oznaczają kwalifikacji do samodzielnego podejmowania decyzji finansowych.

## TSI — stan na 23 października 2026

Obliczenia i odczyt obsługiwanych poleceń korzystają ze wspólnego modułu TSI. Czytnik i narzędzia pozostają w uruchomionym procesie, co usuwa ich wielokrotne ładowanie przy kolejnych zadaniach. Moduł matematyczny znajduje się wewnątrz TSI; aplikacje korzystają z jego interfejsu.

Aktywny moduł dowodowy: **TSI-DUAL-TASK-V3-5f8069b8**, **10 227 859 parametrów**, plik wag **41 276 171 bajtów (39,36 MiB)**. To rozmiar tego checkpointu, a nie wszystkich czytników, bibliotek i aplikacji. Dodatkowe czytniki, modele dziedzinowe oraz solvery są dołączane osobno.

Nowe wagi swobodnej rozmowy pozostają w treningu i **nie są wdrożone**. Wynik 24/24 na wybranym zestawie kolorów i godzin nie potwierdził ogólnej poprawy: szerszy sprawdzian dał 9/12 przed i po korekcie. Nadal rozwijane są wiązanie cech z osobami, aktualizacja faktów i pełny zapis wartości.

## Portable — Windows x64

Paczka zawiera kod źródłowy, aktywne modele, lokalny Python i biblioteki. Rozpakuj cały ZIP do katalogu z prawem zapisu i uruchom **START.bat**. Zatrzymanie: **ZATRZYMAJ.bat**. Nie potrzeba innych katalogów projektów ani instalowania Pythona. Zachowaj całą strukturę folderów.

Portable przechowuje własne dane wykonania w `app/runtime`. Archiwum startowe nie zawiera prywatnych dokumentów bankowych, danych użytkownika, haseł panelu, tokenów, historii Git i katalogów treningu. Baza użytkownika istniejącej lokalnej wersji portable jest zachowywana podczas aktualizacji folderu; ZIP przeznaczony do przenoszenia pozostaje czysty.

Rozmiary składników znajdują się w `PACKAGE_INFO.json` wewnątrz paczki. Rozmiar ZIP i jego SHA-256 zapisuje raport `PORTABLE_PACKAGES_2026-10-23.json` obok archiwów. Zewnętrzne odnośniki słownika wymagają internetu. Import obrazów wymaga dostępnego lokalnego OCR; obecność i działanie OCR są wykazywane w raporcie kontroli paczki.

## Historia

Poprzedni README i opis wcześniejszych etapów: [archiwum dokumentacji](docs/archiwum/README_przed_2026-10-23.md). [Aktualna integracja i sprawdzenia](docs/INTEGRACJA_TSI_2026-10-23.md).
