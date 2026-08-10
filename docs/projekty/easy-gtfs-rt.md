---
description: easy-GTFS-RT — pipeline w chmurze, który nagrywa dane GTFS-RT i codziennie rekonstruuje z nich zrealizowany rozkład jazdy transportu publicznego.
---

# easy-GTFS-RT

easy-GTFS-RT to pipeline w chmurze, który nagrywa dane GTFS-RT (pozycje pojazdów w czasie
rzeczywistym) i codziennie buduje z nich zrealizowany rozkład jazdy, czyli to, co faktycznie
jechało, a nie to, co było zaplanowane.

Dane z easy-GTFS-RT zasilają narzędzia rekonstrukcyjne z [easy-OTP](easy-otp.md)
([`family_a_reconstruction`](https://github.com/GISBoost/easy-OTP/tree/main/tools/family_a_reconstruction),
[`transit_charts`](https://github.com/GISBoost/easy-OTP/tree/main/tools/transit_charts)) oraz
[GTFS Dashboard](gtfs-dashboard.md), gdzie wyniki są publicznie dostępne do przeglądania i
pobrania.

## Linki

- Repozytorium: [github.com/GISBoost/easy-GTFS-RT](https://github.com/GISBoost/easy-GTFS-RT)
