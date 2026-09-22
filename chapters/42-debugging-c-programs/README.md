# 42. Debugging C Programs

## Workflow
Reproduce -> minimize -> compile with warnings -> use sanitizers -> inspect with a debugger -> fix root cause -> add a regression test.

## Recommended build
~~~sh
cc -std=c17 -Wall -Wextra -Wpedantic -g -fsanitize=address,undefined program.c -o program
~~~

## Complete buggy example
~~~c
#include <stdio.h>

int main(void) {
    int a[3] = {10,20,30};
    for (int i = 0; i <= 3; ++i)
        printf("%d\n", a[i]);
    return 0;
}
~~~
The condition must be i < 3. AddressSanitizer can detect the out-of-bounds access.

## Debugger skills
Learn breakpoints, stepping, watchpoints, stack frames, backtraces, and expression inspection. Exact commands depend on the debugger.

## Practice
Diagnose use-after-free, leaks, uninitialized reads, invalid format strings, infinite loops, and pointer arithmetic defects.