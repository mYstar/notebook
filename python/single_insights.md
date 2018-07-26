# Single Insights

mostly from googles python class

* python3: there is a difference between `/` (float division) and `//` (integer division)
* copy a sequence with: `cpy = seq[:]`
* easy printf-like string formatting with `%`: 'int: %d; str: %s' % (42, 'answer')
* list comprehensions: `newlist = [ item*item for item in oldlist]`
    * as compact way to compute on a list
    * constructs a new list automatically
    * variant with `if` statement: `newstr = [ s.upper() for s in oldstr if len(s) < 2 ]`
* string formatting with dicts:

```python 
hash = { "word":"answer", "value":42 }
print "The %(word)s is: %(value)d" % hash 
```

* `print`ing into a file:(**python3 only**) `print(string, file=f)`
    * old fashion: `print >> f, string`
