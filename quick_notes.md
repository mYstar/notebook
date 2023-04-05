# diary
- orga:
  - dayplan 30' OK
  - meetings 2h  OK
- pba-parser: review 2h OK
- REST API casewise
  - planning with template pba 1h
  - new functions whi router 1,5h
- learn: babel 30'
- [X] lernen: Bausteine löschen im Redaktionssystem
  - Anfrage im pba channel


# TODO
- [ ]Bugfix: wrong new codes number (change on automatic is counted)
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
  - [ ]query builder: `DbConnector` in constructor -> damit `quote()` von argumenten möglich
    - aufpassen, dass man angeben kann, was gequotet werden soll
  - [ ]`InsertQuery`: `ON DUPLICATE KEY UPDATE` funktion
  - [ ]new tag for merged pull request
