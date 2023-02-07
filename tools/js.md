# DOM

- forms have an reset Event: `$('form').reset()`
    - in jquery: `$('form').trigger('reset')`
    - as button: ` <input type="reset">`

# Packages

## jquery

- `$.ajax`: builds a request
- `$('form').serialize()`: builds a URL encoded notation (GET) from form
    - e.g.: `var=value&var2=value2&var3=value3`
- `$('element').attr('attrname')`: get attributes
- `$('element').val()`: get tag value