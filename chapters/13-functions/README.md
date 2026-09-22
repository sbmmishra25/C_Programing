# 13. Functions

## Definition
A function is a named unit of code with a return type, parameter list, and body. A prototype declares its interface before use.

## Complete example
~~~c
#include <stdio.h>
#include <stddef.h>

static int max2(int a, int b) {
    return a > b ? a : b;
}

static void swap(int *a, int *b) {
    int t = *a;
    *a = *b;
    *b = t;
}

static int sum_array(const int a[], size_t n) {
    int sum = 0;
    for (size_t i = 0; i < n; ++i) sum += a[i];
    return sum;
}

int main(void) {
    int x = 4, y = 9;
    printf("max = %d\n", max2(x, y));
    swap(&x, &y);
    printf("x=%d y=%d\n", x, y);

    int a[] = {1,2,3,4};
    printf("sum = %d\n", sum_array(a, sizeof a / sizeof a[0]));
    return 0;
}
~~~

## Core concepts
C passes arguments by value. To modify caller-owned data, pass a pointer. Array parameters are adjusted to pointers, so a function receiving an array normally needs its length separately. Use const when the function promises not to modify the referenced data.

A declaration and definition must have compatible types. A prototype such as void f(void) explicitly means no arguments; avoid old-style empty parameter lists in new code.

## Return values and contracts
Functions should clearly document what they return, what inputs are valid, whether pointers may be null, and who owns allocated memory.

## Common mistakes
Missing prototypes, incompatible declarations, returning a pointer to an automatic local object, hidden mutation, and ignored error/status returns.

## Practice
Write functions for GCD, prime testing, array reversal, matrix multiplication, binary search, and safe dynamic-array growth.