# diary
- orga, planning 1h OK
- pull requests:
  - rework: whi-db 0,5h OK (merge + tag OK)
  - review: pba-parser ueberschriften 2h OK
  - rework: ngp-upload 1,5h 
- bugfix: wrong new codes 2h -> 1,5h

# TODO
- [ ]tethering by telephone test
- [ ]neue whi-db features in ngp-upload nutzen
- [ ]?Markus: Was soll ich mit der Fehlermeldung machen?
- [ ] in errorhandler Mailliste eintragen lassen
- [ ]Bugfix: wrong new codes number (change on automatic is counted)
  - [X]new Branch
  - [X]filter automatic codes later
  - [X]distinct ICD and OPS for bargraph
  - [X]remove time estimate
  - [X]test on live db
  - [ ]Kommentar: nicht ganz exakte Zahl
  - +feature: dual prognose ICD OPS ready
- [ ]?Markus: Should DataSource Hash be used like a password for the API? (Should be secure, when transmitted over HTTPS)
- [ ]whi-router: patientenbriefe.de
- [ ]triaphon

# IT-1110
- HELIOS Fallbezogene Daten:
  - insomnia REST recherchieren
- neue Action im Main Controller `$isDataWarehouseApiCall`
- Hash als Secret verwenden
- [X]whi-db
  - [X]`DbConnection->entryFromSql()` auch als `queryBuilder` Variante? 
  - [X]install testing Library
  - xxx query builder: `DbConnector` in constructor -> damit `quote()` von argumenten möglich
    - aufpassen, dass man angeben kann, was gequotet werden soll
  - [X]`InsertQuery`: `ON DUPLICATE KEY UPDATE` funktion
  - [X]pull request
  - [X]new tag for merged pull request

