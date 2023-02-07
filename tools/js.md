# DOM

- forms have an reset Event: `$('form').reset()`
    - in jquery: `$('form').trigger('reset')`
    - as button: ` <input type="reset">`
- `element.checkValidity()`: check form input, returns false and an error if sth. is wrong
- `element.reportValidity()`: check form input, returns false and displays hints sth. is wrong

# Packages

## jquery

- `$.ajax`: builds a request
- `$('form').serialize()`: builds a URL encoded notation (GET) from form
    - e.g.: `var=value&var2=value2&var3=value3`
- `$('element').attr('attrname')`: get attributes
- `$('element').val()`: get tag value
- `element.find('selector');`: searches the descendants of element for a matching selector
- `collection<element>.filter('selector'||function(index, element));`: reduces the collection to the elements that match the selector or return true, given to the 