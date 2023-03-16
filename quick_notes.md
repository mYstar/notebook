- neu: Releasenotes im Slack
- commits möglichst trennen

# TODO
- [X] install phpstorm
- [ ] https://phpstan.org for own use

# IT-821
- route: baustein --> search (SearchController)
- BausteinController --> /Controller/
- Header Suche sucht nach Codes
- soll auch nach Name suchen
- trim whitespace
- Prio ist code

# php
- `array_key_first()`, `array_key_last()`: determine start/end of `foreach` loop

# shell
- `ln -s full_path_name link_full_path`

# Planning
- Kommunikationsausbildung
- PBA Parser optimieren (weniger Durchläufe)
    - mehrere Stellen die Infos aus Text extrahieren (Fehlermeldungen, *Codes, ...)
    - Performance nur in großen OPS Bausteinen problematisch
    - wartende Features: Mengen, Zeilenangabe, Merge bei Seitigkeit nicht relevant
    - testing: es gibt eine Benutzeroberfläche für den Vergleich
    - ich im code Review

- PBA Data Warehouse
    - Besprechung: Datenstrukturen
    - verschiedene Clients nutzen eine DB
    - fallbezogen oder auch nicht
    - aus erzeugten Patientenbriefen kommen Daten
    - legacy bisher gespeicherte Daten
    - Falldaten: Zeiten monatsgranular + Dauer des Aufenthalts in Tagen
    - Kreuz Stern Ausrufezeichen?
    - Felder können auch immer NULL sein (wenn datenquelle diese nicht bereitstellt)
    - später Berichte aus anderen DB mit integrieren
      - https://qb-referenzdatenbank.g-ba.de/#/login
        rebekka.post@washabich.de
        Zdq#K48N7@

# css
- `content:url("image.jpg")`: change image