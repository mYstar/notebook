# diary
- orga:
  - dayplan 1h OK
  - Urlaub beantragen
  - review 1h -> 30'
  - planning 1h -> 45'
- review: Feature/IT-1096 uberschriften 1h -> 30'
- finalize bugfix IT-1119 0.5h -> 1h
- correct pull request: Feature/IT-1083 data warehouse datei upload ngp 2h OK
  - stricter array declarations, code quality
  - new whi-db features
- plan REST interface 0.5h OK
- bugfix: Anmelden auf Mailingliste ohne valide E-Mail -- 30' OK
  - [X]fix & commit
  - [X]deploy (from: origin/feature/IT-591-bilder-im-versionsvergleich-ubersichtlicher-machen)
- buffer: babel 1.0h  OK
- Männertag buy ticket (Breungeshain Waldsiedlung, Schotten) OK

# TODO
- [X]freier Tag verschoben: 17.05. -> 19.05.
- [X]Urlaub: von 10.07. -> 04.08. beantragen
- [X]?Markus: Should DataSource Hash be used like a password for the API? (Should be secure, when transmitted over HTTPS)
- [X]neue whi-db features in ngp-upload nutzen
- [X]?Markus: Was soll ich mit der Fehlermeldung machen?
- [X]in monit Mailliste eintragen lassen
- [ ]registry zugriff für docker
- [X]Bugfix: wrong new codes number (change on automatic is counted)
  - [X]new Branch
  - [X]filter automatic codes later
  - [X]distinct ICD and OPS for bargraph
  - [X]remove time estimate
  - [X]test on live db
  - [X]Kommentar: nicht ganz exakte Zahl
  - [X]pull request
- [ ]whi-router: patientenbriefe.de
- [ ]triaphon
- [ ]tethering by telephone test

# IT-1110
- HELIOS Fallbezogene Daten:
  - insomnia REST recherchieren
- neue Action im Main Controller `$isDataWarehouseApiCall`
- [ ]config: test system
  - [ ]acceptance: upload test file
  - [ ]unit: TDD from now on
- [ ] Hash als Secret verwenden
  - [ ] einfach als https verschlüsseltes passwort name: hash->secret
  - [ ] im confluence dokumentieren
- [ ] new data-source seed for helios
  - [ ] remove autocreate datasources
- [ ] new migration: 
  - [ ] rollback everything and reverse engineer data_warehouse.sql
  - [ ] create HealthCase classes with column names
  - [ ] health_case
  - [ ] health_case_code_icd
  - [ ] health_case_code_ops
- [ ] create new api route (PUT)
- [ ] verify request 
  - [ ]verify hash secret
  - [ ]verify data keys and values
- [ ]build: HealthCase object
- [ ]build: insert statements (Service)
- [ ]integration test: send a request, check response, test DB

# composer
- update git tag and version number in composer.json

# planning
- Vorbereitung: Backlog Pflege (Schätzungen anpassen)