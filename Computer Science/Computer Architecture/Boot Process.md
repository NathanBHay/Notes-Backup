The Boot Process is the series of instructions done as to get the computer into the state that it can run. This set of processes is stored in the **[[Memory|Read Only Memory]]** (ROM) of the computer. The Boot Process follows the steps:
1. Turn power on.
2. Power Good signal sent to motherboard.
3. [[CPU]] is reset and clock starts.
4. [[CPU]] reset triggers execution of instructions in the ROM.
5. Computer **POST**'s which checks all the computer's components.
6. Check video hardware.
7. Initialize other hardware.
8. Find the [[Operating System]].
9. Load the [[Operating System]] **Kernel** into the [[Memory|RAM]].
10. [[Operating System]] boot code loads OS Kernel.
11. Kernel Initializes drivers.
12. GUI Starts.

# BIOS
The Basic Input/Output System or BIOS is the programs microprocessor which starts after the computer starts. It manages the dataflow between the [[Operating System]] and attached devices. Most computers have a **Unified Extensible Firmware Interface** (UEFI) which gives a GUI to the BIOS and allows the user to modify the Boot Process.
