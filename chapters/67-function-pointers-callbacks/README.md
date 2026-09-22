# 67. Function Pointers & Callbacks

## Concept
A callback is a function supplied to another function so that the callee can invoke caller-defined behavior.

## Complete example
~~~c
#include <stdio.h>
#include <stddef.h>

typedef void (*VisitFn)(int value, void *ctx);

void visit_array(const int *a,size_t n,VisitFn visit,void *ctx){
    if(!visit)return;
    for(size_t i=0;i<n;i++) visit(a[i],ctx);
}
void print_value(int value,void *ctx){
    const char *label=ctx;
    printf("%s%d\n",label,value);
}
int main(void){
    int a[]={2,4,6};
    visit_array(a,3,print_value,"value=");
}
~~~

## Context pointers
void *ctx lets the callback carry state without global variables. The API must guarantee that ctx remains valid for every callback invocation.

## Applications
qsort comparators, event systems, GUI callbacks, generic containers, parsers, and plugin interfaces.

## Common mistakes
Incompatible callback signatures, invalid context lifetime, calling NULL callbacks, and hidden ownership assumptions.

## Practice
Implement filter/map/reduce-like functions for arrays and a command dispatcher using callback tables.