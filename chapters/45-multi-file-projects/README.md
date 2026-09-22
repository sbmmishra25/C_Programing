# 45. Multi-File Projects

## Translation units
Each .c file is compiled separately. Headers provide declarations; the linker combines object files.

## Complete project
~~~c
/* math.h */
#ifndef MATH_H
#define MATH_H
int add(int, int);
#endif
~~~
~~~c
/* math.c */
#include "math.h"
int add(int a, int b) { return a + b; }
~~~
~~~c
/* main.c */
#include <stdio.h>
#include "math.h"
int main(void) { printf("%d\n", add(2,3)); return 0; }
~~~

Build:
~~~sh
cc -std=c17 -Wall -Wextra -Wpedantic -c math.c
cc -std=c17 -Wall -Wextra -Wpedantic -c main.c
cc math.o main.o -o app
~~~

## Important notes
Use static for private file-scope functions/objects. Avoid duplicate external definitions. Keep public declarations in headers and implementation details in .c files.

## Practice
Build a three-module program with a public API, private helpers, tests, and separate debug/release configurations.