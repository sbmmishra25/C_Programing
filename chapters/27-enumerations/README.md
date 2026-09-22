# 27. Enumerations

## Definition
An enum defines named integer constants grouped into an enumeration type. Enumerators improve readability and make state machines and modes easier to understand.

## Complete example
~~~c
#include <stdio.h>

typedef enum {
    STATE_IDLE,
    STATE_RUNNING,
    STATE_ERROR
} State;

const char *state_name(State s) {
    switch (s) {
        case STATE_IDLE: return "idle";
        case STATE_RUNNING: return "running";
        case STATE_ERROR: return "error";
        default: return "unknown";
    }
}

int main(void) {
    State s = STATE_RUNNING;
    printf("%s\n", state_name(s));
    return 0;
}
~~~

## Values
By default, enumerators receive successive integer values beginning at zero unless explicitly assigned. Explicit values are useful when interfacing with protocols or stable external representations, but the representation and compatible integer type are implementation-defined aspects.

## Common mistakes
Assuming enum values are strings, forgetting a switch default where invalid values are possible, and exposing raw enum values as a stable file/network format without documenting the contract.

## Practice
Create enums for menu commands, traffic signals, error classes, and parser tokens. Implement exhaustive switch handling.