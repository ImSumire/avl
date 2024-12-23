# Adelson-Velsky & Landis Tree in C

This repository provides a C implementation of an AVL tree data structure. An AVL tree is a self-balancing binary search tree that ensures the height of the two child subtrees of any node differs by at most one.

 * Wikipedia: https://en.wikipedia.org/wiki/AVL_tree
 * Paper: https://dl.acm.org/doi/pdf/10.1145/355609.362340
 * Benchmark: https://www.authorea.com/doi/full/10.22541/au.173377871.17799160

## Features
- **Efficient insertion and removal** of nodes with a time complexity of O(log2(n))
- In-order traversal of the tree with a **time complexity of O(n)**
- **Self-balancing** to maintain a balanced tree structure

## Usage

To use this AVL tree implementation, simply include the `avl_tree.h` file in your project and use the provided functions to create, insert, remove, and traverse the tree.

**Example Usage**

```c
#include "./avl_tree.h"


void print_key(uint64_t key) {
    printf("%lu, ", key);
}

int main() {
    AvlTree* tree = avl_new();

    // Insert keys into the tree
    for (uint64_t i = 0; i < 128; i++)
        avl_insert(tree, i);

    // Perform in-order traversal of the tree
    printf("In-order traversal: [");
    avl_iter(tree, print_key);
    printf("]\n\n");

    // Remove keys from the tree
    for (uint64_t i = 0; i < 64; i++)
        avl_remove(tree, i);

    // Perform in-order traversal of the tree after removal
    printf("In-order traversal after some removal: [");
    avl_iter(tree, print_key);
    printf("]\n\n");

    // Drop the tree
    avl_drop(tree);

    return 0;
}
```

## Functions
- `avl_new()`: Creates a new AVL tree.
- `avl_insert()`: Inserts a new key into the AVL tree.
- `avl_remove()`: Removes a key from the AVL tree.
- `avl_iter()`: Performs an in-order traversal of the AVL tree.
- `avl_drop()`: Drops the AVL tree and frees its memory.

## Data Structures
- `AvlNode`: Represents a node in the AVL tree, containing a key, left and right child pointers, and a height.
- `AvlTree`: Represents the AVL tree data structure, containing a root node.

## Time Complexity
- **In-order traversal**: O(n)
- **Insertion**: O(log2(n))
- **Removal**: O(log2(n))

> For 4 294 967 296 elements, worst step count: 32

## Space Complexity
- **AVL tree**: O(n)
- **Node**: O(1)
