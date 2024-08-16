---
title: "Hash Table"
datePublished: Fri Aug 16 2024 19:51:24 GMT+0000 (Coordinated Universal Time)
cuid: clzx4kgr4000108lah04rgbui
slug: hash-table
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723838573901/4d52d8fb-680e-4646-8b0e-66daa6871945.png
tags: algorithms, data-structures, dsa, hash-table

---

Hash tables, also known as hash maps, are a common data structure used to store key-value pairs.

* They are very efficient for lookups, inserts, and deletions, typically operating in O(1) time.
    
* In JavaScript, the native object can be used as a hash table, though there is also a `Map` object introduced in ES6 that provides similar functionality with some advantages.
    

### Key Concepts of Hash Tables

1. **Hash Function**: A hash function takes an input (or key) and returns a fixed-size string of bytes. The output is usually a numerical index that corresponds to where the value associated with the key should be stored in the array.
    
2. **Collision Handling**: When two keys hash to the same index, this is called a collision. Collisions can be handled using:
    
    * **Chaining**: Each array index points to a list of entries that have the same hash index.
        
    * **Open Addressing**: When a collision occurs, the algorithm searches for the next available slot.
        
3. **Load Factor**: The load factor is a measure of how full the hash table is. A higher load factor means there are more elements in the hash table, which could lead to more collisions. It is usually advisable to resize the hash table when the load factor exceeds a certain threshold.
    

### Code

```javascript
class HashTable {
  constructor(size = 53) {
    this.keyMap = new Array(size);
  }

  _hash(key) {
    let total = 0;
    for (const char of key) {
      console.log(char);
      total = char.charCodeAt(0);
    }
    console.log(total, total % this.keyMap.length);
    return total % this.keyMap.length;
  }

  set(key, value) {
    let index = this._hash(key);
    if (!this.keyMap[index]) {
      this.keyMap[index] = [];
    }
    this.keyMap[index].push([key, value]);
  }

  get(key) {
    let index = this._hash(key);
    if (this.keyMap[index]) {
      for (let i = 0; i < this.keyMap[index].length; i++) {
        if (this.keyMap[index][i][0] === key) {
          return this.keyMap[index][i][1];
        }
      }
    }
    return undefined;
  }

  remove(key) {
    let index = this._hash(key);
    if (this.keyMap[index]) {
      for (let i = 0; i < this.keyMap[index].length; i++) {
        if (this.keyMap[index][i][0] === key) {
          this.keyMap[index].splice(i, 1);
          return true;
        }
      }
    }
    return false;
  }

  display() {
    for (let i = 0; i < this.keyMap.length; i++) {
      if (this.keyMap[i]) {
        for (let j = 0; j < this.keyMap[i].length; j++) {
          console.log(this.keyMap[i][j][0] + " : " + this.keyMap[i][j][1]);
        }
      }
    }
  }
}
```

```javascript
const hash = new HashTable();

hash.set("pink", "#FFC0CB");
hash.set("cyan", "#00FFFF");
hash.set("purple", "#800080");

console.log(hash.get("pink"));
console.log(hash.get("cyan"));

hash.display();

hash.remove("cyan");
hash.display();
```

### Time Complexity

* **Hash Function (**`_hash`): `O(k)` for large keys, but generally `O(1)`.
    
* **Set Method (**`set`): `O(m)` in the worst case due to collisions.
    
* **Get Method (**`get`): `O(m)` in the worst case due to collisions.
    
* **Remove Method (**`remove`): `O(m)` in the worst case due to collisions.
    
* **Display Method (**`display`): `O(n + m)` due to iterating through the entire hash table and key-value pairs.