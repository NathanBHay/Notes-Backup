Parallel computing is a type of computation which leverages multiple calculations simultaneously. There are various different levels of parallelism which are possible which differ in their level 

# Bit-Level Parallelism
Bit-level parallelism operates on [[Integrated Circuits|integrated circuits]] and [[Computer Architecture#Logic Gates|logic gates]] and is the lowest level of parallelism. It is done by reordering circuits in an alternative way such that tasks can be done in parallel. An example of this is in [[Integrated Circuits#Adders|carry look-ahead adders]] which compute the carry flag in parallel to the digit addition operations. Bit-level parallelism is difficult to achieve due to the complexity of modern day circuits however its effects can result in a significant performance increase.

# Instruction Level Parallelism
Instruction level parallelism achieves parallel execution on the level of [[Assembly|assembly instructions]]. There are a variety of approaches to this.

## Pipelining
During execution of instructions there are usually distinct stages where the instruction interacts with a certain part of the [[CPU]]. Parallelism can therefore be implemented by allowing the next instruction to do the previous stage of the current instruction which greatly speeds up efficiency. This is called pipelining and results in instructions executing once per phase of the pipeline. The *throughput* of a pipeline is the amount of time it takes for a single instruction to execute. 

When pipelining it is common to require a pause to wait for another operation to be finished. This is called a **pipeline stall** and results in a performance decrease every time one happens. Stalls are caused by:
- **Data hazards**, which happen when execution of an instruction requires the result of a previous instruction. A common remedy to this is **data forwarding** which places the results of computations directly into the [[Integrated Circuits|ALU]].
- Conditional branches which require knowledge of what instructions to pipeline next.
- Poor CPU design, which results in operations not executing within the correct time.
- [[Cache]] and [[Memory#Virtual Memory|MMU]] misses which cause memory fetch operations.

## Superscalar Processing
Superscalar processing is an expansion upon pipelining where multiple pipelines are maintained. This is done through having multiple ALU's called **execution units** (EU) which all have various different purposes. This leads to a large performance decrease as multiple instructions are able to be executed at the same time, while also pipelining future instructions. Similarly to pipelining there are various cases where the processor needs to stall, these are caused by:
- **Data dependency**, where similar to data hazards a previous instructions results are required. 
- **Resource conflicts** where multiple instructions require the same EU, register, or bus.
- **Procedural dependency** where the processor needs to wait before it knows what instructions can be computed next. This is caused by conditional branches.
- **Anti-dependency** happens when operands are overridden by future instructions. An approach to reducing this is **out-of-order** execution which computes future instructions rather than stalling.