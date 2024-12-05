Threads are a unit of execution responsible for concurrency. Threads are a component of a [[Processes|process]] that is moderated by the [[Operating System#Scheduling|scheduler]]. As such they share process data while maintaining their own program counter, registers, stack and state information. Additionally threads are faster to create than processes and have faster methods of communication. Multi-threading of a process provides a form of [[Parallelism|parallelism]]. There are various implementations of threads at various levels.

# User Level Threads
User level threads are managed by the application rather than the kernel. These threads are implemented on the software side and don't require kernel mode privileges. Despite this blocking system calls can make this form of concurrency difficult on [[Operating System|OS]] that don't support threads.

# Kernel Level Threads
Kernel level threads are managed by the kernel rather than a thread library. This implementation allows easier parallelism by as threads can interact with multiple processors easier. As a result of this implementation kernel mode switches are required resulting in additional overhead.

# POSIX Threads
The most popular implementation of threads are [[Operating System#OS Types#POSIX|POSIX]] threads. These are the standard of all Unix-like systems. The interface, compiled with `-lpthread` in [[C Language|C]], provides a creation function which takes a function and its arguments and a join function to wait for the execution of all threads.
```c
int pthread_create(pthread_t *tid, thread_attr_t tattr, void*(*routine)(void *), void *arg);
int pthread_join(pthread_t tid, void **status);
```