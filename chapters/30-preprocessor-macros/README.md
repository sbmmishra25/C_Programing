# 30. Preprocessor & Macros

## Definition
The preprocessor transforms source text before the compiler parses it. It handles directives such as include, define, if, elif, else, endif, and undef.

## Function-like macros
~~~c
#include <stdio.h>

#define SQUARE(x) ((x) * (x))
#define ARRAY_LEN(a) (sizeof(a) / sizeof((a)[0]))

int main(void) {
    int a[] = {1,2,3,4};
    printf("square=%d length=%zu\n", SQUARE(5), ARRAY_LEN(a));
    return 0;
}
~~~

Parentheses reduce precedence surprises, but macros still perform textual substitution. SQUARE(i++) is unsafe because its argument may be evaluated more than once.

## Conditional compilation
~~~c
#ifdef DEBUG
puts("debug build");
#endif
~~~
Prefer compiler flags such as -DDEBUG rather than editing source for every build configuration.

## Macro vs inline function
Use an inline function when type checking and single evaluation matter. Use macros when compile-time token manipulation, conditional compilation, or generic preprocessor behavior is actually required.

## Common mistakes
Missing parentheses, multiple evaluation, accidental name collisions, macros that leak declarations, and excessive macro use that makes debugging difficult.

## Practice
Create safe min/max macros, a logging macro, feature flags, include guards, and compare each with an inline-function alternative.