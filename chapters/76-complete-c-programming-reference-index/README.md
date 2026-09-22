# 76. Complete C Programming Reference & Index

## Purpose
This chapter is the consolidated navigation point for the complete C curriculum. It connects fundamentals, language rules, memory, data structures, algorithms, systems programming, modern standards, debugging, interviews, exercises, and projects.

## 76-topic map
1–10: Fundamentals, standards, program structure, tokens, variables, types, I/O, operators, conversions, decisions.

11–20: Loops, control transfer, functions, recursion, storage classes, scope/lifetime, arrays, strings, pointers, pointer arithmetic.

21–30: Pointer/array and pointer/function relationships, function pointers, dynamic allocation, structures, unions, enums, typedef, bitwise programming, macros.

31–40: Headers, conditional compilation, files, CLI arguments, variadic functions, qualifiers, linkage, memory layout, stack/heap, behavior categories.

41–50: Integer pitfalls, debugging, error handling, modular/multi-file design, build systems, data structures, linked lists, stacks, queues.

51–60: Circular queues, trees, BSTs, heaps, hash tables, graphs, searching, sorting, recursion problems, dynamic programming.

61–70: Bit manipulation, competitive patterns, system-level concepts, memory management, low-level pointers, generic void*, callbacks, reusable libraries, C11/C17/C23, advanced C.

71–76: Interview questions, programming exercises, debugging exercises, mini-projects, advanced projects, consolidated reference.

## Compilation baseline
~~~sh
cc -std=c17 -Wall -Wextra -Wpedantic program.c -o program
~~~

For debugging:
~~~sh
cc -std=c17 -Wall -Wextra -Wpedantic -g -fsanitize=address,undefined program.c -o program
~~~

## Reference checklist
When studying any topic, verify:
- Definition and language rule
- Syntax
- Complete example
- Expected behavior
- Edge cases
- Undefined/implementation-defined behavior
- Ownership and lifetime
- Time/space complexity
- Common mistakes
- Tests
- Practice problem
- Advanced extension

## Final goal
A learner completing this repository should be able to write portable C, reason about memory and undefined behavior, implement major data structures and algorithms, build multi-file systems, use modern C standards appropriately, debug defects, and develop complete projects with tests and documentation.