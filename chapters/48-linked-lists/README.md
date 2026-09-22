# 48. Linked Lists

## Concept
A singly linked list stores nodes connected by next pointers. It supports insertion/deletion without shifting contiguous elements, but indexed access is O(n).

## Complete implementation
~~~c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int value;
    struct Node *next;
} Node;

int push_front(Node **head, int value) {
    Node *n = malloc(sizeof *n);
    if (!n) return 0;
    n->value = value;
    n->next = *head;
    *head = n;
    return 1;
}

void print(const Node *p) {
    while (p) { printf("%d ", p->value); p = p->next; }
    putchar('\n');
}

void destroy(Node *p) {
    while (p) { Node *next = p->next; free(p); p = next; }
}

int main(void) {
    Node *head = NULL;
    for (int i=1;i<=5;i++) if (!push_front(&head,i)) { destroy(head); return 1; }
    print(head);
    destroy(head);
    return 0;
}
~~~

## Complexity
Push-front O(1); search O(n); deletion after a known predecessor O(1). Extra space is O(n).

## Variants
Doubly linked lists add prev pointers; circular lists connect the tail back to the head.

## Common mistakes
Losing the next pointer before free, dereferencing NULL, memory leaks, and failing to update head when deleting the first node.