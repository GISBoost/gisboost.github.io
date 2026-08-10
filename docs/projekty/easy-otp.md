---
description: easy-OTP — wtyczka processingowa QGIS do analizy dostępności czasowej transportu publicznego przy użyciu OpenTripPlanner. Dostępna w oficjalnym repozytorium wtyczek QGIS.
---

# easy-OTP

easy-OTP to wtyczka processingowa do QGIS, która automatyzuje analizę dostępności czasowej
transportu publicznego przy użyciu OpenTripPlanner 1.5.0. Jest dostępna w oficjalnym
repozytorium wtyczek QGIS (Wtyczki → Zarządzaj i instaluj wtyczki, wpisz "easy-OTP" w
wyszukiwarce), interfejs działa po polsku i po angielsku.

Aktualna wersja: **0.7.0**, licencja GPL-3.0-or-later, wymaga QGIS 3.22 LTR lub nowszego.

## Co robi

Głównym algorytmem jest liczenie powierzchni czasu dojazdu dla każdej minuty okna analizy
i klasyfikacja komórek siatki heksagonalnej na cztery kategorie dostępności, zgodnie z
podejściem znanym z literatury naukowej o dostępności czasowej. Do tego dochodzi zestaw
dodatkowych algorytmów w Processing Toolbox:

- generowanie izochron (pojedynczych i w czasie, do animacji w Temporal Controller)
- macierz czasów dojazdu N × M między wieloma punktami
- analiza pokrycia usługowego (ile punktów, np. aptek czy sklepów, jest osiągalnych z każdej komórki)
- planowanie trasy przez wiele punktów pośrednich, z automatycznym ustalaniem kolejności odwiedzin (RouteViaPoints)
- porównanie dwóch scenariuszy dostępności, np. rozkład bazowy kontra proponowany
- dostępność liczona na żywych opóźnieniach z GTFS-RT zamiast planowego rozkładu, z dopasowaniem po route_id/stop_id dla miast bez wspólnego trip_id (np. Poznań, Kraków)

Wtyczka potrafi sama pobrać Javę 8, plik OTP 1.5.0, wyciąg OSM i pliki GTFS dla wybranego
obszaru, więc nie trzeba tego szukać ręcznie.

## Narzędzia terminalowe

W repozytorium, w folderze `tools/`, jest kilka samodzielnych narzędzi, które nie działają
wewnątrz QGIS, tylko z poziomu terminala:

- **[`family_a_reconstruction`](https://github.com/GISBoost/easy-OTP/tree/main/tools/family_a_reconstruction)** rekonstruuje zrealizowany rozkład jazdy (nie planowy, tylko to, co faktycznie
  jechało) na podstawie nagranych pozycji pojazdów z GTFS-RT. Przydaje się dla miast, które
  publikują tylko VehiclePositions, bez TripUpdates.
- **[`transit_charts`](https://github.com/GISBoost/easy-OTP/tree/main/tools/transit_charts)** liczy z tego wykresy punktualności, regularności i prędkości.

## Instalacja OTP

Jeśli chcesz samodzielnie skonfigurować i uruchomić serwer OpenTripPlanner, na którym
pracuje easy-OTP, zobacz [poradnik OTP](../OpenTripPlanner.md).

## Linki

- Repozytorium: [github.com/GISBoost/easy-OTP](https://github.com/GISBoost/easy-OTP)
- Najnowsze wydanie: [github.com/GISBoost/easy-OTP/releases/latest](https://github.com/GISBoost/easy-OTP/releases/latest)

Testy na innych miastach i innych feedach GTFS niż te, na których sam testowałem, są
najbardziej przydatne, bo tam najłatwiej o niespodzianki (inny format danych, inne
osobliwości feedu GTFS-RT). Błędy, propozycje funkcji i pytania możesz zgłaszać jako issue
na GitHubie.
