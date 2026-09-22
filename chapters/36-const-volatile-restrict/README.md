# 36. const, volatile & restrict

## const
const expresses that an object should not be modified through a particular lvalue. It improves API contracts:
~~~c
void print_array(const int *a, size_t n);
~~~

## volatile
volatile tells the implementation that accesses to a volatile-qualified object are observable and must not be optimized away in ways that violate the language rules. It is useful for certain memory-mapped I/O or signal-related scenarios, but volatile is NOT a thread synchronization mechanism.

## restrict
restrict is a promise about aliasing for an execution of a block/function. If used incorrectly, behavior can become undefined because the program violates the restrict contract.

## Complete example
~~~c
#include <stdio.h>
#include <stddef.h>

void add_arrays(size_t n, int *restrict dst,
                const int *restrict a,
                const int *restrict b) {
    for (size_t i = 0; i < n; ++i)
        dst[i] = a[i] + b[i];
}

int main(void) {
    int a[] = {1,2,3};
    int b[] = {4,5,6};
    int c[3];

    add_arrays(3, c, a, b);
    for (size_t i = 0; i < 3; ++i) printf("%d ", c[i]);
    putchar('\n');
    return 0;
}
~~~

## Common mistakes
Treating const as absolute immutability, using volatile for locking, and adding restrict without satisfying its aliasing contract.

## Practice
Design read-only APIs, investigate a memory-mapped register example on a documented embedded platform, and compare restrict-enabled and ordinary loops.