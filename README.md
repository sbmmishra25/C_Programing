# C Programming — Complete From Basic to Advanced

A structured, textbook-style C programming repository covering **76 topics** from fundamentals to advanced, system-level, data-structure, algorithmic, interview, and project-oriented programming.

## What this repository contains

- 76 sequential chapters with concepts, syntax, examples, complete programs, explanations, pitfalls, and practice.
- Dedicated C source examples and exercises.
- Data structures and algorithms implemented in C.
- Debugging, memory-safety, compilation, modular programming, Makefiles, and low-level programming guidance.
- C11/C17/C23 feature coverage with standards-awareness.
- Interview questions, exercises, mini-projects, and advanced projects.
- A searchable master index and roadmap.

## Recommended compilation

Use a modern conforming compiler where available:

```bash
cc -std=c17 -Wall -Wextra -Wpedantic -O2 program.c -o program
./program
```

For debugging builds, prefer:

```bash
cc -std=c17 -Wall -Wextra -Wpedantic -g -fsanitize=address,undefined program.c -o program
```

Sanitizers are compiler/platform features and are not themselves part of ISO C.

## Curriculum

See [INDEX.md](INDEX.md) for all 76 chapters and [ROADMAP.md](ROADMAP.md) for the recommended learning sequence.

## Repository structure

```
.
├── README.md
├── INDEX.md
├── ROADMAP.md
├── docs/
│   ├── C_PROGRAMMING_REFERENCE.md
│   ├── COMPILATION_GUIDE.md
│   ├── DEBUGGING_GUIDE.md
│   └── C_CHEATSHEET.md
├── chapters/
│   ├── 01-fundamentals/
│   ├── 02-history-standards-compilation/
│   ├── ...
│   └── 76-reference-index/
├── examples/
├── exercises/
└── projects/
```

## Standards note

The repository distinguishes ISO C language/library guarantees from implementation-defined, unspecified, undefined, and platform-specific behavior. System-level examples are explicitly identified when they rely on POSIX or another operating-system API.

## License

Educational material intended for learning, teaching, and academic practice.
