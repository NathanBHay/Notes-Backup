A standard computer is made up of many components which build upon each other to create the modern computer. These levels of abstraction start with the [[Computer Architecture#Transistors Logic Gates|Transistor]] which create [[Computer Architecture#Transistors Logic Gates|Logic Gates]] that form [[Computer Architecture#Integrated Circuits|Integrated Circuits]]. These circuits make up integrated circuits, which are then used to construct components within the computer. Computer architecture isn't the same as implementation, with architecture being concerned with the approach to constructing a computer while implementation features the actual pats used.

# Transistors
The transistor is the lowest level of abstraction. These are basic [[Electronics|electronic]] circuits that have an *On* and *Off* state represented by a [[Number Systems#Binary|Binary]] digit. Originally the approach to constructing device with a Boolean state was handled by relays, these were later replaced by Vacuum tubes before becoming transistors. Transistor's digital nature allows for them to be small in comparison to their predecessors with less heat generation and faster speeds.

# Logic Gates
From transistors logic gates can be created which function on [[Propositional Logic|Boolean Logic]]. A **Circuit Diagram** can be used to represent [[Propositional Logic#Truth Table|Truth Tables]] and integrated circuits. The following gates are represented by:
![[Logic Gate Symbols.png|#invert|400]]
A property of physical gates that differ them from Boolean logic is that they aren't instantaneous. This is called **gate delay** which is the time it takes for a gate's output to change given an input that would switch the gate's state. This gate delay is denoted as $t_G$. The gate delay can be calculated by looking at the input and output states, and seeing how long it takes for the input to effect the output. Gate delay is different from gate to gate and design to design. Gate delay cascades as more gates delay is added causing **hazards**. There are two types of hazards those being:
- **Static hazard** when an input change results in a small reversal in the output before the output settles to the correct value.
- **Dynamic hazard** happens in complex logic circuits where multiple hazard states exist. This results in the value changing multiple times before settling.

To mitigate hazard you either have to design the circuit in a way to minimise hazard or use a circuit such as a latch to wait until it has settled.

# Integrated Circuits
[[Integrated Circuits]] are components made up of logic gates. These circuits build up basic components such as memory and functional components. From these larger circuits can be built that enable for more complex operations to be done on devices. This all builds to the creation of the technology behind the computer.

# Von Neumann Architecture
The Von Neumann Architecture is the standard approach to computer organisation. It defines a computer as three main components:
- **[[CPU]]** or Central Processing Unit which is divided into:
- **[[Memory]]** which is used to store data within the computer.
- **[[IO Devices]]** which includes anyway that the user is able to communicate with the computer's CPU directly.

From this level programs can be executed through the use of code defined by the varying levels of [[Program Exectution|Code Abstraction]].
