A data structure defines how [[Abstract Datatypes]] are implemented at a code level. This means a data structure handles how the data is kept as well as the method to achieve the required operations. There are a variety of different data structure to implement a certain abstract datatype each with their own advantages and disadvantages.

# Data Structure Traits
Data structures can be further classified with traits that illustrate additional functionality.

## Ephemeral Vs Persistence
**Persistent** data structures record their last state in some capacity. Persistent data structures are common in functional languages. This is as opposed to **ephemeral** data structures which only store their current state and are common in imperative languages.

## Rebuilding
Rebuilding is the process of rebuilding a data structure as to ensure an invariant. In the case of search trees this usually comes in the form of balance, while other data structures may need to be rebuilt for a variety of reasons. There are a few different methods to rebuild and these include:
- **Batched Rebuilding**, where a data structure is only rebuilt after a certain amount of operations to guarantee amortized time.
- **Global Rebuilding**, where a data structure is incrementally rebuilt upon every call to a subroutine.

# Basic Data Structures
There are a variety of basic data structures which are commonly found implemented with most [[Programming Languages|basic languages]]. The ones that aren't are easily implementable in their respective languages.

## Array
A array is the most basic data structure that is found within most languages. It stores a series of data usually in a contiguous form. Arrays are usually kept as a pointer that can be indexed to find a specific element in memory. Since arrays are implemented by the language their choice of indexes vary with $0$ being the most common. Additionally some languages store length in the memory allowing $O(1)$ length lookup while others require manual recording with $O(n)$ or not length operation existing at all.

**Multi-dimensional arrays** are the result of nesting multiple arrays within each other. They are considered **regular** if all arrays of the same dimension have the same size. They are considered **irregular** if they aren't all equal.

**Dynamically-sized arrays** are a resizable array, as opposed to **static arrays**. This can be implemented a variety of ways from expanding to adjacent memory, creating a new array in another place within the memory, or storing a pointer to the next section of memory.

**Sorted Arrays** are another common form of arrays that have the advantage of search and order statistics computing faster.

## Linked List
A linked list is a list abstract datatype which keeps data, and the pointer to the next part of the data. This allows it to be linearly traversed and cheaply expanded. Its storage of a pointer does lead to it being larger than an array of the same size. Some extra operations of a linked list include:
- **Index** finds index of given item.
- **Add at Index** rewrites a point at previous index to redirect to new item.
- **Delete at Index** frees memory and rewrites the previous pointer to the next address.

An iterator is sometimes required for a linked list. This can be done by either creating a new variable which keeps the current point its up to, or by making a object to iterate through the datatype.

Any linked datatype is usually referred to as a form of **linked storage**. This is as opposed to the **contiguous storage** which is the array format of data storage, where all data is adjacent. In general the access of elements is constant.

**Doubly Linked List** are an expansion upon a linked list that stores a pointer to both the tail and head. This enables traversal from either way. Another common implementation of linked lists are **circular linked list** that have a tail that connects to the first element.

## Lookup Structures
A lookup structure is a data structure that beyond storing the elements inside the structure, also stores a key that can be used for retrieval of an element in $O(1)$. The most common implementation of this is in a lookup table that stores a key and an item and can be indexed from the key. This basic implementation has a search that finds elements in $O(\log n)$, an insertion that finds the location and shifts all items thus $O(n)$, and a similar deletion. Lookup structures can be improved through the use of trees, or more complex structures such as [[Hashtables|hash tables]] which use a function to index their elements.

## Trees
A [[Tree Data Structures|tree]] is a basic data structure based upon [[Graph Theory|graph theory]] that stores a value and pointers to either a particular amount of nodes, or hold a data structure which stores a sequence of nodes. As a result of this structure a tree usually has a traversal operation, as well as insertion and deletion.

## Stack Data Structures
**Array Stack** is an implementation of a stack using arrays. It allocates a blank array that fills up with stack elements until it reaches the limit. **Linked Stack** is another implementation which uses the nodes from the linked list to operate as the stack elements. This keeps a single pointer of the top as to do push and pop operations.

## Queue Data Structures
**Linear Queue** is an implementation which stores a pointer to the start and rear within an array. A **Circular Queue** is another implementation which uses a **circular linked list**, or linear queue to produce a queue which loops when it reaches the end. **Linked Queue** implements nodes from the linked list as to operate as queue elements. Thus, the first and last pointers need to be kept for enqueueing and dequeuing.
