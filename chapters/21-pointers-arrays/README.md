# 21. Pointers & Arrays

## Core relationship
In most expressions, an array name converts to a pointer to its first element. The array itself is not a pointer: sizeof(array) gives the whole array size while sizeof(pointer) gives pointer size.

## Complete example
~~~c
#include <stdio.h>
#include <stddef.h>

void print(const int *p, size_t n) {
    for (size_t i = 0; i < n; ++i)
        printf("%d ", p[i]);
    putchar('\n');
}

int main(void) {
    int a[] = {4, 1, 7, 2, 9};
    size_t n = sizeof a / sizeof a[0];

    print(a, n);
    int *p = a;
    printf("first=%d third=%d\n", *p, *(p + 2));

    for (int *q = a + n; q != a; ) {
        --q;
        printf("%d ", *q);
    }
    putchar('\n');
    return 0;
}
~~~

## Array parameter forms
int a[] and int *a as function parameters describe the same adjusted parameter type. The length is not carried with the pointer, so pass it explicitly.

For multidimensional arrays, the pointer type must preserve the inner dimension, for example int (*p)[4].

## Important notes
- a[ i ] is defined in terms of pointer arithmetic: *(a+i).
- Pointer traversal must stay within the same array object.
- sizeof a works only while a is an actual array, not after parameter adjustment.
- Use const when a function only reads the array.

## Common mistakes
Treating int** as a substitute for int [rows][cols], losing the array length, and indexing beyond the allocation.

## Complexity
A full traversal is O(n) time and O(1) auxiliary space.

## Practice
Implement array copy, reverse, min/max, duplicate removal in a sorted array, and matrix traversal using pointer-to-array parameters.