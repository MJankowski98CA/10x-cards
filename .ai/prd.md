# Dokument wymagań produktu (PRD) - Aplikacja do Fiszek AI

## 1. Przegląd produktu
Aplikacja do fiszek AI ma na celu przyspieszenie i ułatwienie procesu tworzenia fiszek edukacyjnych. Projekt zakłada możliwość zarówno ręcznego dodawania fiszek, jak i automatycznego generowania ich przez moduł AI na podstawie wprowadzonego tekstu (od 1000 do 10000 znaków). Fiszki są następnie zapisywane i przypisywane do wybranej grupy, co wspiera organizację procesu nauki. Użytkownicy mają możliwość przeglądania fiszek, oznaczania ich jako opanowane, a także resetowania całej grupy, aby powtórzyć materiał. Narzędzie będzie wykorzystywać zewnętrzny algorytm powtórek (spaced repetition) oparty na bibliotekach open-source, co pozwoli optymalnie zaplanować proces nauki.

## 2. Problem użytkownika
Ręczne tworzenie fiszek wysokiej jakości jest pracochłonne i czasochłonne, co często zniechęca użytkowników do korzystania z efektywnych metod nauki typu spaced repetition. Aplikacja rozwiązuje ten problem, dostarczając funkcję automatycznego generowania fiszek przy użyciu AI, przy jednoczesnej możliwości edycji, zatwierdzania i odrzucania wygenerowanych propozycji. Dzięki temu użytkownicy mogą szybciej tworzyć materiały do nauki, zachowując przy tym kontrolę nad jakością fiszek.

## 3. Wymagania funkcjonalne
- System kont użytkowników:
  - Rejestracja i logowanie, aby każdy użytkownik miał bezpieczne, osobiste konto,
  - Uzytkownik moze zresetowac swoje haslo, odzyskac haslo przez podanie e-maila,
  - Przechowywanie fiszek i grup przypisanych do konkretnego użytkownika.

- Moduł generowania fiszek przez AI:
  - Możliwość wprowadzenia tekstu o długości od 1000 do 10000 znaków.
  - Generowanie propozycji fiszek (przód i tył), gdzie:
    - Pole przód może zawierać maksymalnie 200 znaków.
    - Pole tył może zawierać maksymalnie 500 znaków.
  - Użytkownik ma możliwość akceptacji lub odrzucenia każdej propozycji fiszki.

- Manualne tworzenie fiszek:
  - Formularz do ręcznego wprowadzenia treści (przód/tył) z zachowaniem limitów znaków (200 dla przodu, 500 dla tyłu).
  - Przypisanie fiszki do istniejącej lub nowej grupy.

- Przeglądanie, edycja i usuwanie fiszek:
  - Widok listy powinien zawierać grupy a po wejściu w grupę powinien być ukazany widok karuzeli w której będą fiszki w formie przód/tył (domyślnie przód a tył po kliknięciu w fiszkę). Dodatkowo mozna przewijac karuzele w prawo i w lewo.
  - Możliwość edycji i usuwania wcześniej utworzonych (lub wygenerowanych) fiszek, przy czym:
  - Edycja powinna być możliwa również dla fiszek wygenerowanych przez AI, zarówno przed, jak i po ich zatwierdzeniu lub odrzuceniu.
  - Usuwanie fiszek nieodwracalnie usuwa je z grupy.

- Zarządzanie grupami fiszek:
  - Mały formularz do tworzenia nowej grupy fiszek,
  - Tworzenie grupy fiszek z poziomu widoku listy grup,
  - Mozliwość edycji nazwy grupy oraz usuwania grupy,
  - Każda fiszka (manualna lub AI) musi być przypisana do konkretnej grupy.
  - Automatyczne propozycje nazwy grupy na podstawie wprowadzonego tekstu (np. tytuł, temat), z możliwością zmiany przez użytkownika dotyczy fiszek wygenerowanych przez AI.
  - Resetowanie statusu nauki całej grupy (wszystkie fiszki stają się nieopanowane).

