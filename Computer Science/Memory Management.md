Memory management is the idea of ensuring effective declaration, retrieval and freeing of program [[Memory|memory]]. This is important in high-performance applications or languages with greater support for management of internal memory. 

The most basic element of memory management is a **memory allocator**, in a language like [[C Language|C]] this is called `malloc()`, however most languages support some functionality albeit occasionally abstracted. This memory allocator takes as input the size of the space being allocated into [[Memory#Virtual Memory#Memory Allocation|heap]] memory and returns a [[Datatypes#Pointer|pointer]] to the memory location. In addition to the allocator their is usually a method of removing this allocated memory, in C this is called `free()`.

# Lifetimes
A lifetime is the concept within memory management and [[Object Orientated Programming|object orientated design]] of the period of time between the allocation and freeing of a block of memory. The lifetime of memory can either be determined by the programmer, in cases where manual destruction is done, or automatically in cases where a garbage collector exists. Lifetimes can also have direct implementations where the programmer is able to declare them. This can be seen in certain memory structures or as annotations in languages such as [[Rust#Lifetime Annotations|Rust]].

# Memory Issues
A **memory leak** occurs when a lifetime exists longer than its use, meaning memory is left allocated without being freed. In general it is best to minimise memory leaking especially in cases where the program has limited memory or runs for a long time. 

This can lead to a performance degradation and issues as additionally allocated memory proves

# Memory Structures
Within memory management there are a variety of unique [[Data Structures|data structures]] and strategies which give a more effective way of 

## Arena Allocator
An arena or **linear allocator** is a data structure which holds a series of allocated memory and an offset to the current part within the memory. An arena allocator provides the advantage of declaring a [[Memory Management#Lifetimes|lifetime]] for a set of memory. This decreases complexity of an application as it enables easier analysis of lifetimes of associated data (especially in cases where dependencies are prevalent). Additionally arenas also reduce repeated allocation and free calls from the program. Despite this arena allocators can suffer from 'memory leaks' in cases where segments of the arena can be considered dead, as such careful analysis of how to use arenas is important.
```c
struct Arena {
	void *arena;
	size_t offset;
};
void *arena_alloc(size_t size); // Create arena
void arena_free(Arena *arena); // Free arena
size_t arena_offset(Arena *arena);
void *arena_push(Arena *arena, size_t size); // Add to arena
void *arena_pop(Arena *arena, size_t size); // Remove from arena
```

Above is a basic arena implementation, note the similarity to the stack, especially in cases where more helper functions are used. Further improvements to this implementation can include adherence to the word boundary or headers for declaring sizes of blocks. Arenas can also be made to fit a specific use case. Some examples of these are:
- **Frame arenas**, are arenas that are started within a frame and ended by the end. This is useful in cases where stack allocation isn't available.
- **Dynamic arenas**, have the ability to resize themselves. This is good in cases with few resizes.