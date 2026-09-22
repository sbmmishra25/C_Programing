# 34. Command-Line Arguments

## Concept
A hosted C program may define main as int main(void) or int main(int argc, char *argv[]). argc counts arguments and argv points to strings.

## Complete example
~~~c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    if (argc != 3) {
        fprintf(stderr, "Usage: %s a b\n", argv[0]);
        return 2;
    }

    char *end1, *end2;
    long a = strtol(argv[1], &end1, 10);
    long b = strtol(argv[2], &end2, 10);

    if (*end1 || *end2) {
        fprintf(stderr, "Both arguments must be integers.\n");
        return 2;
    }

    printf("%ld\n", a + b);
    return 0;
}
~~~

## Important notes
argv strings are null-terminated. Validate conversion results rather than blindly using atoi; strtol provides an end pointer and error handling.

## Practice
Write command-line programs for calculator operations, file statistics, sorting numbers, and configuration flags.