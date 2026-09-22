# 33. File Handling

## Concept
ISO C provides streams through FILE* and functions such as fopen, fclose, fread, fwrite, fgets, fputs, fprintf, fscanf, fseek, ftell, and fflush.

## Complete example: text file
~~~c
#include <stdio.h>

int main(void) {
    const char *name = "students.txt";
    FILE *fp = fopen(name, "w");
    if (!fp) {
        perror("fopen");
        return 1;
    }

    if (fprintf(fp, "101 Asha 91.5\n102 Ravi 88.0\n") < 0) {
        perror("write");
        fclose(fp);
        return 1;
    }
    if (fclose(fp) != 0) {
        perror("fclose");
        return 1;
    }

    fp = fopen(name, "r");
    if (!fp) { perror("fopen"); return 1; }

    char line[128];
    while (fgets(line, sizeof line, fp))
        fputs(line, stdout);

    if (ferror(fp)) perror("read");
    fclose(fp);
    return 0;
}
~~~

## Binary I/O
fread/fwrite operate on bytes/objects. Binary representation is not automatically portable between different architectures or C implementations because of padding, endianness, type sizes, and representation.

## Common mistakes
Not checking fopen, using feof as the loop condition, failing to close files, assuming text/binary formats are universally identical, and ignoring short reads/writes.

## Complexity
Sequential processing is O(n) in file size; seeking depends on the stream and implementation.

## Practice
Build a CSV-like record reader, a binary record store, and a file-copy utility with complete error checks.