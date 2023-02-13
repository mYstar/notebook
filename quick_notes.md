# 876
- OK tabs weg: Warteliste, Piwik, Team, Aufträge
    - routes müssen nicht angepasst werden
    - .js deteien gelöscht
    - StatController: funktionen entfernt, aus perform() entfernt
- OK nicht mehr alles ausgewählt
    - StatController.auswertungShowSelectionForm(): selected="selected" entfernt
- ! optik anpassen
- ? js-legacy-chart -> TeamStatisticService.php bleibt?

- route: /intern/stat

- StatController->StatisticService: holt alle Daten aus der DB
    - wird an js übergeben `class="js-stat-auswertungen-chart"`
    - per: `data-series="' . htmlspecialchars(json_encode($data))`
    - -> `$data` wird nicht in einem parsebaren Format gespeichert (datasets sind strings)  
- stat-auswertungen-chart.js:
    - instanziiert `ein Highcharts.chart()` übergibt die Attribute aus dem `<div>`
    - ??? passen die Imports?
    - ??? 7: Regex richtig? `\ n`