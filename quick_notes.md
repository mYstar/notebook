# diary
- pba datawarehouse:
  - insert data rows into db 2h --> 2h
    - i: `db->quote()` checks for integer
    - check for sql errors
  - repair routing 0,5h -> 1h
  - refactor 1h++ -> 2h
    - i: null can be multiple times in a unique key in mariadb/mysql
  - bugfix: code duplicates -> 3,5h

# TODO
- [ ] Markus: whi-db
  - [ ] `DbConnection->entryFromSql()` auch als `queryBuilder` Variante? 
  - [ ] query builder: `DbConnector` in constructor -> damit `quote()` von argumenten möglich
- [ ] Datenupload NGP ready: new branch: DataWarehouse for pull-request
  - [X] new Epic
  - [ ] new Branch: datawarehouse
  - [ ] create pull request

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
- [ ] bug: different spelled versions of codes in .csv-file
  - sum count of same codes 
  - [X] don't build `SourceData` and `HealthCodeRequestIcd` Objects in `NgpCsvReaderService`

- refactor:
  - [X] german error messages
  - [X] use `static::ALLOWED_FILETYPES` in template
  - [X] db Services -> Service/Db
  - [X] new class for insert row (also: tablename, column names)
  - [ ] `const` for all instances of table column names

## topics
- [ ] preview before upload?
- [ ] how to calculate hash value of `data_source`
  - now: sha256 of filename
- [ ] check pba database for valid codes?
- [ ] check for `HealthCodeRequestIcd` field length beforehand? -> possibly trim 
- [ ] data upload just inserts and does not update any counters
  - because a new data-source is created every time
- [ ] time reference for values? (only `code_year` for now)
  - typically a datawarehouse stores a timestamp for every item

## nicht Implementierte Features
- [ ] limit access to admin?
- [ ] progress bar bei upload https://www.php.net/manual/de/session.upload-progress.php
- [ ] Upload mehrerer Dateien gleichzeitig
- [ ] ignore csv comments (nonstandard)
