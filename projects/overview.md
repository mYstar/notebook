# Projektseiten

- washabich.de
- longcovid-info.de
- impfen-info.de
- selbst-verstehen.de

# Abkürzungen
PBA - Patienten Brief Ambulanz
MD medizinischer Dienst nordrhein Lernplattform

# PBA Redaktionssystem
- Bausteine für Patientenbriefe
- endständiger Code-> hat keine weiteren Untercodes
- 
# Server Tour
- DBs:
    - api -> HELIOS
    - ma -> medizinische Abk.
    - md -> medizinischer Dienst (washabich greift zu)
- alles administrative auf dem Server macht Sebastian
    - Berechtigungen
    - Backups
    - Mail
- */var/www*
- */var/log/php8.1*: logfiles
    - **errorhandler@washabich.de** Mails werden automatisch von `monit` gesendet
- monit - monitoring software
    - schickt mail, wenn sich an logs was aendert
    - wenn da kein php error steht, gibt es wahrscheinlich kein Problem
- */etc/apache2/*: configs
- cronjobs
    - */etc/crontab*
    - Sebastian kuemmert sich um das meiste
    - auf web01: user cronjobs von Ansgar (washabich: `CronController.php`)