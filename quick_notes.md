# diary
- orga: 
  - dayplan 30' -> 40'
  - meeting 1h -> 45'
- training:
  - delete comment from https://washabich.de/intern/uebersetzung/65710 30'
- datawarehouse REST:
  - test setup 1h -> 1,5h
  - store secrets in db only (move random generation + db insert to script, document, +helios) 2h -> 2,5h
  - new migrations 1,5h OK
  

# TODO
- [X]?Markus: error befunddolmetscher-fastboot? -> Sebastian
- [ ]parser: NGP tests zeigen lassen
- [ ]registry zugriff für docker
- [ ]whi-router: patientenbriefe.de
- [ ]triaphon
- [ ]tethering by telephone test
- [ ]?What ist Zend?
- [ ]?What is Opcache?
- [ ]ES features

# IT-1110
- HELIOS Fallbezogene Daten:
  - insomnia REST recherchieren
- neue Action im Main Controller `$isDataWarehouseApiCall`
- [X]config: test system
  - !stash[ ]acceptance: upload test file
  - unit: TDD from now on
- [X]Hash als Secret verwenden
  - einfach als https verschlüsseltes passwort name: hash->secret
  - [X]im confluence dokumentieren
- [X]new data-source secret for helios
  - [X] remove autocreate datasources
- [ ] new migration: 
  - [X] rollback everything and reverse engineer data_warehouse.sql
  - [X] create HealthCase classes with column names
  - [X] health_case
  - [ ] health_case_code_icd
  - [X] health_case_code_ops
- [ ] create new api route (PUT)
- [ ] verify request 
  - [ ]verify hash secret
  - [ ]verify data keys and values
- [ ]build: HealthCase object
- [ ]build: insert statements (Service)
- [ ]integration test: send a request, check response, test DB

# Aufgaben ab Mai
- woechentlicher Austausch mit Timo und Ansgar zu Timos Themen (Montag)
- meine Rolle: 
  - kleine Anfragen sichten -> alles > 2 min. Ticket anlegen
  - Backlog pflegen 
    - langfristige Sachen -> im naechsten Planning
    - akutes/wichtiges: Absprache mit Ansgar
    - vor Planning: eigenen Plan aus Backlog erarbeiten
  - vor allem Jira nutzen
  - !kein 1st Level Support/Operations
- Ansgars Rolle -> leitet an Sebastian weiter
  - Sebastian -> Operations
- Pressespiegel macht Bea
