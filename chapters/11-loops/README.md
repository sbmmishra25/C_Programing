# 11. Loops

## Definition
A loop repeats a statement or block while a controlling condition remains true. C provides while, do...while, and for.

## Why it matters
Loops are the foundation of traversal, repeated input, simulation, searching, and numerical algorithms. Correct loop design depends on initialization, condition, progress, and a clear termination argument.

## Syntax
~~~c
while (condition) { /* body */ }
do { /* body */ } while (condition);
for (initialization; condition; update) { /* body */ }
~~~

## Complete example
~~~c
#include <stdio.h>

int main(void) {
    int n;
    if (scanf("%d", &n) != 1 || n < 0) {
        fprintf(stderr, "Enter a non-negative integer.\n");
        return 1;
    }

    long long sum = 0;
    for (int i = 1; i <= n; ++i) sum += i;

    unsigned long long fact = 1;
    for (int i = 2; i <= n; ++i) fact *= (unsigned)i;

    printf("sum = %lld\n", sum);
    printf("factorial = %llu\n", fact);

    for (int i = 1; i <= n; ++i) {
        for (int j = 1; j <= i; ++j) putchar('*');
        putchar('\n');
    }
    return 0;
}
~~~

## Explanation and complexity
The first loop computes 1+...+n in O(n). The factorial loop is O(n), although the result can overflow for sufficiently large n. The nested pattern is O(n²) time and O(1) auxiliary space. Every loop should have a clear progress variable or termination argument.

## while vs do...while
while may execute zero times. do...while executes at least once, making it useful for menus and validation.

## Common mistakes
Off-by-one errors, infinite loops, stale variables, unsigned decrement wraparound, and accidental nested O(n²) work.

## Practice
Print primes to n; reverse an integer; compute GCD; print a multiplication table; find an array maximum.

## Interview focus
Explain loop invariants, termination, nested-loop complexity, and the difference between pre-test and post-test loops.