---
title: GISBoost — narzędzia GIS do analizy transportu publicznego
description: Otwarte narzędzia GIS do analizy transportu publicznego (easy-OTP, easy-GTFS-RT, GTFS Dashboard) i materiały edukacyjne o QGIS oraz danych przestrzennych.
---

# GISBoost — GIS, QGIS i dane transportu publicznego

<head>
<meta name="google-site-verification" content="ih1W248cEBofov9EY3iEEdE6AS_Sftsy7er6eC52uxY" />
</head>

GISBoost to mój projekt: otwarte narzędzia GIS do analizy transportu publicznego i materiały
edukacyjne o QGIS. Zajmuję się tym, bo rozkład jazdy nie mówi prawdy o tym, jak transport
faktycznie kursuje, a dane, które to pokazują, są w większości miast publiczne i darmowe.
Trzeba tylko mieć narzędzia, żeby je przetworzyć.

## Projekty

- **[easy-OTP](projekty/easy-otp.md)** — wtyczka QGIS do analizy dostępności czasowej
  transportu publicznego, oparta na OpenTripPlanner. Dostępna w oficjalnym repozytorium
  wtyczek QGIS.
- **[easy-GTFS-RT](projekty/easy-gtfs-rt.md)** — pipeline w chmurze, który nagrywa dane
  GTFS-RT i codziennie rekonstruuje z nich zrealizowany rozkład jazdy.
- **[GTFS Dashboard](projekty/gtfs-dashboard.md)** — przeglądarka tych zrekonstruowanych
  rozkładów: miasto → miesiąc → dzień → szczegóły, z wykresami odchyleń od planu.
  [Zobacz dashboard →](https://gisboost.github.io/gtfs-dashboard/)

W zakładce [Poradniki](OpenTripPlanner.md) znajdziesz materiały o tym, jak samemu
skonfigurować i używać OpenTripPlanner do analiz przestrzennych. Więcej o mnie i moim
zawodowym tle jest na stronie [O mnie](O-mnie.md).

## Artykuł naukowy

Wspólnie z Krzysztofem Ułamkiem opublikowaliśmy artykuł naukowy pod tytułem [Porównanie metod zbierania danych dla mikroskopowej symulacji ruchu w programie VISSIM na przykładzie planowania przestrzennego fragmentu osiedla Złotno w Łodzi](https://doi.org/10.18778/2543-9421.10.01), w czasopiśmie [Konwersatorium Wiedzy o Mieście](https://czasopisma.uni.lodz.pl/konwersatorium/index). Artykuł jest również dostępny na stronie [ResearchGate](https://www.researchgate.net/publication/398536466_Porownanie_metod_zbierania_danych_dla_mikroskopowej_symulacji_ruchu_w_programie_VISSIM_na_przykladzie_planowania_przestrzennego_fragmentu_osiedla_Zlotno_w_Lodzi).

[Kliknij tutaj, aby pobrać lub wyświetlić artykuł w formacie PDF.](./assets/7-23_Kaczorowski_Ulamek.pdf)

<iframe src="assets/7-23_Kaczorowski_Ulamek.pdf" width="100%" height="800" style="border:1px solid #ccc;">
</iframe>
