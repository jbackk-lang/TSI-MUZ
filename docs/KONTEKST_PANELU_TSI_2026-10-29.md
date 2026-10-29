# Kontekst panelu TSI w MUZ — 29 października 2026

W ostatniej rozmowie brak informacji o otwartym widoku powodował odpowiedź słownikową na pytanie o tabelę oraz wyszukiwanie nazw banków po słowie kredyt. Frontend przekazuje teraz tożsamość panelu, wybrany wiersz i filtry. Serwer odczytuje aktualne dane aplikacji, weryfikuje wybór i buduje typowaną ramkę źródłową. Lokalny czytnik pytań o panel korzysta z niej przed słownikiem i wyszukiwaniem, zachowując zwykłą ścieżkę dla pytań spoza kontekstu i jawnego wyszukiwania.

W okienku widoczny jest zakres. Wskazanie nowego panelu lub wiersza zmienia zakres; pytania uzupełniające mogą zachować omawianą pozycję. Dane usuniętej pozycji nie są zastępowane inną. Niezapisany koszt jest oznaczany jako formularz i nie zmienia zapisanej tabeli. Pozostałe panele pokazują dane zapisane w aplikacji; odczyt nie zatwierdza formularzy. W ustawieniach jest przełącznik kontekstu. Nowa rozmowa ma oddzielny stan wyboru.

Odpowiedzi kontekstowe są odczytem strukturalnych danych, nie nowym treningiem generatora ani dowodem gotowości swobodnej rozmowy. Nie wysyłają ramki danych finansowych do zewnętrznego AI. Zapisy rozmów i wybranego zakresu pozostają w lokalnej bazie MUZ. Wagi oraz aplikacje innych modułów pozostają bez zmian.

Weryfikacja: dziewięć testów odczytu i zakresu; pełny transport API–proces rozmowy na oddzielnych danych testowych; scenariusze pytania o tabelę, kategorii kredyt, pytania uzupełniającego i niezapisanej kwoty w innym panelu. Dla przykładowych danych: wydatki tabeli 223,45 zł, kategoria kredyt 123,45 zł, niezapisana edycja kosztu 155,55 zł. Zachowano surowe odpowiedzi testowe. Nie zmieniano rzeczywistych transakcji ani nie publikowano danych użytkownika.
