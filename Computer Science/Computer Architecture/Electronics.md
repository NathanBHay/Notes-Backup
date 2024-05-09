Modern computers are made of a series of electronics which build to create the basic [[Computer Architecture|architecture]] of a computer.

# Switches
A switch is used to convert mechanical actions into electrical [[Propositional Logic|logical]] signals. They operate under a [[Number Systems#Binary|binary]] closed or open wire which determines the state. Switches include pressure, temperature, voltage, limit, and more switch types. Switches can be **normally open** where its unactuated state reads negative or **normally closed** where its unactuated state is open. Switches can be **active high** where actuation causes a positive voltage, or **active low** where it produces a zero or negative voltage. The normal convention for a circuit is active high and normally open.

# Relays
A relay is an electro-mechanical device that changes electrical energy into mechanical movements. A contactor relay is a heavy-current type of relay. Relays were once used instead of circuit boards. Relays are constructed from:
- Iron circuits which are split into two parts, a stationary part and a moveable armature that produces an output.
- Springs which operate the mechanical parts.
- Coils that when energized with AC or DC will produce magnetic flux through the iron path.

Relays can be used as digital transducers as they convert a voltage or current level to another. Relays can be wired to create switch like structure due to their internal switches. Normal convention for relays are active high.

# Programmable Logic Controller
A PLC is an embedded microprocessor based solid state system. PLCs are designed to take inputs and perform [[Propositional Logic|logical]] functions to produce an output. A PLC is required to be cost and power efficient as well as reliable within any conditions. PLC architecture can be split into:
- **[[CPU]]** which runs programs as to produce an output.
- **[[Memory]]** stores the internal state of RAM, and ROM.
- **I/O Processor** directions the flow of signals in and out.
- **Communications** provides one or more port interfaces.
- **Peripheral Devices**, these include other PLCs or network devices.

The PLC operates under a cycle of scanning inputs, examining program logic, updating output and display.

PLCs commonly use a **Ladder Logical Diagram** to be programmed. These comprise a number of horizontal logical rungs that lead to an output coil. The two poles of the coil are labelled **L1** and **L2** where L1 is the hot conductor, and L2 is the grounded conductor. These diagrams can be used to make logic gates, with parallel contacts being or gates, series contacts being and gates, and normally closed contacts being not gates.

# Timers
Timers are devices that count increments as to produce a value given the time. There are three common types of timers:
- **On-Delay Timer** (TON) is a timer that returns a positive output after a select amount of time since the positive input.
- **Retentive On-Delay Timer** (TONR) is a cumulative TON that requires a reset for the timer's time to reset.
- **Off-Delay Timer** is a timer that delays an off output after the positive signal has been cut.

# Counter
A Counters is a timer that increments or decrements one count each time the input changes. These function similar to for loops. The common counter types are:
- **Up/Down Counter** (CTUD) increments or decrements an internal value each time the input transitions from 0 to 1.
