# 68. C Libraries & Reusable APIs

## Concept
A reusable C library separates public contracts from private implementation and provides predictable naming, error handling, ownership, and build integration.

## API example
~~~c
/* buffer.h */
#ifndef BUFFER_H
#define BUFFER_H
#include <stddef.h>
typedef struct Buffer Buffer;
Buffer *buffer_create(size_t capacity);
void buffer_destroy(Buffer *);
int buffer_append(Buffer *, const void *, size_t);
const unsigned char *buffer_data(const Buffer *);
size_t buffer_size(const Buffer *);
#endif
~~~

## API design rules
Use opaque types when representation should remain private. Prefix public symbols to reduce collisions. Document ownership, thread safety, nullability, error reporting, complexity, and lifetime.

## Static library
A typical Unix-like workflow is:
~~~sh
cc -c buffer.c
ar rcs libbuffer.a buffer.o
cc main.c -L. -lbuffer -o app
~~~
Exact commands vary by platform.

## Practice
Create a reusable vector or string library with tests, documentation, semantic versioning, and a stable public header.