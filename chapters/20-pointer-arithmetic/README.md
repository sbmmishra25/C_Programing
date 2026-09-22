# 20. Pointer Arithmetic

## Definition
For a pointer into an array, adding an integer moves by elements rather than raw bytes. Subtracting two pointers into the same array produces a ptrdiff_t distance.

## Complete example
~~~c
#include <stdio.h>
#include <stddef.h>

int main(void) {
    int a[] = {10,20,30,40};
    size_t n = sizeof a / sizeof a[0];

    for (int *p = a; p < a + n; ++p)
        printf("%d\n", *p);

    ptrdiff_t d = &a[3] - &a[0];
    printf("distance=%td\n", d);
    return 0;
}
~~~

## Rules
For an array of n elements, a+i is valid for 0 <= i <= n when used as a pointer value; a+n is one-past and must not be dereferenced. Pointer subtraction is defined only for pointers into the same array object (or one-past it), and the result must be representable as ptrdiff_t.

## Why pointer arithmetic is type-aware
If p is int*, p+1 advances by one int, conceptually by sizeof(int) bytes. This differs from adding one to a char*.

## Common mistakes
Subtracting unrelated pointers, dereferencing one-past pointers, manually treating typed pointers as byte addresses without a valid reason, and performing arithmetic outside the permitted array domain.

## Complexity
Sequential traversal is O(n) time and O(1) auxiliary space.

## Practice
Reverse an array using two pointers, locate a value, implement bounded pointer-based strlen, and explain pointer difference versus byte difference.