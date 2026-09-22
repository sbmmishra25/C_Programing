# 09. Type Conversion & Casting

## 1. Implicit conversion
C converts operands according to its type rules.

```c
int a = 5;
int b = 2;
double x = a / b;
```

Here `a / b` is integer division first, so `x` becomes `2.0`.

## 2. Explicit cast
```c
double x = (double)a / b;
```

Now the result is `2.5`.

## Complete example
```c
#include <stdio.h>

int main(void) {
    int total = 7;
    int count = 2;

    printf("integer average = %d\n", total / count);
    printf("real average = %.2f\n", (double)total / count);
    return 0;
}
```

Output:
```
integer average = 3
real average = 3.50
```

## 3. Narrowing
```c
double value = 123.987;
int n = (int)value;
```

The fractional part is discarded during floating-to-integer conversion when the result is representable.

## 4. Pointer casts
Do not cast pointers simply to silence a warning. Alignment, object type, lifetime, aliasing and representation rules still apply.

## Common mistakes
Casting after integer division, assuming a cast prevents overflow, mixing signed and unsigned types without analysis, and using pointer casts as a universal solution.

## Practice
Predict the results of mixed `int`, `unsigned`, `float`, and `double` expressions before compiling them.