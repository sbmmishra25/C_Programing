# 32. Conditional Compilation

## Concept
The preprocessor can include or exclude source text based on macros. This is useful for platform configuration, feature flags, debug builds, and header guards.

## Complete example
~~~c
#include <stdio.h>

int main(void) {
#ifdef DEBUG
    puts("debug build");
#else
    puts("release-style build");
#endif

#if defined(_WIN32)
    puts("Windows target macro detected");
#elif defined(__linux__)
    puts("Linux target macro detected");
#else
    puts("Other target");
#endif
    return 0;
}
~~~
Build debug with `cc -DDEBUG file.c -o app`.

## Important distinction
Conditional compilation happens before C compilation. It is different from a runtime if statement: excluded code is not compiled.

## Common mistakes
Unbalanced #if/#endif, feature macros with inconsistent meanings, testing compiler-specific macros without documentation, and maintaining too many build combinations.

## Practice
Create DEBUG logging, platform-specific includes, and feature toggles while keeping one portable fallback implementation.