# 28. typedef

## Definition
typedef creates an alias for an existing type; it does not create a distinct type.

## Complete example
~~~c
#include <stdio.h>
#include <stdint.h>

typedef uint32_t UserId;

typedef struct {
    UserId id;
    const char *name;
} User;

typedef int (*CompareInt)(int, int);

int compare_int(int a, int b) {
    return (a > b) - (a < b);
}

int main(void) {
    User u = {42u, "Ravi"};
    CompareInt cmp = compare_int;
    printf("id=%u name=%s compare=%d\n",
           u.id, u.name, cmp(4, 9));
    return 0;
}
~~~

## Good uses
typedef improves readability for structures, callback types, fixed-width integer aliases, and opaque handles. Keep aliases semantically clear; hiding pointer types can make declarations harder to read.

## Common mistakes
Believing typedef creates a new incompatible type, hiding ownership in a pointer alias, or creating confusing chains of aliases.

## Practice
Define aliases for matrices, callbacks, handles, and linked-list nodes. Compare an alias with a struct tag and explain the difference.