# TSI-MUZ

Lokalny zarządca spraw i budżetu. Kod i historia Git pozostają na komputerze.

## Co działa

- Dashboard: sprawy, terminy, statusy, wyniki działań, plan i rzeczywiste wydatki.
- Trwała baza spraw i planów SQLite, historia zmian i rozliczeń.
- Automat co 30 sekund sprawdza wydatki i terminy. Zapisuje tylko zmiany, wykrywa przekroczenia i sprawy po terminie.
- Istniejący silnik MUZ: analiza lokalnych wyciągów, reguły budżetu, projekty pism i bramka zatwierdzeń.
- Integracja TSI przez zadanie strukturalne w `bridge.py`. Router finansowego języka naturalnego nie jest jeszcze wyuczony.

## Uruchomienie

Otwórz `Uruchom_TSI_MUZ.bat`. Menu: 1 — uruchom/otwórz panel, 2 — zamknij serwery tego projektu, 3 — uruchom ponownie, 4 — wyjdź. Panel działa pod http://127.0.0.1:8796/. Jeśli już działa, wykorzystywany jest istniejący serwer. Błędy startu są zapisywane w ignorowanym runtime/server.log. Zamykanie używa lokalnego klucza sterującego i nie zatrzymuje innych aplikacji. Zatrzymanie serwera zatrzymuje też automat; dane pozostają zapisane. Możliwe parametry BAT: `--stop-all`, `--stop`, `--restart` i `--no-browser`.
W tej instalacji plik `.python-path` wskazuje lokalne środowisko Python i nie trafia do Git.
Na innym komputerze: Python 3.10+, `python -m pip install numpy`; PDF wymaga reportlab, import PDF — pdfplumber. Następnie `python dashboard_server.py`.

1. Dodaj sprawy z terminami i następnym krokiem.
2. Ustaw okres planu oraz kategorie i limity, np. `Żywność: 1000` i `Abonament: 89`.
3. Dodaj rzeczywiste wydatki i przypisz kategorie.
4. Włącz automat albo użyj „Sprawdź teraz”.

Automat działa, gdy serwer jest uruchomiony, również po zamknięciu karty przeglądarki. Zatrzymanie serwera zatrzymuje nadzór. Nie jest instalowany przy starcie Windows. Stan włączenia jest zapamiętywany.
Nie pobiera sam danych z banku, nie wykonuje przelewów i nie wysyła pism. Wydatki można wpisywać ręcznie lub importować z wybranych dokumentów. Wynik jest wstępny bez potwierdzenia kompletności wyciągu. Pozostały limit nie oznacza oszczędności.

## Dokumenty z banku

W centrum wybierz „Dokumenty z banku”, wskaż PDF z warstwą tekstową, CSV albo MT940/STA i naciśnij „Przeanalizuj dokumenty”. Panel pokaże zakres dat, wpływy, wydatki, propozycje kategorii, stałe opłaty, wstępny przydział MUZ i wykryte sprawy. Dopiero „Zapisz transakcje” dodaje dane do budżetu. Ponowny import zachowuje liczbę tych samych płatności. Kategorie spoza planu są wykazywane jako nieprzypisane do limitów.

Do 10 plików i łącznie 100 MB. Analiza zaczyna się po wyborze plików; przycisk pozwala powtórzyć ją np. po podaniu hasła. Wynik podaje status każdego pliku. Błąd odczytu jednego dokumentu nie zatrzymuje pozostałych. Rozpoznawane podsumowania salda, limitu i kredytów są obsługiwane osobno, bez tworzenia fikcyjnych transakcji. PDF z hasłem wymaga podania hasła w panelu; hasło nie jest zapisywane. Skanów bez tekstu i nieznanych układów PDF parser może nie odczytać. Brak CPI i potwierdzonych warunków umów ogranicza ocenę podwyżek; raport wskazuje ten brak. Pliki zostają w ignorowanym katalogu runtime. Opcjonalny ignorowany plik `.python-extra-path` może wskazywać zgodne lokalne pakiety Python.

## Pochodzenie kwot z dokumentów

W nowych analizach sekcja „Skąd pochodzą kwoty? · ostatni import” pokazuje plik, jego SHA-256 i pozycję odczytanej transakcji oraz matrycę sum. Kwoty są liczone w groszach. Raport odnosi się do ostatniego importu, nie późniejszych ręcznych korekt. Pozycja nie oznacza strony ani wiersza dokumentu. Starsze raporty wymagają ponownej analizy plików, aby pokazać pochodzenie danych. Testy: 16/16, dodatkowo syntetyczny import i odtworzenie raportu oraz kontrola widoku. [Zakres i ograniczenia](../POCHODZENIE_KWOT_2026-10-16.md).

## Tabela i wykresy budżetu

Po zapisie ręcznego wydatku panel wyświetla potwierdzenie i czyści formularz. Blokada przycisku i identyfikator żądania zabezpieczają przed podwójnym zapisem jednego kliknięcia. Pierwsza strona pokazuje sumy wydatków według kategorii oraz łączną kwotę wpływów i wydatków.

W tabeli transakcji na podstronie budżetu zapisane wpisy mają przyciski „Edytuj” i „Usuń”. Korekta obejmuje datę, odbiorcę, rodzaj wpływ/wydatek, kwotę i kategorię. „Cofnij ostatnią korektę / usunięcie” przywraca poprzedni stan. Zmiany i wcześniejsze wartości są przechowywane lokalnie; podsumowania przeliczają się po zmianie. Wpisy wyłącznie z podglądu importu trzeba najpierw zapisać. Tabela transakcji podsumowuje także kwoty wybranego filtra.

Podstrona „Tabela i wykresy budżetu” w centrum prowadzi do `/budzet`.
Domyślnie pokazuje wczytane transakcje, kategorie i wykresy także bez ustawienia planu; podgląd importu jest oznaczony jako niezapisany. Lista kategorii na pierwszej stronie uzupełnia się po analizie dokumentów. Osobny widok „Plan i wykonanie” pokazuje plan, wykonanie, pozostałe limity, przekroczenia i procent realizacji,
wykres słupkowy planu i wydatków, udział kategorii oraz listę transakcji z filtrem.
Korzysta z tego samego lokalnego planu i wydatków, odświeża dane co 10 sekund.
Na małym ekranie szerokie tabele można przesuwać w poziomie.

## Dane i testy

Panel zaczyna z pustymi danymi. Dane użytkownika w `runtime/` i `.python-path` są ignorowane przez Git. Nie przeniesiono prywatnych plików z poprzedniego MUZ.
Testy: `python -m pytest tests integration_tests -q`. Do pełnych testów: pytest, numpy, reportlab, pdfplumber i opcjonalne zależności silnika.
Historia wcześniejszych funkcji MUZ: `README_MUZ_ORIGINAL.md`.

## Wspólny moduł TSI 0.5 — 20 października 2026

Lokalnie zaktualizowano moduł wspólny: matryce słownika i wymagań są wagami checkpointu z transformerem, a role rozpoznaje uczona warstwa przejść. Potwierdzono przygotowanie projektu budżetu na danych syntetycznych i sprawdzenie wyniku. To aktualizacja modułu; samodzielne zarządzanie całym budżetem nie wynika z tego testu. [Zakres i wyniki wspólnej części](../TSI_MATRIX_CORE_2026-10-20.md).