- Nauka i status fiszek:
  - Oznaczanie fiszek jako opanowane lub wymagające dalszej nauki.
  - Integracja z zewnętrznym algorytmem powtórek, który odpowiada za harmonogram nauki,
  - Liczba opanowanych fiszek na maksymalną ilość fiszek w grupie na liście fiszek w grupie,

- Statystyki:
  - Prezentacja statycznego widoku liczby zaakceptowanych i odrzuconych fiszek (w danej grupie oraz łącznie).
  - Przeliczanie wskaźnika sukcesu (stosunek zaakceptowanych do odrzuconych fiszek generowanych przez AI).

## 4. Granice produktu
- Brak zaawansowanego, własnego algorytmu powtórek (korzystamy z gotowego rozwiązania).
- Ograniczenie importu danych (brak obsługi wielu formatów, w tym PDF/DOCX).
- Brak funkcji współdzielenia zestawów fiszek między użytkownikami.
- Brak integracji z platformami edukacyjnymi zewnętrznymi.
- Brak aplikacji mobilnych – na początek jedynie wersja przeglądarkowa (web).
- Interfejs użytkownika jest prosty i minimalny, pozbawiony zaawansowanych opcji personalizacji czy historii aktywności.
- Brak instrukcji czy przewodników wewnątrz aplikacji.
- Brak funkcjonalności eksportu statystyk.
- Resetowanie statusu nauki dotyczy wyłącznie całej grupy, a nie pojedynczych fiszek.

## 5. Historyjki użytkowników

### US-001
Tytuł: Rejestracja nowego konta
Opis: Jako nowy użytkownik chcę założyć konto w aplikacji, aby móc zapisywać własne fiszki oraz mieć do nich dostęp w bezpieczny sposób.
Kryteria akceptacji:
- Po wypełnieniu formularza rejestracyjnego (e-mail, hasło) konto zostaje utworzone.
- Hasło musi spełniać minimalne wymagania bezpieczeństwa (np. 8 znaków).
- Po pomyślnej rejestracji użytkownik jest automatycznie zalogowany lub przekierowany do ekranu logowania.

### US-002
Tytuł: Logowanie do konta
Opis: Jako zarejestrowany użytkownik chcę móc się zalogować, aby uzyskać dostęp do moich fiszek i grup.
Kryteria akceptacji:
- Po podaniu prawidłowych danych logowania (e-mail, hasło) użytkownik zostaje zalogowany i przeniesiony do głównego panelu aplikacji.
- W przypadku błędnych danych logowania wyświetlany jest komunikat o błędzie.

### US-003
Tytuł: Tworzenie nowej grupy
Opis: Jako użytkownik chcę móc utworzyć nową grupę fiszek, aby organizować fiszki według tematyki.
Kryteria akceptacji:
- Po kliknięciu w opcję utworzenia nowej grupy wyświetla się formularz nazwy grupy.
- Użytkownik może nadać dowolną nazwę grupy.
- Nowa grupa pojawia się na liście dostępnych grup dla tego użytkownika.

### US-004
Tytuł: Generowanie fiszek przez AI
Opis: Jako użytkownik chcę wkleić tekst (od 1000 do 10000 znaków), aby uzyskać propozycje fiszek generowanych przez AI.
Kryteria akceptacji:
- Formularz przyjmuje tylko tekst mieszczący się w zakresie 1000–10000 znaków (wliczając spacje).
- W przypadku mniejszej lub większej liczby znaków system wyświetla komunikat o błędnym zakresie.
- Po przesłaniu tekstu wyświetlane są wygenerowane propozycje fiszek, każda z maksymalnie 200 znaków w polu przód i 500 znaków w polu tył.

### US-005
Tytuł: Akceptowanie lub odrzucanie fiszek AI
Opis: Jako użytkownik chcę zaakceptować lub odrzucić każdą propozycję fiszki wygenerowaną przez AI, aby zachować pełną kontrolę nad treścią.
Kryteria akceptacji:
- Przy każdej wygenerowanej fiszce widoczny jest przycisk Akceptuj lub Odrzuć.
- Akceptowane fiszki zostają przeniesione do wybranej grupy (istniejącej lub nowej).
- Odrzucone fiszki nie są zapisywane w grupie.
- Użytkownik widzi podsumowanie liczby zaakceptowanych i odrzuconych fiszek.

