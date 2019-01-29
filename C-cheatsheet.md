C Cheatsheet
============

##### Import libraries
```#include <stdio.h>```

##### Exit codes
- 0 when the program finished successfully
- Any number greater than 1 when it doesn't

This should be _returned_ at the end of ``ìnt main(){}`` method to properly exit.

##### Print via stdout

```printf("This will be echoed in the standard out");```

####### Printf formatters

- ```%d``` for an integer
- ```%f``` for a floating point number
- ``%.2f`` for a floating point number truncated to two decimal positions 

Of course, the proper library should be imported to invoke such function.

##### Data types
- Signed Integers: ```char```, ```int```, ```short```, ```long```, ```long long```
- Unsigned Integers: same as before but with ``ùnsigned`` prefix
- Floating point numbers: ```float```, ```double``
- Define boolean data type:
```
#define BOOL char
#define FALSE 0
#define TRUE 1
```

Be aware, for calculations to be resolved properly, set all the variables involved in the same type as the result!

##### Arrays
For example:
```int numbers[10];``
``
char vowels[][5] = {
    {'A', 'E', 'I', 'O', 'U'},
    {'a', 'e', 'i', 'o', 'u'}
};
``
