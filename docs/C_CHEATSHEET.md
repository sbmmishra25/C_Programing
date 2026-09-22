# C Programming Cheatsheet

## Core skeleton

```c
#include <stdio.h>

int main(void) {
    printf("Hello, C!\n");
    return 0;
}
```

## Common format specifiers

- `%d` — int
- `%u` — unsigned int
- `%ld` — long
- `%lld` — long long
- `%f` — floating-point output
- `%c` — char
- `%s` — null-terminated string
- `%zu` — size_t
- `%p` — pointer (with a `void *` conversion)

## Pointer rule

Pointer arithmetic is defined within an array object (including the one-past-end position for pointer comparison/arithmetic constraints). It is not a general integer-address arithmetic system.

## Dynamic allocation

```c
int *p = malloc(n * sizeof *p);
if (!p) { /* handle allocation failure */ }
...
free(p);
p = NULL;
```

For resizing, use a temporary pointer with `realloc` so the original allocation is not lost when reallocation fails.

## Strong compile flags

```bash
cc -std=c17 -Wall -Wextra -Wpedantic -O2 file.c -o app
```
