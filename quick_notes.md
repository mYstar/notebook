# IT-1022
- `baustein-code__value` ist bei gleichem `__label` jedes Jahr verschieden
- baustein ID: `.form-group>input[name="id"][value]`
- *web.js*:`ajaxGetDataCode(data, onDone)`: ajax request an API
    - `onDone`: aktualisiert HTML elemente
- routes sind in *MainController.php*

## TODO
- [X] `CodeAddPlugin.addBausteinCode()` und `addBausteinSubCode()` in neue Trait: `CodeAdd`
- [X] Klasse `CodeAddPlugin` --> `CodeSelectorPlugin`
    - [X] css klassen in js, php und scss aendern
    - [X] codeAdd function
- [ ] Klasse `TransferCodesPlugin` nach Vorlage: `ClearYearPlugin`
    - [X] Button anzeigen
    - [X] popup: alle relevanten Jahre anzeigen
    - [ ] popup: code changes anzeigen
    - [ ] UI: codes einfügen
- [ ] Button **transferieren** Tooltip: Übernimmt diese Codes in allen anderen Jahresversionen
    - ? wann soll der Button angezeigt werden (`getCodeTransferButtonHtml()`)
- [ ] Farben der Buttons anpassen (delete -> rot)

