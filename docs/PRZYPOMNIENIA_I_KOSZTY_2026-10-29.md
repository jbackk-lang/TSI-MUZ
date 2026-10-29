# Belka informacyjna i koszty stałe — 29 października 2026

Belka pokazuje po jednym nieprzeczytanym komunikacie, zaczynając od pilnych terminów. Oznaczenie wszystkich jako przeczytane jest dostępne w przeglądzie. Po przeczytaniu ostatniego pozostaje mały przycisk otwierający listę. Kolor uzupełnia opis: niebieski do zrobienia, żółty przypomnienie, czerwony po terminie, zielony załatwione.

Terminy wynikają ze spraw zapisanych w MUZ. Przy dokumentach użytkownik zapisuje wymagane czynności i potwierdza podpięcie lub wysłanie. Nie jest to automatyczne wykrywanie wysłanych wiadomości ani klient pocztowy. Zamknięcie sprawy wycisza powiązane dokumenty. Można wyłączyć przypomnienia o dokumencie i ponownie je włączyć. Przeczytanie nie oznacza wykonania. Czynności oczekujące wracają kolejnego dnia lub po zmianie treści; potwierdzone zakończenia tylko po zmianie treści.

Tabela stałych kosztów korzysta z zapisanych transakcji w PLN. Pomija wpływy, inne waluty i zduplikowane identyfikatory. Typowe opisy rachunków lub podobne kwoty w różnych miesiącach dają propozycję, nie pewność istnienia zobowiązania. Dowodem jest ostatnia płatność i grupa zapisów źródłowych. Oszacowana częstotliwość i dzień płatności wymagają zatwierdzenia. Własne wpisy i poprawki zapisuje się wierszami; zapis jednego wiersza zachowuje edycję pozostałych. Konflikt dwóch okien wymaga ponownego odczytu danych.

Miesięczny koszt jest kwotą za okres podzieloną przez 1, 2, 3 lub 12, z końcowym zaokrągleniem do grosza. Jest to zestawienie kosztów, nie nowy wydatek ani potwierdzenie zapłaty. Wyłączenie pozycji usuwa ją z sumy bez kasowania. Niepotwierdzone propozycje nie trafiają do sumy potwierdzonej. Tabela nie zapisuje wydatków, nie zmienia planu i nie realizuje przelewów.

Dane dodatków są przechowywane lokalnie w runtime/reminders.json i runtime/fixed_costs.json, oddzielnie od księgi spraw i transakcji. Wdrożenie zachowuje wcześniejsze dane i kopie plików aplikacji. Wagi TSI pozostają bez zmian. Nie aktualizowano archiwów portable ani publikacji GitHub.

Weryfikacja: 18 testów mechanizmu przypomnień i kosztów, próby UI na oddzielnych danych przykładowych, przechodzenie czterech kolorów, pamiętanie przeczytania między stronami, edycja dokumentu, potwierdzenie propozycji i ręczny koszt roczny, zachowanie niezapisanych innych wierszy.


## Powiązanie kosztów z belką

Każdy aktywny, potwierdzony koszt ma najbliższą datę płatności. Do siedmiu dni przed nią pojawia się działanie, w terminie żółte przypomnienie, później czerwone. Brak daty daje prośbę o uzupełnienie tabeli. Niepotwierdzone propozycje są zadaniami do sprawdzenia. Otwórz koszt w tabeli przechodzi do właściwego wiersza. Potwierdź opłacenie zapisuje oświadczenie użytkownika, pokazuje zielony komunikat i przesuwa termin dokładnie o jeden okres — nie pomija kilku zaległych okresów. Dzień końca miesiąca jest ograniczany do liczby dni w danym miesiącu. Nie tworzy to transakcji ani przelewu.

## Raporty i zwarty widok

Centralny panel pokazuje liczby i pierwsze trzy zalecane działania wynikające z przypomnień. Są to czynności organizacyjne oparte na zapisanych danych, nie ocena kompletności finansów. Przeczytane, ale niewykonane zadanie może pozostać w zalecanych działaniach. Na stronie budżetu liczby i okres pochodzą z wybranego widoku tabeli. Wykresy, transakcje i stałe koszty są zwijane; import rachunków, metoda oszczędzania i podsumowanie kategorii na głównej stronie również.

Raport ma zakres dat, wybór działów, własne uwagi i przełącznik szczegółów. Ustawienia zapisują się w runtime/report_preferences.json. Transakcje dotyczą wybranego okresu; koszty to aktualny plan, a statusy spraw i dokumentów są bieżące. Uwagi są dołączane jako tekst i nie zastępują wyboru działów. Raport można pobrać jako samodzielny HTML, otworzyć w osobnej karcie (jeśli zezwala przeglądarka) i wydrukować / zapisać PDF z przeglądarki. Nie ma zaplanowanej automatycznej wysyłki raportów.

Próba interfejsu potwierdziła zapis ustawień i eksport HTML. Automatyczna kontrola przeglądarki zablokowała próbę otwarcia wygenerowanego raportu w nowej karcie; tej opcji nie potwierdzono automatycznie. Widok drukowania jest udostępniony, bez wykonywania wydruku podczas testu.


## Zwężenie tabeli i usuwanie kosztów

Każdy wiersz ma przycisk Usuń. Usunięcie usuwa pozycję z bieżących podsumowań i przypomnień, a propozycja z tych samych danych nie wraca po odświeżeniu. Pod tabelą znajdują się Dodaj stały koszt i Cofnij usunięcie. Cofnięcie przywraca koszt, zachowując kontrolę rewizji i nie nadpisując ponownie dodanej pozycji. Rachunki źródłowe i rzeczywiste transakcje nie są usuwane. Nowe niezapisane wiersze również można usunąć i cofnąć tę czynność przed odświeżeniem strony.

Zmniejszono szerokości pól, nagłówki i przyciski; źródła propozycji są rozwijane w wierszu. Przy typowej szerokości pulpitu tabela mieści się bez przewijania poziomego. Dodano cztery testy usuwania i cofania; wykonano próbę interfejsu na oddzielnych danych testowych.
