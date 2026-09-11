---
title: GISBoost — narzędzia GIS do analizy transportu publicznego
description: Otwarte narzędzia GIS do analizy transportu publicznego (easy-OTP, easy-GTFS-RT, GTFS Dashboard, Mapy analiz) i materiały edukacyjne o QGIS oraz danych przestrzennych.
---

# GISBoost — GIS, QGIS i dane transportu publicznego

<head>
<meta name="google-site-verification" content="ih1W248cEBofov9EY3iEEdE6AS_Sftsy7er6eC52uxY" />
<meta property="og:type" content="website">
<meta property="og:site_name" content="GISBoost">
<meta property="og:title" content="GISBoost — GIS, QGIS i dane transportu publicznego">
<meta property="og:description" content="Otwarte narzędzia GIS do analizy transportu publicznego: od codziennego nagrywania GTFS-RT, przez rekonstrukcję rozkładu, po analizę dostępności w QGIS i gotowe mapy.">
<meta property="og:url" content="https://gisboost.github.io/">
<meta property="og:image" content="https://gisboost.github.io/assets/icon_gisboost.png">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="GISBoost — GIS, QGIS i dane transportu publicznego">
<meta name="twitter:description" content="Otwarte narzędzia GIS do analizy transportu publicznego: od codziennego nagrywania GTFS-RT, przez rekonstrukcję rozkładu, po analizę dostępności w QGIS i gotowe mapy.">
<meta name="twitter:image" content="https://gisboost.github.io/assets/icon_gisboost.png">
</head>

GISBoost to mój projekt: otwarte narzędzia GIS do analizy transportu publicznego i materiały
edukacyjne o QGIS. Zajmuję się tym, bo rozkład jazdy nie mówi prawdy o tym, jak transport
faktycznie kursuje, a dane, które to pokazują, są w większości miast publiczne i darmowe.
Trzeba tylko mieć narzędzia, żeby je przetworzyć.

## Jak to działa

<div class="cards" markdown="1">

<div class="card" markdown="1">
<p class="eyebrow">1 · Zbieranie</p>
### easy-GTFS-RT

Codzienne nagrywanie danych GTFS-RT, 27 miast, 9 krajów, od lipca 2026.

[Zobacz →](projekty/easy-gtfs-rt.md)
</div>

<div class="card" markdown="1">
<p class="eyebrow">2 · Rekonstrukcja</p>
### Family A / Family B

Z pozycji pojazdów powstaje zrealizowany rozkład jazdy (P50 / P85).

[Zobacz →](projekty/easy-otp.md)
</div>

<div class="card" markdown="1">
<p class="eyebrow">3 · Publikacja</p>
### GTFS Dashboard

Katalog nagrań, wykresy odchyleń od rozkładu, pliki do pobrania.

[Zobacz dashboard →](https://gisboost.github.io/gtfs-dashboard/)
</div>

<div class="card" markdown="1">
<p class="eyebrow">4 · Analiza</p>
### easy-OTP i Easy-R5

Wtyczki QGIS do analizy dostępności — OpenTripPlanner i Conveyal R5.

[Zobacz →](projekty/easy-r5.md)
</div>

<div class="card" markdown="1">
<p class="eyebrow">5 · Wynik</p>
### Mapy i analizy

Interaktywne mapy, opisy metody i artykuły naukowe.

[Zobacz analizy →](analizy/index.md)
</div>

<div class="card" markdown="1">
<p class="eyebrow">6 · Współpraca</p>
### Usługa na zlecenie

Ten sam łańcuch, uruchomiony dla Twojego obszaru i Twojego pytania.

[Zobacz ofertę →](wspolpraca.md)
</div>

</div>

## Ostatnie analizy

- [Dostępność do uczelni w 6 miastach](analizy/dostepnosc-uczelnie.md) — 61% obszaru
  zamieszkanego przez studentów bez dostępu do uczelni w pół godziny.
- [Dochód na poziomie obwodu spisowego](analizy/dochod-obwody-spisowe.md) — szacowanie
  dochodu tam, gdzie spis go nie mierzy.
- [Dostępność a dochód w Łodzi](analizy/dostepnosc-dochod-lodz.md) — czy bieda oznacza
  gorszy dojazd.

[Wszystkie analizy i mapy →](analizy/index.md)

## Narzędzia

- **[easy-OTP](projekty/easy-otp.md)** — wtyczka QGIS do analizy dostępności czasowej
  transportu publicznego, oparta na OpenTripPlanner. Dostępna w oficjalnym repozytorium
  wtyczek QGIS.
- **[easy-GTFS-RT](projekty/easy-gtfs-rt.md)** — pipeline w chmurze, który nagrywa dane
  GTFS-RT i codziennie rekonstruuje z nich zrealizowany rozkład jazdy.
- **[GTFS Dashboard](projekty/gtfs-dashboard.md)** — przeglądarka tych zrekonstruowanych
  rozkładów: miasto → miesiąc → dzień → szczegóły, z wykresami odchyleń od planu.
  [Zobacz dashboard →](https://gisboost.github.io/gtfs-dashboard/)

W zakładce [Publikacje](OpenTripPlanner.md) znajdziesz materiały o tym, jak samemu
skonfigurować i używać OpenTripPlanner do analiz przestrzennych. Więcej o mnie i moim
zawodowym tle jest na stronie [O mnie](O-mnie.md).

## Artykuł naukowy

Wspólnie z Krzysztofem Ułamkiem opublikowaliśmy artykuł naukowy pod tytułem [Porównanie metod zbierania danych dla mikroskopowej symulacji ruchu w programie VISSIM na przykładzie planowania przestrzennego fragmentu osiedla Złotno w Łodzi](https://doi.org/10.18778/2543-9421.10.01), w czasopiśmie [Konwersatorium Wiedzy o Mieście](https://czasopisma.uni.lodz.pl/konwersatorium/index). Artykuł jest również dostępny na stronie [ResearchGate](https://www.researchgate.net/publication/398536466_Porownanie_metod_zbierania_danych_dla_mikroskopowej_symulacji_ruchu_w_programie_VISSIM_na_przykladzie_planowania_przestrzennego_fragmentu_osiedla_Zlotno_w_Lodzi).

[Kliknij tutaj, aby pobrać lub wyświetlić artykuł w formacie PDF.](./assets/7-23_Kaczorowski_Ulamek.pdf)

<iframe src="assets/7-23_Kaczorowski_Ulamek.pdf" width="100%" height="800" style="border:1px solid #ccc;">
</iframe>
