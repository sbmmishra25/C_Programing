# 31. Header Files

## Concept
A header declares interfaces shared by translation units. It commonly contains function prototypes, type definitions, macros, and constants; definitions of non-inline objects should generally not be duplicated in headers.

## Include guards
~~~c
#ifndef MATH_UTIL_H
#define MATH_UTIL_H

int add(int a, int b);

#endif
~~~
The guard prevents repeated inclusion within one translation unit.

## Complete example
~~~c
/* math_util.h */
#ifndef MATH_UTIL_H
#define MATH_UTIL_H
int add(int a, int b);
#endif
~~~
~~~c
/* math_util.c */
#include "math_util.h"
int add(int a, int b) { return a + b; }
~~~
~~~c
/* main.c */
#include <stdio.h>
#include "math_util.h"
int main(void) {
    printf("%d\n", add(4, 5));
    return 0;
}
~~~
Build with: `cc -std=c17 -Wall -Wextra -Wpedantic main.c math_util.c -o app`.

## Important notes
Use angle brackets for implementation/library headers and quotes for project headers by convention. Headers are textually included by the preprocessor; they are not independently linked modules.

## Common mistakes
Defining ordinary global objects in a header, missing guards, circular dependencies, incompatible declarations, and relying on include order.

## Practice
Create a reusable vector.h/vector.c pair and expose only the intended public API.