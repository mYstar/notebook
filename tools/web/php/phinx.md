- von cake php
- migrations
  - mittels sql files (migrations/sql/*) aktuelle struktur
  - und php library
- seeder füllt Daten ein
  - testdaten trotzdem selbst erzeugen --> faker/php

# our config
- extra composer script in `/database`
- commands:
  - `./migration status`
  - `./migration migrate`
  - `./migration rollback`
  - `./migration seed:run`

# insights
- in `create_table()` column `id` will be created automatically
  - `PRIMARY_KEY`, `NOT NULL` and `AUTO_INCREMENT`
- key names generated automatically
- foreign_key: `<table>_ibfk_<counter>
  - function: `addForeignKeyWithName()`
- `mysql` adapter does not use transactions in `CREATE TABLE, ALTER TABLE, and DROP TABLE`
  - mysql and mariadb have an implicit commit https://mariadb.com/kb/en/sql-statements-that-cause-an-implicit-commit/ for certain commands