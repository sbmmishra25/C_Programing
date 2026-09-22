# 59. Recursion-Based Problems

## Core pattern
Identify the smallest valid input, define the recursive reduction, and prove that the reduction reaches the base case.

## Complete example: generate subsets
~~~c
#include <stdio.h>
#define N 3

void subsets(const int a[N], int i, int chosen[N]) {
    if (i == N) {
        putchar('{');
        for (int j=0;j<N;j++) if(chosen[j]) printf(" %d",a[j]);
        puts(" }");
        return;
    }
    chosen[i]=0; subsets(a,i+1,chosen);
    chosen[i]=1; subsets(a,i+1,chosen);
}

int main(void) {
    int a[N]={1,2,3}, chosen[N]={0};
    subsets(a,0,chosen);
}
~~~

## Complexity
There are 2^n subsets, so generation requires O(n 2^n) output work and O(n) recursion depth.

## Other important problems
Permutations, combinations, Tower of Hanoi, merge sort, quicksort, tree traversals, maze solving, N-Queens, and backtracking search.

## Practice
For each problem, state the recurrence, base case, depth, and time/space complexity.