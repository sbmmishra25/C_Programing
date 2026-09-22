# 41. Integer Overflow & Common C Pitfalls

## Signed and unsigned overflow
Signed integer overflow is undefined behavior. Unsigned arithmetic is modulo the type's range.

## Complete example
~~~c
#include <limits.h>
#include <stdio.h>

int main(void) {
    int a = INT_MAX, b = 1;
    if (b > 0 && a > INT_MAX - b)
        puts("addition would overflow");
    else
        printf("%d\n", a + b);
    return 0;
}
~~~

## Common pitfalls
Off-by-one errors, incorrect printf formats, array-to-pointer decay, string-buffer overflow, allocation-size multiplication overflow, signed/unsigned comparison bugs, use-after-free, double-free, and returning pointers to dead objects.

## Safe allocation principle
Before allocating n objects of size s, check that n <= SIZE_MAX / s.

## Practice
Implement checked add/multiply helpers and boundary tests for INT_MIN, INT_MAX, zero, and negative operands.