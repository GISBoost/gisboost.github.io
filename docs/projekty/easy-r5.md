---
description: "Easy-R5 — wtyczka processingowa QGIS licząca dostępność transportową na silniku Conveyal R5: macierze czasów przejazdu i dostępność skumulowana w oknie odjazdów."
---

# Easy-R5

Easy-R5 to wtyczka processingowa do QGIS, która liczy dostępność transportową na silniku
**Conveyal R5**. Jest siostrą [easy-OTP](easy-otp.md): ten sam użytkownik, ten sam styl
pracy, inny silnik. R5 jest szybki tam, gdzie OpenTripPlanner 1.5 jest wolny — liczy
macierze czasów przejazdu i dostępność skumulowaną **jeden-do-wielu i wiele-do-wielu w oknie
odjazdów**, w tempie liczonym w minutach zamiast godzin.

Wersja rozwojowa (`experimental`), jeszcze nie w oficjalnym repozytorium wtyczek QGIS.
Licencja GPL-3.0-or-later, wymaga QGIS 3.22 LTR lub nowszego.

## Co robi

Algorytmy w Processing Toolbox:

- macierz czasów przejazdu N × M nad oknem odjazdu, z percentylami
- dostępność skumulowana — ile miejsc, usług albo mieszkańców jest w zasięgu z każdego punktu
- izochrony — poligony zasięgu czasowego z jednego punktu
- filtr podtrybów transportu (`TRAM`, `BUS`, …) do kontrfaktycznego wyłączania trybów
- warstwy demograficzne z danych GUS NSP 2021

Wtyczka sama pobiera Javę 21 (Temurin) i silnik R5 (`r5-v7.6-all.jar`) przy pierwszej
konfiguracji — bez R, bez Dockera, bez uprawnień administratora.

## Jak to działa

R5 nie ma trybu serwerowego ani narzędzia wiersza poleceń do macierzy. Easy-R5 uruchamia
silnik jako **proces potomny** przez jeden mały plik Javy — a nie przez biblioteki r5r
(wymaga R) czy r5py (16 pakietów pip). Dlaczego tak i czym to się różni od tamtych:

[Jak QGIS rozmawia z R5 &rarr;](https://gisboost.github.io/easy-R5/)

## Zrealizowane rozkłady jazdy

Do analiz „co się dzieje w gorszy dzień" Easy-R5 potrafi pobrać zrealizowany rozkład
(P50 / P85) z [GTFS Dashboard](gtfs-dashboard.md) — to jedyny sposób, w jaki dane czasu
rzeczywistego wchodzą do R5, bo sam silnik nie czyta GTFS-RT.

## Linki

- Repozytorium: [github.com/GISBoost/easy-R5](https://github.com/GISBoost/easy-R5)
- Jak QGIS rozmawia z R5: [gisboost.github.io/easy-R5](https://gisboost.github.io/easy-R5/)
