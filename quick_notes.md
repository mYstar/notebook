# TODO
- [ ] https://phpstan.org for own use
- [ ] https://jira.washabich.de/secure/TimesheetReport.jspa?reportKey=jira-timesheet-plugin[…]stword=&sum=&groupByField=&sortBy=&sortDir=ASC&Weiter=Weiter
- [ ] Markus: `include_once(INC . 'config.php');` in `ConfigService` kann Probleme verursachen
  - wenn `include_once()` schonmal aufgerufen --> kein Effekt
  - variable: `$config` entsteht aus dem Nichts --> `return` wäre klarer

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
- [ ] convert array to db insert 

# topics
- [ ] preview before upload?
- [ ] how to calculate hash value of `data_source`
  - now: sha256 of filename
  - strip whitespace? extract dates from name?
- code organisation: `inc/class/DataWarehouse/Controller`?

# nicht Implementierte Features
- [ ] limit access to admin?
- [ ] progress bar bei upload https://www.php.net/manual/de/session.upload-progress.php
- [ ] Upload mehrerer Dateien gleichzeitig
- [ ] ignoriere Kommentare in der csv (nonstandard)

# Phinx
- migrations
  - mittels sql files (migrations/sql/*) aktuelle struktur
  - und php library
  - `./migration status`
  - `./migration migrate`
  - `./migration rollback`
  - `./migration seed:run`
- seeder füllt Daten ein
- von cake php
- extra composer script in `/database`
- testdaten trotzdem selbst erzeugen --> faker/php
- ! in `create_table()` column `id` will be created automatically
  - `PRIMARY_KEY`, `NOT NULL` and `AUTO_INCREMENT`
- ! key names generated automatically 
  - foreign_key: `<table>_ibfk_<counter>
  - function: `addForeignKeyWithName()`
- ! `mysql` adapter does not use transactions in `CREATE TABLE, ALTER TABLE, and DROP TABLE`
  - mysql and mariadb have an implicit commit https://mariadb.com/kb/en/sql-statements-that-cause-an-implicit-commit/ for certain commands