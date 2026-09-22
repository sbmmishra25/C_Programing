# 69. C11, C17 & C23 Features

## C11
C11 introduced standardized atomics, threads, _Generic, _Static_assert, _Alignas/_Alignof, _Thread_local, anonymous structures/unions, and other library/language improvements.

## C17
C17 is mainly a corrective revision of C11. It is important for modern portable C, but it intentionally added few headline language features.

## C23
C23 modernizes C with features including nullptr/nullptr_t, standard boolean keywords, binary integer constants, digit separators, attributes, improved enumeration support, and other language/library changes. Actual compiler support varies.

## Feature detection
~~~c
#include <stdio.h>
int main(void) {
#ifdef __STDC_VERSION__
    printf("STDC_VERSION=%ld\n", (long)__STDC_VERSION__);
#endif
}
~~~

Compile explicitly, for example: `cc -std=c17 -Wall -Wextra -Wpedantic file.c`. Test C23 with `-std=c23` only when your compiler supports it.

## Practice
Create a compatibility table for your compiler, compile representative C11/C17/C23 programs, and document unsupported features rather than silently relying on extensions.