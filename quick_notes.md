# diary
- meetings
  - 10:00 review: statistics, ngp upload 30' ok
  - 13:00 planning: ngp upload ready, rest interface 1h ok
- ngp upload:
  - resolve duplication 2h ok
  - refactoring 2h -> 4h

# TODO
- [ ] Markus: whi-db
  - [ ] `DbConnection->entryFromSql()` auch als `queryBuilder` Variante? 
  - [ ] query builder: `DbConnector` in constructor -> damit `quote()` von argumenten möglich
- [ ] code formatter `{` on same line as return type for multiline arguments
- [ ] whi-router: patientenbriefe.de
- [ ] triaphon
- [ ] seatable.washabich.de, login?

# IT-1083
- [X] create route: data-warehouse
- [X] create template view
- [X] DataWarehouseController: file upload
- [X] display success message
- [X] reroute to main route
- [X] parse .csv to array
- [X] transform csv structure to DB structure
  - [X] create mapping definition `[db_name => [colname, regex]]`
- [X] setup migrations
- [X] create test DB migration
- [X] extract metadata
- [X] DI
- [X] convert array to db insert 
  - [X] check datasource
  - [X] break if datasource already there
  - [X] else insert new datasource
  - [X] insert data
- [X] bug: different spelled versions of codes in .csv-file
  - sum count of same codes 
  - [X] don't build `SourceData` and `HealthCodeRequestIcd` Objects in `NgpCsvReaderService`
  - [X] merge duplicates
  - [X] refactor: upload objects
    - [X] `HealthCodeRequestIcd`: strings to lower
    - [X] NgpReaderService: Create Request objects
    - [X] `HealthCodeRequestService->updateDb()`: 
      1. remove duplicates
      2. Rest
- [ ] UI: Auswahl von codeYear, codeSystem, start-enddate
  - [ ] data_source == NGP
  - [ ] random generate hash value of `data_source`
  - [ ] select icd/ops upload
- [ ] DB: time reference for values? --> new column start, end
- [ ] data upload just inserts and does not update any counters
  - collisions of requests are overwritten
- [ ] seed from current ngp data
- [ ] Datenupload NGP ready: new branch: DataWarehouse for pull-request
  - [X] new Epic
  - [ ] beautify
  - [ ] code inspections
  - [ ] new Branch: datawarehouse
  - [ ] create pull request

- refactor:
  - [X] german error messages
  - [X] use `static::ALLOWED_FILETYPES` in template
  - [X] db Services -> Service/Db
  - [X] new class for insert row (also: tablename, column names)
  - [X] `const` for all instances of table column names
  - [X] `SourceData` -> `RequestSourceData`
  - [X] `HealthCodeReportIcd` abgeleitet `abstract HealthCodeReport`
  - [X] `HealthCodeRequestsIcd` abgeleitet `abstract HealthCodeRequests`
  - [X] neuer Name: `ReportData` (vs `DataSource`)

## topics
- [ ] limit access to admin?
- [ ] Upload multiple files

# IT-1110
- HELIOS Fallbezogene Daten:
  - insomnia REST recherchieren