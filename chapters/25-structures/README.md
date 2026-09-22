# 25. Structures

## Definition
A structure groups named members, potentially of different types, into one object. It is the main C mechanism for defining records and nodes.

## Complete example
~~~c
#include <stdio.h>

typedef struct {
    unsigned id;
    char name[32];
    double marks;
} Student;

void print_student(const Student *s) {
    printf("id=%u name=%s marks=%.2f\n", s->id, s->name, s->marks);
}

int main(void) {
    Student s = {101, "Asha", 91.5};
    print_student(&s);

    s.marks += 2.0;
    print_student(&s);
    return 0;
}
~~~

## Layout and padding
Members appear in declaration order, but implementations may insert padding for alignment. Therefore sizeof(struct) can exceed the sum of member sizes.

## Pointer to structure
Use p->member when p is a pointer to a structure; it is equivalent to (*p).member.

## Self-referential structures
A structure cannot contain itself by value, but it can contain a pointer to its own type:
~~~c
struct Node { int value; struct Node *next; };
~~~
This forms the basis of linked lists and trees.

## Common mistakes
Assuming no padding, comparing structures with ==, returning pointers to dead structures, and copying structures that contain pointers without understanding shallow-copy ownership.

## Practice
Define Employee, Book, Date, Matrix, and linked-list node structures. Implement sorting an array of structures with qsort.