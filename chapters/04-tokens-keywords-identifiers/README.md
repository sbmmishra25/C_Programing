# 04. Tokens, Keywords & Identifiers

## 1. Tokens
C source is made from lexical elements including identifiers, keywords, constants/literals, string literals, operators and punctuators.

Example:
```c
int total = price + 10;
```

Tokens include:
- `int` — keyword
- `total`, `price` — identifiers
- `=`, `+` — operators
- `10` — integer constant
- `; ` — punctuator

## 2. Keywords
Examples include `if`, `else`, `for`, `while`, `return`, `struct`, `typedef`, `static`, `const` and `sizeof`.

A keyword cannot be used as an ordinary identifier.

## 3. Identifier rules
An identifier:
- may contain letters, digits and underscores;
- cannot begin with a digit;
- is case-sensitive;
- cannot be a keyword.

Valid:
```c
int student_count;
int _index2;
int totalMarks;
```

Invalid:
```c
int 2value;
int total marks;
int for;
```

## 4. Character versus string literal
```c
char c = 'A';
const char *s = "A";
```

`'A'` is a character constant; `"A"` is a string literal containing a terminating null character.

## Complete example
```c
#include <stdio.h>

int main(void) {
    int student_count = 42;
    char grade = 'A';

    printf("Students: %d\n", student_count);
    printf("Grade: %c\n", grade);
    return 0;
}
```

## Practice
Classify every token in five small statements and identify lexical errors before compiling.