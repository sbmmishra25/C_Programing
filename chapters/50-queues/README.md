# 50. Queues

## Concept
A queue is FIFO: first in, first out. Core operations are enqueue and dequeue.

## Circular-buffer queue
~~~c
#include <stdio.h>
#define CAP 5

typedef struct {
    int a[CAP];
    size_t front, size;
} Queue;

int enqueue(Queue *q, int x) {
    if (q->size == CAP) return 0;
    size_t pos = (q->front + q->size) % CAP;
    q->a[pos] = x; ++q->size;
    return 1;
}
int dequeue(Queue *q, int *out) {
    if (!q->size || !out) return 0;
    *out = q->a[q->front];
    q->front = (q->front + 1) % CAP;
    --q->size;
    return 1;
}

int main(void) {
    Queue q = {0}; int x;
    enqueue(&q,1); enqueue(&q,2); enqueue(&q,3);
    while (dequeue(&q,&x)) printf("%d ",x);
    putchar('\n');
}
~~~

## Complexity
Enqueue and dequeue are O(1). A good queue implementation never shifts all elements on every dequeue.

## Applications
Scheduling, buffering, BFS, producer-consumer designs, and message pipelines.

## Practice
Implement a linked queue, priority queue, and BFS using a queue.