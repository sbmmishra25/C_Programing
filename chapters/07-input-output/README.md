# 07. Input & Output

## 1. Standard streams
C provides `stdin`, `stdout`, and `stderr`.

Output:
```c
printf("Value = %d\n", 42);
fprintf(stderr, "Diagnostic message\n");
```

## 2. Safe line input
For text input, `fgets` is usually easier to bound safely than an unrestricted `scanf("%s", ...)`.

```c
#include <stdio.h>

int main(void) {
    char name[50];

    printf("Enter name: ");
    if (fgets(name, sizeof name, stdin) == NULL) {
        fprintf(stderr, "Input failed\n");
        return 1;
    }

    printf("Hello, %s", name);
    return 0;
}
```

## 3. Formatted input
If using `scanf`, check its return value and constrain string widths:
```c
int age;
if (scanf("%d", &age) != 1) {
    fprintf(stderr, "Invalid integer\n");
    return 1;
}
```

## 4. Output formatting
```c
printf("%d\n", 42);
printf("%.2f\n", 3.14159);
printf("%zu\n", sizeof(int));
printf("%s\n", "C");
```

## Common mistakes
Wrong format specifiers, unchecked input, buffer overflow, and mixing `scanf` and `fgets` without understanding buffered input.

## Practice
Write a menu that reads a complete line, validates it, and performs an operation.