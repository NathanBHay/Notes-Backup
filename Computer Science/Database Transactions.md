Transactions are a logical unit of work within a [[Databases|database]] that must be done entirely completed or aborted, meaning no intermediate states. They result in either a change to the original database given they succeed or get data from the database. A **consistent database state** is one in which all data integrity constraints are satisfied. This means that all databases within the system have the correct data, and don't violate any business rules. A **database request** is the equivalent of a single [[SQL]] statement or an operation in a DBMS software. A transaction has the following properties:
- **Atomicity** requires all operations to be completed, and if not aborted.
- **Consistency** indicates the permanence of the database's consistent state.
- **Isolation** means that data used during the execution of a transaction cannot be used by another transaction until the first is completed.
 - **Durability** means that a transaction's changes can't be undone or lost.
 - **Serializability** states that given multiple concurrent transactions the operations create the same final data base state given they were executed sequentially.

Database transactions have two main operations that have been standardised. **Commit** means that all changes are permanently recorded within the database. While **rollback** means the previous consistent state is restored. These transactions are usually stored within a log.

# Concurrency Controls
Concurrency control is the goal of executing multiple transactions without any issues. Control over this is important as a shared database is at threat of creating data integrity and consistency problems. The three main problems that facer concurrent databases are:
- **Lost Updates** which occur when two concurrent transactions are updating the same data element and one is lost.
- **Uncommitted Data** occurs when two transactions are executed concurrently and the first transaction is rolled back after the second transaction has already accessed the uncommitted data.
- **Inconsistent Retrievals** occur when a transaction accesses data before and after a transaction has finished.

## Schedular
To avoid the above issues a **schedular** can be used to order the operations. This makes concurrent transactions happen in a serial order. This results in a **serializable schedule** of transaction operations. Another approach to ensuring serializability is to use a lock.

## Locks
A **lock** is an operation which stops access from others to access the database. These can either be called before operations that will conflict with others, or just in general during access which is called **pessimistic locking**. Databases commonly have multiple levels of locks referred to as **lock granularity**. These levels include:
- **Database Level** locks ensure the entire database is locked, preventing any access. This approach ensures no conflicting operations however can be slow on systems with many operations.
- **Table Level** locks the entire table as to prevent issues arising from changing that one table. These locks due to their localisation can be much more efficient.
- **Page Level** locks the entire disk page which is the directly addressable section of a disk. These are the most common locks due to them being smaller than a table.
- **Row Level** locks an entire row for an edit. This makes is simple for others to access data without calling conflicts.
- **Field Level** locks are the smallest and lock one field. They are barely used as they have a high over head and usually fields are edited with other fields.

These locks can be further subclassified as a **binary lock** which represents the states of locked and unlocked, as well as **shared/exclusive locks** which is when access is reversed specifically for the transaction of that locked object. This means that operations such as read are shared and don't result in a failure while write will throw an error as the exclusive lock is stopping the operation.

**Two phase locking** (2PL) defines how transactions acquire and relinquish their lock. These locks guarantees serializability. The two phases of these locks are growing phases which the transactions acquires all the required locks, and the **shrinking phase** where all locks are released. These operate on the rule that no two transaction can have a conflicting lock, and no unlock operation can precede a lock operation in the same transaction. Furthermore no data is affected until all locks are obtained. While these locks are effective they are still prone to **deadlocks** which occur when two transactions wait indefinitely for each other to unlock. Deadlocks are usually minimized through a DBMS software's prevention, detection, and avoidance measures.

# Database Recovery
**Database recovery** restores a database from a given state to a previously consistent state. These techniques are based on the atomic transaction property, that all portions of the transaction must be treated as a single logical unit of work. There are four main concepts that are found within the recovery process:
- **Write-ahead-log protocol** ensures that transaction logs are always written before any database data is actually updated. This ensures in case of a failure the data can always be restored.
- **Redundant transaction logs** states that multiple logs should be kept.
- **Buffers** are temporary storage areas in primary memory to speed up disk operations/
- **Checkpoints** are operations which write data into the memory buffer. These are usually periodically done through certain parameters.

The recovery procedure uses a **deferred-write technique** that states operations don't immediately update the database but instead the transaction log is updated and the database is physically updated only with data from committed transactions. This recovery technique follows the order:
1. Identify the last checkpoint in the log.
2. For transactions that performed a commit operation after the last checkpoint the DBMS uses a transaction log to redo the transactions and updates in the database. Doing oldest operations first.
3. For any transaction that had a rollback operation after the last checkpoint nothing needs to be done.

Another recovery process is the **write-through technique** where the database is immediately updated by a transaction operation during the transactions execution. This follows a process of:
1. Identify the last checkpoint in the log.
2. For transactions committed after the checkpoint the DBMS repeats the transaction after using values from the transaction log.
3. For any rollback operations after the last checkpoint before the failure occurred uses the records to undo them before using the values in the log.
