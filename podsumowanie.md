Jasne, mistrzu. Oto podsumowanie naszej dyskusji, przygotowane zgodnie z Twoimi wytycznymi, aby ułatwić kolejny etap tworzenia dokumentu wymagań produktu (PRD).

<conversation_summary>
<decisions>
1.  Imię użytkownika nie jest zbierane ani wykorzystywane; personalizacja dotyczy tylko rekomendacji, a nie tekstu.
2.  Rezygnacja z przycisku "obejrzany" – ocena filmu jest równoznaczna z jego obejrzeniem.
3.  W MVP nie będzie paginacji; wyszukiwarka zwróci do 20 wyników, a listy będą wyświetlane w całości.
4.  Funkcjonalność konta w MVP ogranicza się do zmiany hasła.
5.  Aplikacja będzie witać użytkownika ekranem z instrukcją oceny 10 filmów w celu uzyskania pierwszej rekomendacji.
6.  Zdefiniowano dwie oddzielne listy: "Ulubione" i "Do obejrzenia".
7.  System będzie rekomendował 5 tytułów w formie kafelków (plakat + tytuł) z przyciskami akcji ("Do obejrzenia", "Oceń", "Ulubione").
8.  Możliwość oceniania filmów bezpośrednio z wyników wyszukiwania; oceniony film trafia na listę "ocenione".
9.  Rekomendacje nie będą zawierać tytułów już ocenionych przez użytkownika.
10. Po kliknięciu przycisku "oceń" na kafelku, staje się on nieaktywny.
11. Przycisk "Do obejrzenia" działa jak przełącznik (toggle), dodając lub usuwając film z listy.
12. Rejestracja w MVP nie wymaga weryfikacji adresu e-mail.
13. Lista "ocenione" będzie wyświetlana jako siatka kafelków (plakat + tytuł), a kliknięcie przenosi do strony szczegółów.
14. System weryfikuje w tle, czy tytuły zwrócone przez AI istnieją w bazie TMDb, odrzucając te nieznalezione.
15. Dodanie filmu do "ulubionych" automatycznie usuwa go z listy "do obejrzenia".
16. Tabela `users` w bazie danych będzie zawierać tylko `id`, `email` i zahaszowane `password`.
17. Przyciski akcji na kafelkach rekomendacji będą odzwierciedlać aktualny stan (np. czy film jest już na liście użytkownika).
18. W MVP nie będzie funkcji sortowania ani filtrowania na listach.
19. Na stronie szczegółów ocenionego filmu dostępne będą opcje "Zmień ocenę", "Usuń ocenę" oraz przełącznik "Dodaj/Usuń z ulubionych".
20. Listy "ulubione" i "do obejrzenia" również będą wyświetlane jako siatka kafelków.
21. Model AI ma zwracać odpowiedź w formacie JSON.
22. W przypadku pustych list "ulubione" i "do obejrzenia" wyświetlany jest komunikat z zachętą do działania.
23. W przypadku błędu technicznego API AI, użytkownik zobaczy ogólny komunikat o błędzie.
24. Proces zmiany hasła wymaga podania starego hasła oraz dwukrotnego podania nowego.
25. Sesja użytkownika będzie zarządzana za pomocą ciasteczek (cookies).
26. Do AI, oprócz tytułu filmu, przekazywany będzie również rok jego produkcji.
27. Usunięcie filmu z listy "ulubione" nie wpływa na jego ocenę.
28. System wyświetli błąd, jeśli użytkownik spróbuje zarejestrować się na istniejący już adres e-mail.
</decisions>

