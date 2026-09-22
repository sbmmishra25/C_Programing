# Debugging Guide

## Compile with diagnostics

Always start with:

```bash
cc -std=c17 -Wall -Wextra -Wpedantic -g source.c -o app
```

## Frequent bug classes

- out-of-bounds array access
- use-after-free
- double free
- memory leak
- uninitialized reads
- invalid string termination
- incorrect format specifiers
- signed integer overflow
- invalid pointer dereference
- incorrect ownership/lifetime assumptions

## Sanitizers

Where supported:

```bash
-fsanitize=address,undefined
```

Use a debugger such as GDB or LLDB to set breakpoints, inspect variables, examine stack frames, and step through execution.

## Debugging discipline

1. Reproduce the failure.
2. Reduce to the smallest failing input.
3. Read compiler warnings.
4. Inspect boundaries and lifetimes.
5. Add assertions or targeted diagnostics.
6. Verify the fix against the original and edge-case inputs.
