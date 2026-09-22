# 51. Circular Queues

## Concept
A circular queue treats a fixed array as a ring. Front and rear wrap using modulo, avoiding the shifting cost of a simple array queue.

## Complete implementation
~~~c
#include <stdio.h>
#define CAP 5

typedef struct { int a[CAP]; size_t front, size; } CQueue;

int enqueue(CQueue *q, int x) {
    if (q->size == CAP) return 0;
    size_t rear = (q->front + q->size) % CAP;
    q->a[rear] = x; ++q->size;
    return 1;
}
int dequeue(CQueue *q, int *out) {
    if (!q->size || !out) return 0;
    *out = q->a[q->front];
    q->front = (q->front + 1) % CAP;
    --q->size;
    return 1;
}
int main(void) {
    CQueue q = {0}; int x;
    for (int i=1;i<=5;i++) enqueue(&q,i);
    dequeue(&q,&x); dequeue(&q,&x);
    enqueue(&q,6); enqueue(&q,7);
    while (dequeue(&q,&x)) printf("%d ",x);
    putchar('\n');
}
~~~

## Invariant
0 <= size <= CAP. The logical rear is (front + size) % CAP. This avoids ambiguity between empty and full states.

## Complexity
Enqueue and dequeue are O(1), with O(CAP) storage.

## Practice
Implement a dynamically growing circular queue and use one for a BFS traversal.