# Organizator debaty studenckiej

**ASD1-M2-03 · Algorytmy i struktury danych I · Mini-projekt M2**  
Daniel Nedvecki · nr albumu 93797 · Informatyka  
Uniwersytet w Białymstoku, Filia w Wilnie · 2026/2027

## Uruchomienie

Otwórz `index.html` w aktualnej przeglądarce. Aplikacja działa lokalnie i nie wymaga konta ani serwera. Internet jest potrzebny wyłącznie do załadowania fontów; bez niego użyta zostanie czcionka zastępcza.

## Funkcje

- Ustawianie tematu debaty i limitu wypowiedzi 1–3600 sekund.
- Dodawanie uczestników z unikalnym ID, zgłoszenia do kolejki FIFO i rezygnacja z kolejki.
- Wywołanie następnej osoby, pomiar start/stop i ręczny zapis czasu testowego.
- Historia wystąpień, informacja o przekroczeniu limitu, podsumowanie i ranking.
- Własne wyszukiwanie liniowe i sortowanie przez wstawianie; widoczne liczniki operacji.
- Import i eksport JSON w wersji formatu 1. Import waliduje cały zestaw przed zastąpieniem danych.
- Trzy gotowe scenariusze: typowy, graniczny oraz większy zestaw 1000 wystąpień.
- Przykład kontrolny z opisem wyniku dostępny z przycisku.
- Porównanie wyszukiwania liniowego oraz sortowania na 10, 100 i 1000 rekordach.

## Reguły i algorytmy

Kolejka przechowuje zgłoszenia w tablicy. Dopisanie na koniec ma koszt O(1) amortyzowany, a pobranie pierwszego zgłoszenia usuwa element z początku tablicy (O(n), bo pozostałe elementy są przesuwane). Wyszukiwanie uczestnika ma koszt O(n). Ranking jest sortowany własnym sortowaniem przez wstawianie: czas malejąco, a przy remisie ID rosnąco. Koszt wynosi O(n²) w najgorszym przypadku i O(n) dla danych już uporządkowanych. Sumy wystąpień są obliczane pętlą.

ID uczestnika jest niepuste, unikalne i składa się z liter A–Z, cyfr lub łącznika. Jedna osoba może mieć najwyżej jedno oczekujące zgłoszenie. Osoba przemawiająca nie może być równocześnie w kolejce. Czas zapisujemy w całkowitych sekundach 0–3600. Limit wynosi 1–3600 sekund.

## Testy

Testy automatyczne są w `tests.js` i można je uruchomić poleceniem `node --test tests.js` w środowisku z Node.js. Obejmują przykład kontrolny, reguły kolejki, limit czasu, walidację importu, wyszukiwanie oraz sortowanie względem niezależnego wzorca.

## Przykład kontrolny

Limit 60 s; zgłoszenia A, B, A, C; B rezygnuje; A przemawia 65 s, a C 40 s. Drugie zgłoszenie A jest odrzucone, kolejka przed rozpoczęciem ma kolejność A, C, a końcowa suma czasu wynosi 105 s. A przekracza limit o 5 s, C mieści się w limicie. Przycisk „Przykład kontrolny” wczytuje ten przebieg.

## Scenariusze demonstracyjne

- **Typowy:** 4 osoby i 8 wystąpień o zróżnicowanych czasach.
- **Graniczny:** wystąpienia 0 s, dokładnie 60 s i 61 s przy limicie 60 s.
- **Większy zestaw:** 20 osób i 1000 powtarzalnie generowanych wystąpień.

Przycisk porównania pokazuje liczbę porównań sortowania dla danych uporządkowanych oraz odwróconych, a wyszukiwanie na początku, końcu i dla braku dopasowania.

## Ograniczenia wersji

Stan aplikacji pozostaje w pamięci bieżącej karty; do zachowania pracy użyj eksportu JSON. Pomiar jest ograniczony do 3600 s zgodnie z regułami zadania.

## Materiały M2

- `Dokumentacja_M2.docx` — dokumentacja przygotowana na bazie szablonu UwB. Przed oddaniem wpisz rzeczywiste wyniki uruchomionych testów i uzupełnij link do repozytorium.
- `Dokumentacja_M2.pdf` — eksport dokumentacji; sprawdzony układ ma dokładnie 10 stron.
- `prezentacja.html` — prezentacja lokalna z 10 slajdami. Użyj klawiszy strzałek albo przycisków nawigacji; klawisz F włącza pełny ekran.
- Repozytorium GitHub nie zostało jeszcze utworzone ani podłączone.
