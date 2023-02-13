# php call stack

1. index.php: MainController.perform();
2. MainController: perform() -> handleRoute(action, DIContainerWashabich dependency injection, Route)
    - gets handling Controller via: DIContainerWashabich.getController
    - 
3. <handlingController>.perform($action): 
    - uses class View() to render template
    - renders html directly

# washabich testumgebungen
- siehe: Confluence/IT/Liste aller Programme
- test.washabich.de --> !original Datenbank
- dev.washabich.de
- demo.washabich.de
- beta.washabich.de

# Admin Menu in Testinstanz freischalten
- *templates/intern/header.php* -> ruft: `AuthController::berechtigt('administration')`
- php -> DB: `$row['admin'] == 'ja'`
- DB: `gruppe_benutzer` Tabelle abgefragt
    - ich bin benutzer: 4786