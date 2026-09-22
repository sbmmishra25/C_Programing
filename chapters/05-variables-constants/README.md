# 05. Variables & Constants

## 1. Objects and variables
A variable is an object whose stored value can be changed through an appropriate lvalue.

```c
int age = 20;
double salary = 55000.0;
char grade = 'A';
```

Local automatic variables should be initialized before they are read.

## 2. const
```c
const double PI = 3.141592653589793;
```

The declaration prevents modification through that object expression. It does not mean every occurrence of the value is necessarily a compile-time constant.

## 3. enum constants
```c
enum { MAX_STUDENTS = 100 };
int students[MAX_STUDENTS];
```

Enumeration constants are useful for named integral values.

## 4. Complete example
```c
#include <stdio.h>

int main(void) {
    const double PI = 3.141592653589793;
    double radius = 5.0;
    double area = PI * radius * radius;

    printf("Radius = %.2f\n", radius);
    printf("Area = %.2f\n", area);
    return 0;
}
```

Output:
```
Radius = 5.00
Area = 78.54
```

## Common mistakes
- Reading an uninitialized local variable.
- Assuming `const` always means compile-time constant.
- Using macros when a typed constant or enum would be clearer.
- Shadowing an outer variable accidentally.

## Practice
Create a program using constants for tax rate, maximum capacity and conversion factors.