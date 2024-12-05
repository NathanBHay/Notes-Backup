Virtual Memory is the abstraction of memory into an **address space** that a programmer is able to access without hardware level concerns. The address space is a mapping from the **physical memory** into a space that hides the boundary between devices, and optimises through caching mechanisms. Virtual memory is calculated through a **memory management unit** (MMU) which resides on the [[CPU]]. There are two main approaches to virtual memory **paged memory** and **segmented memory**.

# Paged Memory
Paged virtual memory uses equally sized blocks called *pages* to represent virtual memory. Pages are kept within a table with the high-order bits indexing into the pages  and the low-order bits finding the word within the page. These high-order bits commonly being called the *virtual page number*. The page table is placed within main memory with calls to a virtual address not found within the table causing the page to be retrieved from secondary storage. This process is called **paging** or page fault which is handled by the *page fault handler*.

**Multi-level page tables** are an approach that improves performance by having multiple tables for different parts of the word. This enables a faster lookup at the cost of increased fragmentation and overall overhead.

**Internal fragmentation** is an effect of paged memory where when pulling data from the secondary memory the data isn't in the same increments and thus, some additional memory is unused within the page. 

## Page Replacement
Page replacement algorithms are used to handle page faults, freeing room for the new page to be loaded. The quality of page replacement policy is usually considered through the HK-paging problem which compares the worst-case performance of a given algorithm with the optimal policy. With this theoretical optimal policy replaces the page that will not be referenced for the longest time.

### FIFO
First in first out ([[Abstract Datatypes#Queue|FIFO]]) is the simplest policy which removes the longest existing page from memory. This approach is simple but suffers when data is read multiple times.

### Second-Chance
Second chance modifies FIFO to maintain a reference bit which is a bit used to represent whether a page has been accessed since paging in. Upon reaching the start of the queue the algorithm checks if the reference bit is set, if it is unset it and put it at the end of the queue, otherwise remove the page. This improves the paging as it ensures regularly used pages are still cached.

### Least Recently Used
Least recently used (**LRU**) chooses the page that hasn't been used in the longest time. This has more overhead and is more difficult to implement. An approach to implementing this is to use a hardware counter that increments after each instruction. With the page containing its own value that measures the time since it was last read. This data is then used during a page fault to remove a page.

### Clock
Clock is an efficient implementation of second chance that rather than keeping a queue keeps a pointer to the front that moves. This movement is triggered by clearing the reference bit, moving to the next element in the queue. This improves the speed as no pop and push operations are required. This can be implemented with a [[Data Structures#Queue Data Structures|circular queue]].

### Not Frequently Used
Not frequently used (**NFU**) is an approximation of LRU that uses a software counter whereupon each clock interrupt if the page has been referenced in that time, checked from the $R$-bit, that page's number will increment. This can cause issues when pages are initially heavily used but aren't later as they will stay in memory longer than recently paged data.

### Aging
Aging is an expansion upon NFU that increments a counter by shifting the timer before adding the $R$-bit to the front. This ensures more recent pages have more of an impact on paging. Mathematically using shifts this can be computed as:
$$V_{i+1}\gets(R_i\ll(k-1))\;|\;(V_i\gg1)$$
Where $R_i$ is replacement bit and $k$ is the length of the counter in bits.

# Segmented Memory
Segmented virtual memory uses dynamically sized segments which are the size of the required data. A *segment fault* happens as a result of a miss, and is resolved by copying memory into virtual memory. In the event of virtual memory being full segments are removed until space can be made for the new segment. Segment tables are usually smaller than their page counter parts and operate by keeping a segment number and offset which determines location.

**External fragmentation** happens to segmented memory as a result of removing blocks to fit new memory leads to left over memory between the blocks. **Compaction** is a technique to reducing this by periodically reordering segments to fill spaces,

## Segment Placement Algorithms
During a segment fault the choice of a new segment's location is important for minimising future segmentation. 

### Best-Fit
Best-fit is an approach which chooses the location with minimal space around it such that it fits the best. This is good for cases where segments are allocated somewhat spare with small gaps. Despite this it can be slow as it needs to find the best location and may result in a large gap.

### First-Fit
First-Fit finds the first location that the segment fits into. This algorithm is fast at the cost of having high fragmentation. This high fragmentation can make it worse as it searches through gaps to small to fit in resulting in a overall poor algorithm.

### Next-Fit
Next fit finds the next free area starting from the most recently placed segment. This is cheaper than first-fit but suffers from some of its disadvantages, but can make fragmentation worse in some cases.

### Worst-Fit
Worst-Fit searches for the largest available space around it. This ensures large holes meaning future locations will be easier to fill. Similar to best-fit this is a slow process.

# Translation Lookaside Buffer
Since a page and segment space can't be held within a register file a memory access is required to access virtual memory. To speed this process up a translation lookaside buffer is used which stores recent translations of virtual memory into physical therefore improving translation times. It therefore stores a table of entries for a certain amount of pages.

# Swaps
Swaps are a scheme for maintaining a main memory cache in secondary storage. This enables pages from the RAM to be stored and retrieved from the swap location in cases where the main memory overflows. While this may result in a performance decrease for cases where there is less memory used than RAM, in most cases it results in a performance increase due to stopping main memory overflows. They are also commonly used to save data during crashes. The two main approaches for maintaining swaps are:
- **Swap Partitions**, a drive partition which holds the swap files. This is supported by most distributions as the default.
- **Swap Files**, are files within a partition that hold pages. These function better if they are less fragmented.

**Swappiness** is the threshold which represents the chance a page is written to a swap or space is freed up from memory.  Changing this value allows for optimisation of performance in some cases.

**Z-Swap** is a kernel feature which compresses pages that are going to be swapped into a section of the main memory.

# Buffer Cache
The buffer cache is an [[Operating System|OS]]-level cache that stores recent secondary memory reads. On Unix this is handled through the *sync* command which flushes the buffer and forces all unwritten data to be written to disk. This command is done through the **update daemon** which syncs every 30 seconds. Linux also has a **bdflush daemon** which does a more infrequent but less complete.

# Thrashing
Thrashing occurs in virtual memory when excessive time is spent on page faults and swapping pages. This is as a result of either there being too much utilised memory.

# Memory Allocation
Memory is allocated within a computer through the use of [[Memory#Virtual Memory|virtual memory]]. This process leads to a section of the memory named the **heap** being kept as free space for [[Program Exectution|programs]] to allocate to. This model of heap data places data throughout this free space dynamically. The heap provides issues when considering multiple programs, as all memory can be accessed globally which leads to greater execution time as programs need to find where there memory is kept. To stop this a **stack** is put at the bottom of the heap. This stack follows the [[Abstract Datatypes#Stack|abstract datatype]] of the same name, and builds upwards towards the start of the heap by allocating values relative to the bottom. This process leads to separate **frames** being created where local values are kept for specific programs and functions.