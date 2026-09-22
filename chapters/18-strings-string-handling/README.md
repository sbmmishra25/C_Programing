# 18. Strings & String Handling

## Definition
A C string is a contiguous character sequence terminated by a null character, '\0'. C has no built-in string object type.

## Complete example
~~~c
#include <stdio.h>
#include <string.h>

int main(void) {
    char first[32], last[32];

    if (scanf("%31s %31s", first, last) != 2) {
        fprintf(stderr, "Expected two words.\n");
        return 1;
    }

    char full[65];
    int written = snprintf(full, sizeof full, "%s %s", first, last);
    if (written < 0 || (size_t)written >= sizeof full) {
        fprintf(stderr, "Formatting failed or was truncated.\n");
        return 1;
    }

    printf("Name: %s\nLength: %zu\n", full, strlen(full));
    return 0;
}
~~~

## Important library functions
strlen measures a valid string; strcmp compares strings; memcpy copies non-overlapping storage; memmove permits overlap; snprintf provides bounded formatted construction. strcpy and strcat require the caller to guarantee destination capacity and are frequent sources of overflow.

## Input safety
Use a field width for scanf string input or prefer fgets for complete lines. fgets may retain the newline, which can be removed deliberately after checking whether it was read.

## Common mistakes
Missing null terminators, allocating one byte too few, buffer overflow, comparing strings with ==, and passing non-terminated character data to string functions.

## Complexity
Basic string scans are O(n), where n is the examined length.

## Practice
Implement reverse, palindrome, substring search, frequency counting, safe trimming, and a bounded string-copy routine with explicit capacity.