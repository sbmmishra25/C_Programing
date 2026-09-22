# 55. Hash Tables

## Concept
A hash table maps keys to slots using a hash function. Collisions require a strategy such as chaining or open addressing.

## Complete chaining example
~~~c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define N 8
typedef struct Entry { char *key; int value; struct Entry *next; } Entry;
Entry *table[N];

unsigned hash(const char *s){
    unsigned h=2166136261u;
    while(*s) h=(h^(unsigned char)*s++)*16777619u;
    return h%N;
}
int put(const char *key,int value){
    unsigned i=hash(key);
    for(Entry *e=table[i];e;e=e->next)
        if(strcmp(e->key,key)==0){e->value=value;return 1;}
    Entry *e=malloc(sizeof *e); if(!e)return 0;
    e->key=malloc(strlen(key)+1); if(!e->key){free(e);return 0;}
    strcpy(e->key,key); e->value=value; e->next=table[i]; table[i]=e;
    return 1;
}
int get(const char *key,int *out){
    for(Entry *e=table[hash(key)];e;e=e->next)
        if(strcmp(e->key,key)==0){if(out)*out=e->value;return 1;}
    return 0;
}
void destroy(void){for(size_t i=0;i<N;i++){Entry *e=table[i];while(e){Entry*n=e->next;free(e->key);free(e);e=n;}}}
int main(void){int x;put("alice",91);put("bob",84);if(get("alice",&x))printf("%d\n",x);destroy();}
~~~

## Complexity
Expected O(1) insertion/search with a good hash function and controlled load factor; worst-case O(n).

## Design issues
Hash quality, collision strategy, resizing, load factor, key ownership, and deletion semantics determine practical performance.

## Practice
Implement open addressing with linear/quadratic probing and resize when load factor becomes high.