The Boot Process is the series of instructions done as to get the computer into the state that it can run. This set of processes is stored in the **[[Memory|Read Only Memory]]** (ROM) of the computer. The boot process is handled. The Boot Process follows the steps:
1. Power on sent to the motherboard.
2. [[CPU]] is reset and clock starts, triggering execution of instructions in the ROM.
3. Computer **POST**'s which checks all the computer's components and starts to initialise hardware
4. Find and load the [[Operating System|OS kernel]] into the [[Memory|RAM]], booting from this.
5. Kernel starts drivers and other applications

# BIOS
The Basic Input/Output System or BIOS is the programs microprocessor which starts after the computer starts. It manages the data-flow between the [[Operating System]] and attached devices. It is considered a legacy approach to managing your computer's boot procedure.

# UEFI
More common is the **Unified Extensible Firmware Interface** (UEFI) which gives a GUI to the BIOS and allows the user to modify the Boot Process. Some UEFI implementations have a partition called an **EFI partition** which contains the boot-loader and files for rendering the UEFI.