# Compilation Guide

## GCC / Clang

```bash
cc -std=c17 -Wall -Wextra -Wpedantic source.c -o app
```

Use `-std=c11`, `-std=c17`, or a supported C23 mode to study language-version differences.

## Debugging build

```bash
cc -std=c17 -Wall -Wextra -Wpedantic -g -fsanitize=address,undefined source.c -o app
```

## Multiple files

```bash
cc -std=c17 -Wall -Wextra -Wpedantic main.c stack.c queue.c -o app
```

## Make

```bash
make
make clean
```

The exact compiler, linker, sanitizer, and standard-library behavior can vary by platform.
