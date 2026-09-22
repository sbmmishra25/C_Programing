# 19. Pointers: Complete Introduction

## Definition
A pointer is an object whose value can designate another object or function, subject to C's pointer rules. & obtains an object's address and * dereferences a valid pointer.

## Complete example
~~~c
#include <stdio.h>

int main(void) {
    int value = 42;
    int *p = &value;

    printf("value=%d\n", value);
    printf("*p=%d\n", *p);
    printf("address=%p\n", (void *)p);

    *p = 99;
    printf("after modification=%d\n", value);
    return 0;
}
~~~

## Pointer states
A pointer can be null, designate a live object, be one-past an array for limited operations, or be invalid/dangling. Only a valid pointer to a live object may be dereferenced.

## const and pointers
const int *p prevents modification of the int through p. int *const p prevents reassignment of p. const int *const p prevents both.

## Pointer-to-pointer
int ** is useful when a function must change the caller's pointer, for example when an allocation function stores a newly allocated address into an output parameter.

## Common mistakes
Dereferencing null or uninitialized pointers, use-after-free, returning addresses of dead locals, invalid casts, and out-of-bounds pointer arithmetic.

## Practice
Swap integers through pointers, find an array maximum through a pointer, allocate an object through an output parameter, and implement a safe linked-list insertion.