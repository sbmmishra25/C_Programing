# 53. Binary Search Trees

## Property
For a BST, keys in the left subtree are ordered before the node key and keys in the right subtree after it, according to the chosen duplicate policy.

## Complete insertion/search
~~~c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node { int key; struct Node *left,*right; } Node;

Node *insert(Node *r,int x) {
    if(!r) {
        r=malloc(sizeof *r);
        if(!r) return NULL;
        *r=(Node){x,NULL,NULL}; return r;
    }
    if(x < r->key) r->left=insert(r->left,x);
    else if(x > r->key) r->right=insert(r->right,x);
    return r;
}
int contains(const Node *r,int x) {
    while(r) {
        if(x==r->key) return 1;
        r=(x<r->key)?r->left:r->right;
    }
    return 0;
}
void inorder(const Node *r){if(r){inorder(r->left);printf("%d ",r->key);inorder(r->right);}}
void destroy(Node *r){if(r){destroy(r->left);destroy(r->right);free(r);}}

int main(void){
    int a[]={8,3,10,1,6,14,4,7,13}; Node *r=NULL;
    for(size_t i=0;i<sizeof a/sizeof a[0];++i){Node *nr=insert(r,a[i]);if(!nr){destroy(r);return 1;}r=nr;}
    inorder(r); putchar('\n'); printf("contains 7: %d\n",contains(r,7)); destroy(r);
}
~~~

## Complexity
Search/insert are O(h). Balanced BST: O(log n) expected height; a degenerate tree can reach O(n).

## Practice
Implement deletion, predecessor/successor, height, validation of the BST invariant, and iterative traversals.