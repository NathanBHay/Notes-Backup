The operating system is the level of abstraction which handles the interface between [[Program Exectution|programs]] and the [[Computer Architecture|hardware]]. It allows users to access commonly called functions while also protecting memory. OS are required for **end users** and programmers to access the lower levels of the system. It thus **virtualises** physical operations.

# OS Types
There are a variety of different operating systems used for different purposes. Broadly these can be categorised as:
- **Mainframe OS** for room sized HPC devices.
- **Server OS** for maintaining services for multiple users.
- **Multiprocessor OS** for parallel computing units.
- **PC OS** for home computer users.
- **Handheld OS** for small devices that maintain basic functions.
- **Embedded OS** for control devices that maintain basic OS functionality.
- **Sensor-node OS** for sensors networks that communicate with nodes.
- **Real-time OS** for systems that require time operations that are precise.
- **Smart card OS** for very small chips with basic functionality, some equipped with [[Java|JVM]] functionality.

Some commonly used operating systems include:
- **Windows**, Microsoft's proprietary OS which is the most common operating system due to its compatibility.
- **MS-DOS**, an early operating system developed by Microsoft for IBM compatible computers.
- **MacOS**, Apple's proprietary OS the main competitor of Windows.
- **Linux**, open-source OS common among developers.
- **FreeBSD**, free and open-source OS.

## POSIX
**Portable Operating System Interface** (**POSIX**) is the IEEE standard for Unix-like operating systems. It defines the system and user-level APIs along with shells and utility that should be present on any Unix-like OS. Some of these include Bash, [[Threads]].

# Kernel Mode & System Calls
The key to an operating system is its two modes of operation. These are:
- **Kernel Mode** which code has no restrictions and interrupts are handled.
- **User Mode** which has a limited subset of instructions and applications that can run, and is the mode users interact with the OS.

The purpose of these dual modes enables computers to restrict dangerous actions that may cause issues to the OS and hardware.

A **system call** is used to obtain services from the [[CPU]]. This allows a user to call the processor, trapping it in kernel mode (usually using a `trap` instruction) to allow for it to do the desired action, before switching back. Generally system calls are used to manage [[Processes|processes]], manage the file system, and general other useful operations like directory movement.

## Windows API
In contrast to Unix Windows operates on very different concepts. Its main system is based around events, with programs being event driven. In Unix system calls are mapped to library calls however in the Win32 API these calls are decoupled allowing for future modifications to the library without causing errors.

# Multitasking
Multitasking are the various methods of [[Parallelism|concurrent]] execution of multiple computer processes. Multitasking operates through **context switches** which rotate the register values and loaded memory to allow processes to continue their individual computations. A **multi-programming** system achieves this through the use of a scheduler which determines which tasks are run by the CPU.

# Scheduling
The **schedular** determines the order of programs/[[Processes|processes]] to be ran. Scheduling ensures maximal resource efficiency, especially in relation to power, and performance. This is important as context switches are expensive and need to be minimised. An aspect t be careful of is **starvation** which happens when a process isn't scheduled in the required time or at all due to prioritisation.

**Non-pre-emptive** scheduling picks a process to run until another process blocks its execution through a *clock-interrupt*. This clock-interrupt determines then which process will next execute based on priority.

