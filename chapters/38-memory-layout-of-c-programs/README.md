# 38. Memory Layout of C Programs

## Concept
A typical process has regions commonly described as text/code, read-only data, initialized data, zero-initialized data, heap, and stack. Exact layout is implementation and operating-system dependent, not an ISO C guarantee.

## Complete demonstration
~~~c
#include <stdio.h>
#include <stdlib.h>

int global_init = 10;
int global_zero;

static int file_static = 20;

int main(void) {
    static int local_static = 30;
    int local_auto = 40;
    int *heap = malloc(sizeof *heap);

    if (!heap) return 1;
    *heap = 50;

    printf("&global_init = %p\n", (void *)&global_init);
    printf("&global_zero = %p\n", (void *)&global_zero);
    printf("&file_static = %p\n", (void *)&file_static);
    printf("&local_static = %p\n", (void *)&local_static);
    printf("&local_auto = %p\n", (void *)&local_auto);
    printf("heap = %p\n", (void *)heap);

    free(heap);
    return 0;
}
~~~

## Important note
Do not infer portable relationships from printed addresses. ASLR, compiler choices, linker scripts, ABI, optimization, and OS behavior can change them.

## Practice
Use an object-file/map-file tool on your platform to inspect sections and compare initialized versus zero-initialized globals.