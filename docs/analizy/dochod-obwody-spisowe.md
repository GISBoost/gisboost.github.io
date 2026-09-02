---
description: Jak oszacować dochód mieszkańców na poziomie obwodu spisowego w Polsce, skoro spis powszechny go nie zbiera. Metoda, weryfikacja i wyniki dla 6 miast.
---

# Ile zarabia Twój obwód? Szacowanie dochodu tam, gdzie spis go nie mierzy

> **Uwaga: treść eksperymentalna.** Ten wpis w całości wygenerowała AI (Claude) na
> podstawie mojego kodu i danych — to wstępna, robocza wersja, która ma pomóc mi
> rozeznać się w temacie, nie ostateczne wnioski badawcze. Liczby i interpretacje
> traktuj jako punkt wyjścia do dalszej weryfikacji, nie jako gotowy wynik.

Polski spis powszechny (NSP 2021) nie pyta o dochód. W ogóle, na żadnym poziomie
drobniejszym niż gmina. Jeśli chcesz wiedzieć, czy bogatsza część miasta ma lepszy dostęp
do transportu, do szkół, do przychodni, nie masz z czego tego policzyć wprost, bo w Polsce
po prostu nie ma publicznych danych o dochodzie w rozdzielczości poniżej całej gminy.

Do tego typu pytań doszedłem po lekturze artykułu Bragi, Loureiro i Pereiry (2026, *Journal
of Transport Geography*, 131, 104526) o nierównościach dostępności transportu publicznego
w Fortalezie, w Brazylii. Oni mogli po prostu wziąć dochód z brazylijskiego spisu, bo tam
zbiera się go na poziomie *setor censitário*, czyli odpowiednika naszego obwodu spisowego.
U nas trzeba było dochód najpierw oszacować. Ten wpis opisuje jak, dla sześciu miast:
Łodzi, Krakowa, Warszawy, Poznania, Gdańska i Szczecina.

## Skąd wziąć dochód, którego nikt nie zmierzył

Rozwiązanie nazywa się w literaturze MRP (Multilevel Regression + Poststratification)
z predyktorem obszarowym, czyli wynikiem wyborczym (Hanretty, Lauderdale i Vivyan, 2016,
*Political Science Research and Methods*, 6(3), 571–591). Sedno: skoro wiadomo mniej
więcej, jaki profil dochodowy ma elektorat każdej partii, a wyniki głosowania per obwód są
publiczne i bardzo dokładne, to można policzyć ważoną średnią.

**To nie jest zmierzony dochód. To estymacja.** Warto to powiedzieć na samym początku,
zanim ktokolwiek pomyśli, że to jest coś innego. Zakładam, że skład polityczny obwodu
głosowania koreluje z jego profilem dochodowym w taki sposób, jak wynika z ogólnopolskiej
ankiety. To założenie ma ograniczenia, do których wracam na końcu.

### Krok 1: dochód deklarowany przez elektoraty partii

