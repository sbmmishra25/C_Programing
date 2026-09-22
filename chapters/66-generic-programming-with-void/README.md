# 66. Generic Programming with void *

## Concept
void* can point to an object of any object type after appropriate conversion. It is the basis of generic C APIs such as qsort and callback-based containers.

## Complete example: generic swap
~~~c
#include <stdio.h>
#include <string.h>

void swap_bytes(void *a, void *b, size_t size) {
    unsigned char *pa=a, *pb=b;
    for(size_t i=0;i<size;i++){
        unsigned char t=pa[i]; pa[i]=pb[i]; pb[i]=t;
    }
}
int main(void){
    int a=10,b=20;
    swap_bytes(&a,&b,sizeof a);
    printf("%d %d\n",a,b);
}
~~~

## Contract
The API must know element size, alignment, lifetime, and any required comparator/destructor callback. void* does not carry this metadata.

## Common mistakes
Using the wrong size, violating alignment, treating arbitrary bytes as an incompatible typed object, and losing ownership information.

## Practice
Build a generic dynamic array with void*, element size, comparator, and destructor callback.