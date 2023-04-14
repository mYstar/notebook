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
- `__DIR__`,`__FILE__`: magic constants containing current fileinfo
- `global $var`: macht $var aus dem globalen Kontext in scope bekannt
    - kann auch eine noch nicht definierte Variable sein (Zuweisung definiert sie)
    - `$GLOBALS['var']`: zugriff auf alle globalen Variablen via Array
- `const VAR`: makes VAR a constant in global or class context
- anonymous functions:
    - closure: `function(args) {}`
    - arrow-function: `fn(args) => <statement>`
- ellipsis: `function fname(...args){}`
- interfaces
  - defined like class (only method stubs)
  - has to be autoloaded/required to work
  - usage: `class className implements interfaceName`
- `$newObj = clone $obj`: shallow copy of object
  - overwrite `__clone()` for deep copy
- `(string|int)[]`: array in phpdoc
- return type `self`

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
- Custom PHP 8 Attributes:
  - `#[NoReturn]`
  - `#[ArrayShape]`
  - phpstorm provides an implementation
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
- `assert()`: tests assumptions -> triggers exception
- `is_string()`, `is_int()`: check for types
- `$obj instanceof <class, baseclass, interface>`: check objects
- `json_encode($var)`: encodes $var content as json string 
- `header('Location: ' . $url)`: sends a raw http header (here: to redirect to `$url`)
- `array_reduce($array, callback, startvalue)`
    - callback: `function($carry, $cur_item)`
- `array_merge(...$array)`: flattens the array by 1 dimension
  - also can be used to append single arrays
- `array_push(altered_array, ...appended_array);`
- `array_walk()` `array_walk_recursive()`: go through all array (and all subarrays) elements in order
- `array_key_first()`, `array_key_last()`: determine start/end of `foreach` loop
- `pack()` `unpack()`: convert data to binary representation
  - strings are a binary representation (`pack` can be used to add numbers etc. to that representation)
- `bin2hex(random_bytes(64/2))`: create random hex number with length 64
- `file_put_contents()`, `file_get_contents()`: reading/writing whole files
- `RecursiveDirectoryIterator`, `RecursiveIteratorIterator`: combined they can list all files in a directory
- `strtotime($time, 'Y-m-d')`: generates a Unix timestamp
- `strspn`: counts how often a given substring occurs at the start of a given string

## dates
- `date('Y-m-d')`: formats a string from current date
- use: `DateTimeInterface`, `DateTimeImmutable`, `DateTime`
- `date->format('Y-m-d H:i:s')`: string formatieren (auch um Teile zu extrahieren)
- `DateInterval('P1M')`: definiert Zeitintervall (hier 1 Monat)
- `DatePeriod($startDate, $interval, $endDate)`: Iterator im Zeitintervall

# regex:
  - `\w` word char = [0-9a-zA-Z_]
  - `\W` non word char
  - `\d` digit
- `preg_match_all()`: alternative to global flag in php regex
- `preg_replace('/patte(rn)/', 'replacement$1', $input)`: regex replace `$1` is the first match group