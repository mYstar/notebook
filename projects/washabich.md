# php call stack

1. index.php: MainController.perform();
2. MainController: perform() -> handleRoute(action, DIContainerWashabich, Route)
    - gets handling Controller via: DIContainerWashabich.getController
3. <handlingController>.perform($action): 
    - uses class View() to render template
    - renders html directly