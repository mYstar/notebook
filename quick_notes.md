# diary
- pba statistic pull request review
- pba parser development update 45'
- pba datawarehouse development 4,5h
  - new config scheme (DI takes Config class for DbService class)
  - new db service
  - update phinx autoloader
  - DataSourceService implementation
- washabich liste 1h 
  - patientenbrief studie I
  - verstehen ist gesund
  - patientenbriefe.de

# TODO
- [ ] Markus: whi-db
  - [ ] `DbConnection->entryFromSql()` auch als `queryBuilder` Variante? 

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
  - [X] check datasource
  - [X] break if datasource already there
  - [X] else insert new datasource
  - [ ] insert data
  - [ ] refactor: new class for insert row (also: tablename, column names)

## topics
- [ ] preview before upload?
- [ ] how to calculate hash value of `data_source`
  - now: sha256 of filename
  - strip whitespace? extract dates from name?
- code organisation: `inc/class/DataWarehouse/Controller`?

## nicht Implementierte Features
- [ ] limit access to admin?
- [ ] progress bar bei upload https://www.php.net/manual/de/session.upload-progress.php
- [ ] Upload mehrerer Dateien gleichzeitig
- [ ] ignoriere Kommentare in der csv (nonstandard)

# php
