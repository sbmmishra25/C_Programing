# 71. Common Interview Questions

## Fundamental questions
1. What is the difference between declaration and definition?
2. Why does an array often decay to a pointer?
3. What is the difference between sizeof(array) and sizeof(pointer)?
4. Explain const int*, int *const, and const int *const.
5. What is a dangling pointer?
6. Why is signed overflow undefined?
7. Difference between malloc, calloc, realloc, and free?
8. What is static at block scope versus file scope?
9. What is the difference between scope, storage duration, and linkage?
10. Why should qsort comparators avoid subtraction?

## Pointer question
Explain:
~~~c
int *p;
int **pp;
int (*pa)[4];
int (*fp)(int,int);
~~~
p points to int; pp points to an int pointer; pa points to an array of four int; fp points to a compatible function.

## Coding questions
Implement reverse array, linked-list reversal, binary search, stack, queue, BST insertion/search, heap operations, hash lookup, BFS/DFS, merge sort, quicksort, and LRU-style structures.

## Interview method
State assumptions, choose types deliberately, discuss edge cases, give complexity, and explain ownership/lifetime. Do not merely provide code.