A **process** is an instance of a computer program that is being executed. This process is assigned an **address space**, which is a list of memory location that it can manipulate. This space includes the program's executable called an **image**, memory (usually [[Memory#Virtual Memory|virtual]] arranged in a stack/heap), operating system descriptors such as file descriptors, and context of the program. This information is commonly stored in a **process control block** which tracks this information from a process ID. These blocks are then allocated to a **process table** in most OS.

An **active process** is a process that a user interacts with, in contrast a **background process** without user intervention. Background processes which exist to handle one process upon a request are called **daemons**.

Unix processes have a various states.
- **User/kernel running** whether process is executing in user or kernel space.
- **Ready to run, in memory**, in memory waiting for kernel to schedule.
- **Asleep in memory** unable to execute until event occurs.
- **Ready to run, swapped**, process is ready to run but process not in memory.
- **Sleeping, swapped**, process is awaiting event to swap to secondary storage.
- **Preempted**, process is returning from kernel to user.
- **Created**, newly created and not ready to run.
- **Zombie**, process no longer running but leaving data for parent.

 Processes are allocated in a hierarchy in Unix with the root maintaining its own processes, with one of these processes being the user. This user then maintains its own individual processes. A *child processes* can be spawned by the parent process. The parent cannot disinherit its child process. In Win32 processes don't conform to a hierarchy, rather they give a parent token to a child, allowing easier manipulation of the order.

## Process Creation/Termination
Process creation depends on the [[Operating System|OS]] with `fork` used to create processes by copying the process that called the operation. This allows the parent to create a child one. While `CreateProcess` is used on windows. 

Process termination happens in 4 different contexts:
- *Normal exit* where the process terminates as the program execution as ended.
- *Error exit* where the process discovers a fatal error, such as a compilation error.
- *Fatal error* where the process terminates due to an internal error.
- *Killed by another process* where the process is killed by another process ending it.
  
## Inter-Process Communication
Inter-process communication (**IPC**) is usually handled by the [[Operating System|operating system]] to ensure safe interaction between processes. Communication can be handled through a variety of methods both within the device and over [[Networks|networks]]. The broad approaches to this are:
- **Stream-orientated IPC** which communications through streams of data interpreted in a [[Abstract Datatypes#Queue|FIFO]] form. This form is considered *reliable* if no information is lost during sending. Some examples of stream orientated IPC are [[Sockets|sockets]] and [[Processes#Inter-Process Communication#Pipes & Process Substitution|pipes]].
- **[[Message Passing|Discrete message passing]]**  where data is transferred through structured messages. This usually is better in cases where data needs to be interpreted in a more complex way than FIFO. Some examples include [[Processes#Message Queues|message queues]], [[Processes#Signals|signals]], or any message passing interface like OpenMPI.

### Pipes & Process Substitution
**Pipes** are a method to one-way connect processes that is commonly found in many shells. A **anonymous pipe** `|` is a pipe which connects the output of one related process to the input of another. A **named pipe** `>` allows writing process information to be transferred to a file, allowing IPC through [[Shared Memory|shared memory]]. These methods enforce synchronisation between reader and writer with a circular buffer implemented by the kernel. Both create pseudo-files to represent the input and output buffers.

**Process substitution** allows for multiple arguments to be substituted by the shell through the `<(...)` syntax. This allows for more advanced operations and decreases the need to write files.

### Signals
A Unix signal is a standardised set of messages in Unix used to communicate between processes. These signals are asynchronous and are directed by the kernel. The signal is then either handled by the operating system's default method of handling the signal or intercepted by a *signal handler* which determines what action will occur. Signals provide a simple form of IPC however suffer from slow speeds and low bandwidth. Some common signals are:
- `SIGKILL`, kills a process and can't be caught by a signal handler.
- `SIGSTOP`, pauses a process and also can't be modified by handler.
- `SIGINT`, an interrupt signal that can be called with `Ctrl-C`.
- `SIGTSTP`, terminal stop that can be called with `Ctrl-Z`.
- `SIGQUIT`, quit and is sent by `Ctrl-\`
- `SIGSEGV`, when a segmentation fault occurs.

Creating a signal handler can be done through the `signal.h` library. This allows definition of a handler that can take an enum representing the number.

### Message Queues
Message queues are a kernel resource used for creating messages with distinct types. Queues can be used to allow multiple processes to communicate in a asynchronous way. A message consists of a header with the *type*, *destination id*, *source id*, message length and other control information, and a body. These message queues provide structure but lack a fast speed.