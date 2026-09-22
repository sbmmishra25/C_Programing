# 06. Data Types

## 1. Fundamental types
Common C types include:
`char`, `short`, `int`, `long`, `long long`, `float`, `double`, `long double`, `_Bool` and `void`.

Exact sizes are implementation-dependent unless a fixed-width type is used.

## 2. Inspecting sizes
```c
#include <stdio.h>
#include <limits.h>

int main(void) {
    printf("char bits: %d\n", CHAR_BIT);
    printf("sizeof(char): %zu\n", sizeof(char));
    printf("sizeof(int): %zu\n", sizeof(int));
    printf("sizeof(double): %zu\n", sizeof(double));
    printf("int range: %d to %d\n", INT_MIN, INT_MAX);
    return 0;
}
```

Use `%zu` for `size_t`.

## 3. Fixed-width integers
```c
#include <stdint.h>

int32_t id = 1001;
uint64_t mask = 1ULL;
```

These are useful when a precise width is required and the implementation provides the requested type.

## 4. Arrays and pointers are derived types
```c
int values[5];
int *p = values;
```

A pointer is not an integer and an array is not a pointer, even though an array expression often converts to a pointer to its first element.

## Practice
Print sizes and limits from `<limits.h>` and compare platforms rather than assuming all machines use the same representation.