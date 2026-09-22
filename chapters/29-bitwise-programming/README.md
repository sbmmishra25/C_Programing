# 29. Bitwise Programming

## Definition
Bitwise operators manipulate the bits of integer operands: &, |, ^, ~, <<, and >>. They are essential for flags, masks, packed fields, protocols, and low-level algorithms.

## Complete example
~~~c
#include <stdio.h>
#include <stdint.h>

#define READ_FLAG  (UINT8_C(1) << 0)
#define WRITE_FLAG (UINT8_C(1) << 1)
#define EXEC_FLAG  (UINT8_C(1) << 2)

int main(void) {
    uint8_t flags = 0;

    flags |= READ_FLAG;
    flags |= WRITE_FLAG;

    printf("read=%s\n", (flags & READ_FLAG) ? "yes" : "no");
    printf("execute=%s\n", (flags & EXEC_FLAG) ? "yes" : "no");

    flags &= (uint8_t)~WRITE_FLAG;
    flags ^= EXEC_FLAG;

    printf("flags=0x%02X\n", flags);
    return 0;
}
~~~

## Core patterns
Set a bit with x |= mask; clear it with x &= ~mask; toggle it with x ^= mask; test it with x & mask.

## Shift safety
Use unsigned integer types for predictable bit manipulation. Avoid shifting by a negative amount or by a count greater than or equal to the width of the promoted left operand. Left-shifting signed values can introduce undefined behavior in cases involving unrepresentable results.

## Common mistakes
Operator-precedence errors, signed shifts, incorrect mask widths, and using bitwise operators when logical && or || was intended.

## Practice
Count set bits, test power of two, reverse bits, extract bit fields, build permission flags, and implement a compact set representation.