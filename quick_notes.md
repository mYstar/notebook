# 876
- OK tabs weg: Warteliste, Piwik, Team, Aufträge
    - routes müssen nicht angepasst werden
    - .js deteien gelöscht
    - StatController: funktionen entfernt, aus perform() entfernt
- OK nicht mehr alles ausgewählt
    - StatController.auswertungShowSelectionForm(): selected="selected" entfernt
- ! optik anpassen
    - css classes: `box-tabs__header box-tabs__header--big box-tabs__header--active` + `box-tabs__tab`
    - nochmal neu, jeden Tab einzeln laden
- OK Header korrigieren
- ! remove: StatController L: 672 `return $content;`
- ! back button für Auswertungen (Graph und Tabelle)
- !? potentieller bug: `View->__set()` nutzt kein: `str_replace('-', '', $name)`
- ? js-legacy-chart -> TeamStatisticService.php bleibt?
- ? switch statement in view: *mailings-list.php* nötig?

- route: /intern/stat

- StatController->StatisticService: holt alle Daten aus der DB
    - wird an js übergeben `class="js-stat-auswertungen-chart"`
    - per: `data-series="' . htmlspecialchars(json_encode($data))`
    - -> `$data` wird nicht in einem parsebaren Format gespeichert (datasets sind strings)  
- stat-auswertungen-chart.js:
    - instanziiert `ein Highcharts.chart()` übergibt die Attribute aus dem `<div>`
    - ??? passen die Imports?
    - ??? 7: Regex richtig? `\ n`

# whi: Box Tabs (kompletter Content geladen)
- class: `BoxTabs`
1. `$boxTabs = BoxTabs::create()`
2. `->addTab(BoxTab::create(id, title, html));`
3. `$boxTabs->createHtml(activeTabId)`

# whi: Box Tabs (reload on click)
- see: `TeamInternController->createBenutzerPage()`

# php
- output buffering: 
    1. `ob_start()`: starts buffering, all output is redirected to buffer 
    2. `ob_get_clean()` =
        a. `ob_get_contents()`: returns buffer content
        b. `ob_end_clean()`: discard buffer, end output buffering
- alternative Syntax: Templating
```
<?=$value>
<? foreach(...): >
<? endforeach; >
```
- `str_pad()`: pads string to a given length
- `extract(array)`: creates a variable for every element in the array 