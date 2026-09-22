# 40. Undefined, Implementation-Defined & Unspecified Behavior

## Definitions
**Undefined behavior (UB):** the C standard imposes no requirements after the program performs the operation. Examples include out-of-bounds access and signed integer overflow.

**Implementation-defined behavior:** the implementation chooses a behavior and documents the choice. Example categories include some properties of integer types and representation.

**Unspecified behavior:** the implementation may choose among permitted alternatives and need not document which one it chose.

## Examples
~~~c
#include <limits.h>
#include <stdio.h>

int main(void) {
    printf("CHAR_BIT=%d\n", CHAR_BIT);
    int a = 1, b = 2;
    printf("%d %d\n", a, b);
    return 0;
}
~~~

Do not write programs that depend on an unguaranteed evaluation order or assume a specific representation unless the program has explicitly chosen that implementation contract.

## Debugging rule
Compiler optimization can expose UB dramatically. A program that appears to work in one build is not evidence that UB is safe.

## Practice
Classify examples involving signed overflow, uninitialized reads, pointer comparisons, implementation integer widths, and evaluation order.