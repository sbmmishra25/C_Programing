# 39. Stack vs Heap

## Concept
Automatic objects commonly use implementation-managed storage associated with function/block execution; dynamically allocated objects use the allocation facilities and have explicitly controlled lifetime. The terms stack and heap describe common implementations, not complete ISO C categories.

## Example
~~~c
#include <stdio.h>
#include <stdlib.h>

void demo(void) {
    int local = 10;
    int *dynamic = malloc(sizeof *dynamic);
    if (!dynamic) return;

    *dynamic = 20;
    printf("local=%d dynamic=%d\n", local, *dynamic);
    free(dynamic);
}

int main(void) {
    demo();
    return 0;
}
~~~

## Lifetime
The local object's lifetime ends when its execution block ends. The allocated object's lifetime ends when free is called, unless allocation failure occurs first.

## Comparison
Automatic storage is convenient and usually fast but has scope/lifetime constraints. Dynamic storage supports variable-size data and longer lifetimes but requires explicit ownership and release.

## Common mistakes
Returning pointers to locals, leaking allocations, double-free, use-after-free, and assuming every large object must be heap allocated.

## Practice
Compare a fixed array, a VLA where supported by the selected C standard/compiler, and a malloc-based dynamic array. Measure behavior rather than assuming an optimization outcome.