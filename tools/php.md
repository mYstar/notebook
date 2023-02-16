# Language Constructs
- `obj1 = clone obj2;`: makes a deep copy
- `array[] = value` fügt value hinten an

- alternative Syntax: Templating
```
<?=$value>
<? foreach(...): >
<? endforeach; >
```

# functions
- `str_pad()`: pads string to a given length
- `extract(array)`: creates a variable for every element in the array
- output buffering: 
    1. `ob_start()`: starts buffering, all output is redirected to buffer 
    2. `ob_get_clean()` =
        a. `ob_get_contents()`: returns buffer content
        b. `ob_end_clean()`: discard buffer, end output buffering