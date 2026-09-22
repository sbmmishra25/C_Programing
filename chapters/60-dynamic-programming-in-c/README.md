# 60. Dynamic Programming in C

## Concept
Dynamic programming (DP) solves overlapping subproblems with optimal substructure by storing results instead of recomputing them.

## Complete example: Fibonacci
~~~c
#include <stdio.h>
#include <stdlib.h>

unsigned long long fib(size_t n) {
    if (n < 2) return n;
    unsigned long long *dp = malloc((n+1) * sizeof *dp);
    if (!dp) return 0;
    dp[0]=0; dp[1]=1;
    for(size_t i=2;i<=n;i++) dp[i]=dp[i-1]+dp[i-2];
    unsigned long long ans=dp[n];
    free(dp);
    return ans;
}
int main(void){printf("%llu\n",fib(20));}
~~~

## DP recipe
1. Define the state.
2. Write the transition.
3. Set base cases.
4. Choose memoization or tabulation.
5. Determine iteration order.
6. Optimize memory when only a small window of states is needed.

## Major problems
0/1 knapsack, unbounded knapsack, coin change, LIS, LCS, edit distance, matrix-chain multiplication, interval DP, grid DP, subset sum, and digit DP.

## Complexity
A correct DP generally changes exponential recomputation into polynomial state-count × transition-cost work. Always state both time and memory.

## Practice
Implement top-down and bottom-up Fibonacci, 0/1 knapsack, LCS, LIS, coin change, and edit distance.