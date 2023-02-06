# sed

For rowwise editing of files with regex.
usage:

```shell
# pipe some stream into it  
cat file.txt | sed ...
# give a file directly
sed -i <manipulation> file.txt  
sed -i <manipulation> *.txt  
```

## substitute

use the expression `-e` command: substitute `s///`.
global `/g` replaces not only the first occurance in a row.
*very similar to vim*

```shell
sed -e "s/<from>/to/g"
```
