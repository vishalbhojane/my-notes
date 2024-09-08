### Memory life cycle includes
1. Allocate the memory you need
2. Use the allocated memory (read, write)
3. Release the allocated memory when it is not needed anymore

Low-level languages like C, have manual memory management primitives such as` malloc()` and `free()`

Some high-level languages, such as JavaScript, utilize a form of automatic memory management known as garbage collection (GC).

the purpose of a garbage collector is to monitor memory allocation and determine when a block of allocated memory is no longer needed and reclaim it