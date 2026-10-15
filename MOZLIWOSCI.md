# Możliwości i sposób użycia

## Typowy przebieg

1. Dodaj sprawę, np. sprawdzenie rachunku za abonament. Zapisz termin i następny krok.
2. Ustal okres budżetu oraz limity kategorii.
3. Dodawaj rzeczywiste wydatki i przypisuj im kategorię.
4. Sprawdzaj wykonanie planu ręcznie albo włącz lokalny automat.
5. Zapisz wynik działania i kolejny krok. Zakończenie sprawy wymaga opisu wyniku.

## Przykład syntetyczny

Plan abonamentu wynosi 89 zł, a rzeczywisty rachunek 119 zł. System pokazuje przekroczenie **30 zł**. Użytkownik może zapisać sprawę „Wyjaśnij rachunek” i wynik porównania. Sama deklaracja operatora o obniżce nie jest dowodem oszczędności.

## Dane i trwałość

Sprawy, plany oraz ich rozliczenia pozostają w lokalnej bazie SQLite. Panel przechowuje wydatki, kategorie i ustawienie automatu lokalnie. Dane użytkownika są wyłączone z historii Git. Przeglądarka komunikuje się z serwerem na tym samym komputerze.

Rozliczenie operuje na całkowitych groszach. Wydatki bez kategorii są jawnie wykazane. Powtórzony identyfikator transakcji nie nalicza jej ponownie; sprzeczne dane z tym samym identyfikatorem są odrzucane. Nieprzeliczone waluty obce są odrzucane. Ręczne wpisanie tego samego zakupu drugi raz tworzy nowy identyfikator i wymaga kontroli użytkownika.

## Dokumenty i analiza

Silnik MUZ ma lokalny import wyciągów i przygotowanie projektów dokumentów. Nowy dashboard obejmuje obecnie sprawy, plan, ręcznie wpisywane wydatki i automat. Import wyciągów oraz pisma z poziomu dashboardu są dalszym etapem.

## Granice automatyzacji

Automat sprawdza lokalnie zapisane dane co 30 sekund, gdy działa serwer. Zapisuje istotne zmiany, a nie powtarzające się komunikaty bez zmian. Nie zmienia sam statusów spraw ani nie potwierdza wykonania działania za użytkownika.

Brak integracji bankowej, powiadomień poza panelem, autostartu Windows i samodzielnego wykonywania operacji finansowych.
