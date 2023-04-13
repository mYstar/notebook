# diary
- bake OK
- clean bath OK
- monte research integration options 2h OK
- read & work 2h OK
- pass dishwasher in 1h OK
- repair ipad 1h -> 1,5h
- cook 1,5h OK
- call Jenny 30' OK

# TODO
- [ ]registry zugriff für docker
- [ ]whi-router: patientenbriefe.de
- [ ]triaphon
- [ ]tethering by telephone test
- [ ]?What ist Zend?
- [ ]?Whst is Opcache?

# IT-1110
- HELIOS Fallbezogene Daten:
  - insomnia REST recherchieren
- neue Action im Main Controller `$isDataWarehouseApiCall`
- [ ]config: test system
  - [ ]acceptance: upload test file
  - [ ]unit: TDD from now on
- [ ] Hash als Secret verwenden
  - [ ] einfach als https verschlüsseltes passwort name: hash->secret
  - [ ] im confluence dokumentieren
- [ ] new data-source seed for helios
  - [ ] remove autocreate datasources
- [ ] new migration: 
  - [ ] rollback everything and reverse engineer data_warehouse.sql
  - [ ] create HealthCase classes with column names
  - [ ] health_case
  - [ ] health_case_code_icd
  - [ ] health_case_code_ops
- [ ] create new api route (PUT)
- [ ] verify request 
  - [ ]verify hash secret
  - [ ]verify data keys and values
- [ ]build: HealthCase object
- [ ]build: insert statements (Service)
- [ ]integration test: send a request, check response, test DB

# composer
- update git tag and version number in composer.json

# planning
- Vorbereitung: Backlog Pflege (Schätzungen anpassen)

# pragmatic programmer
- keep a sw engineering daybook
- code defence
  - assertions
  - constraints
  - validation
  - check consistency
- design by contract
  - preconditions (caller responsible for input data)
  - postconditions
  - class invariants/state 
    - conditions that are true always for an object (precise: before and after execution of every method)
    - example: bank account not below limit
  - error handling (when contract is broken, exceptions, always a bug)
  - implementation:
    - guard clauses can mimic this
    - `assert` checking state at start of function -> preconditions
    - check should have no side effects
    - use like exceptions
    - postconditions cannot be easily checked (different return points)
    - assert is not preserved by inheritance
    - boilerplate code would be necessary to check against old state of variables (not feasible)
  - the caller is responsible for correct inputs
    - check beforehand at the interfaces between libraries/real world
- crashing
  - raise exeptions early
  - don't reraise exceptions, when you can't fix the problem -> just don't catch
  - only use of catch: cleaning up
  - Exceptions are for 'impossible' states -> program should not be able to run after reaching
- error handling
  - possible errors (like: user input, the ones that have a recovery scenario) -> check via `if` and handle result
  - impossible errors (not expected behaviour) -> `assert`
  - leave assertions in production -> only turn off the performance problematic

# english
- tenet --> Grundsatz