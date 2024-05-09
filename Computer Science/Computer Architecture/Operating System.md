The operating system is the level of abstraction which handles the interface between [[Program Exectution|programs]] and the [[Computer Architecture|hardware]]. It allows users to access commonly called functions while also protecting memory. OS are required for **end users** and programmers to access the lower levels of the system. It thus **virtualises** physical processes.

# Time Sharing
Time Sharing is a process done when the OS Kernel switches between processes to create an illusion of concurrency. To do this the OS has two forms of operation those being:
- **Kernel Mode** which code has no restrictions and interrupts are handled.
- **User Mode** which has a limited subset of instructions and applications that can run.

To use the computer's [[IO Devices]] a **system call** is triggered to switch to Kernel mode. This switch runs on a timer circuit that generates [[IO Devices#Interrupt I O|Interrupts]]. A method of doing these calls is called **round robin time-slicing**.
