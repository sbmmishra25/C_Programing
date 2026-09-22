# 46. Makefiles & Build Systems

## Concept
A build system tracks dependencies and invokes compilation/linking commands only when required.

## Complete Makefile
~~~make
CC = cc
CFLAGS = -std=c17 -Wall -Wextra -Wpedantic -g
OBJ = main.o math.o
TARGET = app

$(TARGET): $(OBJ)
	$(CC) $(OBJ) -o $@

main.o: main.c math.h
	$(CC) $(CFLAGS) -c main.c

math.o: math.c math.h
	$(CC) $(CFLAGS) -c math.c

clean:
	rm -f $(OBJ) $(TARGET)

.PHONY: clean
~~~

## Dependency graph
Changing math.h should rebuild every object that includes it. Source-to-object compilation and object-to-executable linking are separate stages.

## Common mistakes
Missing header dependencies, tabs replaced by spaces in recipes, hard-coded compiler flags, and clean targets that delete unrelated files.

## Practice
Add test, sanitize, release, and install targets. Learn automatic variables such as $@ and $<.