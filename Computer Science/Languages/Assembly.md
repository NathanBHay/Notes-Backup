An assembly language is any low-level [[Programming Languages|programming language]] that uses the specific architectures [[Computer Architecture|instruction set]] to write programs. Code written in assembly is compiled with an **assembler** and possibly a **linker**. Instructions take up a [[Datatypes#Word|word]] per-line and are usually written as 3 or 4 letter mnemonics. Programming within assembly allows for management of the [[Memory#Registers|registers]] directly as well as [[Memory#Memory Allocation|heap]] and [[Memory#Memory Allocation|stack]] allocations.

# Language Design
Assembly languages are usually characterised by Opcode mnemonics, data definitions, and assembly directives. A **opcode mnemonic** is a basic instruction which takes operands and performs an operation. These operands can either be in the form of *[[Memory|memory addresses]]* or *immediate values*. **Data directives** define data and variables usually allowing for memory declarations. **Assembly directives** are commands given to an assembler which may generate code. The standard instruction types include:
- Memory Operations, that move copy and move data around.
- Arithmetic operations, that include basic maths and logic operations.
- Branching operations, that jump to other locations within the program.

## Operands
Every instruction has a set of operands. The differences in the amount of operands for the language greatly effect the amount of operations that can be done.

**One-address** instruction sets usually rely on an accumulator variable to function as the output or input of the instruction. **Two address** instruction sets usually function around having an output and input operand. **Three address** instruction sets are a more general arrangement that allow for combination of two operands resulting in a third. The trade-off for more instructions is increased instruction size which results in a speed decrease due to fetch cycles.

# Implementation
An instruction set is implemented on hardware through the [[CPU]] which decodes instructions into a set of control signals to other [[Integrated Circuits|integrated circuits]] on the computer. These control signals are determined by the [[CPU#Microcode|microcode]] or hardwired instructions of the computer.

# RISC vs CISC
Instruction sets vary in the their approach to design.  These design approaches can be classified as either RISC or CISC, depending on how complex their instructions are.

**Reduced Instruction Set Computers** (RISC) have a simple instruction set. In general these instructions take a single clock cycle per instruction. This is due to the fact that instruction opcodes have a fixed length that relates to the word size. Due to this RISC processors have a fewer transistors and are efficient. This is at the cost of more registers and a higher RAM requirement to store machine code instructions. RISC also has the advantage of pipelining which enables parallel execution of instructions. The most popular RISC instruction set is **ARM**

**Complex Instruction Set Computers** have many complex instructions. This minimises the amount of instructions at the cost of instructions being multiple clock cycles. These complex instructions allow greater memory efficiency. CISC processors are commonly implemented with [[CPU#Microcode|microcode]]. The most popular CISC instruction set is **x86**.