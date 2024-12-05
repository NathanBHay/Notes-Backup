The memory within a computer is the place which data is stored. This data functions through the use of [[Computer Architecture#Sequential Circuit|sequential circuits]] as to store results. Memory is commonly indexed through an **address** which holds a **value**. Each address holds a single [[Datatypes#Word|word]] if the memory is considered **word-addressable**, if not some devices provide smaller word size memory addressing. All values even **constants** used within code take up memory. A memory cell has 3 types of lines going out of it.
- **Address bus**, these are the lines that allow for the memory itself to be accessed.
- **Data path**, these are the lines which determine where to get the memory from. This usually involves a **memory multiplexer** used to get the byte and then select the *row* and *column* within the memory.
- **Control line** this is where you determine whether you want to read, write, or do any other operations with the results.

Memory can be addressed through **Direct Addressing** which uses the exact location in memory which a value is stored or **Indirect Addressing** which uses the relative location in memory from a starting point. Indirect is commonly used within arrays.

# Locality of Reference
Locality of reference is the tendency of a processor to access the same memory multiple times. This trait can be used to speed up memory operations through caching and other techniques. The types of reference locality:
- **Spatial locality** is the trait that subsequent memory accesses to an area within memory are likely to be in nearby locations.
- **Temporal locality** where accesses to a particular area in memory will likely happen multiple times.

Memory commonly leverages these traits as to optimise memory within the system.

# Memory Hierarchy
Memory is kept in multiple sections defined under the **memory hierarchy** which have varying speeds and locations. From fastest to slowest these are:
- **[[Memory#Registers|Register]]** which stores words inside the CPU.
- **[[Cache|L1 Cache]]** which is around 100kb stored inside the CPU.
- **L2-3 Cache** which is 1-8mb inside or close to the CPU.
- **RAM** which is several gigabytes within the main bus.
- **SSD/HDD** which is terabytes kept externally.
- **[[Networks|Network]]** which is theoretically infinite.

The performance of a computer is largely dependent on the storage memory hierarchy it employs. This is as the [[CPU|CPU's]] ability to fetch instructions and access program memory is based on the time it takes to access this data. With a *stall* happening when the computer has to wait for this access as the CPU remains unused. This means efficient **swapping**, which is the process of moving memory from secondary storage to main memory, is required for a system to operate at maximum efficiency.

Memory that is located within this hierarchy is usually abstracted away by [[Virtual Memory|virtual memory]] which maps these physical locations to a virtual address space.

## Registers
A registers is a memory device located within the CPU that is used to hold temporary word sized data. This is done by [[Integrated Circuits#Sequential Circuit|latching]] a value from the CPU bus and returning it to the bus. These are the fastest type of memory and can be divided into:
- **Special Purpose Registers** (SPR) which are used for specific functions and commonly include:
	- **Instruction Register** (IR) holds the currently executed instruction.
	- **Program Counter** (PC) also called the Instruction Pointer counts the current position in the assembly code.
	- **Stack Pointer** (SP) defines the start of the stack location.
- **General Purpose Registers** (GPR) which are used to store temporary data by the programmer.
- **Program Status Word** (PSW) is a register used to contain condition bits set by comparison instructions and other control instructions.

## Hardware Cache
The [[Cache|hardware cache]] (CPU-level cache) is a set of memory stored either within the CPU or close to it. It uses **static random access memory** (SRAM) technology as to store quick access memory. Memory stored here usually includes data which is commonly accessed by programs such as instructions. A hardware cache usually functions within a hierarchy with levels corresponding to their position 

## RAM
**Random Access Memory** (RAM) is stored outside of the CPU further on the main bus than the cache. It uses **dynamic random access memory** (**DRAM**) as to store large amounts of data that operate fast. The time to access an item within RAM is the same amount of time no matter its position.

**Synchronous dynamic random access memory** (**SDRAM**) is DRAM that operates on a clock. Meaning operations aren't recognised until given a [[CPU#Clocks|clock]] signal. **High bandwidth memory** is a form of SDRAM that stacks memory chip dies to increase density.

## Secondary Memory
Secondary memory is considered **non-volatile** as the memory remains permanent after system executions. This is in comparison to the **volatile** memory within the upper layers, called **primary memory**. The common devices associated with secondary memory are SSDs and HDDs.

A common practice with secondary memory is [[Storage Virtualisation|data virtualisation]], which is the process of treating multiple disks as a pool of memory. This enables a variety of improvements when it comes to memory access speeds and memory recovery.

### Disk Formats
Secondary memory is allocated along the boundaries of **disk sectors**, where each sector holds three main parts. These are the *preamble*, a bit pattern that idicates the start of a sector as well as possible cylinder information, the data itself (usually allocated in 512-bytw sectors), and error correcting codes. 

### Solid State Drives
**Solid State Drives** (SSD) use semiconductor materials as to store data, meaning they are just a series of transistors which are built as [[Integrated Circuits#Sequential Circuit|latches]]. Due to this they are faster than their HDD counterparts as they are only limited by gate delay. They employ a *write-multiple-read-erase-rewrite cycle*. *Wear levelling* occurs from the write/erases of SSD data, causing the SSD to fail over time. To minimise this these operations are spread out across sectors.

### Hard Drives
**Hard Drives** (HDD) use a moving disk to store memory. This data is written serially onto cylinders which contain large blocks of data by using a electromagnetic transducer. A pivoting arm is used to position this transducer over the part of the disk the data is kept on. The time it takes to access data depends on the *rotational latency* which is the time is takes for the disc to move to the correct position, and the *seek time* which is the time it takes to move the head over the cylinder holding the data. 

Hard drives are further organised by **cylinders** which are full rotations on one track which contain multiple disk sectors. This can be optimised by ensuring cylinders are aligned such that multiple can be read at the same time. The process of aligning this is done with *cylinder skew*, with further improvements of reading the same sectors achieved with *sector offsetting*. Another optimisation is *interleaving sectors* as it gives the computer time to write data to the previous sector before reading the next. To improve the speeds of these HDD block data is used to minimise access time. HDD quality is dependent on the density and RPM of the disc. 

**Onboard HDD [[Cache|caches]]** are able to significantly improve speed of commonly accessed memory. Caching can also happen during the read on adjacent sectors on other cylinders as to minimise disk movement. 

#### Disk Arm Scheduling
Disk arm scheduling is the process of optimising disk reads by handling the order of disk read/write requests. Some common approaches to this are:
- **First-come first served** (FCFS), this approach uses a [[Abstract Datatypes#Queue|queue]] to order requests.
- **Shortest seek first** (SSF), pursues the request with minimum distance from the head. This can be slow when disk requests are high.
- **Elevator algorithm**, maintains a direction bit (up or down) which it reads for all requests. This direction bit determines whether the arm moves in one direction or another, allowing it to move its head back and forth while maintaining its velocity.
- **Circular scan**, moves in one direction until reaching the end before moving in the other direction.

#### Kryder's Law
**Kryder's law** states that the density of hard drives double every 13 months. Kryder's law doesn't take in account performance as HDD speeds haven't decreased at the same rate due to the limit of read/write head movement. SSD's are said to follow [[CPU#Moore's Law|Moore's law]] due to the use of transistors to store data.

# Direct Memory Access
DMA is an approach to reduce [[CPU]] load by using an external controller to handle the process of  copying data between locations rather than the CPU. This device functions by allowing the CPU to initialise a controller that handles the moving of data in the background; sending an [[IO Devices#Interrupt I/O|interrupt]] once the operation is complete.