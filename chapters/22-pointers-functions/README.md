# 22. Pointers & Functions

## Definition
Pointers let functions read or modify caller-owned objects and represent optional outputs. C still uses pass-by-value: the pointer itself is copied, while both copies can designate the same object.

## Complete example
~~~c
#include <stdio.h>
#include <stdbool.h>

bool divide(int a, int b, int *quotient, int *remainder) {
    if (b == 0 || quotient == NULL || remainder == NULL)
        return false;
    *quotient = a / b;
    *remainder = a % b;
    return true;
}

int main(void) {
    int q, r;
    if (!divide(17, 5, &q, &r)) {
        fprintf(stderr, "division failed\n");
        return 1;
    }
    printf("q=%d r=%d\n", q, r);
    return 0;
}
~~~

## Output parameters
Output pointers are useful when a function needs to return multiple results. Document whether each pointer may be NULL and whether the function writes through it.

## const correctness
A parameter such as const int *input promises not to modify the referenced integer through that pointer. This allows read-only data to be passed safely.

## Pointer-to-pointer
Use T ** when the function must modify a caller's T *:
~~~c
bool allocate_int(int **out) {
    if (!out) return false;
    int *p = malloc(sizeof *p);
    if (!p) return false;
    *p = 42;
    *out = p;
    return true;
}
~~~
The caller owns the returned allocation and must eventually free it.

## Common mistakes
Passing an uninitialized pointer instead of its address, dereferencing NULL, returning pointers to local objects, and failing to document ownership.

## Practice
Implement swap, safe string duplication, dynamic-array growth, linked-list insertion, and a function that returns both minimum and maximum.