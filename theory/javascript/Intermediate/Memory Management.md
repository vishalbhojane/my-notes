Memory management in JavaScript is handled automatically by the runtime environment, typically the JavaScript engine in web browsers or Node.js

JavaScript uses a garbage collector to manage memory and ensure that developers do not need to manually allocate or deallocate memory

Memory Life Cycle
1. Allocates the memory we need:
2. Use the allocated memory
3. Release the memory when not in uses

### JavaScript engines have two places to store data
##### Stack
used to store static data.
Static data refers to data whose size is known by the engine during compile time
includes primitive values like strings, numbers, Boolean, null, and undefined
References that point to objects and functions are also included
process is known as static memory allocation.
##### Heap
used to store objects and functions in JavaScript
The engine doesn’t allocate a fixed amount of memory.
Instead, it allocates more space as required.

| Stack                               | Heap                       |
| ----------------------------------- | -------------------------- |
| Primitive data types and references | Objects and functions      |
| Size is known at compile time       | Size is known at run time  |
| Fixed memory allocated              | No limit for object memory |
