# 62. Competitive Programming Patterns

## Core workflow
Read constraints first, derive a target complexity, choose a representation, handle input/output efficiently, then test edge cases.

## Essential patterns
Prefix sums, difference arrays, two pointers, sliding window, binary search on answer, sorting + greedy, hash maps, monotonic stack/queue, BFS/DFS, shortest paths, union-find, heaps, coordinate compression, bitmasking, and DP.

## Complete example: prefix sums
~~~c
#include <stdio.h>
#include <stddef.h>

int main(void){
    int a[]={2,4,1,7,3};
    size_t n=sizeof a/sizeof a[0];
    long long pref[6]={0};
    for(size_t i=0;i<n;i++) pref[i+1]=pref[i]+a[i];

    size_t l=1,r=4; /* 1-based inclusive */
    printf("%lld\n",pref[r]-pref[l-1]);
}
~~~

## Constraint thinking
n around 10^2 may permit O(n²); n around 10^5 usually calls for O(n log n) or O(n); n around 10^9 often requires logarithmic, mathematical, or binary-search reasoning. These are heuristics, not universal rules.

## Practice
Solve range-sum queries, longest subarray, interval scheduling, kth-element problems, DSU connectivity, and binary-search-on-answer problems.