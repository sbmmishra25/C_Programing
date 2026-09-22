# 08. Operators

## 1. Major operator groups
Arithmetic: `+`, `-`, `*`, `/`, `%`

Relational/equality: `<`, `<=`, `>`, `>=`, `==`, `!=`

Logical: `&&`, `||`, `!`

Bitwise: `&`, `|`, `^`, `~`, `<<`, `>>`

Assignment: `=`, `+=`, `-=`, `*=`, `/=`, etc.

Other important operators include `?:`, `sizeof`, address-of `&`, dereference `*`, member access `.` and `->`.

## 2. Short-circuit evaluation
```c
if (ptr != NULL && *ptr > 0) {
    puts("positive");
}
```

The second operand is evaluated only if the first operand permits it. This can protect a dereference.

## 3. Arithmetic example
```c
#include <stdio.h>

int main(void) {
    int a = 17;
    int b = 5;

    printf("sum = %d\n", a + b);
    printf("division = %d\n", a / b);
    printf("remainder = %d\n", a % b);
    return 0;
}
```

Output:
```
sum = 22
division = 3
remainder = 2
```

## 4. Precedence
Prefer parentheses when an expression is not immediately obvious:
```c
int result = (a + b) * c;
```

## Common mistakes
Confusing `&&` with `&`, `||` with `|`, `=` with `==`, dividing by zero, and writing expressions with difficult-to-reason-about side effects.