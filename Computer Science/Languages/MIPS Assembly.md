**Micro Computer without Interlocking Pipeline Stages** (MIPS) is a assembly language which is a simplification of modern assembly languages. Its simplicity is due to its 1 clock cycle run time for programs, with instructions being 4 bytes. It runs on a MIPS processor which provides an environment for programming.

# MIPS Memory
MIPS uses 32 [[Memory#Registers|general purpose registers]] sized as a [[Datatypes#Word|word]]. Its registers are called with the *$* prefix. MIPs general purpose registers include:
- **Temporary** registers which are index $t0 to $t9.
- **Zero** registers which has a constant 0 stored within $0 or $zero.
- **Argument** registers, which are used to pass arguments called with $v0, $v1.
- **Return** registers, which are used to return arguments with $a0 to $a3.
- **Stack Pointer** which is the location of the stack, used to indirectly address as $sp.
- **Frame Pointer** which is used to keep the location of the bottom of the stack within the function, called with $fp.
- **Return Address** is used to keep the location of where to jump when exiting the function, kept at $ra.

The use of **(** var/register **)** is used to get the **pointer** or **dereference** a value. When dereferencing a *shift value* can be put in front as a indirect address. This indirect addressing is done through increments of 4.

**Variables** in MIPs are stored like most languages with them either within the [[Memory#Memory Allocation|heap]] or [[Memory#Memory Allocation|stack]]. Local variables use the indirect addressing with the stack. To **allocate** memory within the stack minus it and add to free. The frame pointer being used to change the frames of differing functions. Most of these within the heap can be called with assembler directives. **Assembler Directives** tell the assembler where data from the code, should be stored within the memory segments. These segments being:
- **.data** which is used for variables.
- **.text** which is used for assembly instructions.
- **.space** which allocates n-bytes.
- **.word** which allocates words.
- **.half** which allocates half word.
- **.byte** which allocates a single byte.
- **.ascii** which stores a string.
- **.asciiz** which stores a string with null-terminate.
A **label** is used within a memory segment to provide a memory location. This memory location can be used for global variables, control structures, or functions.

**Arrays** are commonly kept with a length cell at the start. This allows iteration and other functions.

**Overflow** happens within MIPS when an instruction results in a return greater than a word. To fix this some operations return a **HI** and **LO** value. Where the **LO** stores the lowest digits, a **HI** stores the highest.

The **Function Call Cycle** follows a specific order in which the function **caller** follows a process where it:
1. Saving temporary registers by pushing onto stack.
2. Pushing arguments onto the stack.
3. Calling the function with jal.
4. Clears function arguments by popping.
5. Restores saved temporary registers.
6. Use return values.

Within the call cycle the **callee** follows a process where it:
1. Saves $ra by pushing onto the stack.
2. Saving $fp by pushing onto stack.
3. Copying $sp to $fp.
4. Allocates local variables.
5. Chooses return value.
6. Pops local variables.
7. Restores $fp and $ra.
8. Returns with *Jr* $ra.

# MIPS Architecture
MIPS architecture follows the [[Computer Architecture|Von Neumann architecture]] paradigms used throughout most computers. The main CPU has a structure that consists of a PC which feeds into a device which reads the instruction's memory. This device then inputs the registers into a read device, which gives the registers to an ALU. The ALU is informed by the instructions reader what operation will be done, and if the program counter needs to be added to as to do a jump operation. If there is no jump operation the data is read by an ALU that either reads the result from a memory location or writes the result to a memory location or register.

The control unit has 8 main control wires which are determined by the given instruction. These control wires are:
- **RegDst** which gets the register destination that is being written to if it reads true.
- **Branch** which rewrites the PC if true.
- **MemRead** which reads from memory if true.
- **MemtoReg** which determines if data should be passed from memory to a register.
- **ALUOP** which determines if the operation is a load or store (00), a branch (01), or a R-Format instruction (10).
- **MemWrite** which writes to the memory if the given value is true.
- **ALUSrc** which extends to the lower 16 bits, which reads true for save and load operations.
- **RegWrite** which writes to the registers if true.

# MIPS Instructions
MIPS instruction set features many common assembly commands. Some of these instructions are considered pseudo instructions as they don't appear on the native machine. This means multiple operations are done as to simulate these operations. The main formats these instructions follow are:
- **R-Format** which are instructions which have a operation (OP), write register (RS), and two read registers(RT & RD).
- **I-Format** which are read and write instructions which have a operation (OP), a register (RS), and a memory location (RT) which is modified by the offset.

## Arithmetic Instructions
| Instruction | Note |
| --- | --- |
| **add** $1, $2, $3| Add |
| **sub** $1, $2, $3| Subtract |
| **addi** $1, $2, val| Add Immediate/constant |
| **addu** $1, $2, $3| Add unsigned integer |
| **addiu** $1, $2, val | Add Immediate unsigned integer |
| **subu** $1, $2, $3| Subtract unsigned integer |
| **mul** $1, $2, $3| Multiply |
| **mult** $2, $3| Multiply and return result in LO and lower digits in HI |
| **div** $2, $3| Divides and returns result in LO and Remainder in Hi |

## Logical
| Instruction | Note |
| --- | --- |
| **and** $1, $2, $3 | Bitwise And |
| **or** $1, $2, $3 | Bitwise Or |
| **andi** $1, $2, $val | Bitwise And with immediate/constant |
| **ori** $1, $2, $val | Bitwise Or with immediate/constant |
| **srl** $1, $2, $3 | Shifts right logical |
| **sll** $1, $2, $3 | Shift left logical |
| **slt** $1, $2, $3 | If value is less than |
| **slti** $1, $2, $val | If value is less than immediate/constant |

## Data Transfer
| Instruction | Note |
| --- | --- |
| **lw** $1, shift($2) | Load word from register |
| **la** $1, label | Load address |
| **lui** $1, val | load constant to upper 16 bits |
| **li** $1, val | Load Immediate
| **sw** $1, shift($2) | Save word from register |
| **mfhi** $1 | Get value from HI |
| **mflo** $1 | Get value from LO |
| **move** $1, $2 | Copy |

## Branch
| Instruction | Note |
| --- | --- |
| **beq** $1, $2, address | Branch if equal |
| **bne** $1, $2, address | Branch if not equal |
| **bgt** $1, $2, address | Branch if greater than |
| **bge** $1, $2, address | Branch if greater than or equal|
| **blt** $1, $2, address | Branch if less than |
| **ble** $1, $2, address | Branch if less than or equal|
| **j** address | Jump |
| **jr** $1 | Jump to Register |
| **jal** address | Jump and link |

## System Call
A system call, called with **syscall** takes an argument from $v0, which does an action. These actions are indexed 1-17 and are:

| Service         | Code | Arg/Result            |
| --------------- | ---- | --------------------- |
| Print Int       | 1    | $a0 input             |
| Print Float     | 2    | $f12 input            |
| Print Double    | 3    | $f12 input            |
| Print String    | 4    | $a0 input             |
| Read Int        | 5    | $v0 return            |
| Read Float      | 6    | $f0 return            |
| Read Double     | 7    | $f0 return            |
| Read String     | 8    | $a0, $a1 return       |
| Allocate Memory | 9    | $a0 input, $v0 return |
| Halt            | 10   | None                  |