### US-006
Tytuł: Manualne tworzenie fiszek
Opis: Jako użytkownik chcę wprowadzić własną treść (przód i tył), aby stworzyć fiszkę bez korzystania z modułu AI.
Kryteria akceptacji:
- Formularz umożliwia wpisanie tekstu w polu przód (max 200 znaków) i tył (max 500 znaków).
- Po zapisaniu fiszka jest przypisana do wybranej lub nowo utworzonej grupy.
- W przypadku przekroczenia limitu znaków system wyświetla komunikat o błędzie.

### US-007
Tytuł: Edycja i usuwanie fiszek
Opis: Jako użytkownik chcę móc edytować treść fiszki oraz usuwać niepotrzebne fiszki, aby zachować aktualność i porządek w moich materiałach.
Kryteria akceptacji:
- Edycja może odbywać się zarówno dla fiszek tworzonych manualnie, jak i generowanych przez AI (po akceptacji lub przed ponownym zapisaniem).
- Po wprowadzeniu zmian pola przód/tył weryfikowane są limity znaków.
- Usunięta fiszka znika z listy i nie jest uwzględniana w statystykach.

### US-008
Tytuł: Przeglądanie i nauka fiszek
Opis: Jako użytkownik chcę widzieć fiszki w wybranej grupie i mieć możliwość przeglądania ich, aby się uczyć.
Kryteria akceptacji:
- Widok grupy prezentuje listę fiszek w niej zawartych.
- Kliknięcie w przód fiszki pokazuje jej tył (i odwrotnie), symulując tradycyjną fiszkę.
- Użytkownik może na tym etapie oznaczać fiszkę jako opanowaną lub nieopanowaną.

### US-009
Tytuł: Oznaczanie fiszek jako opanowane lub nieopanowane
Opis: Jako użytkownik chcę oznaczyć stan opanowania fiszki, aby móc śledzić swój postęp w nauce.
Kryteria akceptacji:
- Po kliknięciu przycisku (np. opanowane) fiszka zmienia swój status w systemie.
- Status jest zapisywany indywidualnie dla każdego użytkownika.
- Informacja o statusie jest wykorzystywana przez zewnętrzny algorytm powtórek do planowania kolejnych sesji nauki.

### US-010
Tytuł: Resetowanie statusu nauki całej grupy
Opis: Jako użytkownik chcę zresetować status nauki całej grupy fiszek, aby móc od nowa przejść przez ich przegląd.
Kryteria akceptacji:
- Po wybraniu opcji resetu system wyświetla potwierdzenie.
- Po potwierdzeniu status wszystkich fiszek w danej grupie jest ustawiany jako nieopanowane.
- Reset nie usuwa fiszek, a jedynie zmienia ich status.

### US-011
Tytuł: Przeglądanie statystyk zaakceptowanych i odrzuconych fiszek
Opis: Jako użytkownik chcę zobaczyć statystykę pokazującą liczbę i stosunek zaakceptowanych oraz odrzuconych fiszek, aby ocenić użyteczność modułu AI.
Kryteria akceptacji:
- Statystyki wyświetlane są w postaci tabeli (liczba zaakceptowanych, liczba odrzuconych) dla grupy lub dla całego konta użytkownika.
- Wskaźnik sukcesu (procent zaakceptowanych) jest obliczany na podstawie fiszek generowanych przez AI.
- Dane te są przedstawiane w prostym widoku, bez możliwości filtrowania czy eksportu.

## 6. Metryki sukcesu
1. Proporcja zaakceptowanych fiszek wygenerowanych przez AI – docelowo 75% zaakceptowanych fiszek na 25% odrzuconych.
2. Odsetek fiszek utworzonych z wykorzystaniem modułu AI (co najmniej 75% wszystkich fiszek użytkownika).

