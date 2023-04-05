# diary
- orga, planning 0,5h OK
- whi-db: new features 2h -> 2,5h
- meeting: how to server 1h -> 1,5h
- pb-redaktion: bugfix statistics + new codetype estimate 2,5h
- learn babel 0.5h

# TODO
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
  - [X] pull request
  - [ ]new tag for merged pull request

# terminal
- `mkpasswd -m SHA-512 <password>`

# sql
- `INSERT INTO table SET name = value, name2 = value, name3 = value3;`

# php
- return type `self`
- `array_push(altered_array, ...appended_array);`

# Server Tour
- DBs:
  - api -> HELIOS
  - ma -> medizinische Abk.
  - md -> medizinischer Dienst (washabich greift zu)
- alles administrative auf dem Server macht Sebastian 
  - Berechtigungen
  - Backups
  - Mail
- /var/www
- /var/log/php8.1
  - errorhandler@washabich.de
- /etc/apache2/ configs
- monit - monitoring software
  - schickt mail, wenn sich an logs was aendert
  - wenn da kein php error steht, gibt es wahrscheinlich kein Problem
- cronjobs
  - /etc/crontab
  - Sebastian kuemmert sich um das meiste
  - auf web01: user cronjobs von Ansgar (washabich: CronController.php)

# docker
- `docker pull <repo>:latest`: downloads the latest image of a repo from docker hub
- `docker images`: lists all pulled images
- `docker stop <container>`
- `docker ps -a` or `docker container list`
- `docker rm <container>`
- `docker rmi <image>`
- `docker exec <container> <command>`: executes a command in a container
  - `-d` detached mode
  - `-it` interactive terminal

## docker-compose
- `docker-compose up/down`: start/stop an image according to the *docker-compose.yml*
  - option `-d`: detached mode

## docker-compose.yml
- settings for deployment of the image
- `volumes:`: `<local file>:<container-file>` maps a local file/dir to another place in the container

# seatable
- install directory: `/opt/seatable`
- config: `<install>/conf/seatable_settings.py`
  - `docker exec -d seatable /shared/seatable/scripts/seatable.sh`: admin script
    - `start|stop|restart`: restart on config change
- data docker volumes: 
  - `<install>/mysql-data`: DB
  - `<install>/seatable-data`: seatable (log and config of nginx and seatable)

# git
- `git log`: shows the last commits and their hashes
- `git revert <hash1> <hash2>`: undoes the last commits in a new commit
  - `git reset --hard <hash>`: removes the commit with <hash> and all following from the branch (use: `git push --force`)
  - git reset alters the branch, it should be the last resort, when revert is not possible  
