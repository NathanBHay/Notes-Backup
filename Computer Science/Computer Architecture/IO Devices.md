All interaction with a computer done by a user is through I/O devices. In early computers the I/O was handled by punch tape and a read/write header. Modern computers use many I/O devices (internal and external) whether it be mice, keyboards, disc, sensors, or any other device. These devices communicate through **standardised interfaces** such as USB, SATA or HDMI. I/O devices communicate with the [[CPU]] through **I/O Registers** with each device having its own registers. There are two types of **I/O Registers** these are:
- **Memory-Mapped I/O** use the same address space as user memory, with the same instructions.
- **Port-Mapped I/O** uses a separate memory space for its own unique set of instructions.

I/O is interpreted by the [[CPU]] through 2 methods [[IO Devices#Programmed I O|Programmed I/O]] and [[IO Devices#Interrupt I O|Interrupt I/O]].

# Programmed I/O
Programmed I/O uses a process called **polling** which cycles through devices to work out device is being used. This is a simple approach which requires no extra hardware. Despite this the response time is long waiting for a whole polling loop before the device can be serviced. This causes the devices to be unpredictable as the amount of devices depend on the time it takes to be serviced. Systems that use this approach usually are made for a specific purpose.

# Interrupt I/O
Interrupt I/O communicates by sending a message to the **Interrupt Handler** within the [[CPU]] which pauses the current execution and does the required process. This handler depends on the type of device with [[CPU#Microcode|microcoded]] machines checking between micro programs for interrupts, vectored systems telling the device to assert a vector, and hardwired machines with dedicated logic. 

To determine what device caused the interrupt the basic approach is to use an **interrupt register**. This consists of a binary number which lists what specific devices have caused the interrupt. Another approach is the **interrupt vectoring** which sends a memory address to the CPU as to allow it to execute the code specified by the interrupting device. A **vector table** follows this principle by moving CPU's execution to a table which then determines which device caused the interruption. This decreases the amount of memory used at the cost of additional jumps.

Priority resolution happens when multiple devices interrupt simultaneously. There are two commonly used approaches:
- **Priority pre-emptive** servicing interrupts are assigned with a fixed priority which determines order.
- **Round robin** scheduling which services the first interrupt before others.

The **interrupt service routine** is called by the handler for the individual device to cause a [[CPU#Context Switch|context switch]] through the use of two methods. Those being:
- **Shadow Registers** which store old registers in a separate file.
- **Software** which saves and returns registers.

Interrupts that happen during the ISR of other interrupts can be handled in a few ways. The most basic is to disable all interrupts. This however can cause issues and as a result most of the time an **interrupt mask** is used. This bit-mask disables certain interrupts from interrupting the execution of the ISR. 

Interrupts used to be physical however currently they are done through **Advanced Programmable Interrupt Controller** (APIC).

## Software Interrupts
**Software interrupts** also called machine checks, exceptions and traps are a type of interrupt caused by software with [[Defensive Programming|exceptions]] being an example of this. 