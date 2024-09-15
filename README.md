# Doubly Linked List in Python

## Overview

This repository contains a Python implementation of a doubly linked list, a data structure where each node points to both its previous and next nodes. This implementation supports various operations including insertion, deletion, replacement, rotation, and more.

## Features

- **Node Class:**
  - Represents a single element in the doubly linked list.
  - Contains `value`, `next`, and `previous` attributes.

- **LinkedList Class:**
  - Implements a doubly linked list with multiple functionalities such as:
    - `append(value)`: Adds a node to the end of the list.
    - `push(value)`: Adds a node to the beginning of the list.
    - `insert_after(previous_value, value)`: Inserts a node after a specified value.
    - `insert_before(next_value, value)`: Inserts a node before a specified value.
    - `remove_first_occurrence(value)`: Removes the first occurrence of a specified value.
    - `remove_last_occurrence(value)`: Removes the last occurrence of a specified value.
    - `remove_duplicates()`: Removes all duplicate values in the list.
    - `replace_first_occurrence(old_value, new_value)`: Replaces the first occurrence of a value with a new value.
    - `rotate(k)`: Rotates the list by `k` positions, either left or right based on the sign of `k`.
    - `reverse()`: Reverses the entire list.
    - `clear()`: Clears the list.
    - `count_occurrences(value)`: Counts the number of occurrences of a value.
    - `is_empty()`: Checks if the list is empty.
    - And more.

## Time & Space Complexity

- **Time Complexity:** Most operations like append, push, and deletion have an average time complexity of `O(1)` due to the constant-time access to the head and tail nodes. Searching or traversing nodes (e.g., for inserts) has a time complexity of `O(n)`.
- **Space Complexity:** The space complexity is `O(n)` where `n` is the number of nodes in the list.

## Usage

### Requirements
- Python 3.x

### Example

```python
from linkedlist import LinkedList

# Create a new linked list
ll = LinkedList()

# Append elements
ll.append(10)
ll.append(20)
ll.append(30)

# Push an element to the beginning
ll.push(5)

# Insert a node after a value
ll.insert_after(10, 15)

# Remove first occurrence of a value
ll.remove_first_occurrence(20)

# Reverse the list
ll.reverse()

# Print the list
print(ll)
