# Language Constructs
- `obj1 = clone obj2;`: makes a deep copy
- `array[] = value` fügt value hinten an
- `list($var1, $var2) = $array`: unpacks `$array` into the vars

- alternative Syntax: Templating
```
<?=$value>
<? foreach(...): >
<? endforeach; >
```
- `global $var`: macht $var aus dem globalen Kontext in scope bekannt
    - kann auch eine noch nicht definierte Variable sein (Zuweisung definiert sie)
    - `$GLOBALS['var']`: zugriff auf alle globalen Variablen via Array
- `const VAR`: makes VAR a constant in global or class context

# functions
- `str_pad()`: pads string to a given length
- `extract(array)`: creates a variable for every element in the array
- output buffering: 
    1. `ob_start()`: starts buffering, all output is redirected to buffer 
    2. `ob_get_clean()` =
        a. `ob_get_contents()`: returns buffer content
        b. `ob_end_clean()`: discard buffer, end output buffering
- `htmlspecialchars()`: encodes characters for display on website
- `trigger_error()`: display error message
    - whi: error level ab `E_USER_WARNING` zeigen den Fehler an, default `E_USER_NOTICE` nicht

