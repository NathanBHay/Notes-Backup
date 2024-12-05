Shared memory is [[Memory|memory]] that can be accessed by multiple programs to provide a form of communication. Shared memory can be found between [[Processes|processes]], or within a [[Parallelism|parallel]] context like through [[Threads|threads]]. These approaches are easier than other IPC approaches however require [[Concurrency Control|synchronisation protections]]. Shared memory can be done on a software or hardware level.

# Hardware-Level Shared Memory
Hardware-level shared memory is concerned ensuring the [[CPU|processor]] has a form of shared memory, whether on a cache or more often a [[Memory|RAM]] level. This approach can be classified into:
- **Uniform memory access** (**UMA**), where all processes share physical memory uniformly. This means access time is independent of processor or memory location. This is better for general purpose and time-sharing applications. It can be used to improve speed of large programs.
- **Non-uniform memory access** (**NUMA**), where memory access time depends on memory location relative to the processor, with each processor being able to have local memory. This is better for high [[Memory#Locality of Reference|locality]] operations.
- **Cache-only memory** (**COMA**), maintains a local cache for all processors along with central shared memory.
- **Cache coherent non-uniform memory access** (**CC-NUMA**) maintains a global shared memory as well as a cache that has a write-invalidate [[Cache|cache]] coherence protocol.

Commonly **hybrid memory** approaches are used with a shared memory and a cluster of processors amongst a network. This shared memory is called a **cache coherent SMP** (symmetrical multi-processing) machine, with each SMP communicating through the network.

# Software-Level Shared Memory
Software-level shared memory is implemented in a variety of operating systems as to allow joint access of resources either for IPC or parallelism. UNIX supports interfaces for sharing memory between processes.
- **System V Style** which is from old SVR4 UNIX systems where the `sys/shm.h` library is used. This shares memory through `shmget()` and `shmat()` where a key is exchanged for sharing data.
- **POSIX STYLE** which uses the `sys/mman.h` library which opens a file used as shared memory. This allows shared memory to be written by `mmap()` which gives a [[Virtual Memory|virtual memory]] address to the data.