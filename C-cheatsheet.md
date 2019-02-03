C Cheatsheet
============

##### Import libraries
```#include <stdio.h>```

##### Import local header files
```#include "myFunctions.h"```

##### Exit codes
- 0 when the program finished successfully
- Any number greater than 1 when it doesn't

This should be _returned_ at the end of ``ìnt main(){}`` method to properly exit.

##### Print via stdout

```printf("This will be echoed in the standard out");```

###### Printf formatters

- ```%d``` for an integer
- ```%f``` for a floating point number
- ``%.2f`` for a floating point number truncated to two decimal positions 
- ```%s``` for strings

Of course, the proper library should be imported to invoke such function.

##### Data types
- Signed Integers: ```char```, ```int```, ```short```, ```long```, ```long long```
- Unsigned Integers: same as before but with ``unsigned`` prefix
- Floating point numbers: ```float```, ```double```
- Define boolean data type:
```
#define BOOL char
#define FALSE 0
#define TRUE 1
```

Be aware, for calculations to be resolved properly, set all the variables involved in the same type as the result!

##### Arrays
For example:
```
int numbers[10];
```
or
```
char vowels[][5] = {
    {'A', 'E', 'I', 'O', 'U'},
    {'a', 'e', 'i', 'o', 'u'}
};
```

Size of an array:
```
int a[17];
size_t n = sizeof(a)/sizeof(a[0]);
return site_t; 
```

##### Strings
Read-only string:
```
char * name = "John Smith";
```
Read and write string:
```
char name[] = "John Smith";
/*
watch out!!! it contains at the end the char '\0' (string termination) which is invisible, 
so its length is visible chars + 1!!
*/
```
To know the length of a string:
```
strlen(aString);
```
To compare strings:
```
strncmp(aString, anotherString, maxComparisonWidth) //Will only return 0 if the compared parts are equal

// if(strncmp(... , ... , ...) == 0)

```
To concatenate:
```
char destination[20]="Hello";
char source[20]="World";
strncat(destination,source,5); //HelloWorld
strncat(destination,source,20); //HelloWorldWorld
```
The last int parameter is to select the max num of characters from source to append, or its length, it the parameter is greater.
Watch out!! As strings are arrays and they are objects, they are __passed by reference!!!__

Other way to concatenate:
```
char name[]="Marta";
char surname[]="Arcones";
char result[100];
sprintf(result,"%s %s",name,surname);
printf("%s\n",result); // will print "Marta Arcones"
```
To delete contents of a string to reuse it:
```
myString[0] ='\0';
```

##### Loops
```
// while
int n = 0;
while (n < 10) {
    printf("The value of the index of the loop is %d\n", n);
    n++;
}


//for
int i;
for (i = 0; i < 10; i++) {
    printf("The value of the index of the loop is %d\n", i);
}

```

##### Functions
- Arguments are passed *by value* unless in the case of pointers.
- Functions should be *declared first*
- Their default scope is all the project 
```
/* function declaration */
int foo(int bar);

int main() {
    /* calling foo from main */
    printf("The value of foo is %d", foo(1));
}

int foo(int bar) {
    return bar + 1;
}
```

##### Static
- In case is used with a variable, it increases its scope up to the file containing them   
- In case is used with a function, it decreases its scope down to the file containing them   
```
// variables
static int count = 0;

//functions
static void fun(void) {
   printf("I am a static function.");
}

```
