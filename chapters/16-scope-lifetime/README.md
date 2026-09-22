# 16. Scope & Lifetime

## Definition
Scope describes where an identifier is visible in source code. Lifetime describes how long an object exists during execution.

## Main scopes
C has file scope, block scope, function scope for labels, and function-prototype scope. Scope is primarily a source-language concept; lifetime is an execution-time object property.

## Complete example
~~~c
#include <stdio.h>

int global_value = 10;

void demo(void) {
    static int persistent = 0;
    int local = 20;
    ++persistent;

    printf("global=%d local=%d persistent=%d\n",
           global_value, local, persistent);

    {
        int local = 99;
        printf("inner local=%d\n", local);
    }
}

int main(void) {
    demo();
    demo();
    return 0;
}
~~~

The inner local shadows the outer local. The static object persists between calls; each automatic local has a separate lifetime.

## Lifetime categories
C objects can have static, thread, automatic, or allocated storage duration. An allocated object exists from successful allocation until it is released.

## Dangling pointers
A pointer becomes invalid for dereference when the designated object's lifetime ends. Returning the address of an automatic local is therefore invalid.

## Common mistakes
Confusing scope with lifetime, accidental shadowing, use-after-lifetime, and assuming an unchanged address means an object is still alive.

## Practice
Trace nested scopes, identify lifetime categories, and design an API that returns data without exposing a pointer to a dead local.