# 44. Modular Programming

## Concept
Modular programming separates cohesive responsibilities behind narrow interfaces. Good modules minimize coupling and hide implementation details.

## Opaque API
~~~c
/* vector.h */
#ifndef VECTOR_H
#define VECTOR_H
#include <stddef.h>
typedef struct Vector Vector;
Vector *vector_create(void);
void vector_destroy(Vector *);
int vector_push(Vector *, int);
size_t vector_size(const Vector *);
#endif
~~~
The incomplete struct prevents clients from depending on internal representation.

## Design checklist
Document ownership, mutation, error returns, thread-safety assumptions, complexity, and valid input ranges.

## Practice
Split a student-record application into input, model, storage, and reporting modules, with a test module for the public API.