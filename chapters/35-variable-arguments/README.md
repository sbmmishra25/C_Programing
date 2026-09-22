# 35. Variable Arguments

## Concept
stdarg.h provides va_list, va_start, va_arg, va_copy, and va_end for functions whose final parameter is followed by an unspecified number of arguments.

## Complete example
~~~c
#include <stdio.h>
#include <stdarg.h>

double average(size_t count, ...) {
    va_list ap;
    va_start(ap, count);

    double sum = 0.0;
    for (size_t i = 0; i < count; ++i)
        sum += va_arg(ap, double);

    va_end(ap);
    return count ? sum / (double)count : 0.0;
}

int main(void) {
    printf("%.2f\n", average(4, 10.0, 20.0, 30.0, 40.0));
    return 0;
}
~~~

## Critical rule
The callee cannot know the number or types of variadic arguments automatically. The API must provide a contract, such as a count, format string, or sentinel. Default argument promotions apply: float becomes double and integer types narrower than int are promoted.

## Common mistakes
Using the wrong type in va_arg, missing va_end, relying on an invalid sentinel, and assuming the compiler can infer the argument count.

## Practice
Implement a variadic sum, a tagged logging function, and explain how printf's format string supplies type information.