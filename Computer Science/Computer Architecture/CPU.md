The CPU or Central Processing Unit is one of the components listed in [[Computer Architecture#Von Neumann Architecture|Von Neuman's Model]] of computer architecture. It functions as the central device which reads inputs from [[Memory]] and [[IO Devices]] and produces a given result. This makes it central into the functioning of a computer. Each CPU has its own **[[Assembly|Instruction Set Architecture]]** which is the language that the CPU understands. The CPU can be divided into the [[Computer Architecture#Integrated Circuits|ALU]], [[Memory#Registers|Registers]] and [[CPU#Control Unit|Control Unit]], which all communicate through a **bus**.

# Busses
The bus is a strategy for communicating between components within a machine. This strategy in comparison to the **spaghetti strategy**, which uses individual wires to connect components, is more efficient as it shares an address line. A bus is a group of wires which allows data to communicate between devices given it follows the bus's protocols. Busses are grouped by three main purposes:
- **Address bus** for lines carrying [[Memory|memory addresses]].
- **Data bus** for lines carrying the data.
- **Control bus** for lines that delegate operations to components.

There are a few different schemes for how to handle a busses operations. These are:
- **Centrally controlled** bussing is a basic approach to handling a bus where a **bus controller** determines all transfer operations between components on the bus.
- **Centrally arbitrated** busses change the **bus master** with the **bus arbitrator** delegating these requests.
- **Distributed arbitration** busses function through all devices being able to negotiate bus access. This is determined by a bus protocol which determines precedence.

# Control Unit
The control unit (CU) directs the operation of the processor. The control unit also determines if the memory is in read or write mode and then tells the ALU operations to perform. It also performs the *fetch-decode-execute cycle* which is defined as:
- **Fetch** where the *CU* gets the address of the *PC* and then increments it.
- **Decode** looks at the instruction in the *instruction register (IR)* and [[Integrated Circuits#Combinational Circuit|decodes]] it. Getting the memory ready for operations in the next phase.
- **Execute** encodes the instructions as a series of **control signals** which interface with the other CPU components. 

Each of these actions time is determined by the **clock** which oscillates between 0 and 1. This **clock cycle** is measured in *hertz* (*Hz*).

A control unit can be built in different ways depending on its architecture. [[Assembly#RISC vs CISC|CISC]] machines usually implement microcode on the control unit to allow for operations, while [[Assembly#RISC vs CISC|RISC]] uses hardwired logic to execute instructions.

## Microcode
The execution encoding for CISC architectures is usually in the form of a **micro programs** that are stored in the **control store**. These contain **micro instructions** that occupy a **micro word**. The **micro program counter** points to these instructions within the store, typically using part of the micro word to point to the next instruction. These control stores are usually stored in ROM but may be loaded into RAM after booting.

The control store usually holds a set of operations at arbitrary places within the memory. Therefore to access specific instructions a block of jump statements are placed at the start to direct the decoded [[Assembly#Implementation|instruction]] to the correct operation.

### Horizontal Microcode
**Horizontal microcode** are types of micro words in the control store that all have a direct mapping to a control signal value. This type of code is inefficient as it requires hundreds of bits for complex operations as multiple micro instructions are within the a single word. Despite this horizontal microcode can be accessed quickly with few limits to how its programmed. In cases where microcode isn't expensive horizontal is preferred as its easier to debug, test and has better performance. 

### Vertical Microcode
**Vertical microcode** uses a decoder to to convert bits from the control store into multiple control signals. This means that the decoder maps $N$ control store bits into $M$ signals where $M>N$. This higher packing allows for smaller devices but introduces performance loss due to decoder delay. Hybrid approaches also exist where some control store fields are encoded.

## Hardwired
The execution for RISC architecture usually involves direct decoding of instructions as control signals driven by dedicated circuits. This is potentially faster and simpler but at the cost of difficulty to debug and modify code. These models are based upon [[Automata Theory|state machines]] as the CPU moves from state determined by the instruction.

# Context Switch
A context switch happens when an interrupt occurs or scheduling leads to the changing of a task. This results in the saving of all current [[Memory#Registers|registers]] and creating a new state for the given task. This happens many times within a CPU as it jumps from process to process.

# Moore's Law
 In 1965 Gordon Moore observed the amount of [[Computer Architecture#Transistors|transistors]] doubles every year. This observation has proved true as transistors get smaller leading to exponential transistor growth. Moore's law doesn't necessarily predict performance as the decrease in transistor size results in performance decreases due to heat, energy consumption, and errors.
