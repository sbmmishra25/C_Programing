# 73. Debugging Exercises

## Exercise 1: out-of-bounds
~~~c
int a[5];
for(int i=0;i<=5;i++) a[i]=i;
~~~
Fix the loop to use i < 5.

## Exercise 2: use-after-free
~~~c
int *p=malloc(sizeof *p);
*p=10;
free(p);
printf("%d\n",*p);
~~~
Remove the dereference after free or establish a new valid object.

## Exercise 3: realloc bug
~~~c
p=realloc(p,new_size);
if(!p){ /* original allocation has been lost */ }
~~~
Use a temporary pointer.

## Exercise 4: string overflow
~~~c
char dst[4];
strcpy(dst,"hello");
~~~
Provide sufficient capacity or use a bounded design such as snprintf.

## Debugging protocol
Compile with `-Wall -Wextra -Wpedantic -g`, then use AddressSanitizer/UndefinedBehaviorSanitizer where supported. Add regression tests after each fix.

## Practice
Create ten deliberately buggy programs covering leaks, double-free, invalid format specifiers, signed overflow, uninitialized reads, infinite loops, wrong recursion base cases, and linked-list corruption.