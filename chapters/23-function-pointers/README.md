# 23. Function Pointers

## Definition
A function pointer stores the address of a function and can be called through a compatible pointer type. It enables callbacks, dispatch tables, sorting comparators, and plugin-like interfaces.

## Complete example
~~~c
#include <stdio.h>

typedef int (*binary_op)(int, int);

int add(int a, int b) { return a + b; }
int multiply(int a, int b) { return a * b; }

int apply(binary_op op, int a, int b) {
    return op(a, b);
}

int main(void) {
    binary_op operations[] = {add, multiply};
    printf("add=%d\n", apply(operations[0], 3, 4));
    printf("multiply=%d\n", apply(operations[1], 3, 4));
    return 0;
}
~~~

## Type compatibility
The pointed-to function's return type and parameter types must be compatible with the function pointer type. Do not cast incompatible function pointers merely to silence a diagnostic.

## Callbacks
A callback API should specify when it is called, what arguments are valid, whether the callback may modify context, and how long the context pointer remains valid.

## Complexity
A function-pointer call itself is conceptually O(1); the callback's implementation determines the actual cost.

## Practice
Build a calculator dispatch table, a generic array traversal callback, and a command menu using function pointers.