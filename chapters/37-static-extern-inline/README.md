# 37. static, extern & inline

## static
At file scope, static gives internal linkage. At block scope, static gives static storage duration while retaining block scope.

## extern
extern declares an entity whose definition is provided elsewhere, commonly across translation units.

## inline
inline is a request/definition facility for functions, not a guarantee that the compiler will physically inline the call.

## Complete example
~~~c
#include <stdio.h>

static int helper(int x) {
    return x * x;
}

inline int cube(int x) {
    return x * x * x;
}

int main(void) {
    printf("%d %d\n", helper(4), cube(3));
    return 0;
}
~~~

## Multi-file note
Inline linkage rules can be subtle, especially with external definitions. For ordinary projects, place a static inline helper in a header when each translation unit may have its own internal copy, or provide a normal external definition when one externally linked function is required.

## Practice
Build a two-file library using extern and a header containing static inline utilities. Inspect symbols with your platform's object-file tools.