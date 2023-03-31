# diary
- data-warehouse: 
  - datum monatsweise 2h -> 1,5h
  - seed erstellen 2h -> 45'
  - pull request 2h 
- pba-parser: review 2h

# TODO
- [ ]Markus: whi-db
  - [ ]`DbConnection->entryFromSql()` auch als `queryBuilder` Variante? 
  - [ ]query builder: `DbConnector` in constructor -> damit `quote()` von argumenten möglich
  - [ ]`InsertQuery`: `ON DUPLICATE KEY UPDATE` funktion
- [ ]whi-router: patientenbriefe.de
- [ ]triaphon

# IT-1083
- [X]create route: data-warehouse
- [X]create template view
- [X]DataWarehouseController: file upload
- [X]display success message
- [X]reroute to main route
- [X]parse .csv to array
- [X]transform csv structure to DB structure
  - [X]create mapping definition `[db_name => [colname, regex]]`
- [X]setup migrations
- [X]create test DB migration
- [X]extract metadata
- [X]DI
- [X]convert array to db insert 
  - [X]check datasource
  - [X]break if datasource already there
  - [X]else insert new datasource
  - [X]insert data
- [X]bug: different spelled versions of codes in .csv-file
  - sum count of same codes 
  - [X]don't build `SourceData` and `HealthCodeRequestIcd` Objects in `NgpCsvReaderService`
  - [X]merge duplicates
  - [X]refactor: upload objects
    - [X]`HealthCodeRequestIcd`: strings to lower
    - [X]NgpReaderService: Create Request objects
    - [X]`HealthCodeRequestService->updateDb()`: 
      1. remove duplicates
      2. Rest
- [X]UI: Auswahl von codeYear, codeSystem, start-enddate
  - [X]select: data_source == NGP
  - [X]select icd/ops upload
  - [X]input codeYear
  - [X]store all form values as metadata
  - [X]select reader from source
  - [X]use catalog year input
  - [X]new start/end date column in table
  - [X]dont enforce new data_source every time
  - [X]use form start/end date in reader/db insert
  - [X]select db writer from code System
  - [X]generate hash value of `data_source`
  - [X]new ngp ops reader (Bezeichnung mit /)
  - [X]new `health_code_requests_ops` migration
  - [X]format form look
- [X]refactor:
  - [X]`DataWarehouseController` make most constants private
  - [X]`data_warehouse.php` View: use `DataWarehouseController` constants instead of parameters
  - [X]`DataWarehouseController` new function `showForm()` for default action
  - [X]new abstract class `HealthCodeRequests`: member `getDataKeys()`
  - [X]introduce: 'ICD' and 'OPS' constants
  - [X]determine Report Type via match
  - [X]create `Util/CsvReader` from `ReaderCsvNgpService`
    - Report constructor takes array and builds Requests on his own
- [X]data upload just inserts and does not update any counters
  - collisions of requests are overwritten
- [X]upload current NGP Data
  - [X]shellscript for .csv conversion
  - [X]implement: ignore not readable rows
- [X]many non ICD, OPS codes in the tables (e.g. 46874, de, /icd-code-sucheI71-9, Gesamt / Mittel)
- [X]neuer menupunkt bei login namen
- [X]`data_source` table: unique name
  - [X]random hash
- [X]how to detect collisions for health_code_requests in timespan
  - monthwise
  - no easy solution for overlapping timespan
- [X]seed from current quarter ngp data
  - [X]manual upload
- [ ]Datenupload NGP ready: new branch: DataWarehouse for pull-request
  - [X]new Epic
  - [X]beautify
  - [X]code inspections
  - [ ]new Branch: datawarehouse
  - [ ]create pull request

- refactor:
  - [X]german error messages
  - [X]use `static::ALLOWED_FILETYPES` in template
  - [X]db Services -> Service/Db
  - [X]new class for insert row (also: tablename, column names)
  - [X]`const` for all instances of table column names
  - [X]`SourceData` -> `RequestSourceData`
  - [X]`HealthCodeReportIcd` abgeleitet `abstract HealthCodeReport`
  - [X]`HealthCodeRequestsIcd` abgeleitet `abstract HealthCodeRequests`
  - [X]neuer Name: `ReportData` (vs `DataSource`)

## topics

# IT-1110
- HELIOS Fallbezogene Daten:
  - insomnia REST recherchieren

# SQL
- `TRUNCATE TABLE table_name`: deletes the content of a table

# php
- `strtotime($time, 'Y-m-d')`: generates a Unix timestamp
- `(string|int)[]`: array in phpdoc