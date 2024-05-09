Logic gates form integrated circuits which are made to fulfil a certain function. These circuits can be broken up by there sizes, small-scaled integrated (SSI), medium-scaled integrated (MSI), large-scaled integrated (LSI), or even very-large-scaled integrated (VLSI). Most integrated circuits constructed today are made with VLSI or programmable logic devices (PLD). Integrated circuits are made up of many abstract levels. These levels are:
1. **Logic level** (gates, latches, buffers)
2. **Functional level** (registers, multiplexers, adders)
3. **Block level** (ALU, register file, etc)

When creating circuits there are a few traits which need to be considered:
- **Propagation delay** is the time it takes for a logic input to propagate throughout the circuit. This is the circuit's speed limit.
- **Power dissipation** is the amount of heat produced by operating the gate at a given speed. This limits the amount of gates within a certain area. **Landauer's** principle states  there is a lower theoretical limit of energy consumption. 
- **Circuit compatibility** is determined by creating a standard on certain attributes of the circuits. These include, power levels, propagation delay per-gate, dissipation, identical pin outs, and more. If all logical gates are identical then the device should be compatible.

# Logic Device Families
Logical device families are the chosen circuits used to build up an integrated circuit. A family needs to be considered **complete**. A complete set means it can implement any logical rule with the gates. Some complete sets include Nand, Nor, and the basic set of and, or, not. Some common families are:
- **Transistor transistor logic** (TTL) which has bipolar transistors with a low cost, with modest dissipation per gate and speed.
- **Complementary MOS** (CMOS) metal oxide field effect transistors, low dissipation with modest speeds. This makes them low cast and high density.
- **Emitter coupled logic** (ECL) which uses fast bipolar transistors, with high dissipation and high speed. These have a high chip cost.

Logic families are independent of architecture and organisation. Meaning any family can be used to implement any architecture. Most devices these days implement TTL, CMOS has become preferred for modern microprocessors and memory. Transistors within these devices use one signal to control another.

# Combinational Circuit
A combinational circuit is one which has an output dependent on a combination of inputs, which means they are used to implement [[Propositional Logic|logical]] equations.

# Arithmetic Circuits
**Shifters** are circuits which shift all bits in one direction, similar to the `>>` operator. Shifters can be used to make up multiplication algorithms. 

Another type is a **Decoder** which produces a unique output no matter the inputs. This means that given $n$ inputs it will produce up to $2^n$ outputs.
![[Pasted image 20220424072020.png|#invert|350]]
A **Multiplexer** is used to select and route and one input to a single output. This means it can be seen as the opposite of a decoder. It takes multiple input lines and directs information to single output line.

**Equality comparator** functions as a way of checking equality of datatypes of more than one bit. **Magnitude comparators** are used for comparison operations.

All of these types of operations can be merged into an **Arithmetic Logic Unit** (ALU). This functions as a central unit that is able to do mathematical and boolean operations.

## Adders
**Adders** are devices which take two input words and add them together to produce an output. A basic adder is the **half adder**, this device adds two bits together and outputs a result and a carry. A **full adder** consists of multiple half adders as to allow for the addition of binary numbers and a carry. A **Ripple Carry Adder** uses these full adders to add digit by digit to add to full binary numbers. This type of adder's speed is proportional to the number of bits. **Carry-lookahead** functions by calculating the carry in parallel to the actual addition. This speeds up execution, as the speed isn't proportional to the number of bits, at the cost of adding more gates. 
![[Pasted image 20220424071220.png|#invert|400]]

## Multipliers
Implementation of [[Multiplication Algorithms|multiplication]] usually involves a series of multiplication and shift operations. This allows for the operation to be significantly sped up. A common implementation of this is **Wallace multipliers** which uses half and full adders to compute partial sums.

# Sequential Circuit
A sequential circuit is a circuit which incorporates state. This makes them useful to create memory units. A basic memory unit is called a **latch** as it remembers a value. These latches can be expanded into **flip-flops** which require a clock signal to change their value. The most basic form of a sequential circuit is the **SR Latch**. It is a simple circuit that has two inputs, *set* and *reset*. This circuit is able to remember the previous set or reset inputs, outputting this memory when both set and reset are false. These latches can be expanded by adding a clock input that only allows for value changes when the clock is true. This can be created by:
![[Pasted image 20220424072853.png|#invert]]
A **D-latch** is similar to an SR latch but rather only has one input flag and a clock flag. It is similar to a SR-latch with an inverse of the input being fed into the reset.
