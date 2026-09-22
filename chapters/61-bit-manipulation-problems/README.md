# 61. Bit Manipulation Problems

## Fundamental identities
Test bit: x & (1u << k). Set: x |= mask. Clear: x &= ~mask. Toggle: x ^= mask. Lowest set bit: x & -x is commonly used with unsigned-compatible reasoning.

## Complete example: count set bits
~~~c
#include <stdio.h>
#include <stdint.h>

unsigned count_bits(uint32_t x) {
    unsigned count=0;
    while(x){ x &= x-1; ++count; }
    return count;
}
int main(void){printf("%u\n",count_bits(0xF0F0u));}
~~~

Each iteration clears one set bit, so the loop runs O(popcount(x)) rather than O(bit width).

## Problems
Power-of-two test, parity, XOR-based single-number problems, subset masks, bit-field extraction, Gray codes, bit reversal, and compact boolean sets.

## Pitfalls
Use unsigned types for bit-level algorithms, respect integer promotions, and never shift by an invalid count.

## Practice
Implement popcount without library support, next power of two, reverse bits, and subset enumeration with masks.