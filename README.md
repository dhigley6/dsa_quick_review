# dsa_quick_review
Quick review of Data Structures and Algorithms

## About

I'm using this README for two things: 1. A way for me to periodically review data structures and algorithms, 2. A checklist of sorts for my current understanding of data structures and algorithms. If I don't feel fluent with a particular topic in reviewing it, then I know to spend more time reviewing it. A third purpose of this for myself is to solidify my understanding of Data Structures and Algorithms by making this document. This could be useful for others seeking either of these same uses. This is going to describe things quickly without a pedagogical foucs. If one is interested in learning parts of Data Structures and Algorithms without significant prior exposure, then I recommend the book "Data Structures and Algorithms in Python" by Goodrich, Tamassia and Goldwasser and the set of Leetcode problems organized by Neetcode and his associated solution videos (https://neetcode.io/roadmap). I've also found this video on Dynamic Programming helpful https://www.youtube.com/watch?v=oBt53YbR9Kk. 

This is currently a work in progress and may be a bit rough.

## Algorithm Analysis

## Data Structures

A data structure is a collection of data values with the relationships between them and the operations that can be applied to the data.

### 1. Array

An array is a collection of items of the same variable type stored at contiguous locations in memory.

Implementation in Python
```Python
# Dynamic array (elements are added and removed as needed)
array = []
```

### 2. Linked List

A linked list a collection of elements where each element has a link to the next element (singly linked list), or a link to both the next and previous elements (doubly linked list).

Tips
- Create pointers to needed nodes before breaking links. Often in linked list problems, there will be situations where you need to manipulate the links between elements. In such cases, it is often important to first traverse the linked list in its original state to find nodes that you will need during or after the link manipulations. A well-known example occurs in reversing a linked list (https://leetcode.com/problems/reverse-linked-list/description/).
- Dummy node. Often, linked list problems require iterating through the list elements. In such cases, it can be useful to create a dummy node as the first node in the iteration. The dummy node helps to not have to setup additional logic to handle the first element in the linked list, but is not used in the final returned result.

Implementation in Python
```Python
class Node:

    def __init__(self, value, next):
        self.value = value
        self.next = next
```

### 3. Stack

A stack is a collection of elements with the ability to insert an additional element at the top of the stack or remove the element currently at the top of the stack. Sice the most recently inserted element is the first to be removed, stacks are FILO (First In Last Out).

Implementation in Python
```Python
# initialization
stack = []

# add elements to the stack
stack.append(0)
stack.append(5)

# pop the element from the stack and print its value
popped_element = stack.pop()
print(popped_element)     # 5

# Using a list to implement a stack gives amortized constant time complexity for append and pop operations.
# If you need constant time complexity, you can use the collections.deque class
```

### 4. Queue

A queue, similarly to a stack, is a collection of elements with the ability to insert additional elements or remove elements. Unlink a stack, for a queue the least recently inserted element is the next to be removed (First In First Out).

Implementations in Python:
```Python
from collections import deque

# initialization
queue = deque()

# add elements to the queue
queue.append(0)
queue.append(5)

# pop an element from the queue and print its value
popped_element = queue.popleft()
print(popped_element)    # 0
```

### 5. Hashmap
Uses a hash function to map keys to a fixed-size array, called a hash table.

Implementation in Python
```Python
# initialization
hashmap = {}

# add elements to the hashmap
hashmap['a'] = 5
hashmap['b'] = 0

# retrieve an element from the hashmap
print(hashmap['b'])    # 0
```

### 6. Hashset
A collection of items where every item is unique. Uses a hash function to achieve constant time operations.

Implementation in Python
```Python
# Initialization
hashset = set()

# add elements to the hashset
hashset.add(5)
hashset.add(6)

# check whether element is in hashset
print(5 in hashset)    # True
print(0 in hashset)    # False
```

### 7. Tree
Stores data in a hierarchical manner with a root node having various child nodes, which can then have their own child nodes, etc. Nodes are connected by edges. There are many different special cases of the tree data structure.

Implementation in Python
```Python
class TreeNode:
    def __init__(self, data):
        self.data = data
        self.children = []

root = TreeNode(data=5)
child_1 = TreeNode(data=2)
child_2 = TreeNode(data=5)
root.children = [child_1, child_2]
```

### 8. Heap
A heap is a complete binary tree that satisfies the heap property (for every node, the value of its children is less than or equal to its own value (for a min heap), or for every node, the value of its children is greater than or equal to its own value (for a max heap).).

Implementation in Python
```Python

```

### 9. Trie

### 10. Graph

## Algorithms

### 1. Sorting

#### 1.a. Merge Sort

Basic idea: 

#### 1.b. Quick Sort

#### 1.c. Sorting in Python

In Python, you can use the list.sort method to sort lists in place or the sorted function, which returns a list of sorted elements of the iterable passed to it.

https://docs.python.org/3/howto/sorting.html

### 2. Recursion

### 3. Two Pointers

Basic idea: 

### 4. Sliding Window

### 5. Backtracking

### 6. Dynamic Programming

Top-Down Memoization

Bottup-Up Tabulation

### 7. Graph Algorithms

Depth First Search

Breadth First Search

Topological Sort

Union Find

Shortest paths: Djikstra's Algorithm

Minimum Spanning Tree: Prim's Algorithm

### 8. Greedy Algorithms

### 9. Pattern Matching

Knuth-Morris-Pratt algorithm

### 10. Bit Manipulation
