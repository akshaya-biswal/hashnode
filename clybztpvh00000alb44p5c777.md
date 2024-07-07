---
title: "Hash Table"
datePublished: Sun Jul 07 2024 20:15:46 GMT+0000 (Coordinated Universal Time)
cuid: clybztpvh00000alb44p5c777
slug: hash-table
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720383227758/7715de4d-70c5-408b-a812-92e4cc3750d6.jpeg
tags: programming-blogs, python, data-structures, python3, hash-table, codenewbies, hashmap

---

* A **hash table** (or hash map) is a data structure that implements an associative array, a structure that can map keys to values.
    
* It uses a hash function to compute an index.
    

### Operations

| Operation | Average Time Complexity | Worst-Case Time Complexity | Space Complexity |
| --- | --- | --- | --- |
| Insert | O(1) | O(n) | O(n) |
| Delete | O(1) | O(n) | O(n) |
| Search | O(1) | O(n) | O(n) |
| Update | O(1) | O(n) | O(n) |

### Code

```python
class HashTable:
    def __init__(self, size):
        self.size = size
        self.table = [None] * size

    # Computes the hash index for the given key
    def _hash_function(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        index = self._hash_function(key)
        # Initializes the list at the bucket if it's empty
        if self.table[index] is None:
            self.table[index] = []

        for pair in self.table[index]:
            # If key is found, update the value
            if pair[0] == key:
                pair[1] = value
                return
        # If key is not found, append the new key-value pair
        self.table[index].append([key, value])

    def delete(self, key):
        index = self._hash_function(key)
        # If the bucket is empty, key doesn't exist
        if self.table[index] is None:
            return

        for i, pair in enumerate(self.table[index]):
            # If key is found, delete the key-value pair
            if pair[0] == key:
                del self.table[index][i]
                return

    def search(self, key):
        index = self._hash_function(key)
        # If the bucket is empty, key doesn't exist
        if self.table[index] is None:
            return None

        for pair in self.table[index]:
            # If key is found, return the value
            if pair[0] == key:
                return pair[1]
        # If key is not found in the list
        return None

    # Update is same as insert in this case
    def update(self, key, value):
        self.insert(key, value)

    def display_table(self):
        for index, bucket in enumerate(self.table):
            print(f"Bucket {index}: {bucket}")


# Example Usage
hash_table = HashTable(10)
hash_table.insert("apple", 100)
hash_table.insert("banana", 200)
hash_table.insert("cherry", 300)
hash_table.insert("date", 400)
hash_table.insert("mango", 100)


print(hash_table.search("apple"))  # Output: 100
print(hash_table.search("banana"))  # Output: 200

hash_table.update("mango", 150)

hash_table.display_table()
```

### Advantages

* Hash tables provide O(1) average time complexity for search, insert, and delete operations, making them extremely efficient for lookups.
    
* Hash tables can handle a wide variety of data types as keys, including integers, strings, and even objects, as long as the keys can be hashed.
    

* Dynamic resizing ensures that the average-case time complexity remains efficient even as the number of elements grows.
    

### Disadvantages

* Hash tables may require more memory compared to other data structures due to the need for storing keys, values, and handling collisions.
    

* Hash tables do not maintain the order of elements. If you need to traverse elements in a specific order, other data structures like balanced trees or linked lists might be more appropriate.
    
* In the worst-case scenario, when many collisions occur, the time complexity for operations can degrade to O(n), where n is the number of elements in the hash table.
    

### Real Example

* Dictionary in python
    
* Object in JavaScript