Functional data structures are an implementation of [[Abstract Datatypes|abstract datatypes]] through a [[Functional Programming|functional programming]] lens. All functional data structures are considered **immutable data structures** and furthermore are in general **persistent**. Due to the functional nature of most data structures use recursion as the primary method of loop control and take advantage of garbage collection. **Path Copying** is a common strategy for implementing persistent data structures. It functions similar to a traversal algorithm however copies the node at each recursion. This enables the recreation of the data structure with any required additions.

The advantages of functional data structures usually come in the form of persistence and being less error prone. Despite this there are a few common traits that data structures that can't be created functionally share. These are:
- **Random access** is hard to simulate with path copying and requires a complex implementation to create associative arrays.
- **Cycles** are also difficult to simulate since path copying only copies a certain direction. This means doubly linked lists and similar types are difficult to create.
- **Multiple Entry Points** mean data structures that can be accessed from places other than the root can't be path copied successfully.
- **Unpredictable Access Patterns** are difficult to simulate.

# Persistence
Most data structures within functional languages can either be used ephemerally, where the previous version of the data structures is ignored, or persistently. If used persistently the process of [[Algorithms#Amortized Analysis|amortized analysis]] becomes difficult as the previous version of the data structure doesn't bank up credits from previous operations as the previous version is immutable. This means there are multiple logical futures each competing to spend the same credit. To fix this problem lazy evaluation is used to create a logical future where the amortized complexity is guaranteed.

# Cons List
Cons List are a type of [[Abstract Datatypes#Linked List|linked list]] which is composed of [[Functional Programming#Pure Functions|pure functions]] as to make up each item stored. This leads to a series of nested functions keeping the data in closured pockets. It can be visualised as:
```
(<data>, <func>) -> (<data>, <null>)
```
With the end signified by a null function as it has reached the end. Each of these **cons** segments take arguments in the form of a bit of data, as well as a function which links to the next set of data. This has functions which are able to read the `head` of the data, as well as to read the `rest` of the data through a function which links the data.
```haskell
data List a = Nil | Cons a (List a)
```
Cons list allow also for a basic **stack** implementation in functional languages. This is usually achieved through a similar approach to a cons list.

# Common Data Structures
There are a variety of imperative data structures that can be easily implemented functionally. A [[Search Trees|Binary Tree]] is one such data structure that can be easily implemented functionally, usually requiring a ordering type class. A type signature for the nodes can easily be created in every functional language. A Haskell type signature would follow:
```haskell
data BinaryTree a = Nil | Node a (BinaryTree a) (BinaryTree a)
```
This signature can similarly be used for [[Heap Structures#Leftist Trees|leftist heaps]], and with some expansion [[Search Trees#Red-Black Trees|red-black trees]].

# Queue
The most basic implementation is through the use of a pair of lists for the **front** and **rear** of the queue, with the rear queue being reversed. This means the front of the queue is accessible from the first element of the front, and the last element is accessible from the first element of the rear. **Insertion** into the queue simply adds an element to the front of the rear. While **removal** removes the first element of the front. Additionally both of these operations maintain the invariant that if the front lit is empty reverse the rear and set it as the new front with an empty rear. A Haskell implementation would follow:
```haskell
data BatchedQueue a = BatchedQ [a] [a]

checkf :: (Ord a) => [a] -> [a] -> BatchedQueue a
checkf [] r = BatchedQ (reverse r) []
checkf f r = BatchedQ f r

enqueue :: (Ord a) => a -> BatchedQueue a -> BatchedQueue a
enqueue x (BatchedQ f r) = checkf f (x:r)

front :: (Ord a) => BatchedQueue a -> a
front (BatchedQ [] _) = error "Empty Queue"
front (BatchedQ (x:_) _) = x

dequeue :: (Ord a) => BatchedQueue a -> BatchedQueue a
dequeue (BatchedQ [] _) = error "Empty Queue"
dequeue (BatchedQ (f:fs) r) = checkf fs r
```

This approach allows an $O(1)$ amortized complexity for all operations given the queue is used ephemerally, discarding the old queue and only using the new variant. However, if used persistently this amortized complexity can be ignored
