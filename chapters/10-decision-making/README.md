# 10. Decision Making

## 1. if/else
```c
if (marks >= 90) {
    puts("A");
} else if (marks >= 75) {
    puts("B");
} else {
    puts("C or below");
}
```

Use braces consistently to make control flow obvious.

## 2. Complete grading program
```c
#include <stdio.h>

int main(void) {
    int marks;

    printf("Enter marks (0-100): ");
    if (scanf("%d", &marks) != 1 || marks < 0 || marks > 100) {
        fprintf(stderr, "Invalid marks\n");
        return 1;
    }

    if (marks >= 90)
        puts("Grade A");
    else if (marks >= 75)
        puts("Grade B");
    else if (marks >= 60)
        puts("Grade C");
    else if (marks >= 40)
        puts("Grade D");
    else
        puts("Grade F");

    return 0;
}
```

## 3. switch
```c
switch (choice) {
    case 1:
        puts("Add");
        break;
    case 2:
        puts("Delete");
        break;
    default:
        puts("Unknown choice");
        break;
}
```

Without a control-flow exit such as `break`, execution can fall through into the next case intentionally or accidentally.

## Practice
Implement leap-year checking, maximum of three values, calculator menu, and a character classifier.

## Common mistakes
Accidental assignment, missing `break`, invalid ranges, and deeply nested conditions that could be simplified.