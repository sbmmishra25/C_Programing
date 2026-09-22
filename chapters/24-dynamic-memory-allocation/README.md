# 24. Dynamic Memory Allocation

## Definition
Dynamic allocation obtains storage whose lifetime is controlled explicitly by the program. The standard library provides malloc, calloc, realloc, and free.

## Complete example
~~~c
#include <stdio.h>
#include <stdlib.h>
#include <stddef.h>

int main(void) {
    size_t n = 5;
    int *a = calloc(n, sizeof *a);
    if (!a) {
        fprintf(stderr, "allocation failed\n");
        return 1;
    }

    for (size_t i = 0; i < n; ++i) a[i] = (int)(i * i);

    size_t new_n = 10;
    int *tmp = realloc(a, new_n * sizeof *a);
    if (!tmp) {
        free(a);
        fprintf(stderr, "resize failed\n");
        return 1;
    }
    a = tmp;

    for (size_t i = n; i < new_n; ++i) a[i] = (int)i;
    for (size_t i = 0; i < new_n; ++i) printf("%d ", a[i]);
    putchar('\n');

    free(a);
    return 0;
}
~~~

## Ownership
After successful allocation, establish exactly who owns the object. The owner is responsible for releasing it once, after the final use.

## realloc rule
Always store realloc's result in a temporary pointer. If realloc fails, the original allocation remains valid. Assigning directly to a may lose the only pointer to it.

## Allocation-size overflow
Before allocating n elements of size s, ensure n <= SIZE_MAX / s. Include stdint.h or stdint-related definitions as appropriate for SIZE_MAX availability on the target.

## Common errors
Leaks, double free, use-after-free, freeing a non-heap pointer, reading uninitialized allocated storage, and overflow in size calculations.

## Debugging
Compile with -g -fsanitize=address,undefined when supported. Sanitizers can expose out-of-bounds accesses, use-after-free, and related defects.

## Practice
Implement a dynamic vector, string duplication, matrix allocation, and a linked list with complete ownership rules.