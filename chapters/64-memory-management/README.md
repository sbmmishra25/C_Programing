# 64. Memory Management

## Ownership model
For every dynamically allocated object, identify creator, owner, transfer rules, and destruction point.

## Complete safe-resize helper
~~~c
#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>

int resize_ints(int **p,size_t old_n,size_t new_n){
    (void)old_n;
    if(new_n > SIZE_MAX/sizeof **p) return 0;
    int *tmp=realloc(*p,new_n*sizeof **p);
    if(new_n && !tmp) return 0;
    *p=tmp;
    return 1;
}
int main(void){
    int *a=malloc(3*sizeof *a);
    if(!a)return 1;
    if(!resize_ints(&a,3,10)){free(a);return 1;}
    free(a);
}
~~~

## Defects to prevent
Leaks, double-free, use-after-free, invalid free, buffer overflow, allocation-size overflow, lifetime errors, and stale aliases.

## Tools
Use AddressSanitizer, UndefinedBehaviorSanitizer, Valgrind where available, static analyzers, and compiler warnings.

## Advanced concepts
Arena allocation, pools, reference counting, ownership-transfer APIs, alignment, flexible array members, and custom allocators.

## Practice
Implement an arena allocator and a reference-counted object, with tests for allocation failure and destruction order.