<matched_recommendations>
1.  **Interfejs oceniania:** Zalecono, aby po kliknięciu "oceń" wyświetlić okno modalne ze skalą 1-10, a przycisk stał się nieaktywny, co zostało zaakceptowane.
2.  **Unikanie duplikatów w rekomendacjach:** Zalecono, aby do promptu AI dołączać listę wykluczonych (już ocenionych) tytułów, co zostało zaakceptowane.
3.  **Logika przycisku "Do obejrzenia":** Zalecono, aby przycisk działał jak przełącznik (toggle), co zostało zaakceptowane.
4.  **Uproszczona rejestracja:** Zalecono rezygnację z weryfikacji e-mail w MVP, co zostało zaakceptowane.
5.  **Wygląd list:** Zalecono, aby wszystkie listy personalne miały spójny wygląd siatki kafelków, co zostało zaakceptowane.
6.  **Walidacja odpowiedzi AI:** Zalecono, aby system weryfikował rekomendacje z bazą TMDb przed ich wyświetleniem, co zostało zaakceptowane.
7.  **Logika list "Ulubione" i "Do obejrzenia":** Zalecono, aby dodanie filmu do "ulubionych" usuwało go z listy "do obejrzenia", co zapobiega nielogicznym stanom.
8.  **Struktura tabeli `users`:** Zalecono ograniczenie tabeli `users` do `id`, `email` i `password`, co zostało zaakceptowane.
9.  **Stan przycisków akcji:** Zalecono, aby przyciski odzwierciedlały, czy film jest już na listach użytkownika, co zostało zaakceptowane.
10. **Format odpowiedzi AI:** Zalecono, aby AI zwracało dane w formacie JSON, co zostało zaakceptowane.
11. **Jednoznaczność danych dla AI:** Zalecono przekazywanie do AI tytułu wraz z rokiem produkcji, co zostało zaakceptowane.
12. **Akcje na stronie szczegółów:** Zalecono dodanie opcji "Zmień ocenę", "Usuń ocenę" i przełącznika "Ulubione", co zostało zaakceptowane.
</matched_recommendations>

<prd_planning_summary>
**a. Główne wymagania funkcjonalne produktu:**
*   **Zarządzanie kontem:** Rejestracja (e-mail/hasło bez weryfikacji), logowanie (sesja na cookies), zmiana hasła (wymaga starego hasła).
*   **Interakcja z filmami:** Wyszukiwarka zintegrowana z TMDb (do 20 wyników w formie kafelków). System oceniania 1-10. Strona szczegółów filmu z opcjami: "Oceń"/"Zmień ocenę"/"Usuń ocenę", przełącznik "Ulubione", przełącznik "Do obejrzenia".
*   **Listy personalne:** Trzy listy ("Ocenione", "Do obejrzenia", "Ulubione") wyświetlane jako siatka kafelków bez opcji sortowania/filtrowania. Puste listy wyświetlają zachętę do działania.
*   **Rekomendacje AI:** Dostępne po ocenieniu 10 filmów. Użytkownik może wywołać je przyciskiem (z opcjonalnym promptem tekstowym). System generuje 5 rekomendacji (kafelki z przyciskami akcji), wykluczając już ocenione filmy. Obowiązuje limit 3 zapytań dziennie. Komunikacja z AI odbywa się przez JSON.

**b. Kluczowe historie użytkownika i ścieżki korzystania:**
*   **Onboarding nowego użytkownika:** Użytkownik rejestruje się, widzi ekran powitalny z instrukcją, wyszukuje i ocenia 10 filmów, aby odblokować funkcję rekomendacji.
*   **Otrzymywanie rekomendacji:** Użytkownik, mając ocenionych >10 filmów, klika przycisk "daj rekomendację". System wysyła do AI listę ocenionych filmów (tytuł, rok, ocena). AI zwraca 5 tytułów, które są walidowane z TMDb i wyświetlane jako kafelki.
*   **Interakcja z rekomendacją:** Użytkownik widzi polecony film i klika przycisk "Dodaj do obejrzenia" na kafelku, co powoduje dodanie filmu do odpowiedniej listy.
*   **Zarządzanie oceną:** Użytkownik przechodzi na swoją listę "Ocenione", klika na film, przechodzi do jego szczegółów i zmienia ocenę.

**c. Ważne kryteria sukcesu i sposoby ich mierzenia:**
*   **Aktywacja użytkowników:** Mierzona liczbą użytkowników, którzy ocenili co najmniej 10 filmów.
*   **Zaangażowanie:** Mierzone średnią liczbą ocenionych filmów na aktywnego użytkownika oraz stosunkiem liczby filmów dodanych do list z rekomendacji do liczby wygenerowanych rekomendacji.
*   **Stabilność:** Monitorowanie i utrzymanie niskiej liczby błędów krytycznych aplikacji przez pierwsze 3 miesiące działania.

**d. Wszelkie nierozwiązane kwestie lub obszary wymagające dalszego wyjaśnienia:**
*   Brak. Wszystkie kluczowe aspekty dla MVP zostały omówione i decyzje zostały podjęte.
</prd_planning_summary>

<unresolved_issues>
Brak.
</unresolved_issues>
</conversation_summary>

