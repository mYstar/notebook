# functions
- match in array: `['a', 'b', 'c'].includes('b')`
- keine native traits/mixins
    - workaround: 
```
// trait
export default {
    function1() {...},
    function2() {...},
}

// class
import traitname from 'path'

class ClassName { ... }

Object.assign(ClassName.prototype, traitname);
```
- template literals: 
```
`start ${variable} end`
```
- `alert()`, `confirm()`: popup boxes
- **MutationObserver**: listen to changes in the DOM + define callback

# DOM
- forms have an reset Event: `$('form').reset()`
    - in jquery: `$('form').trigger('reset')`
    - as button: ` <input type="reset">`
- `element.checkValidity()`: check form input, returns false and an error if sth. is wrong
- `element.reportValidity()`: check form input, returns false and displays hints sth. is wrong
- focus: `document.activeElement`