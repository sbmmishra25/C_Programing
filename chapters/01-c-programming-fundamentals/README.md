# 01. C Programming Fundamentals

## 1. Concept
C is a compiled, procedural, general-purpose language designed for efficient systems and application programming. It gives direct control over memory and data representation while remaining portable across many platforms.

### Why learn C?
C is used in operating systems, embedded systems, compilers, networking software, databases, device software, and performance-sensitive applications. Many higher-level languages and libraries are implemented partly in C.

## 2. First program
```c
#include <stdio.h>

int main(void) {
    printf("Hello, C!\n");
    return 0;
}
```

### Explanation
- `#include <stdio.h>` makes the declaration of `printf` available.
- `main` is the entry point of a hosted C program.
- `printf` writes formatted output to standard output.
- `return 0` indicates successful termination to the environment.

## 3. Variables and expressions
```c
#include <stdio.h>

int main(void) {
    int a = 15;
    int b = 4;
    int sum = a + b;
    int remainder = a % b;

    printf("sum = %d\n", sum);
    printf("remainder = %d\n", remainder);
    return 0;
}
```

Output:
```
sum = 19
remainder = 3
```

## 4. Program-development cycle
1. Write source code.
2. Preprocess included headers/macros.
3. Compile and diagnose errors/warnings.
4. Link object files and libraries.
5. Execute.
6. Test boundary cases.
7. Debug and refactor.

Compile with:
```bash
cc -std=c17 -Wall -Wextra -Wpedantic program.c -o program
```

## 5. Important rules
- Local automatic variables are not automatically initialized.
- C array indexing starts at zero.
- Integer division discards the fractional part.
- Compiler warnings should be treated seriously.
- C performs no automatic array-bounds checking.

## 6. Practice
1. Read two integers and print sum, difference, product and quotient.
2. Convert Celsius to Fahrenheit.
3. Calculate simple interest.
4. Find the largest of three integers.
5. Explain source code, object code, executable, compiler and linker.

## Common mistakes
Using `void main()`, forgetting semicolons, using an uninitialized variable, using the wrong `printf` format, and ignoring warnings.

## Complexity
A constant-size arithmetic program is O(1) time and O(1) auxiliary space.