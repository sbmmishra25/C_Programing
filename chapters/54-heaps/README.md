# 54. Heaps

## Concept
A binary heap is a complete binary tree represented compactly in an array. In a min-heap, each parent is <= its children.

## Array formulas
For zero-based index i: parent=(i-1)/2 for i>0; left=2*i+1; right=2*i+2.

## Complete min-heap operations
~~~c
#include <stdio.h>
#define CAP 32

typedef struct { int a[CAP]; size_t n; } Heap;

void swap(int *a,int *b){int t=*a;*a=*b;*b=t;}
int push(Heap *h,int x){
    if(h->n==CAP)return 0;
    size_t i=h->n++; h->a[i]=x;
    while(i>0){size_t p=(i-1)/2;if(h->a[p]<=h->a[i])break;swap(&h->a[p],&h->a[i]);i=p;}
    return 1;
}
int pop_min(Heap *h,int *out){
    if(!h->n||!out)return 0;
    *out=h->a[0];h->a[0]=h->a[--h->n];
    size_t i=0;
    for(;;){size_t l=2*i+1,r=l+1,s=i;
        if(l<h->n&&h->a[l]<h->a[s])s=l;
        if(r<h->n&&h->a[r]<h->a[s])s=r;
        if(s==i)break;swap(&h->a[i],&h->a[s]);i=s;}
    return 1;
}
int main(void){Heap h={0};int x;int a[]={7,2,9,1,5};for(size_t i=0;i<5;i++)push(&h,a[i]);while(pop_min(&h,&x))printf("%d ",x);putchar('\n');}
~~~

## Complexity
Push/pop O(log n); peek O(1); build-heap can be O(n). Heapsort is O(n log n).

## Applications
Priority queues, scheduling, Dijkstra's algorithm, top-k selection, and heapsort.

## Practice
Implement max-heap, heapify, heapsort, and a priority queue with dynamic capacity.