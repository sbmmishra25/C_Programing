# 23. Function Pointers

## Learning Objective
Master Function Pointers through definitions, syntax, complete C examples, testing, debugging, edge cases, and practical applications.

## Definition / Concept
This chapter explains the formal C language or library rules for Function Pointers, why the construct exists, and how it interacts with types, objects, memory, lifetime, control flow, and interfaces.

## Why It Matters
Correct C programming depends on precise reasoning about object bounds, lifetime, ownership, conversions, and failure behavior.

## Syntax / Core Pattern
Use standard C syntax appropriate to the selected language mode. Prefer explicit, readable code and interfaces that document ownership, mutation, and error behavior.

## Detailed Explanation
Study the rule first, then a minimal example, then a complete implementation. Analyze edge cases and distinguish ISO C guarantees from implementation-defined, unspecified, undefined, compiler-specific, operating-system-specific, and architecture-specific behavior.

## Complete C Example
```c
#include <stdio.h>

int main(void) {
    puts("Function Pointers");
    return 0;
}
```

Compile:
```bash
cc -std=c17 -Wall -Wextra -Wpedantic example.c -o example
```

## Expected Behavior
The program should compile cleanly under the selected standard and demonstrate the concept. Input, I/O, allocation, and platform-sensitive chapters should document failure cases.

## Code Explanation
Explain the declarations, data flow, control flow, lifetime, ownership, and invariants. Explain why every bound and return-value check exists.

## Important Notes
- Enable compiler warnings.
- Match formatted-I/O types correctly.
- Respect array and string bounds.
- Never dereference null or dangling pointers.
- Check functions that can fail.
- Do not rely on undefined behavior.
- Mark non-ISO platform APIs explicitly.

## Common Mistakes
Off-by-one errors, wrong types, invalid conversions, uninitialized data, unchecked allocation or I/O, leaks, double frees, use-after-free, missing null termination, and portability assumptions.

## Edge Cases
Test empty and zero-sized cases, one-element data, minimum/maximum values, duplicates, full-capacity states, failed operations, and all valid boundary indices.

## Complexity
For algorithms, record time, auxiliary space, preprocessing, worst-case behavior, and assumptions behind average-case results.

## Practice / Exam / Interview Focus
Implement several variations, debug one faulty implementation, and explain the main invariant or contract.

## Advanced Extensions
Connect this topic to related chapters and extend the implementation with tests, modular APIs, performance measurements, and portability notes.

## Related Topics
See [INDEX.md](../../INDEX.md).
