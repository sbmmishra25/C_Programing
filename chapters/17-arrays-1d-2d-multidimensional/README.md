# 17. Arrays: 1D, 2D & Multidimensional

## Definition
An array is a contiguous sequence of objects of one type. Valid indices are zero through length minus one.

## Complete example: matrix addition
~~~c
#include <stdio.h>

#define ROWS 2
#define COLS 3

int main(void) {
    int a[ROWS][COLS] = {{1,2,3},{4,5,6}};
    int b[ROWS][COLS] = {{6,5,4},{3,2,1}};
    int c[ROWS][COLS];

    for (size_t i = 0; i < ROWS; ++i)
        for (size_t j = 0; j < COLS; ++j)
            c[i][j] = a[i][j] + b[i][j];

    for (size_t i = 0; i < ROWS; ++i) {
        for (size_t j = 0; j < COLS; ++j)
            printf("%d ", c[i][j]);
        putchar('\n');
    }
    return 0;
}
~~~

## Memory layout
A multidimensional array is an array of arrays. The rightmost dimension is contiguous, so a row-major traversal matches the actual C layout and is normally cache-friendly.

Do not confuse a true 2-D array with an array of pointers. Their types, layout, allocation, and indexing semantics differ.

## Function parameters
A fixed-column matrix can be passed as a pointer to an array:
~~~c
void print_matrix(size_t rows, const int a[rows][3]);
~~~
For variable-length array parameters, dimensions needed for address calculation must be available in the parameter list.

## Common mistakes
Out-of-bounds access, wrong row/column limits, using sizeof after array-to-pointer conversion, and assuming a 2-D array is interchangeable with int**.

## Complexity
An n-element traversal is O(n); an r by c matrix traversal is O(rc).

## Practice
Transpose, multiply, rotate, search, and dynamically allocate matrices with checked size calculations.