# 03. Structure of a C Program

## 1. Basic structure
A typical hosted C program contains preprocessing directives, declarations/definitions, functions, statements and expressions.

```c
#include <stdio.h>

int add(int a, int b);

int main(void) {
    int result = add(10, 20);
    printf("Result = %d\n", result);
    return 0;
}

int add(int a, int b) {
    return a + b;
}
```

Output:
```
Result = 30
```

## 2. Components
- Header inclusion: supplies declarations such as `printf`.
- Function prototype: tells the compiler the interface of `add`.
- `main`: program entry point.
- Local declaration: `int result`.
- Function call: `add(10, 20)`.
- Return statement: terminates the function and supplies its result.

## 3. Comments
```c
// Single-line comment

/*
   Multi-line comment
*/
```

Comments are ignored by the compiler after preprocessing and should explain intent, not merely restate syntax.

## 4. Blocks and scope
```c
#include <stdio.h>

int main(void) {
    int x = 10;

    {
        int y = 20;
        printf("%d %d\n", x, y);
    }

    printf("%d\n", x);
    return 0;
}
```

`y` is declared in the inner block and is not visible after that block.

## Common mistakes
- Missing prototypes.
- Mismatching declaration and definition.
- Using undeclared identifiers.
- Writing `void main()` for a hosted program.
- Confusing declaration with definition.

## Practice
Rewrite one large `main` function into three focused functions and create a header for their prototypes.