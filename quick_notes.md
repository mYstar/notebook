# TODO

- ![ ] HDMI im Konferenzraum testen

# IT-1022
- `baustein-code__value` ist bei gleichem `__label` jedes Jahr verschieden
- baustein ID: `.form-group>input[name="id"][value]`
- *web.js*:`ajaxGetDataCode(data, onDone)`: ajax request an API
    - `onDone`: aktualisiert HTML elemente
- routes sind in *MainController.php*
- ? Sind gruppierte Codes immer vollständig -> ja
- ? In Jahre mit existierenden Codes kopieren --> Fehlermeldung (OK, Abbrechen)
- ? Codes sind in einzelnen Jahren nicht vorhanden --> Fehlermeldung (OK, Abbrechen)

- i: Wie Codes der anderen Jahre für Code herausfinden?
    - alle endständigen Codes für ausgewaehltes Jahr sammeln
        - verfügbare Infos: `baustein-code__label` = Code Name/Label
    - alle Codes: `DataCodeService.getByCode()`
    - ! per Ajax: `DataCodeControllerAjax` hat keine Abfrage dafür
        - neuer Request:  `$action == transferCodes`
        - `GET` Parameter: `years`, `codes`
        - `json` return: `{ "2018": [123456, 654321, ...], "2019": [789465, 456789], ... }`

## TODO
- [X] `CodeAddPlugin.addBausteinCode()` und `addBausteinSubCode()` in neue Trait: `CodeAdd`
- [X] Klasse `CodeAddPlugin` --> `CodeSelectorPlugin`
    - [X] css klassen in js, php und scss aendern
    - [X] codeAdd function
- [X] Klasse `TransferCodesPlugin` nach Vorlage: `ClearYearPlugin`
    - [X] Button anzeigen
    - [X] endständige Codes finden
    - [X] popup: alle anderen Jahre anzeigen
    - [X] popup: code changes anzeigen
    - [X] UI: codes einfügen
- [X] Button **transferieren** Tooltip: Übernimmt diese Codes in allen anderen Jahresversionen
    - ? wann soll der Button angezeigt werden (`getCodeTransferButtonHtml()`), nur wenn Codes im Jahr vorhanden
- [X] Farben der Buttons anpassen (delete -> rot)
    - [X] neue css klasse, bootstrap entfernen
- [X] Fehlermeldungen:
    - [X] In Jahre mit existierenden Codes kopieren --> Fehlermeldung (OK, Abbrechen)
    - [X] Codes sind in einzelnen Jahren nicht vorhanden --> Fehlermeldung (OK, Abbrechen)
- [X] bug: http://pb-redaktionssystem.localhost/baustein/9/3434 - leeren und transferieren erscheinen nicht bei 2021
- [X] bug: leeren und transferieren Buttons erscheinen nicht bei neu angelegten codes
    - (`DataCodeControllerAjax` sollte Buttons liefern)
    - besser: js prüft automatisch bei jeder Änderung das jeweilige Jahr
        - (bei: delete(x), leeren, transferieren, add)
        - **MutationObserver** (caniuse: 98.33%)
        - [X] new class `CodesListObserver` listen to `baustein-codes__list` --> alert()
        - [X] manipulate button --hidden classes
- [X] Bug: leeren und transferieren Buttons funktionieren nicht nachdem die liste einmal gelehrt wurde
    - [X] leeren und transferieren nie löschen, sondern nur --hidden markieren
    - [X] beim leeren keine neuen buttons zurück geben
- [X] transferieren und löschen von komplett zum löschen markierten codeListen möglich
    - [X] buttons ausblenden
    - [X] `baustein-code--temp-del` nicht transferieren
- [X] bug: observer not checking grandchildren...?
- [X] bug: observer counting non final codes
- [X] Refactor: 
    - [X] `ajaxGetDataCode()` in eigenen `code/data.js`?
    - [X] `DataCodeControllerAjax.perform()` --> alle routes per `$action` auswählen
        - [X] searchString
        - [X] clearYear/codesToDelete
        - [X] codeToDelete
        - [X] newCode
        - [X] codeToUndelete
    - [X] `Object.assign(CodeSelectorPlugin.prototype, codeAdd);` rückgängig machen
    - [X] DatCodeControllerAjax: `isset($_GET['years']) && isset($_GET['codes']) && isset($_GET['bausteinId'])` --> function
    - [X] `CodeTransfer.transferCodesToOtherYears(): yearsToChange` --> member variable?
    - [X] getClearButtonHtml: css-class --hidden
- [X] Icons statt Beschreibung der Buttons
- [X] Kommentare
- [X] pull request

# php
- ellipsis: `function fname(...args){}`

# js
- `object.fn` alias for `object.prototype`

# IT-961
- blacklist: codes die nicht in Patientenbrief angezeigt werden
    - Sterncodes: können als Sekundärcodes dazucodiert werden
- BlacklistService.getByUniqueKey
- in Baustein Vorschau: (VorschauController)
- Ansicht: strikethrough, ausgegraut
- ?idee: blacklist codes umsortieren