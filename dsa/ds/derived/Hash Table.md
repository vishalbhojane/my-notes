Introduction to Hash Table:
- A Hash Table is a data structure that stores key-value pairs.
- It uses a hash function to compute an index into an array of buckets or slots.
- Ideal for quick insertion, deletion, and retrieval of data.
- Provides average time complexity of O(1) for basic operations.
- Handles collisions through methods like chaining or open addressing.

Real-world examples of Hash Table usage:
1. Database indexing
2. Caching systems (e.g., web browser cache)
3. Symbol tables in compilers and interpreters
4. Password verification
5. Spell checkers and dictionaries

JavaScript Implementation of a Hash Table:

```js
class HashTable {
  constructor(size = 53) {
    this.table = new Array(size);
    this.size = size;
  }

  // Hash function to convert key to index
  hash(key) {
    let total = 0;
    for (let i = 0; i < key.length; i++) {
      total += key.charCodeAt(i);
    }
    return total % this.size;
  }

  // Set a key-value pair in the hash table
  set(key, value) {
    const index = this.hash(key);
    if (!this.table[index]) {
      this.table[index] = [];
    }
    // Handle collisions by chaining (storing multiple key-value pairs at the same index)
    for (let i = 0; i < this.table[index].length; i++) {
      if (this.table[index][i][0] === key) {
        this.table[index][i][1] = value;
        return;
      }
    }
    this.table[index].push([key, value]);
  }

  // Get a value by key from the hash table
  get(key) {
    const index = this.hash(key);
    if (this.table[index]) {
      for (let i = 0; i < this.table[index].length; i++) {
        if (this.table[index][i][0] === key) {
          return this.table[index][i][1];
        }
      }
    }
    return undefined;
  }

  // Remove a key-value pair from the hash table
  remove(key) {
    const index = this.hash(key);
    if (this.table[index]) {
      for (let i = 0; i < this.table[index].length; i++) {
        if (this.table[index][i][0] === key) {
          this.table[index].splice(i, 1);
          return true;
        }
      }
    }
    return false;
  }

  // Display the hash table
  display() {
    for (let i = 0; i < this.table.length; i++) {
      if (this.table[i]) {
        console.log(i, this.table[i]);
      }
    }
  }
}

// Usage example
const ht = new HashTable(10);
ht.set("name", "John");
ht.set("age", 30);
ht.set("city", "New York");
ht.display();
console.log(ht.get("name")); // Output: John
ht.remove("age");
ht.display();
```

```
CLASS HashTable
  table = new Array(size)
  size = given size or default 53

  FUNCTION hash(key)
    total = 0
    FOR EACH character in key
      total += ASCII value of character
    RETURN total % size

  FUNCTION set(key, value)
    index = hash(key)
    IF table[index] is empty
      table[index] = new array
    FOR EACH pair in table[index]
      IF pair[0] equals key
        pair[1] = value
        RETURN
    ADD [key, value] to table[index]

  FUNCTION get(key)
    index = hash(key)
    IF table[index] exists
      FOR EACH pair in table[index]
        IF pair[0] equals key
          RETURN pair[1]
    RETURN undefined

  FUNCTION remove(key)
    index = hash(key)
    IF table[index] exists
      FOR EACH pair in table[index] with index i
        IF pair[0] equals key
          REMOVE pair from table[index]
          RETURN true
    RETURN false

  FUNCTION display()
    FOR EACH bucket in table with index i
      IF bucket is not empty
        PRINT i and bucket

END CLASS
```

This implementation provides a basic structure for a hash table with methods for setting, getting, removing, and displaying key-value pairs. The hash function used here is simple for demonstration purposes; in practice, more sophisticated hash functions are often used to ensure a good distribution of keys.

The pseudocode offers a quick overview of the logic behind each operation. Note that this implementation uses chaining to handle collisions, where multiple key-value pairs can be stored at the same index in a nested array.