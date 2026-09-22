# 65. Low-Level Pointers

## Concepts
Advanced pointer work includes void*, pointer-to-pointer, pointer-to-array, function pointers, alignment, object representation, and byte-wise access through character types.

## Complete example: pointer-to-array
~~~c
#include <stdio.h>

void print_matrix(size_t rows, const int (*a)[3]) {
    for(size_t i=0;i<rows;i++){
        for(size_t j=0;j<3;j++) printf("%d ",a[i][j]);
        putchar('\n');
    }
}
int main(void){
    int a[2][3]={{1,2,3},{4,5,6}};
    print_matrix(2,a);
}
~~~

## Alignment
Objects have alignment requirements. Do not cast an arbitrary byte address to a stricter-aligned pointer and dereference it. malloc returns storage suitably aligned for any object type whose size/alignment requirements it can satisfy.

## Object representation
Character types can inspect the bytes of an object's representation. This does not mean every byte sequence is a valid value for every type.

## Common mistakes
Misaligned access, strict-aliasing violations, invalid pointer arithmetic, integer-to-pointer assumptions, and treating addresses as portable integers.

## Practice
Implement byte dumps using unsigned char, safely inspect structure padding, and explain pointer-to-pointer versus pointer-to-array declarations.