Źródło: komunikat CBOS nr 98/2023, [*Kim są wyborcy partii politycznych w
Polsce?*](https://www.cbos.pl/SPISKOM.POL/2023/K_098_23.PDF), zagregowane dane z czerwca
i lipca 2023, N=1604. W ankiecie respondenci deklarują dochód per capita w gospodarstwie
w przedziałach, więc każdemu przedziałowi przypisałem środek (górny, otwarty przedział
„4000 zł i więcej" domknąłem arbitralnie na 4500 zł, to jedyne miejsce w całej metodzie,
gdzie musiałem coś założyć zamiast policzyć).

| Partia | Dochód (zł/mies., szacowany) |
|---|---|
| PiS | 2593,8 |
| KO | 3178,1 |
| Trzecia Droga | 3226,2 |
| Nowa Lewica | 3232,9 |
| Konfederacja | 3344,2 |
| Ogółem (dla partii spoza tej piątki) | 2898,6 |

### Krok 2: udział głosów per obwód

Dla każdego obwodu głosowania (wyniki Sejm 2023, dane KBW) liczę udział procentowy każdej
partii i mnożę przez jej dochód z tabeli wyżej. Suma tych iloczynów to `income_index_pln`
dla obwodu. Przykład z obwodu nr 1 w Łodzi, 1124 głosy ważne: KO 602 głosy (53,6% × 3178,1
zł) plus Trzecia Droga 170 (15,1% × 3226,2 zł) plus PiS 132 (11,7% × 2593,8 zł) plus Lewica
122 (10,9% × 3232,9 zł) plus Konfederacja 67 (6,0% × 3344,2 zł) plus reszta drobnych
komitetów po średniej ogólnej. Wychodzi 3124,9 zł. Przeliczyłem to ręcznie i zgadza się ze
skryptem co do dziesiątej części złotówki.

### Krok 3: z obwodu głosowania do obwodu spisowego

Obwody spisowe GUS są dużo drobniejsze niż obwody głosowania: dla Łodzi to 3854 obwodów
spisowych na 283 obwody głosowania. Każdy obwód spisowy dostaje dokładnie taki
`income_index_pln`, jaki ma obwód głosowania, w którym leży jego centroid. To oznacza brak
zróżnicowania dochodu wewnątrz jednego obwodu głosowania, ale to nie jest błąd
implementacji: głosuje się per obwód głosowania, nie per budynek, więc dokładniejszej
informacji po prostu nie ma skąd wziąć.

### Krok 4: ludność jako mianownik

Populacja obwodu spisowego to kolumna „Ogółem" z arkusza GUS NSP2021 (nie domyślna kolumna
„20-29 lat", z której korzysta jeden z algorytmów w easy-OTP przy zupełnie innym zadaniu:
łatwo je pomylić, jeśli nie sprawdzi się nazwy kolumny).

## Co poszło nie tak po drodze (i jak to wykryto)

Dwie pomyłki, obie realne, obie wykryte przez porównanie z niezależnym źródłem, nie przez
„wygląda dobrze":

Pierwsza próba dla Łodzi wzięła zły kod TERYT gminy: to była geometria Piotrkowa
Trybunalskiego, nie Łodzi. Wyszło na jaw, bo suma ludności wyniosła 68 978, a Łódź ma
prawie 670 tysięcy mieszkańców. Od tej pory każde miasto weryfikuję sumą populacji
z arkusza GUS, zanim zaufam geometrii.

Druga: przy łączeniu warstw w QGIS (`native:joinattributestable`) kolejność pól w liście
`FIELDS_TO_COPY` nie odpowiadała kolejności w warstwie źródłowej, więc `income_index_pln`
i liczba głosów ważnych zamieniły się miejscami w części rekordów. Wykryte przez ręczne
sprawdzenie jednego rekordu względem CSV źródłowego. Od tego czasu robię to sprawdzenie po
każdym takim złączeniu.

