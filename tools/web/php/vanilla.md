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
- anonymous functions:
    - closure: `function(args) {}`
    - arrow-function: `fn(args) => <statement>`
- ellipsis: `function fname(...args){}`

## 8.0
- named arguments: `fname(argname: argument)`
- attributes instead of JavaDoc `#[namespace\attribute, attr2(arg)]` --> Reflection API can read
- constructor property promotion: `__construct(public|readonly arg)` --> creates getter/setter
    - `readonly` since 8.1
- union types: `int|float $number`
- match statt switch: 
```
$res = match($var) {
    0 => 'zero',
    1 => 'one',
};
```
- nullsafe Operator: `$res = $db?->$conn?->query()?;`
## 8.1
- enums:
```
enum Status {
    case Wip;
    case Ready;
}
function acceptStatus(Status $s) {}
```
- loop over enum: `foreach(Status::cases() as status) {}`
- functions are first class objects
- Objects as default parameter, static var or global constant `__construct(Logger $log = new BaseLogger()) {}`
- intersection Types `function fname(Iterator&Countable $values) {}`
- never Return type: `function app() :never {}`
- final class constants: cannot be overwritten by child
- octal notation: `0o16`
- fibers: very lightweight threads
- array unpacking for string keyed arrays: `$newarr = [...$oldarr, ...$newvalues];`

## 8.2
- readonly classes
- DNF Types (disjunctive normal form): `function test((A&B)|null $arg) {}`
- false true and null as return types: `function test() :false {}`
- constants in traits

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
- `json_encode($var)`: encodes $var content as json string 
- `header('Location: ' . $url)`: sends a raw http header (here: to redirect to `$url`)
- `array_reduce($array, callback, startvalue)`
    - callback: `function($carry, $cur_item)`
- `array_merge(...$array)`: flattens the array by 1 dimension
- `array_walk()` `array_walk_recursive()`: go through all array (and all subarrays) elements in order

## dates
- use: `DateTimeInterface`, `DateTimeImmutable`, `DateTime`
- `date->format('Y-m-d H:i:s')`: string formatieren (auch um Teile zu extrahieren)
- `DateInterval('P1M')`: definiert Zeitintervall (hier 1 Monat)
- `DatePeriod($startDate, $interval, $endDate)`: Iterator im Zeitintervall

