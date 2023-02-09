PBA?

# 876
- route: /intern/stat
- optik anpassen
- ansgar fragen was noch drin bleiben soll

- StatController->StatisticService: holt alle Daten aus der DB
    - wird an js übergeben `class="js-stat-auswertungen-chart"`
    - per: `data-series="' . htmlspecialchars(json_encode($data))`