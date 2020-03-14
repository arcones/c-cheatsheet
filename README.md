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
Take note that all the strings created will have the null terminator `/0` at the end. This null terminator can also be used to delete the contents of a string variable in order to reuse it:
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

##### Pointers
They are simple integers that holds a memory address that points to a value, instead of holding the actual value itself.
For example, this line:
```
char * name = "Arcones";

```
will create the string `Arcones` somewhere in the memory and the position of the first character `A` will be stored in `name` variable.

###### Dereferencing
Dereferencing is the act of referring to where the pointer points, for example:
```
int a = 1;

int * pointer_to_a = &a;

printf("The value a is %d\n", a);
printf("The value of a is also %d\n", *pointer_to_a);
```
So:
- `*a_pointer` is the way to access the actual value behind the pointer
- `&a_variable` is the way to access to the memory address of a variable  

##### Structures
Are large variables which contain several *named* variables inside.
```
struct point {
    int x;
    int y;
};

struct point p;
p.x = 10;
p.y = 5;
```
For *customize* the struct name:
```
typedef struct {
    char * brand;
    int model;
} vehicle;

vehicle mycar;
mycar.brand = "Ford";
mycar.model = 2007;
```

###### Function arguments by reference
This is the only way to modify a variable inside a function and see the result outside it:
```
void addone(int * n) {
    (*n)++;
}

int n = 0;
printf("Before: %d\n", n); //this will print "Before: 0"
addone(&n);
printf("After: %d\n", n); //this will print "After: 1"
```
This is widely used to modify structs members:
```
void move(point * p) {
    (*p).x++;
    (*p).y++;
}
```
or with its equivalent:
```
void move(point * p) {
    p->x++;
    p->y++;
}
```

###### Dynamic allocation
Allocating memory dynamically is used to store data without initially knowing its size. For example:
```
typedef struct {
    char * name;
    int age;
} person;

person * myPerson = malloc(sizeof(person));
/*
malloc will dynamically allocate just enough to hold a 
person struct in memory, returning a pointer to its first memory position

malloc declaration is in stdlib.h
*/
/*
sizeof will tell malloc the bit length of the person
*/
```
Then, we will use standard pointer notation to access `myPerson` members.
It is important to free up memory when the pointer is not required any more:
```
free(myPerson);
```

###### Recursion
A recursive method consists in two main parts:
 - A terminating case that indicates when the recursion will finish
 - A call to itself that must make progress towards the terminating case
For example:
```
#include <stdio.h>

unsigned int multiply(unsigned int x, unsigned int y) {
    if (x == 1) {
        return y;
    }
    else if (x > 1) {
        return y + multiply(x-1, y);
    }
    return 0;
}
```

###### Header files
TODO
 

###### References
http://www.learn-c.org
