# 14. Recursion

## Definition
Recursion solves a problem by calling the same function on a smaller instance until a base case is reached.

## Requirements
A correct recursive design needs a base case, a recursive case that reduces the problem, and a termination argument.

## Complete example
~~~c
#include <stdio.h>

unsigned long long factorial(unsigned n) {
    if (n <= 1) return 1;
    return (unsigned long long)n * factorial(n - 1);
}

unsigned gcd(unsigned a, unsigned b) {
    if (b == 0) return a;
    return gcd(b, a % b);
}

int main(void) {
    printf("5! = %llu\n", factorial(5));
    printf("gcd(84,30) = %u\n", gcd(84,30));
    return 0;
}
~~~

## Call stack and complexity
Each active call requires stack storage. Factorial takes O(n) time and O(n) stack space. Euclid's GCD takes O(log min(a,b)) calls.

Recursion is natural for trees, divide-and-conquer, backtracking, and recursively defined structures. Iteration is often preferable for simple repetition or very deep input because it can use O(1) auxiliary stack space.

## Common mistakes
Missing base cases, non-decreasing recursive arguments, exponential recomputation, and excessive recursion depth.

## Practice
Implement Tower of Hanoi, recursive binary search, merge sort, tree traversals, permutations, subsets, and maze backtracking.