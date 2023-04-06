# diary
- orga, planning 0,5h OK
- whi-db: new features 2h -> 2,5h
- meeting: how to server 1h -> 1,5h
- pb-redaktion: bugfix statistics + new codetype estimate 2,5h ++

# TODO
- [ ]?Markus: Was soll ich mit der Fehlermeldung machen?
- [ ] in errorhandler Mailliste eintragen lassen
- [ ]Bugfix: wrong new codes number (change on automatic is counted)
  - [X]new Branch
  - [X]filter automatic codes later
  - [X]distinct ICD and OPS for bargraph
  - [ ]distinct estimate for ICD and OPS ready time TODO: calculate avg codecount for every code system
  - [ ]write tests
  - [ ]test on live db
  - +feature: dual prognose ICD OPS ready
- [ ]?Markus: Should DataSource Hash be used like a password for the API? (Should be secure, when transmitted over HTTPS)
- [ ]whi-router: patientenbriefe.de
- [ ]triaphon

# PBA Parser Review
- [X]question: When is `AddToCurrentAndStack` needed when `AddToCurrent`?
  - nodes die keine Kinder haben können müssen nicht auf den Stack
- [X]question: Why is Stack Operation as class needed?
  - manche haben Member Variablen
  - StackOperationService gibt es als Objekt 
- [X]PbaParserLexerTest: Warum werden auf Zeile 183 und 185 leere StringNodes erzeugt?

# IT-1110
- HELIOS Fallbezogene Daten:
  - insomnia REST recherchieren
- neue Action im Main Controller `$isDataWarehouseApiCall`
- Hash als Secret verwenden
- [ ] whi-db
  - [X]`DbConnection->entryFromSql()` auch als `queryBuilder` Variante? 
  - [X]install testing Library
  - xxx query builder: `DbConnector` in constructor -> damit `quote()` von argumenten möglich
    - aufpassen, dass man angeben kann, was gequotet werden soll
  - [X]`InsertQuery`: `ON DUPLICATE KEY UPDATE` funktion
  - [X]pull request
  - [ ]new tag for merged pull request
