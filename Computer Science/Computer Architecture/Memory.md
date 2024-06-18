The memory within a computer is the place which data is stored. This data functions through the use of [[Computer Architecture#Sequential Circuit|sequential circuits]] as to store results. Memory is commonly indexed through an **address** which holds a **value**. Each address holds a single [[Datatypes#Word|word]] if the memory is considered **word-addressable**, if not some devices provide smaller word size memory addressing. All values even **constants** used within code take up memory. A memory cell has 3 types of lines going out of it.
- **Address bus**, these are the lines that allow for the memory itself to be accessed.
- **Data path**, these are the lines which determine where to get the memory from. This usually involves a **memory multiplexer** used to get the byte and then select the *row* and *column* within the memory.
- **Control line** this is where you determine whether you want to read, write, or do any other operations with the results.

Memory can be addressed through **Direct Addressing** which uses the exact location in memory which a value is stored or **Indirect Addressing** which uses the relative location in memory from a starting point. Indirect is commonly used within arrays.

# Memory Hierarchy
Memory is kept in multiple sections defined under the **memory hierarchy** which have varying speeds and locations. From fastest to slowest these are:
- **[[Memory#Registers|Register]]** which stores words inside the CPU.
- **[[Cache|L1 Cache]]** which is around 100kb stored inside the CPU.
- **L2-3 Cache** which is 1-8mb inside or close to the CPU.
- **RAM** which is several gigabytes within the main bus.
- **SSD/HDD** which is terabytes kept externally.
- **[[Networks|Network]]** which is theoretically infinite.

The performance of a computer is largely dependent on the storage memory hierarchy it employs. This is as the [[CPU|CPU's]] ability to fetch instructions and access program memory is based on the time it takes to access this data. With a *stall* happening when the computer has to wait for this access as the CPU remains unused. To enable a computer to run fast two storage traits are exploited:
- **Spatial locality** is the trait that subsequent memory accesses to an area within memory are likely to be in nearby locations.
- **Temporal locality** where accesses to a particular area in memory will likely happen multiple times.

## Registers
A registers is a memory device located within the CPU that is used to hold temporary word sized data. This is done by [[Integrated Circuits#Sequential Circuit|latching]] a value from the CPU bus and returning it to the bus. These are the fastest type of memory and can be divided into:
- **Special Purpose Registers** (SPR) which are used for specific functions and commonly include:
	- **Instruction Register** (IR) holds the currently executed instruction.
	- **Program Counter** (PC) also called the Instruction Pointer counts the current position in the assembly code.
	- **Stack Pointer** (SP) defines the start of the stack location.
- **General Purpose Registers** (GPR) which are used to store temporary data by the programmer.

## Hardware Cache
The [[Cache|hardware cache]] is a set of memory stored either within the CPU or close to it. It uses **static random access memory** (SRAM) technology as to store quick access memory. Memory stored here usually includes data which is commonly accessed by programs such as instructions. A hardware cache usually functions within a hierarchy with levels corresponding to their position 

## RAM
**Random Access Memory** (RAM) is stored outside of the CPU further on the main bus than the cache. It uses **dynamic random access memory** as to store large amounts of data that operate fast. The time to access an item within RAM is the same amount of time no matter its position.

## Secondary Memory
Secondary memory is considered **non-volatile** as the memory remains permanent after system executions. This is in comparison to the **volatile** memory within the upper layers, called **primary memory**. The common devices associated with secondary memory are SSDs and HDDs.

A common practice with secondary memory is [[Storage Virtualisation|data virtualisation]], which is the process of treating multiple disks as a pool of memory. This enables a variety of improvements when it comes to memory access speeds and memory recovery.

### Solid State Drives
**Solid State Drives** (SSD) use semiconductor materials as to store data, meaning they are just a series of transistors which are built as [[Integrated Circuits#Sequential Circuit|latches]]. Due to this they are faster than their HDD counterparts as they are only limited by gate delay.

### Hard Drives
**Hard Drives** (HDD) use a moving disk to store memory. This data is written serially onto cylinders which contain large blocks of data by using a electromagnetic transducer. A pivoting arm is used to position this transducer over the part of the disk the data is kept on. The time it takes to access data depends on the *rotational latency* which is the time is takes for the disc to move to the correct position, and the *seek time* which is the time it takes to move the head over the cylinder holding the data. To improve the speeds of these devices block data is used to minimise access time. An onboard cache is another approach to speed up accesses to commonly used memory. HDD quality is dependent on the density and RPM of the disc.

#### Kryder's Law
**Kryder's law** states that the density of hard drives double every 13 months. Kryder's law doesn't take in account performance as HDD speeds haven't decreased at the same rate due to the limit of read/write head movement. SSD's are said to follow [[CPU#Moore's Law|Moore's law]] due to the use of transistors to store data.

# Virtual Memory
Virtual Memory is the abstraction of memory into an **address space** that a programmer is able to access without hardware level concerns. The address space is a mapping from the **physical memory** into a space that hides the boundary between devices, and optimises through caching mechanisms. Virtual memory is calculated through a **memory management unit** (MMU) which resides on the [[CPU]]. There are two main approaches to virtual memory **paged memory** and **segmented memory**.

## Paged Memory
Paged virtual memory uses equally sized blocks called *pages* to represent virtual memory. Pages are kept within a table with the high-order bits indexing into the pages  and the low-order bits finding the word within the page. These high-order bits commonly being called the *virtual page number*. The page table is placed within main memory with calls to a virtual address not found within the table causing the page to be retrieved from secondary storage. This process is called **paging** or page fault which is done by the *page fault handler*.

**Multi-level page tables** are an approach that improves performance by having multiple tables for different parts of the word. This enables a faster lookup at the cost of increased fragmentation and overall overhead.

**Internal fragmentation** is an effect of paged memory where when pulling data from the secondary memory the data isn't in the same increments and thus, some additional memory is unused within the page. 

## Segmented Memory
Segmented virtual memory uses dynamically sized segments which are the size of the required data. A *segment fault* happens as a result of a miss, and is resolved by copying memory into virtual memory. In the event of virtual memory being full segments are removed until space can be made for the new segment. Segment tables are usually smaller than 

**External fragmentation** happens to segmented memory as a result of removing blocks to fit new memory leads to left over memory between the blocks.

## Translation Lookaside Buffer
Since a page and segment space can't be held within a register file a memory access is required to access virtual memory. To speed this process up a translation lookaside buffer is used which stores recent translations of virtual memory into physical therefore improving translation times. It therefore stores a table of entries for a certain amount of pages.

## Memory Allocation
Memory is allocated within a computer through the use of [[Memory#Virtual Memory|virtual memory]]. This process leads to a section of the memory named the **heap** being kept as free space for [[Program Exectution|programs]] to allocate to. This model of heap data places data throughout this free space dynamically. The heap provides issues when considering multiple programs, as all memory can be accessed globally which leads to greater execution time as programs need to find where there memory is kept. To stop this a **stack** is put at the bottom of the heap. This stack follows the [[Abstract Datatypes#Stack|abstract datatype]] of the same name, and builds upwards towards the start of the heap by allocating values relative to the bottom. This process leads to separate **frames** being created where local values are kept for specific programs and functions.

# Direct Memory Access
DMA is an approach to reduce [[CPU]] load by using an external controller to handle the process of  copying data between locations rather than the CPU. This device functions by allowing the CPU to initialise a controller that handles the moving of data in the background; sending an [[IO Devices#Interrupt I/O|interrupt]] once the operation is complete.