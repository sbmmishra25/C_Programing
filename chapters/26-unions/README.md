# 26. Unions

## Definition
A union provides overlapping storage for its members. At most one member's stored representation should be treated as the active member according to the program's design and the applicable C rules.

## Complete example
~~~c
#include <stdio.h>
#include <string.h>

typedef enum { VALUE_INT, VALUE_DOUBLE, VALUE_TEXT } ValueKind;

typedef struct {
    ValueKind kind;
    union {
        int i;
        double d;
        char text[32];
    } data;
} Value;

int main(void) {
    Value v = {.kind = VALUE_INT, .data.i = 42};
    printf("int=%d\n", v.data.i);

    v.kind = VALUE_DOUBLE;
    v.data.d = 3.14;
    printf("double=%.2f\n", v.data.d);

    v.kind = VALUE_TEXT;
    strcpy(v.data.text, "C");
    printf("text=%s\n", v.data.text);
    return 0;
}
~~~

## Why unions are useful
Unions save storage when several alternative representations are mutually exclusive. They are common in tagged variants, protocol data, embedded systems, and interpreters.

## Important caution
Do not use a union as a generic license to reinterpret arbitrary object representations. Type-punning rules, effective type, representation bytes, and aliasing require careful treatment. memcpy is often the safer way to inspect object representation.

## Common mistakes
Reading an unintended member, forgetting the tag that identifies the active alternative, and assuming union size equals the largest member exactly without considering alignment.

## Practice
Build a tagged value type, an expression node, and a packet representation with explicit serialization/deserialization.