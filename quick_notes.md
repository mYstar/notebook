PBA?

# vscode
- git diff: GitLens: Open Changes with Branch or Tag...

# jquery

- `$.ajax`: builds a request
- `$('form').serialize()`: builds a URL encoded notation (GET) from form
    - e.g.: `var=value&var2=value2&var3=value3`
- `$('element').attr('attrname')`: get attributes
- `$('element').val()`: get tag value

# js

- forms have an reset Event: `$('form').reset()`
    - in jquery: `$('form').trigger('reset')`
    - as button: ` <input type="reset">`

# FormSubmitAjaxPlugin/ModalFrageNewSavePlugin uses (search: js-form-submit-ajax)

## php
- UebersetzungController.php -> UebersetzungenPageService.pnp -> MeineUebersetzungenService.php BLEIBT
- Service/Ui/BefundBoxService.php BLEIBT

## CommentSectionService OK
- NewsInternController CHECK
- AngeboteController CHECK
- AktionenController OLD

## Views bleibt
- templates/intern/frage.php
- templates/intern/auftrag-liste-meine.php

## js
- AuftragListePlugin: js-auftrag-liste-back


# whi call order

1. index.php: MainController.perform();
2. MainController: perform() -> handleRoute(action, DIContainerWashabich, Route)
    - gets handling Controller via: DIContainerWashabich.getController
3. <handlingController>.perform($action): 
    - uses class View() to render template
    - renders html directly