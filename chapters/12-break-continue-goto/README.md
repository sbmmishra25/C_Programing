# 12. break, continue & goto

## Definition
break terminates the nearest loop or switch. continue skips the remainder of the current loop iteration. goto transfers control to a label in the same function.

## Complete example
~~~c
#include <stdio.h>

int main(void) {
    for (int i = 1; i <= 10; ++i) {
        if (i == 3) continue;
        if (i == 8) break;
        printf("%d ", i);
    }
    putchar('\n');

    int value = -1;
    if (value < 0) goto cleanup;

    printf("value = %d\n", value);

cleanup:
    puts("cleanup path reached");
    return 0;
}
~~~

## Output
The loop prints 1 2 4 5 6 7. The cleanup label is reached because value is negative.

## Structured cleanup
In C, goto can be useful for one cleanup path when several resources may have been acquired:
~~~c
int result = -1;
FILE *fp = fopen("data.txt", "r");
if (!fp) goto cleanup;

char *buf = malloc(1024);
if (!buf) goto close_file;

/* work */
result = 0;
free(buf);

close_file:
fclose(fp);
cleanup:
return result;
~~~
Each cleanup action must correspond to a resource that was actually acquired.

## Common mistakes
Using goto for ordinary branching, creating spaghetti control flow, forgetting that break affects only the nearest loop or switch, and using continue in a way that skips required progress.

## Complexity
These statements do not inherently change complexity; the surrounding algorithm determines it.

## Practice
Implement an early-exit search, a validation loop using continue, and a multi-resource cleanup routine.