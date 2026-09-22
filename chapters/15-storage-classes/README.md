# 15. Storage Classes

## Definition
Storage-class specifiers describe properties such as storage duration and linkage. Common specifiers include auto, static, extern, register, and the C11 _Thread_local specifier.

## Static local example
~~~c
#include <stdio.h>

static int file_calls = 0;

void counter(void) {
    static int local_count = 0;
    ++local_count;
    ++file_calls;
    printf("local=%d file=%d\n", local_count, file_calls);
}

int main(void) {
    counter();
    counter();
    counter();
    return 0;
}
~~~

The static local retains its value between calls. The file-scope static object has internal linkage, so another translation unit cannot refer to it through external linkage.

## extern
An extern declaration refers to a definition provided elsewhere. In multi-file projects, put declarations in headers and provide exactly one definition where appropriate.

## register
register is a historical optimization hint. Modern compilers normally choose registers automatically. An address cannot be taken for an object declared with register storage-class specifier.

## Key distinction
Scope, storage duration, and linkage are different. A block-scope static variable is visible only in its block but exists for the entire execution of the program.

## Practice
Create two source files using extern; compare automatic and static locals; investigate _Thread_local in a C11 program.