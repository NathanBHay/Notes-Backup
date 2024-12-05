**Race conditions**, also called race hazard, are errors caused by the timing of actions resulting in a different result than expected. In [[Integrated Circuits|logic gates]] these issues are present when propagation delay leads to circuits having incorrect outputs. In terms of [[Threads|threads]] and [[Databases|databases]] race conditions happen when shared memory is written at the same time. To avoid race conditions **synchronisation** through concurrency control must happen between [[Parallelism|parallel]] and concurrent code in [[Distributed Computing|distributed systems]]. To achieve these there are three approaches, through using locks, or using timestamps or the optimistic approach.

A **reusable** resource can only be used by one process at a time and can't be depleted by its use. A **consumable** resource is one that can be created and destroyed by using it.

# Atomic
An atomic operation is one or more instructions that are indivisible and are considered as one operation by the parallelism model. On an [[Operating System|OS]]/concurrency level it means no context switch occurs during it. This means atmocity guarantees isolation from concurrent processes.

An atomic [[Datatypes|datatype]] is a type in a language that guarantees all its operations are atomic. This ensures accesses to the value aren't done during calculation of its new state. Most languages either ensure atomic datatypes or have standard library supporting them.

# Lock Based Concurrency Controls
Lock based concurrency controls are an approach to synchronising transactions through the use of locks which deter processes from reading or writing data. This ensures that data can be accessed concurrency without errors caused by reading data that hasn't been written or other similar race condition issues. There are two broad types of locks:
- **Shared-exclusive lock** allows for data to be read concurrently but stops writes from happening.
- **Exclusive-exclusive lock** ensures a lock can't be read or written.

Lock granularity is the amount of data that a lock is associated with. A more coarse lock may lock additional data that isn't used in a calculation however has less overhead during the locking process. In contrast a fine lock has less data locked as a result.

## Mutual Exclusion
A **critical region** is when a segment of code accesses a shared resource that can't be accessed by others at the same time. These sections require serial execution of the code as to avoid issues arising from synchronisation. **Mutual exclusion** is the idea of ensuring concurrent execution units don't access a critical region at the same time. To achieve this a enter and exit critical region constructs are provided. These function by holding onto a certain resource until the exit statement is called. There are various approaches to these with respective advantages and disadvantages.

### Semaphores
Semaphores are a [[Abstract Datatypes|abstract datatype]] used to implement mutual exclusion. They enable threads to be limited by the number of shared resources. A semaphore uses an integer value that can be modified with the atomic operations. 
- *Semaphore wait* which decrements the value, and given that it becomes negative the process will wait.
- *Semaphore signal* which increments the value, where if the value is less than or equal to zero then a process that is blocked by a wait continues.

Their are two types of semaphores, those being **binary semaphores** which only take 0 or 1, and **counting or general semaphores** which have a larger range. Due to their simplicity semaphores have very little overhead at the cost of no knowledge of the semaphores state until the operations are done. This means smart scheduling based upon priority or amount of current waiting operations can be done.

### Mutex
**Mutual exclusion locks** (Mutex) is an implementation of mutual exclusion that holds a flag set to 0 when the value is locked, and 1 when its unlocked. This allows one process or thread to hold the lock. The difference between a mutex and a binary semaphore is that the mutex must release the lock that holds it.


## Deadlocks
**Deadlocks** occurs when multiple locks are held by processes in a chain. This means unblocking data is impossible as unblocking one requires unblocking another that is required on the original holder. For a deadlock to occur four conditions must be present:
- Mutual exclusion, where a reusable resource must be only accessed by one process.
- Hold and wait, where processes may hold allocated resources while waiting.
- No preemptive, where no resource can be forcibly removed from a lock.
- Circular wait, where a closed chain of processes exists.

To handle deadlocks one of these conditions needs to be removed. Refactoring code to remove locking shared resources is one approach to this. Ensuring required resources are all requested as once or blocks being granted simultaneously is another approach. The last approach is to ignore deadlocks which is commonly called the **ostrich algorithm**.

### Deadlock Avoidance
Banker's algorithm is a deadlock avoidance algorithm that uses *resource allocation denial* to not grant resources to processes which may lead to a deadlock. This determines a state to be safe it at least one sequence of resource allocations frees the chain of locks. 

The algorithm works by maintaining two matrices with columns and rows being processes $i$ and resources $j$. The first matrix is a *claim matrix* $C$, which are integer values representing the amount of resources claimed, the second is the *allocation matrix* $A$ which are integers presenting where these resources are allocated. Two vectors are also kept representing the existing resources $R$ and the available $V$. When a process makes a class for a resource the values are calculated as:
$$C_{ij}-A_{ij}\leq V_j,\;\forall j$$

### Deadlock Detection
Deadlock detection is another approach to managing deadlocks reducing deadlocks depending on the likeliness for a deadlock to occur. As this is poled detection can be done upon all resource requests or less often for better performance. 

Deadlock detection uses a request matrix $Q$ and an allocation matrix $A$ which hold boolean values, and a resource $R$ and available vector $W$. The algorithm calculates a deadlock by searching if the process $i$ is currently unmarked in the row of $Q$ and is less than or equal to $W$. If no row is found terminate, if it is add a new row to the allocation matrix.

Recovery after detection involves either aborting process, restarting from checkpoints, or successively aborting individual processes until a deadlock doesn't occur.

## Concurrency Issues
In addition to deadlocks their are other possible issues that can be caused as the result of concurrency.
- **Starvation** occurs when a process is waiting to enter the critical section but other processes use it leading to the first process waiting as newer process enter it.
- **Priority inversion** happens when a high-priority process is in the critical section and is interrupted by a lower priority process causing potential issues.
- **Busy waiting** is when the process waiting has to run an expensive poll operation that steals resources from other processes.

# Timestamp
Timestamp based concurrency control uses timestamps to determine what actions can occur. This is done through transactions which check for the ordering of events to ensure that data isn't in a critical region.

# Barriers
A barrier is an approach to synchronisation that uses a method to specify a barrier for all concurrent execution units to wait at.