Do tego kilka mniejszych rzeczy: pole `all_votes` w danych `wybory.it` nie jest sumą głosów
na listy partyjne (różnica kilkanaście głosów na obwód, inna definicja PKW), więc właściwym
mianownikiem jest pole `total`. `native:downloadvectortiles` w QGIS crashował aplikację przy
pobieraniu kafli wyborczych, zastąpiony własnym skryptem po HTTP. Po naprawie tych dwóch
błędów: **0 rozbieżności głosów na 805 obwodach w Warszawie, 202 w Gdańsku, 258 w Poznaniu
i 207 w Szczecinie** względem oficjalnego CSV PKW. Dla Łodzi i Krakowa mam własną geometrię
miejską (ArcGIS), dla pozostałych czterech miast geometrię obwodów wziąłem z serwisu
[wybory.it](https://wybory.it) (kafle wektorowe, [kod źródłowy na GitHubie](https://github.com/michalpazur/obwody-wyborcze)).

Wynik końcowy zgadza się z oficjalną populacją GUS dokładnie w 5 z 6 miast, 99,9%
w Łodzi (3854 obwody spisowe, suma ludności 669 995 wobec oficjalnych 670 642).

## Dochód to nie jedyny wymiar. Doszła struktura rodzin

`income_index_pln` to jedna liczba, a rodzina, w której ktoś mieszka, mówi o sytuacji
życiowej co najmniej tyle samo. GUS NSP2021 publikuje na poziomie obwodu spisowego (nie
estymowane, tylko zmierzone wprost spisem) typ rodziny, skład gospodarstwa domowego,
liczbę dzieci i wielkość gospodarstwa. Doszły więc pola takie jak `fam_pct_matki_samotne`,
`hh_avg_size` czy `fam_avg_children`, dla wszystkich 6 miast.

Część obwodów ma tu wartość `NULL`: to nie błąd, tylko anonimizacja małych prób przez GUS
(obwody z brakującą wartością mają średnio ok. 28 mieszkańców, maksymalnie 133, czyli
realnie za mało rodzin, żeby publikować rozkład bez ryzyka identyfikacji osoby). Dotyczy to
1 do 6 procent obwodów, zależnie od miasta.

## Co z tego wynika: pięć hipotez, jedna się potwierdziła

Z korelacją Pearsona, per miasto, sprawdziłem pięć prostych hipotez o związku dochodu,
głosowania i struktury rodzinnej:

| Hipoteza | Wynik |
|---|---|
| Niższy dochód → więcej samotnych matek | **Potwierdzona, spójnie we wszystkich 6 miastach** (od −0,11 w Łodzi do −0,34 w Gdańsku) |
| Wyższy dochód → mniejsze gospodarstwa domowe | Nie, znak niespójny między miastami |
| Wyższy dochód → mniej dzieci w rodzinie | Nie, korelacja bliska zeru |
| Więcej głosów na PiS → więcej dzieci | Nie, w Warszawie (największa próba) wręcz odwrotnie |
| Wyższy dochód → więcej gospodarstw jednoosobowych | Częściowo, niespójnie (silna w Krakowie, zerowa gdzie indziej) |

Tylko pierwsza hipoteza potwierdza się powtarzalnie, we wszystkich miastach naraz. Reszta to
szum albo coś specyficznego dla jednego miasta, nie ogólna prawidłowość.

Sprawdziłem też, czy te zmienne są sklastrowane przestrzennie (globalny wskaźnik I Morana,
sąsiedztwo k-NN, k=8, test permutacyjny 299 permutacji). Wszystkie są, istotnie, we
wszystkich miastach, ale z bardzo różną siłą: `income_index_pln` i udział głosów na PiS
mają I Morana 0,71–0,84, czyli bardzo silne skupienie przestrzenne, podczas gdy struktura
rodzinna (np. `fam_pct_matki_samotne`) ma tylko 0,19–0,32. To akurat nie zaskakuje: dochód
jest z konstrukcji jednolity w obrębie całego obwodu głosowania, więc zmienia się tylko na
jego granicach, a struktura rodzinna zmienia się drobniej, na poziomie obwodu spisowego.
Praktyczna konsekwencja: porównywanie dochodu z czymkolwiek zmierzonym w drobniejszej
skali przestrzennej tłumi siłę korelacji, po prostu dlatego że jedna zmienna jest dużo
„gładsza" niż druga. Do tego wracam w kolejnym wpisie, bo to się potwierdziło jeszcze raz,
w zupełnie innym kontekście.

## Ograniczenia, których nie chcę chować w przypisie

To estymacja obszarowa, nie zmierzony dochód. Zakłada, że relacja partia-dochód z ankiety
CBOS (ogólnopolskiej) jest zbliżona do tej w każdym z sześciu miast osobno. Górny przedział
dochodowy domyka arbitralna liczba (4500 zł). Rozdzielczość efektywna to obwód głosowania,
nie obwód spisowy, mimo że dane są przypisane do tego drugiego. Próby CBOS dla mniejszych
partii (Lewica, Trzecia Droga) są rzędu 80 osób, więc mniej pewne niż dla PiS czy KO
(450–500 osób). I jest ryzyko błędu ekologicznego: wniosek „w tym obwodzie mieszkają ludzie
o dochodzie X" to średnia obszarowa, nie cecha każdego mieszkańca z osobna.

## Dane i kod

Sześć plików GPKG (jeden per miasto, warstwy `obwody_spisowe` i `obwody_glosowania`) razem
ze skryptami są w repozytorium
[easy-R5](https://github.com/GISBoost/easy-R5), folder `tools/ses_income_lodz/`. Pełna
metodologia z każdym wzorem i pełną listą źródeł jest tam w `METHODOLOGY.md`, krok po kroku
pipeline'u w `HANDOFF.md`.

W następnym wpisie tę warstwę dochodową łączę z pomiarem dostępności czasowej transportu
publicznego w Łodzi, na danych o tym, co faktycznie jeździło konkretnego dnia, nie co
obiecuje rozkład. Wynik jest inny, niż się spodziewałem.
