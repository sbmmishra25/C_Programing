# 52. Trees

## Concept
A tree is a hierarchical, connected, acyclic structure. A binary tree has at most two children per node.

## Complete example: traversals
~~~c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int key;
    struct Node *left, *right;
} Node;

Node *node(int x) {
    Node *n = malloc(sizeof *n);
    if (!n) return NULL;
    *n = (Node){x, NULL, NULL};
    return n;
}
void preorder(const Node *r) {
    if (!r) return;
    printf("%d ",r->key); preorder(r->left); preorder(r->right);
}
void inorder(const Node *r) {
    if (!r) return;
    inorder(r->left); printf("%d ",r->key); inorder(r->right);
}
void postorder(const Node *r) {
    if (!r) return;
    postorder(r->left); postorder(r->right); printf("%d ",r->key);
}
void destroy(Node *r) {
    if (!r) return;
    destroy(r->left); destroy(r->right); free(r);
}
int main(void) {
    Node *r=node(1); if(!r) return 1;
    r->left=node(2); r->right=node(3);
    if(!r->left || !r->right){destroy(r);return 1;}
    preorder(r); putchar('\n'); inorder(r); putchar('\n'); postorder(r); putchar('\n');
    destroy(r);
}
~~~

## Complexity
Traversal is O(n). Recursive auxiliary stack is O(h), where h is tree height.

## Key concepts
Root, leaf, parent, child, depth, height, subtree, balanced tree, full/perfect/complete tree.

## Practice
Implement level-order traversal, height, node count, leaf count, and mirror transformation.