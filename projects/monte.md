# seatable

## TODO
- [ ]checkout long-text markdown options
- [X]checkout views
- prototype write daily documentation to other base (complete Documentation)
    - [ ] design complete documentation
        - 3 tables: Tätigkeiten, Beobachtungen, Anschlussarbeiten
        - columns: Name, Tag, Notiz --> later: split Notiz into parts (Fach, Material, Status, ...)
        - every textline in daily-cell --> new row here
    - [ ] design daily documentation
        - only today for now --> later: create|archive days automatically
        - header, name are fixed
        - trigger Form on cell click (?js) -> prefill with content --> later: make a difference between add and change?
        - webhook creates a new row in complete documentation
        - check for changes -> only update changes
          - [ ]idea: make a Admin->Kommandos table with buttons (Neuen Tag anlegen, ...)
- [ ]use seatable webhooks to be informed about changes

## long term
- [ ]design autocompletion for daily documentation
  - ?button
  - ?leads to form
  - ?textinput has fuzzysearch in other base
  - ?select other kids
- [ ]later: setup backup options
  - configure cronjobs
  - test recovery of backup
- [ ]later: check how many rows are created in table
  - does it hold a schoolyear (<100000 rows)
  - archive old schoolyears to prevent running into limit

## ideas
- organize bases:
  - Woche, Monat, Schuljahr
  - unterschiedliche Granularität (Tag, Woche, Monat)
  - Archiv: vergangene Schuljahre
- Ferien ausblenden (vorangegangener Schultag = vor den Ferien)