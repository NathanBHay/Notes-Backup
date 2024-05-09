A computer program is a set of instructions that a computer executes to provide a result. This **program layer** is the lowest level above the hardware of the [[Computer Architecture]] layer and executes on the [[Operating System|OS]]. A program is executed through a **compilation** or **interpretation** sequence. This sequence sees the starting **source code** become machine readable instructions.

# Instruction Execution
Execution of [[Assembly|assembly]] instruction sets involve a process of fetching the instruction from an executable into the main memory by the [[CPU]]. This is done through switching the [[Memory#Registers|program counter]] to the current instruction which allows for this instruction to be loaded into the instruction register. This register's instruction is then [[Integrated Circuits#Combinational Circuit|decoded]] by the CPU allowing for the CPU to send control signals to execute commands.

**x86**, **[[MARIE Assembly]]**, **[[MIPS Assembly]]**.
# High Level Execution
High level [[Programming Languages|programming language]] execution usually involves [[Compilers|compilation]] of code into the machine's instruction sets. This enables a more readable language with additional features such as complex branching operations and functions to be used instead of a low level language. Compilation usually involves parsing the language and then generating the machine specific instructions.

# Scoping
One of the processes that happen during program execution is scoping. A scope is a block of space where a namespace is accessible. A **namespace** or environment being a **mapping** of **bound** names to objects upon the interpreter or compiler's start. Each file has its own namespaces, while functions have a local namespace. A scope is **static** however upon runtime is found **dynamically**. The interpreter or compiler goes from the lowest to highest scope to generate a namespace.
