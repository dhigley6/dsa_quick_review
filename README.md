# dsa_quick_review
Quick review of Data Structures and Algorithms

## About

I'm using this README for two things: 1. A way for me to periodically review data structures and algorithms, 2. A checklist of sorts for my current understanding of data structures and algorithms. If I don't feel fluent with a particular topic in reviewing it, then I know to spend more time reviewing it. A third purpose of this for myself is to solidify my understanding of Data Structures and Algorithms by making this document. This could be useful for others seeking either of these same uses. This is going to describe things quickly without a pedagogical foucs. If one is interested in learning parts of Data Structures and Algorithms without significant prior exposure, then I recommend the book "Data Structures and Algorithms in Python" by Goodrich, Tamassia and Goldwasser and the set of Leetcode problems organized by Neetcode and his associated solution videos (https://neetcode.io/roadmap). I've also found this video on Dynamic Programming helpful https://www.youtube.com/watch?v=oBt53YbR9Kk. 

This is currently a work in progress and may be a bit rough.

## Algorithm Analysis

$f(n)$ is $O(g(n))$ if there is a real constant $c > 0$ and an integer constant $n_0 \geq 1$ such that 

$f(n) \leq cg(n)$

for $n \geq n_0$. We typically seek to characterize running times of algorithms in terms of their asymptotic time complexity (often worst case). For example, merge sort is worst case $O(n\log n)$. In amortized analysis of an algorithm, we analyze the average performance of an algorithm over multiple operations. For example, appending to a dynamic array has worst case time complexity $O(n)$ since this may require resizing and moving the array in memory, eventhough most operations have constant $O(1)$ time complexity. By amortizing the analysis over many append operations though, the amortized time complexity is $O(1)$ since the resizing operation will only need to occur once every ~1/n operations.

In the same manner as for time complexity of an algorithm, we can also examine its asymptotic memory usage (often called space complexity). For example, the memory usage of a dynamic array is $O(n)$.

## Data Structures

A data structure is a collection of data values with the relationships between them and the operations that can be applied to the data.

### 1. Array

An array is a collection of items of the same variable type stored at contiguous locations in memory.

Implementation in Python
```Python
# Dynamic array (elements are added and removed as needed)
array = []
```

TODO: Add notes on referential, dynamic arrays

| Operation | Time Complexity |
| Access | O(1) |
| Insert | O(n) |
| Insert at end | O(1) |
| Remove | O(n) |
| Remove at end | O(1) |

### 2. Linked List

A linked list a collection of elements where each element has a link to the next element (singly linked list), or a link to both the next and previous elements (doubly linked list). Unlinke an array, the elements in a linked list are not necessarily stored in sequential blocks of memory.

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

TODO: Add notes on positional linked list

| Operation | Time Complexity |
| Access | O(n) |
| Search | O(n) |
| Insert | O(1) (assuming you have traversed to the insertion position) |
| Remove | O(1) (assuming you have traversed to the removal position) |

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

| Operation | Time Complexity |
|-----------|-----------------|
| Top | O(1) |
| Push | O(1) |
| Pop | O(1) |

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

| Operation | Time Complexity |
| Enqueue | O(1) |
| Dequeue | O(1) |
| Front | O(1) |

### 5. Hashmap
Uses a hash function to map keys to a fixed-size array, called a hash table. During lookup, the key is hashed and the resulting value indicates where the corresponding value is stored.

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

| Operation | Time Complexity |
|--------|----------------|
| Search | O(1) (average) |
| Insert | O(1) (average) |
| Remove | O(1) (average) |

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

#### 7a. Binary Search Tree

| Operation | Time Complexity |
|-----------|-----------------|
| Access | O(log(n)) |
| Search | O(log(n)) |
| Insert | O(log(n)) |
| Remove | O(log(n)) |

### 8. Heap
A heap is a complete binary tree that satisfies the heap property (for every node, the value of its children is less than or equal to its own value (for a min heap), or for every node, the value of its children is greater than or equal to its own value (for a max heap).). A heap balances time complexity of finding the minimum/maximum with time complexity of insertion/removal. It is a good data structure when it is necessarily to repeatedly remove the minimum/maximum or when insertions need to be interspersed with removals of the minimum/maximum.

Implementation in Python
```Python
import heapq

# initialization of min heap
heap = [5, 6, 7]
heapq.heapify(heap)

# adding items
heapq.heappush(heap, 10)
heapq.heappush(heap, 20)
heapq.heappush(heap, 30)

# removing element
element = heapq.heappop(heap)
print(element)    # 5
```

| Operation | Time Complexity |
|-----------|-----------------|
| Find max/min | O(1) |
| Insert | O(log(n)) |
| Remove | O(log(n)) |
| Heapify (create a heap out of a given array of elements) | O(n) |

### 9. Trie
A Trie is a tree used for storing a dynamic set of strings. If a string is stored in a Trie, then it will have nodes traversable from the root node that correspond to its characters in the same order as the word. At the last node of the Trie for the word, a Node parameter indicating whether that Node corresponds to the end of a word is set to True.

Implementation in Python
```Python
# from Neetcode solution for Leetcode 208
class TrieNode:
    def __init__(self):
        self.children = {}
        self.end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word: str) -> None:
        """Insert a new word into the Trie
        """
        cur = self.root
        for c in word:
            if c not in cur.children:
                cur.children[c] = TrieNode()
            cur = cur.children[c]
        cur.end_of_word = True

    def search(self, word: str) -> bool:
        """Check for presence of word in Trie
        """
        cur = self.root
        for c in word:
            if c not in cur.children:
                return False
            cur = cur.children[c]
        return cur.end_of_word
```

In the below table, m is the length of the string used in the operation
| Operation | Time Complexity |
|-----------|-----------------|
| Search | O(m) |
| Insert | O(m) |
| Remove | O(m) |

### 10. Graph
A graph is a collection of nodes connected by edges. Graphs can be either directed (have edges that are oriented in particular directions) or undirected. A tree is a special case of a graph which has no cycles. A linked list is another special case of a graph. Graphs can be implemented in different ways with tradeoffs in space/time complexities.

Implementation of graph as edge list in Python
```Python
# An edge list simply lists the edges between nodes in a graph
# (the nodes are numbered between 0 and n-1, where n is the number of nodes)
edge_list = [ [0,1], [0,6], [0,8], [1,4], [1,6], [1,9], [2,4], [2,6], [3,4], [3,5],
[3,8], [4,5], [4,9], [7,8], [7,9] ]
# from https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs
# having a sorted edge list allows us to search for the presence of a particular edge in logarithmic time
```

Implementation of graph as adjacency list in Python
```Python
# adapted from https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs
# for each vertex, we store an array of the verticies adjacent to it
adjacency_list = [ [1, 6, 8],
  [0, 4, 6, 9],
  [4, 6],
  [4, 5, 8],
  [1, 2, 3, 5, 9],
  [3, 4],
  [0, 1, 2],
  [8, 9],
  [0, 3, 7],
  [1, 4, 7]
]
# above, row i in the matrix lists the nodes that are adjacent to node i
```

Implementation of graph as adjacency matrix in Python
```Python
# adapted from https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs
# For a graph with n nodes, an adjacency matrix is a n by n matrix of 0s and 1s where the entry at (i, j) is 1 if and
# only if there is an edge from i to j, otherwise it is 0.

adjacency_matrix = [
    [0, 1, 0],
    [1, 0, 1],
    [0, 1, 0]
]
```

## Algorithms

### 1. Sorting

#### 1.a. Merge Sort

Basic idea: Recursively divide array into two halfs, sort the halfs, then combine them back together to obtain the sorted array.

Implementation in Python
```Python
# TODO
```

#### 1.b. Quick Sort

Basic idea: Recursively pick an element in the array as the pivot. Arrange the array such that values lower than the pivot are before it and values higher than the pivot are after it. Next, apply quicksort to the sub-arrays before and after the pivot. Repeat until the array is sorted.

Implementation in Python
```Python
# TODO
```

#### 1.c. Sorting in Python

In Python, you can use the list.sort method to sort lists in place or the sorted function, which returns a list of sorted elements of the iterable passed to it. Each of these a 'reverse' argument which can be specified as True to sort in descending order.

```Python
# Sorting a list with Python's list.sort method:
basic_list = [2, 5, 7, 1, 1, 0]
basic_list.sort()
print(basic_list)    # [0, 1, 1, 2, 5, 7]

# Using Python's built-in sorted function to sort a list:
basic_list = [2, 5, 7, 1, 1, 0]
sorted_list = sorted(basic_list)
print(sorted_list)    # [0, 1, 1, 2, 5, 7]

# Using Python's built-in sorted function to sort another iterable (returns a list):
basic_set = {1, 2, 0, -1}
sorted_set = sorted(basic_set)
print(sorted_set)    # [-1, 0, 1, 2]

# Using key argument to apply a function to the elements before sorting (can also be used in list.sort)
basic_set = {1, 2, 0, -1}
absolute_value_sorted_set = sorted(basic_set, key=abs)
print(absolute_value_sorted_set)    # [0, 1, -1, 2]
```

See https://docs.python.org/3/howto/sorting.html for more information.

### 2. Recursion

Recursion is a way to achieve repetition in a porgram. In recursion, a function makes one or more calls to itself during execution. In analyzing the space complexity of recursive algorithms, remember to take into account the memory of the entire call stack. An algorithm that uses recursion typically includes base cases which can complete without recursive calls along with a recurrent part.

TODO: Add note on converting recursive algorithms to iterative
TODO: Add note on tail recursion

### 3. Two Pointers

Basic idea: Create two pointers that point to indicies in an array and move them across the array to solve the problem.

### 4. Sliding Window

Basic idea: Iteratively move a window across an array, calculating properties of the window as you go, to solve a problem.

### 5. Binary Search

Basic idea: Find an element with a particular value in a sorted array (if it exists) by recursively dividing the array in half and searching the half that it must belong in (if it is there).

Implementation in Python
```Python
# Adapted from https://www.geeksforgeeks.org/python-program-for-binary-search/
def binary_search(arr, low, high, x):
    """Searches for the presence of x in arr between indicies low and high, inclusive
    Returns index of x in arr if it exists, otherwise returns -1
    """
    if high >= low:
        mid = (high + low) // 2
        if arr[mid] == x:
            return mid
        elif arr[mid] > x:
            return binary_search(arr, low, mid-1, x)
        else:
            return binary_search(arr, mid+1, high, x)
    else:
        return -1
```

### 6. Working with Intervals

#### 6a. Checking if Two Intervals Overlap

```Python
# Adapted from https://www.techinterviewhandbook.org/algorithms/interval/
def intervals_overlap(a, b):
    return a[0] < b[1] and b[0] < a[1]
```

#### 6b. Merging Two Intervals

```Python
# Adapted from https://www.techinterviewhandbook.org/algorithms/interval/
def merge_intervals(a, b):
    return [min(a[0], b[0]), max(a[1], b[1])]
```

### 6. Backtracking

Basic idea: Try different options to solve a problem, undoing decisions where they are found to not work. Repeat until a solution is found or all possibilities are exhausted.

Template in Python
```Python
# Adapted from https://christianjmills.com/posts/backtracking-notes/index.html
# Note: if you have a problem where the state can repeat elements, then you can
# represent the state as a list instead of a set.

def is_valid_solution(state):
    # replace with logic to check if state is a valid solution
    return True

def get_candidates(state):
    # replace with logic to get list of potential next steps from state
    return []

def search(state, solutions):
    """Perform recursive depth first search to find solutions.
    """
    if is_valid_solution(state):
        solutions.append(state.copy())
        # if you only need one solution, then add a return here
    for candidate in get_candidates(state):
        state.add(candidate)
        search(state, solutions)
        state.remove(candidate)

# Entry point
def solve():
    solutions = []
    state = set()
    search(state, solutions)
    return solutions
```

### 7. Dynamic Programming

Dynamic programming provides efficient methods to solve certain problems.

Depending on the source, both top-down memoization and bottum-up tabulation may be considered dynamic programming techniques or just bottum-up tabulation. Bottom-up tabulation is iterative and benefits from not having the overhead of recursive top-down memoization, but memoization benefits from not having to solve all subproblems where that is not required. If all subproblems need to be solved at least once, then tabulation will usually outperform memoization by a constant factor.

#### 7a. Top-Down Memoization

Basic idea: speed up solutions to problems by saving solutions to solved subproblems, and reusing those solutions later.

Template implementation in Python
```Python
result_memo = {}

def solver(k):
    if k is base_case:
        # replace with base case logic
        return 0
    elif k not in result_memo:
         # replace below line with logic to calculate result for k
         result_for_k = 1
         result_memo[k] = result_for_k
    return result_memo[k]
```

#### 7b. Bottup-Up Tabulation

Basic idea: iteratively build up a table of solutions to subproblems, starting from the smallest subproblems, and using the solutions of already solved subproblems to calculate the solution to the current subproblem.

### 8. Graph Algorithms

#### 8a. Depth First Search

Basic idea: Recursively traverse a graph by traveling along each path until it is no longer possible to continue on that path, then going back to the nearest previous point where we can continue traversal. Repeat until all reachable nodes have been traversed.

Template in Python
```Python
# Adapted from https://dev.to/alexhanbich/dfs-python-templates-4g7l
# We can expand the below template to handle passing up information from nodes
# that are traversed later by using information returned from do_something.
# We can also expand it to handle passing down information from nodes that
# have been traversed before as additional parameters of do_something.
# Note that if we are traversing a tree, keeping track of visited nodes
# is not required as long as we simply traverse from parent nodes to child
# nodes.

visited = set()

def do_something(node):
    # replace with problem logic
    pass

def get_neighbors(node):
    # replace with problem logic
    pass

def dfs(node, visited):
    if node in visited:
        return
    do_something(node)
    visited.add(node)
    for neighbor in get_neighbors(node):
        dfs(neighbor, visited)
```

#### 8b. Breadth First Search

Basic idea: iteratively traverse a graph by visiting a node, then all of its neighbors, then all of its neighbors' neighbors, then all of its neighbors' neighbors' neighbors, etc. (while not revisiting nodes).

Template in Python
```Python
# Note that if we are traversing a tree, keeping track of visited nodes
# is not required as long as we simply traverse from parent nodes to child
# nodes.
from collections import deque

visited = set()

def do_something(node):
    pass

def get_neighbors(node):
    pass

def bfs(start_node, visited):
    to_visit = deque()
    to_visit.append(start_node)
    while len(to_visit) > 0:
        node = to_visit.popleft()
        if node in visited:
            continue
        do_something(node)
        neighbor_list = get_neighbors(node)
        for neighbor in neighbor_list:
            to_visit.append(neighbor)
```

#### 8c. Topological Sort

#### 8d. Union Find

#### 8e. Shortest paths: Djikstra's Algorithm

#### 8f. Minimum Spanning Tree: Prim's Algorithm

### 9. Greedy Algorithms

### 10. Pattern Matching

Knuth-Morris-Pratt algorithm

### 11. Bit Manipulation


## References

Templates: https://dev.to/alexhanbich/dfs-python-templates-4g7l

Algorithms cheat sheets of Tech Interview Handbook: https://www.techinterviewhandbook.org/algorithms/study-cheatsheet/