**Pre-emptive** scheduling picks a process and runs it a maximum fixed time. Switches then occur at the end of these periods through a clock interrupt. A [[CPU#Clocks|clock]] is required to implement this form of scheduling.

## Scheduling Types
Scheduling algorithms can be classified by their purpose, including the time period their processes will be executed across, and what the algorithm optimises for. The main classifications include:
- **Batch/long-term** scheduling being used for long continuous jobs. This optimises for throughput and CPU utilisation, while minimising time between jobs.
- **Interactive/medium-term** scheduling used in cases where multiple users must be served or certain processes require more cpu-time. This optimises for fairness and response time.
- **Real-time/short-term** where small processes with ranked priorities are important for critical operations. This optimises for adhering to deadlines and predictability.

## Scheduling Approaches
There are various approaches to writing scheduling algorithms depending on their use.

### First-Come First-Served
First-Come First-Served (FCFS) are algorithms which use a [[Abstract Datatypes#Queue|queue]] to determine execution. This usually result in minimal overhead and no starvation at the cost of low throughput.

### Shortest Job First
**Shortest job first** (SJF) is a strategy which orders based upon the remaining time of the process. This maximises throughput at the cost of possible starvation and overhead as each new process needs to be ordered. **Shortest remaining time next** (SRTN) is the preemptive version of SJF, which enables analysis of the remaining run-time rather than the predicted total runtime.

### Round-Robin Scheduling
Round robin scheduling assigns processes a time-interval called its *quantum*. Switching occurs either when the quantum ends and the process is running or as the result of a block/process finishing. While easy to implement this exhibits an extensive overhead. Despite this it has a good average response time and a balanced throughput. Time-slice effects throughput with a larger one being closer to FCFS in performance.

### Priority Scheduling
Priority scheduling assigns priorities to processes to determine order. This has various implementations including:
- **Earliest deadline first**, is a basic example of this where deadline is used to determine order.
- **Fixed-priority pre-emptive** assigns final priorities before-hand.

Priority scheduling can be used to categories groups of processes while using another technique, such as round robin, to determine ordering amongst the priority classes. This is also called **multilevel queue scheduling**.

### Guaranteed Scheduling
Guaranteed scheduling attempts to balance CPU-time amongst users by measuring the process execution time of a process per-user. This runs processes depending on the user with the lowest ratio of time.

### Lottery Scheduling
Lottery scheduling runs a lottery to determine which process should be executed. This decreases starvation as it ensures all processes have a chance of execution. Tickets can be assigned non-uniform if implementation of priority is important. In some systems cooperating process can exchange tickets. Lottery is useful in simulating other scheduling methods especially in cases where they can't be implemented.

### Fair-Share Scheduling
Fair-share scheduling balances based on ownership of processes before scheduling. This avoids processes with many child processes having higher distribution of scheduling. 

# File System
A file system virtualises [[Memory#Secondary Memory|secondary memory]] allowing a user to access it. This system is usually allocated in a *file hierarchy* that determines the structure of multiple memory devices. Commonly [[Storage Virtualisation|storage virtualisation]] techniques are applied to optimise these storage devices.

**Files** are the primary way of containing text and other information. These usually have a name and an associated extension `file.ext` which indicates the contents of the file. On UNIX systems this has no effects while on Windows and other systems this determines more aspects. Files can be accessed and created by [[Processes|processes]] with them usually persisting. Files can be allocated in three possible ways:
- **Byte sequence**, where files are a unstructured sequence of bytes that the OS has limited interpretation of. Meaning is therefore imposed by a user-level program. Both Unix and Windows use this approach due to its flexibility.
- **Record sequence** are fixed-length records with internal structure where read/write operations manipulate these records.
- **Tree** where files are allocated as a tree of records, where the key is position in the record. This allows for quick searches of particular locations.

## File Types
**Regular files** are the standard user files found on the system, as opposed to **special files** which provide a way for [[IO Devices|I/0]], [[Memory#Secondary Memory|secondary memory]] and other devices to have an interface. These files can be further classified into **block special files** which model devices as addressable blocks and **character special files** which model printers, modems and other devices that output characters. A [[Processes#Inter-Process Communication|pipe]] is a pseudo-file used to connect processes together.

**Directories** are files that provide structure for maintaining sets of files. On a single-level directory system all files are contained in a single root directory. A hierarchical system allows for multiple directories that contain each other in a tree structure.

A path is a way to identify where a file is in relation to its directories. An **absolute paths** is a file path which is relative to the system's top-level root directory. This is usually is represented through a path starting with `/`. A **relative path** is located relative to the currently accessed directory called the **current working directory** (CWD). This path can use the `.` and `..` pseudofiles for navigation from the current or from the parent directory.

## File Access
The method of accessing a file differs between implementation with the two approaches being:
- **Sequential access** is the basic approach to reading files where data is read sequentially requiring files to be rewound to be access earlier data. Insertion through this method is usually appended.
- **Random-access** is able to read bytes or records in any order. This enables efficient searches, updates and retrieval of bytes and records. To achieve this a key is used to indicate locations of data. This approach is best for frequent direct access and modification of specific locations is required.

## File System Layout
**Master boot record** (MBR) is an approach to this where sector 0 is the MBR which contains a partition table. During the [[Boot Process|boot process]] the CPU reads from this record and the partition table to find where the *boot block* is to execute. This boot block will have the OS located within it. Within the file system there are many possible special purpose blocks such as:
- *Super block* contains key information about the file system. This data includes number of blocks in the system, admin information, and magic numbers to identify file-system type.
- *Free block management* is a bitmap or list of pointers to free sectors on the device.
- *Index-nodes*, also called I-nodes are an array of data structures which give information about specific files.
- *Root-directory* the main file-system on the system.

## File Allocation
Implementation of how files are allocated on the drive is dependent on how individual data is allocated. This has impacts on both how files are implemented and directories.

An important aspect of file allocation is the **block size**, which is the smallest size data on a drive can fit. In cases where this block size is larger it reduces the amount of effective space, however decreasing the size of blocks does result in a performance decrease due to the need to search more blocks. 

### Contiguous allocation
**Contiguous allocation** where files are allocated in order of their placement into the file system. This is easy to implement as the header only requires a disk address to the first block and a length. They are also high-performance in cases like HDD's where adjacent reads are faster. This approach leads to greater amounts of fragmentation. Directories in this approach contain a list of all the blocks.

### Linked-List Allocation
**Linked-list allocation** keeps files in linked dist blocks, maintaining a pointer to the next sector of data. This almost removes fragmentation at the cost of overhead from all operations being linear by nature, causing slow random accesses. They also reduce data storage and have risks of the pointers become corrupted causing issues. 

*Table memory linked-list allocation* improves this approach by using a central table for managing data. This improves random accesses but at the cost of requiring more space. Directories implemented this way have a pointer to the first-block.

### Index-Nodes
**Index-nodes** keep track of blocks by creating a list of attributes and disk addresses of the file's blocks. This means access of files depends on the entire node to be in memory, which results in some overhead but with the advantage of the ability to maintain more open files. These can have nested spaces used for containing blocks of pointers. Directories are implemented as a link to the respective I-node.

### Fragmentation
Fragmentation occurs as the result of allocating and removing files on a device. This causes excess space to be lost as replacement of previous files isn't the exact size. In cases such as HDDs this can cause a performance decrease as the read head has to move greater distances. **Defragmentation** is the process of filling these gaps by placing information into adjacent sectors and removing gaps.

## Shared Files
Shared files are any files that must appear within the hierarchy at multiple points. There are two approaches to achieving this:
- *Hard-links* use the data structure that is associated with the file such as I-nodes or linked lists to create a direct link to the file. This means the file is the exact same file despite the change in directory location. This doesn't use additional disk space and means deletion of one of the files doesn't keeps the other.
- *Soft-links* or **symbolic links** (symlinks) that are files that link to another file but are treated as the file itself. This requires extra overhead as the link needs to be followed. Additionally problems might happen during interaction such as including the link during copies or copying the file multiple times. 

## File Hierarchy Standard
The **file hierarchy standard** is the Unix-like standard for organising the file hierarchy. This starts at a **root directory** which is located top-level of the system and contains:
- `/bin` the location of binaries that are usually accessed through the path variable.
- `/sbin` the location of essential system binaries.
- `/usr` the path of specific user binaries.
- `/lib` libraries that are essential for binaries.
- `/boot` [[Boot Process|boot loader]] files.
- `/dev` device nodes that provide a way to interface with devices.
- `/tmp` temporary files that can be located on the main memory.
- `/home` the location of users and their respective directories. Users commonly contain
- `/etc` files used by the system administrator, mostly including core system configuration files.
- `/var` mounts points for files that vary between machines.
- `/media` mount points for removable media.

Many of these files such as those within `/dev` can be classified as **special files** as they provide a way for [[IO Devices|I/0]] and other devices to have a file.

# Permissions
Operating systems provide an interface for managing multiple users of a system. Broadly these users include the **root** user, which manages the system and *normal users* who have permissions assigned to them by the root. The ability to raise a user temporarily to the root user is done with **Super User DO** `sudo`. In Unix systems the **wheel group** refers to a group of users who have access to additional privileges.

File permissions are handled on a Unix system through three categories, those being file owner, wheel and other. Each file category maintains three bits representing the *read*, *write* and *execute* actions. Changing file permissions can be done with the `chmod` command which specifies these three bits for all three categories of user.

# Shell
A shell is an interface that allows for execution of programs within a UNIX environment. There are multiple commonly used shells including **bash**, **z-shell**, **fish**, and **c-shell**.

# OS Structure
The operating system
- **Monolithic systems**, view the OS as a set of executable procedures that can call each other, therefore creating a fully integrated system.
- **Layered systems** organise the OS in a hierarchy of layers with each one constructed from calls of the previous.
- **Microkernels** split the OS into small modules with minimal purposes. This minimises issues caused by kernels crashing. A *reincarnation server* is usually required in these systems to check if kernels are functioning.
- **Client-server model** is a variation of microkernels that seperates processes **servers** which provide a service, and **client** which are these services. This allows communication between microkernels using the client which will receive a result from the server.
- **Virtual machines** are a way of running a OS kernel on a computer. This is usually done through an image that is managed by the main OS itself, connecting system calls.
- **Exokernels** are a way of partitioning virtual machine as to allow for distinct resources for each kernel. This allows VMs to be more isolated.