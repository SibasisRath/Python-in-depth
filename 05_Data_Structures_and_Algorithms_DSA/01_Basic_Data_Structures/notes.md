# Basic Data Structures

## Explanation

This section covers the fundamental data structures you'll use when solving algorithmic problems or implementing more complex structures:

- **Arrays/Lists**: Ordered collections of items. Python's built-in `list` is a dynamic array supporting indexing, slicing, and mutability.
- **Linked Lists**: Nodes containing data and a reference to the next node (singly), optionally previous (doubly). Useful for constant-time insertions/deletions when you have a pointer.
- **Stacks and Queues**: Abstract data types implemented typically using lists or linked lists. Stacks follow LIFO (last-in-first-out), queues follow FIFO (first-in-first-out).
- **Hash Tables/Dictionaries**: Key-value stores with average constant-time lookups. In Python, `dict` and `set` are hash-based.
- **Trees** (covered lightly here but in later topics): hierarchical structures; binary trees are a starting point.
- **Heaps/Priority Queues**: Binary heap underneath; Python provides `heapq` module.
- **Graphs** (overview here): Collections of nodes and edges, represented by adjacency lists or matrices.

## Examples

### List operations
```python
fruits = ["apple", "banana", "cherry"]
fruits.append("date")
print(fruits[1])  # banana
print(fruits[:2])  # ['apple', 'banana']
```

### Implementing a simple singly linked list
```python
class Node:
    def __init__(self, data, nxt=None):
        self.data = data
        self.next = nxt

class SinglyLinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        if not self.head:
            self.head = Node(data)
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = Node(data)

    def __iter__(self):
        current = self.head
        while current:
            yield current.data
            current = current.next

# usage
lst = SinglyLinkedList()
lst.append(1)
lst.append(2)
print(list(lst))  # [1, 2]
```

### Stack using list
```python
stack = []
stack.append(10)
stack.append(20)
print(stack.pop())  # 20
```

### Queue using collections.deque
```python
from collections import deque
queue = deque()
queue.append('a')
queue.append('b')
print(queue.popleft())  # 'a'
```

### Dictionary usage
```python
phonebook = {'Alice': '555-1234', 'Bob': '555-5678'}
phonebook['Carol'] = '555-9012'
print(phonebook.get('Bob'))
```

## Tasks

### Beginner
1. Create a list of numbers and compute the sum and average.
2. Use a dictionary to count the frequency of words in a sentence.
3. Simulate a stack using a Python list and perform push/pop operations.

### Intermediate
1. Implement a `Queue` class using a linked list.
2. Write a function that reverses a singly linked list in place.
3. Use a set to remove duplicates from a list of items and return the unique list.

### Advanced
1. Implement a basic binary tree node class and traverse it in-order.
2. Write a program to detect a cycle in a linked list (Floyd's tortoise and hare).
3. Build a min-heap from an unordered list without using `heapq`.

## Quick Review
- What are the time complexities for inserting and deleting at the beginning of a linked list?
- How does a hash table achieve average constant-time lookup?
- Explain the difference between a stack and a queue.
- When would you prefer a linked list over a dynamic array?

---

These foundations will be revisited when we cover algorithms and advanced structures.