# dsa_quick_review
Quick review of Data Structures and Algorithms

## About

I'm using this README for two things: 1. A way for me to periodically review data structures and algorithms, 2. A checklist of sorts for my current understanding of data structures and algorithms. If I don't feel fluent with a particular topic in reviewing it, then I know to spend more time reviewing it. A third purpose of this for myself is to solidify my understanding of Data Structures and Algorithms by making this document. This could be useful for others seeking either of these same uses. This is going to describe things quickly without a pedagogical foucs. If one is interested in learning parts of Data Structures and Algorithms without significant prior exposure, then I recommend the book "Data Structures and Algorithms in Python" by Goodrich, Tamassia and Goldwasser and the set of Leetcode problems organized by Neetcode and his associated solution videos (https://neetcode.io/roadmap). I've also found this video on Dynamic Programming helpful https://www.youtube.com/watch?v=oBt53YbR9Kk. 

This is currently a work in progress and may be a bit rough.

## Algorithm Analysis

## Data Structures

### 1. Array

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

### 3. Stack and Queue

Stacks and queues are both collections of elements with the ability to insert additional elements or remove elements. In a stack, the most recently inserted element is the first to be removed (FILO, First In Last Out), whereas in a queue the first element inserted is the 

Implementations in Python: In python, you can use a simple list as a stack with the append (add element) and pop (remove element) methods if you don't mind that these methods only have amortized constant time complexity. If you do mind, you can use the collections.deque class with the same methods. The collections.deque class can also be used as a queue with the append (add element) and popleft (remove element) methods.

### 4. Hashmap and Hashset

### 5. Tree

### 6. Trie

### 7. Heap

### 8. Graph

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

### 7. Greedy Algorithms

### 8. Pattern Matching

### 9. Bit Manipulation
