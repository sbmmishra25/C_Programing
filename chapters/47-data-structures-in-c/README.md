# 47. Data Structures in C

## Concept
A data structure organizes data and defines operations plus invariants. In C, structures, pointers, arrays, and dynamic allocation are combined to implement custom structures.

## Example: dynamic vector
~~~c
#include <stdio.h>
#include <stdlib.h>
#include <stddef.h>

typedef struct {
    int *data;
    size_t size, capacity;
} Vector;

void vector_free(Vector *v) { free(v->data); *v = (Vector){0}; }

int vector_push(Vector *v, int x) {
    if (v->size == v->capacity) {
        size_t cap = v->capacity ? v->capacity * 2 : 4;
        if (cap > SIZE_MAX / sizeof *v->data) return 0;
        int *p = realloc(v->data, cap * sizeof *p);
        if (!p) return 0;
        v->data = p; v->capacity = cap;
    }
    v->data[v->size++] = x;
    return 1;
}

int main(void) {
    Vector v = {0};
    for (int i=0;i<10;i++) if (!vector_push(&v,i*i)) return 1;
    for (size_t i=0;i<v.size;i++) printf("%d ",v.data[i]);
    putchar('\n');
    vector_free(&v);
}
~~~

## Invariants
size <= capacity; data is NULL when capacity is zero; ownership belongs to Vector.

## Complexity
Amortized push is O(1), worst-case resize O(n), indexed access O(1).

## Practice
Implement linked lists, stacks, queues, trees, heaps, hash tables, and graph representations while documenting invariants and ownership.