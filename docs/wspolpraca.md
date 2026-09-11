---
description: Współpraca z GISBoost — analizy dostępności transportu publicznego, weryfikacja gminnych standardów dostępności z planu ogólnego (art. 13f) oraz wdrożenia i szkolenia z wtyczek easy-OTP i Easy-R5 dla biur urbanistycznych, samorządów i zespołów badawczych.
---

# Współpraca

Buduję otwarte narzędzia do analizy dostępności transportu publicznego i używam ich
do liczenia rzeczy, których nie da się odczytać z rozkładu jazdy ani z mapy w linii prostej.
Część tej pracy wykonuję na zlecenie.

## Co robię

**Analiza dostępności transportu publicznego**

: Ile osób, szkół, przychodni albo miejsc pracy jest realnie w zasięgu z danego miejsca —
liczone na sieci ulic i rozkładzie jazdy, z uwzględnieniem pory dnia, czasu oczekiwania
i przesiadek. Nie bufor, nie linia prosta. Wynik jako mapa, warstwa GIS i tabela.

**Weryfikacja gminnych standardów dostępności (art. 13f)**

: Ustawa liczy odległość do szkoły podstawowej i terenów zieleni jako **drogę dojścia
ogólnodostępną trasą dla pieszych od granicy działki** — nie jako promień. To zadanie
sieciowe. Sprawdzam, które działki spełniają przyjęty standard, a które nie, i jak wynik
zmienia się przy innym progu. To samo dla katalogu fakultatywnego: przystanek, apteka,
przedszkole, przychodnia POZ.

**Rozkład planowany kontra zrealizowany**

: Co się dzieje z dostępnością, gdy zamiast rozkładu z rozkładówki podstawimy to, co
pojazdy faktycznie zrobiły danego dnia. Prowadzę codzienne archiwum danych czasu
rzeczywistego dla 27 miast w Polsce i za granicą, więc taki porównawczy przebieg jest
możliwy dla konkretnej daty wstecz.

**Wdrożenie i szkolenie — easy-OTP i Easy-R5**

: Postawienie narzędzi u Ciebie w zespole i przeprowadzenie ludzi przez pierwszą własną
analizę, na Twoich danych i Twoim obszarze. Po szkoleniu robicie to sami — wtyczki są
otwarte i darmowe.

## Dla kogo

- **Biura urbanistyczne i projektowe** — warstwa analityczna do planu ogólnego lub studium,
  jako podwykonawstwo albo jako narzędzie dla Waszego zespołu.
- **Samorządy i organizatorzy transportu** — diagnoza obsługi komunikacyjnej, ocena skutków
  zmiany siatki połączeń, materiał do konsultacji i do wniosków o finansowanie.
- **Zespoły badawcze i uczelnie** — dane, metoda i odtwarzalny przebieg do publikacji.

## Na czym to stoi

Nie proszę o zaufanie na słowo — wszystko poniżej da się sprawdzić.

- **Metoda jest recenzowana.** Pierwszy [artykuł naukowy](artykuly.md) opublikowany w 2025 r.
  w *Konwersatorium Wiedzy o Mieście*; drugi, opisujący metodę *service time* stojącą za
  easy-OTP, jest w druku w *European Spatial Research and Policy*.
- **Wyniki są walidowane wobec narzędzi referencyjnych.** Easy-R5 odtwarza wynik dostępności
  biblioteki `r5r` dla Gdańska **co do wiersza** —
  [zapis porównania](https://github.com/GISBoost/easy-R5/blob/main/docs/notes/validation-gdansk.md).
- **Narzędzia są publiczne.** [easy-OTP](projekty/easy-otp.md) jest w oficjalnym repozytorium
  wtyczek QGIS; [Easy-R5](projekty/easy-r5.md), [easy-GTFS-RT](projekty/easy-gtfs-rt.md)
  i [GTFS Dashboard](projekty/gtfs-dashboard.md) mają otwarty kod i dokumentację.
- **Ograniczenia są opisane, nie schowane.** Każde narzędzie ma listę znanych problemów
  i opis tego, czego metoda **nie** mierzy. Dostajesz to razem z wynikiem, przed wnioskami.
- **Gotowe analizy do obejrzenia:** [dostępność do uczelni w 6 miastach](analizy/dostepnosc-uczelnie.md),
  [dostępność a dochód w Łodzi](analizy/dostepnosc-dochod-lodz.md),
  [dochód na poziomie obwodu spisowego](analizy/dochod-obwody-spisowe.md).

## Czego nie robię

Żeby nie tracić Twojego czasu na rozmowę, która i tak skończy się odmową:

- Nie sporządzam planów miejscowych, planów ogólnych ani operatów — nie mam uprawnień
  urbanistycznych. Robię **warstwę analityczną** do dokumentu, który sporządza ktoś inny.
- Nie utrzymuję systemów produkcyjnych ani nie podpisuję umów SLA. Dostarczam analizę
  i narzędzia, nie usługę ciągłą.
- Pracuję **wyłącznie na danych otwartych** — OpenStreetMap, GTFS i GTFS-RT, GUS, dane
  publiczne gminy. Nie korzystam z komercyjnych danych o ruchu. GISBoost jest projektem
  niezależnym od mojego pracodawcy.
- Nie przyjmuję zleceń, w których wynik jest ustalony z góry. Mogę policzyć, co się stanie
  przy danym progu — nie mogę obiecać, że liczba wyjdzie po właściwej stronie.

## Jak to wygląda

1. **Rozmowa, 30 minut.** Mówisz, co chcesz wiedzieć i dla jakiego obszaru. Ja mówię, czy
   to wykonalne na danych otwartych — i jeśli nie, to dlaczego.
2. **Zakres na piśmie.** Co dokładnie zostanie policzone, na jakich danych, z jakiej daty,
   i czego wynik **nie** będzie znaczył.
3. **Wycena i termin.**
4. **Wykonanie i przekazanie.** Dostajesz raport, warstwy GIS, dane wejściowe i skrypty.
   Wszystko na danych otwartych, więc przebieg da się powtórzyć i sprawdzić — także beze mnie.

Prowadzę GISBoost obok pracy zawodowej i doktoratu, więc przyjmuję **1–2 zlecenia na
kwartał**. Jeśli termin jest napięty, powiem o tym od razu.

## Kontakt

Napisz na **kontakt@example.com** albo przez
[LinkedIn](https://www.linkedin.com/in/michal-kaczorowsky/).

Najprościej zacząć od jednego zdania: **co chcesz policzyć i dla jakiego obszaru**.
Odpowiem, czy da się to zrobić na danych otwartych i jak — nawet jeśli ostatecznie
nie mielibyśmy współpracować.
