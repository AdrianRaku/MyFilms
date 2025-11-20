# Aplikacja - MyFilms (MVP)

### Główny problem
Jako kinomaniak amator, często mam problem ze znalezieniem nowego interesującego mnie filmu lub serialu. Obecne platformy streamingowe oferują ogromne biblioteki treści, ale brak im spersonalizowanych rekomendacji opartych na moich unikalnych preferencjach. Często tracę czas na przeglądanie tysięcy tytułów, co prowadzi do frustracji i niezadowolenia z doświadczenia oglądania.

### Najmniejszy zestaw funkcjonalności (MVP)

**1. Zarządzanie kontem użytkownika:**
*   Rejestracja za pomocą adresu e-mail i hasła (bez weryfikacji e-mail w MVP).
*   Logowanie i zarządzanie sesją oparte na ciasteczkach.
*   Możliwość zmiany hasła przez zalogowanego użytkownika.

**2. Wyszukiwanie i ocenianie filmów:**
*   Integracja z bazą danych The Movie Database (TMDb) w celu wyszukiwania filmów.
*   Wyszukiwarka zwracająca do 20 wyników (kafelek z plakatem i tytułem).
*   System oceniania filmów w skali 1-10. Ocenienie filmu jest równoznaczne z jego obejrzeniem.
*   Możliwość oceniania filmów bezpośrednio z wyników wyszukiwania.
*   Ocenione filmy trafiają na listę "Ocenione".

**3. Strona szczegółów filmu:**
*   Każdy film (z wyszukiwania, listy czy rekomendacji) ma swoją stronę szczegółów z plakatem, opisem i oceną.
*   Dostępne akcje na stronie szczegółów:
    *   "Oceń" / "Zmień ocenę" / "Usuń ocenę".
    *   "Dodaj do ulubionych" / "Usuń z ulubionych" (przełącznik).
    *   "Dodaj do obejrzenia" / "Usuń z listy do obejrzenia" (przełącznik).

**4. Listy personalne:**
*   **Lista "Ocenione"**: Wyświetla wszystkie ocenione przez użytkownika filmy w formie siatki kafelków.
*   **Lista "Do obejrzenia"**: Użytkownik może dodawać filmy, które chce obejrzeć w przyszłości.
*   **Lista "Ulubione"**: Specjalna lista na filmy, które użytkownik darzy szczególnym sentymentem. Dodanie do ulubionych jest traktowane przez AI jako ocena 10/10, ale nie zmienia oceny wystawionej przez użytkownika.
*   Wszystkie listy mają spójny wygląd (siatka kafelków: plakat + tytuł).

**5. Rekomendacje AI:**
*   Funkcja dostępna po ocenieniu co najmniej 10 filmów.
*   Użytkownik może wywołać rekomendacje za pomocą przycisku, opcjonalnie dodając własny prompt tekstowy.
*   System generuje 5 rekomendacji w formie kafelków z przyciskami akcji. Możliwość kliknięcia i przejścia do szczegółów filmu.
*   AI otrzymuje historię ocen (tytuł, rok, ocena) oraz listę filmów do wykluczenia (już ocenione), aby zapewnić trafność i unikalność propozycji.
*   Limit 3 zapytań o rekomendacje na dzień na użytkownika w celu kontroli kosztów API. Tokeny nie są zużywane w przypadku błędu technicznego.
*   Integracja z modelem AI poprzez `openrouter` z prośbą o odpowiedź w formacie JSON.

### Co NIE wchodzi w zakres MVP
*   Aplikacja mobilna.
*   Komentarze do filmów.
*   Zaawansowane funkcje społecznościowe (np. profile publiczne, fora).
*   Obsługa wielu języków.
*   Paginacja (stronicowanie) list i wyników wyszukiwania.
*   Usuwanie konta i zmiana adresu e-mail przez użytkownika.

### Kryteria sukcesu
*   Pojawienie się pierwszych aktywnych użytkowników, którzy ocenili min. 10 filmów i korzystają z rekomendacji.
*   Użytkownicy dodają polecone filmy do listy "do obejrzenia" lub od razu je oceniają.
*   Stabilne działanie aplikacji bez krytycznych błędów przez okres pierwszych 3 miesięcy.
*   Zaangażowanie użytkowników mierzone średnią liczbą ocenionych filmów na aktywnego użytkownika.