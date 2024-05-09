Caching is a strategy of maintaining a store of data so that it can be quickly accessed. Caches exist on software and [[Memory|hardware]] depending on the purpose of data. A cache's architecture is built around fixed size blocks called **cache lines** or cache blocks. When a cache line is copied from memory into the cache a **cache entry** is created. This entry includes the data as well as a memory location which is called a **tag**. This allows data requests to check if the cache contains the requested memory location in a line. In the event it does a **cache hit** has occurred, allowing it to quickly read the data. In the event it doesn't a **cache miss** occurs where a new entry needs to be opened. The effectiveness of a cache is measured by the hit ratio.

# Cache Hierarchy
The speed of a cache is effected by its location and type/length of the bus used. The cache hierarchy represents the arrangement of these caches. The **Level 1** cache is usually the smallest cache while the **Level 2+** are usually further away but with the advantage of larger space. The amount of cache levels usually result in an increased overall hit ratio at the cost of more comparison time before a miss is registered. 

# Cache Placement Policies
Cache placement policies are policies for determining where memory blocks are placed within the CPU cache. This is as memory needs to be placed in a way that allows for fast accesses depending on the data's priority.

## Directly Mapped Caches
Directly mapped caches hold a valid bit which is used to determine if entries are fields and uses a *cache tag memory*. This memory is accessed through an index into the cache tag memory using low order address bits (LOAB), before a comparator validates that the high order address bits (HOAB) are within the memory. This method is effective as we know form spatial locality that addresses will share HOAB but differ in LOAB. This does have the disadvantage that only one set of data from those low order bits can be stored. This means as we increase the number of cache lines we reduce the number of tag entries. Despite this their simplicity to design makes them common.

## Fully Associative Caches
A fully associative caches has a comparator for every line therefore not requiring LOAB to index into the cache. This enables a high cache hit rate at the cost of it being expensive and power-hungry as more hardware is required. The lack of indexing mean data can be stored anywhere within the cache meaning less misses. These allow a wide variety of cache replacement policies.

## Set Associative Caches
Set associative caches is a cross between directly mapped and fully associative caches. They function through grouping cache lines together allowing lines to have the same LOAB but different HOAB. This is done by separate comparator for comparisons within the set. This enables lines to have a better hit ratio in the cases where data shares HOAB. *Two-way set associative caches* are a simple implementation which have to halves, and provide the most significant increase in hit ratio compared to n-way set associative caches. These offer a smaller variety of cache replacement policies.

# Cache Management Policies
Cache management policies are the techniques for ensuring that the cache is consistent with memory. **Cache inconsistency** or cache coherence problem can be mitigated through:
- The **write through** policy works by writing changes to the cache and memory. This is simple but at the cost of being inefficient with high bus traffic on writes.
- The **write back** policy only writes to the cache in the event of a write. After this the memory is only updated when the cache is flushed. This minimises bus traffic at the cost of complexity. Commonly there exists an instruction to cause a software *cache flush*.

[[IO Devices|I/O devices]] commonly allow for memory operations independent of the CPU. Due to this some devices are limited to accessing non-cacheable data.

**Multiprocessor cache coherency** happens as the result of multiple processors having separate caches. 

# Split Architecture
**Harvard architecture cache schemes** have separate caches for instructions and data. This enables the instruction-cache to be optimised for locality and limited write operations. This allows the data cache to be fast for read and write operations. The disadvantage of this caching approach is that its hard to determine the size of the respective caches with analysis of instruction fetches and data accesses being required. In many cases the L1 cache is split while higher levels are combined. 

# Cache Analysis
The performance of cache can be calculated as:
$$E=\text{CH}\cdot\text{W}\cdot\text{MW}+\text{CH}\cdot(1-\text{W})\cdot C+(1-\text{CH})\cdot\text{W}\cdot(MW)+(1-\text{CH})\cdot(1-\text{W})\cdot \text{MR}$$
Where $\text{CH}$ cache hit ratio, $\text{W}$ is ratio of writes to memory, $C$ is the time required to read a cache entry, $\text{MW}$ is the time required to write memory, $\text{MR}$ is time to read memory. In this equation the most important term is the hit-ratio. 

Caches can be optimised through increasing cache size as to improve hit ratio. Cache speed can be improved with faster bus speeds and bus widths. 