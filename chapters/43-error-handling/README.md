# 43. Error Handling

## Concept
C commonly reports errors through return values, NULL, EOF, errno, and application-defined status codes. There is no built-in exception mechanism.

## Complete example
~~~c
#include <errno.h>
#include <stdio.h>
#include <string.h>

int main(void) {
    FILE *fp = fopen("missing.txt", "r");
    if (!fp) {
        fprintf(stderr, "open failed: %s\n", strerror(errno));
        return 1;
    }
    fclose(fp);
    return 0;
}
~~~

## Design principles
Check failures at API boundaries, clean up acquired resources exactly once, preserve useful diagnostics, and return a status that callers can act on.

errno should be examined when the failed API documents that it sets errno. A successful operation does not imply errno is zero.

## Practice
Design status codes for a file library, implement resource cleanup, and distinguish invalid input from system/resource failures.