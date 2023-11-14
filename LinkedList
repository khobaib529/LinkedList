class Node:
    """A node in a doubly linked list.

    Attributes:
        value: The value of the node.
        next: The next node in the linked list (or None if there is no next node).
        previous: The previous node in the linked list (or None if there is no previous node).
    """
    def __init__(self, value):
        self.value = value
        self.next = None
        self.previous = None

    def __str__(self):
        return str(self.value)

class LinkedList:
    """A doubly linked list.

    Attributes:
        head: The first node in the linked list (or None if the linked list is empty).
        tail: The last node in the linked list (or None if the linked list is empty).
        size: The number of elements in the linked list.
    """
    def __init__(self, iterable=None):
        """Creates a new doubly linked list.

        Args:
            iterable: An iterable of elements to add to the linked list.
        """
        self.head = None
        self.tail = None
        self.size = 0
        if iterable is not None:
            for element in iterable:
                self.append(element)

    def front(self):
        """Returns the first element in the doubly linked list.

        Returns:
            The first element in the doubly linked list, or None if the list is empty.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        return self.head if self.head is None else self.head.value

    def back(self):
        """Returns the last element in the doubly linked list.

        Returns:
            The last element in the doubly linked list, or None if the list is empty.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        return self.tail if self.tail is None else self.tail.value

    def append(self, value):
        """Appends a new element to the end of the linked list.

        Args:
            value: The element to append.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        new_node = Node(value)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            new_node.previous = self.tail
            self.tail = new_node
        self.size += 1

    def push(self, value):
        """Adds a new element to the beginning of the linked list.

        Args:
            value: The element to add.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        new_node = Node(value)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            new_node.next = self.head
            self.head.previous = new_node
            self.head = new_node
        self.size += 1

    def __insert_node_after(self, previous_node, new_node):
        """Inserts a new element at the head of the doubly linked list.

        Args:
            value: The element to insert.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        new_node.previous = previous_node
        if previous_node.next is not None:
            previous_node.next.previous = new_node
            new_node.next = previous_node.next
        else:
            self.tail = new_node
        previous_node.next = new_node
        self.size += 1

    def insert_after(self, previous_value, value):
        """Inserts a new element after a specified element in the linked list.

        Args:
            previous_value: The value of the element to insert the new element after.
            value: The element to insert.
        Raises:
            ValueError: If the previous element is not found in the linked list.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        previous_node = self.head
        while previous_node is not None and previous_node.value != previous_value:
            previous_node = previous_node.next
        if previous_node is None:
            raise ValueError("Node not found")
        new_node = Node(value)
        self.__insert_node_after(previous_node, new_node)

    def __insert_node_before(self, next_node, new_node):
        new_node.next = next_node
        if next_node.previous is not None:
            next_node.previous.next = new_node
            new_node.previous = next_node.previous
        else:
            self.head = new_node
        next_node.previous = new_node
        self.size += 1

    def insert_before(self, next_value, value):
        """Inserts a new element before a specified element in the linked list.

        Args:
            next_value: The value of the element to insert the new element before.
            value: The element to insert.
        Raises:
            ValueError: If the next element is not found in the linked list.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        next_node = self.head
        while next_node and next_node.value != next_value:
            next_node = next_node.next

        if next_node is not None:
            new_node = Node(value)
            self.__insert_node_before(next_node, new_node)
            return
        raise ValueError("Node not found")

    def __remove_node(self, node):
        """Removes a node from the linked list.

        Args:
            node: The node to remove.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        if node.previous is None:
            self.head = node.next
        else:
            node.previous.next = node.next
        if node.next is None:
            self.tail = node.previous
        else:
            node.next.previous = node.previous
        self.size -= 1

    def remove_all_occurrences(self, value):
        """Removes an element from the linked list.

        Args:
            value: The value of the element to remove.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        current_node = self.head
        while current_node is not None:
            if current_node.value == value:
                self.__remove_node(current_node)
            current_node = current_node.next

    def remove_first_occurrence(self, value):
        """Removes the first occurrence of an element from the linked list.

        Args:
            value: The value of the element to remove.

        Returns:
            True if the element was removed, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        current_node = self.head
        while current_node is not None:
            if current_node.value == value:
                self.__remove_node(current_node)
                return True
            current_node = current_node.next
        return False

    def remove_last_occurrence(self, value):
        """Removes the last occurrence of an element from the linked list.

        Args:
            value: The value of the element to remove.

        Returns:
            True if the element was removed, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        current_node = self.tail
        while current_node is not None:
            if current_node.value == value:
                self.__remove_node(current_node)
                return True
            current_node = current_node.previous
        return False

    def remove_first_n_occurrences(self, value, n):
        """Removes the first n occurrences of a specified value from the linked list.

        Args:
            value: The value to remove.
            n: The number of occurrences to remove.

        Returns:
            None.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """

        current_node = self.head
        count = 0
        while current_node is not None and count < n:
            if current_node.value == value:
                self.__remove_node(current_node)
                count += 1
            current_node = current_node.next

    def remove_last_n_occurrences(self, value, n):
        """Removes the first n occurrences of a specified value from the linked list.

        Args:
            value: The value to remove.
            n: The number of occurrences to remove.

        Returns:
            None.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """

        current_node = self.tail
        count = 0
        while current_node is not None and count < n:
            if current_node.value == value:
                self.__remove_node(current_node)
                count += 1
            current_node = current_node.previous

    def remove_first(self):
        """Removes the first element from the linked list.

        Raises:
            IndexError: If the linked list is empty.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        if self.head is None:
            raise IndexError("remove_head from empty LinkedList")
        self.__remove_node(self.head)

    def remove_last(self):
        """Removes the last element from the linked list.

        Raises:
            IndexError: If the linked list is empty.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        if self.tail is None:
            raise IndexError("remove_tail from empty LinkedList")
        self.__remove_node(self.tail)

    def __remove_first_at_index (self, index):
        """Removes the node at the specified index from the front of the linked list.

        Args:
            index: The index of the node to remove.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        current_node = self.head
        for i in range(index):
            current_node = current_node.next
        self.__remove_node(current_node)

    def __remove_last_at_index(self, index):
        """Removes the node at the specified index from the back of the linked list.

        Args:
            index: The index of the node to remove.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        current_node = self.tail
        for i in range(-1, index, -1):
            current_node = current_node.previous
        self.__remove_node(current_node)

    def remove_at_index(self, position):
        """Removes the element at the specified position in the linked list.

        Args:
            position: The position of the element to remove.

        Raises:
            IndexError: If the linked list is empty or if the position is out of range.

        Returns:
            True if the element was removed successfully, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        if self.size > position >= 0:
            self.__remove_first_at_index(position)
            return True
        if -self.size <= position < 0:
            self.__remove_last_at_index(position)
            return True
        raise IndexError("LinkedList index out of range")

    def remove_duplicates(self):
        """Removes all duplicate elements from the linked list.

        Returns:
            None.

        Time complexity: O(n)
        Space complexity: O(n)
        Auxiliary space: O(0)
        """
        current_node = self.head
        unordered_set = set()
        while current_node is not None:
            if current_node.value in unordered_set:
                self.__remove_node(current_node)
            else:
                unordered_set.add(current_node.value)
            current_node = current_node.next

    def replace_first_occurrence(self, old_value, new_value):
        """Updates the value of the first node in the linked list that matches the specified old value.

        Args:
            old_value: The old value to match.
            new_value: The new value to update to.

        Returns:
            True if the value was updated successfully, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        current_node = self.head
        while current_node is not None:
            if current_node.value == old_value:
                current_node.value = new_value
                return True
            current_node = current_node.next
        return False

    def replace_last_occurrence(self, old_value, new_value):
        """Updates the value of the first node in the linked list that matches the specified old value.

        Args:
            old_value: The old value to match.
            new_value: The new value to update to.

        Returns:
            True if the value was updated successfully, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        current_node = self.tail
        while current_node is not None:
            if current_node.value == old_value:
                current_node.value = new_value
                return True
            current_node = current_node.previous
        return False

    def replace_all_occurrences(self, old_value, new_value):
        """Updates the value of the all node in the linked list that matches the specified old value.

        Args:
            old_value: The old value to match.
            new_value: The new value to update to.

        Returns:
            True if at least one occurrence of the old value was replaced, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        current_node = self.head
        while current_node is not None:
            if current_node.value == old_value:
                current_node.value = new_value
            current_node = current_node.next

    def replace_first_n_occurrences(self, old_value, new_value, n):
        """Replaces the first n occurrences of the old value with the new value in the linked list.

        Args:
            old_value: The old value to replace.
            new_value: The new value to replace with.
            n: The number of occurrences to replace.

        Returns:
            True if all of the required occurrences of the old value were replaced, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        current_node = self.head
        count = 0
        while current_node is not None and count < n:
            if current_node.value == old_value:
                current_node.value = new_value
                count += 1
            current_node = current_node.next

        return True if count == n else False

    def replace_last_n_occurrences(self, old_value, new_value, n):
        """Replaces the last n occurrences of the old value with the new value in the linked list.

        Args:
            old_value: The old value to replace.
            new_value: The new value to replace with.
            n: The number of occurrences to replace.

        Returns:
            True if all of the required occurrences of the old value were replaced, False otherwise.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        current_node = self.tail
        count = 0
        while current_node is not None and count < n:
            if current_node.value == old_value:
                current_node.value = new_value
                count += 1
            current_node = current_node.previous
        return True if count == n else False

    def clear(self):
        """Clears all elements from the linked list.

        Time complexity: O(n)
        Space complexity: O(n)
        Auxiliary space: O(0)
        """
        self.head = None
        self.tail = None
        self.size = 0

    def reverse(self):
        """Reverses the linked list.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        self.tail = self.head
        current_node = self.head
        while current_node is not None:
            current_node.next, current_node.previous = current_node.previous, current_node.next
            self.head = current_node
            current_node = current_node.previous

    def count_occurrences(self, value):
        """Counts the number of occurrences of the specified value in the linked list.

        Args:
            value: The value to count.

        Returns:
            The number of occurrences of the specified value in the linked list.

        Time complexity: O(n)
        Space complexity: O(1)
        Auxiliary space: O(1)
        """
        current_node = self.head
        count = 0
        while current_node is not None:
            if current_node.value == value:
                count += 1
            current_node = current_node.next
        return count

    def is_empty(self):
        """Checks if the linked list is empty.

        Returns:
            True if the linked list is empty, False otherwise.

        Time complexity: O(1)
        Space complexity: O(1)
        Auxiliary space: O(0)
        """
        return self.head is None

    def __rotate_at(self, rotation_point):
        """Rotates the linked list at the given node.

        Args:
            node: The node at which to rotate the linked list.

        Returns:
            None.
        """
        self.tail.next = self.head
        self.head.previous = self.tail
        rotation_point.previous.next = None
        self.tail = rotation_point.previous
        rotation_point.previous = None
        self.head = rotation_point

    def __rotate_right(self, k):
        """Rotates the linked list to the right by `k` positions.

        Args:
            k: The number of positions to rotate the linked list to the right by.

        Returns:
            None.
        """
        current_node = self.head
        index = 0
        while index != k:
            current_node = current_node.next
            index += 1
        self.__rotate_at(current_node)

    def __rotate_left(self, k):
        """Rotates the linked list to the left by `k` positions.

        Args:
            k: The number of positions to rotate the linked list to the left by.

        Returns:
            None.
        """
        current_node = self.tail
        index = -1
        while index != k:
            current_node = current_node.previous
            index -= 1
        self.__rotate_at(current_node)

    def rotate(self, k):
        """Rotates the linked list by `k` positions.

        Args:
            k: The number of positions to rotate the linked list by.

        Returns:
            None.
        """
        if 0 < k < self.size:
            self.__rotate_right(k)
        if 0 > k > -self.size:
            self.__rotate_left(k)

    def __get_backward_element(self, item):
        """Gets the element at the specified index in the linked list, starting from the tail of the list.

        Args:
            item: The index of the element to get.

        Returns:
            The element at the specified index in the linked list.
        """
        index = -1
        for element in reversed(self):
            if index == item:
                return element
            index -= 1

    def __get_forward_element(self, item):
        """Gets the element at the specified index in the linked list, starting from the head of the list.

        Args:
            item: The index of the element to get.

        Returns:
            The element at the specified index in the linked list.
        """
        index = 0
        for element in self:
            if index == item:
                return element
            index += 1

    def __len__(self):
        """Returns the length of the linked list."""
        return self.size

    def __iter__(self):
        """Returns an iterator over the linked list."""
        current_node = self.head
        # Iterate over the linked list and yield the value of each node.
        while current_node is not None:
            yield current_node.value
            current_node = current_node.next

    def __getitem__(self, item):
        """Gets the element at the specified index in the linked list.

        Args:
            item: The index of the element to get.

        Raises:
            IndexError: If the index is out of range.

        Returns:
            The element at the specified index in the linked list.
        """
        if 0 <= item < self.size:
            return self.__get_forward_element(item)
        if -self.size <= item < 0:
            return self.__get_backward_element(item)
        raise IndexError("LinkedList index out of range")

    def __str__(self):
        """Returns a string representation of the linked list."""
        return f"[{', '.join(str(node) for node in self)}]"

    def __repr__(self):
        return f"LinkedList({self.__str__()})"

    def __reversed__(self):
        """Returns an iterator over the linked list in reverse order."""
        current_node = self.tail

        # Iterate over the linked list in reverse order and yield the value of each node.
        while current_node is not None:
            yield current_node.value
            current_node = current_node.previous
