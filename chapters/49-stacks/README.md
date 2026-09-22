# 49. Stacks

## Concept
A stack is LIFO: last in, first out. Operations are push, pop, peek, and is_empty.

## Array implementation
~~~c
#include <stdio.h>
#define CAP 8

typedef struct { int a[CAP]; size_t top; } Stack;

int push(Stack *s, int x) {
    if (s->top == CAP) return 0;
    s->a[s->top++] = x;
    return 1;
}
int pop(Stack *s, int *out) {
    if (s->top == 0 || !out) return 0;
    *out = s->a[--s->top];
    return 1;
}

int main(void) {
    Stack s = {0}; int x;
    push(&s,10); push(&s,20);
    while (pop(&s,&x)) printf("%d ",x);
    putchar('\n');
}
~~~

## Complexity
Push/pop/peek are O(1). Array storage is O(capacity); a linked stack uses O(n) nodes.

## Applications
Function-call stacks, expression evaluation, parentheses matching, DFS, undo operations, and backtracking.

## Practice
Implement infix-to-postfix conversion, postfix evaluation, balanced parentheses, and a dynamic stack.