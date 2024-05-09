An abstract [[Datatypes|datatype]] is a mathematical model that represents data through a definition of possible operations and values. This is as opposed to a **data structure** which defines how this abstract datatype is implemented. Many abstract datatypes share a set of common operations, those being:
- **Create** which forms the ADT.
- **Empty** checks if the datatype is empty.
- **Length** returns the length of the ADT.
- **Top/Peek** returns the top element of the ADT.

In comparison to a [[Data Structures|data structure]], a abstract datatype is used to define the basic operations and how the resources are stored in an abstract capacity, rather than an actual implementation of how these operations are done.

# Variables
A variable is a single element that can be used to represent a model. Most datatypes can be considered as comprising multiple variables to form them. A variable, and most data types in general, can either be considered **mutable** or **immutable**. With an immutable variable being unable to be changed after compilation has happened. This is usually declared with a constant syntax.

# List
A list or array is an abstract datatype that contains a set of data. The amount of elements within an list can have a fixed or dynamic size. Lists can declared within each other leading to a list defined by n-dimensions. Within mathematics a list proves similar to a [[Linear Algebra|matrices]] or vector.

# Deque
A deque or **double ended queue** is an abstract datatype that is accessible from the front and back, usually with an operation to add to the back, and occasionally the front. It will therefore usually have the following operations:
- **Append** which adds an item to the end of the list.
- **Front** which gets the first element in the list.
- **End** which gets the last element in the list.

# Sorted List
A sorted list is an ADT which keeps a list sorted in increasing or decreasing order. The list has the invariant that every item is greater or equal to the previous one. To operate a sorted list requires a search algorithm to find the index of a given item, as well as an add item that automatically sorts it into the list. Its common methods are:
- **Add** sorts the item into the list.
- **Remove** finds the item and removes it.
- **Index** finds the index of an item.

# Stack
A stack is a **Last-in-First-Out** (LIFO) list that can't be accessed from any element other than the top. Its unique operations are:
- **Push** adds an item to the top of the stack.
- **Pop** removes and returns the top element off the stack.

# Queue
A queue is a **First-in-First-Out** (FIFO) list than can only be accessed from the front. Its main operations are:
- **Enqueue/Append** adds an item to the back.
- **Dequeue/Serve** removes and returns an item from the front.

# Priority Queue
A priority queue is a queue that keeps an index for order.
- **Enqueue/Append** adds an item to the given index.
- **Dequeue/Serve** removes and returns an item from the front.
- **Update** changes an item's index.

A priority queue can be implemented through the use of a sorted list if the data stored is contiguous. Another method uses binary trees where each inserted element is put as the connection between two nodes with a key between the two. The last method is a heap.

**Double ended priority queues** are a version of priority queues that maintain an ability to get the minimum and maximum keyed elements.

# Dictionary
A dictionary is a datatype which stores a key, and a value. This is similar to a two dimensional array, however has further implementations of search for key features. Its key operations are:
- **Search** gets an item and returns the key.
- **Find** gets the key and returns the item.

Commonly dictionaries are implemented with hash tables.
