# 02. C History, Standards & Compilation

## 1. Concept
C evolved from early systems-programming languages at Bell Labs and became widely used because it combined low-level control with structured programming. Standardization made portable reasoning possible.

Important milestones include K&R C, ANSI C/C89, C99, C11, C17 and C23. Compiler support for newer revisions varies.

## 2. Translation pipeline
A useful model is:

`source.c → preprocessing → translation/compilation → object file → linking → executable`

For example:
```bash
cc -std=c17 -E main.c > main.i
cc -std=c17 -S main.c -o main.s
cc -std=c17 -c main.c -o main.o
cc main.o -o main
```

The exact intermediate commands and files are compiler-dependent, but the conceptual stages are useful.

## 3. Compilation example
Source:
```c
#include <stdio.h>

int square(int x) {
    return x * x;
}

int main(void) {
    printf("%d\n", square(7));
    return 0;
}
```

Output:
```
49
```

## 4. Compiler versus linker
The compiler translates each translation unit and diagnoses many language errors. The linker combines object files and libraries and resolves external references.

If `main.c` calls `square` but `square` is defined in `math.c`, both files can be compiled and then linked:
```bash
cc -std=c17 -Wall -Wextra -Wpedantic -c main.c
cc -std=c17 -Wall -Wextra -Wpedantic -c math.c
cc main.o math.o -o app
```

## 5. Standards versus extensions
A compiler may provide extensions beyond ISO C. Portable code should identify its target standard and avoid silently depending on compiler-specific behavior.

## Practice
- Compare C11 and C17 compilation modes.
- Inspect preprocessor output.
- Split a program into two source files and link it.
- Find one compiler warning and explain its cause.

## Common mistake
Assuming that code accepted by one compiler is automatically portable ISO C.

## Interview focus
Explain preprocessing, compilation, assembly/object generation, linking, and execution.