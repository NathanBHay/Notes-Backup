MARIE is an assembly abstraction used in academia to teach the basics of assembly. Marie's architecture follows a basic Von Neumann model with the addition of a single **[[Memory#Registers|GPR]]** called the **Accumulator Register** (AR). This is used as the output of all commands. The MARIE commands include:
| Instruction | Note|
| --- | --- |
| Jns (0000)| Jumps and Stores PC at address |
| Load (0001) | Loads value into AC |
| Store (0010) | Stores value from AC into Memory |
| Add (0011) | Add value to AC |
| Subt (0100) | Subtracts value from AC |
|  Input (0101) | Request Input to AC |
| Output (0110) | Outputs AC Value |
| Halt (0111) | Halts Execution |
| Skipcond (1000) | Skips next instruction where: <br> 000 Skips Negative AC <br> 400 Skips AC = 0 <br> 800 Skips Positive AC
| Jump (1001) | Jumps to Address|
| Clear (1010) | Sets AC to 0 |
| Addi (1011) | Adds indirect
| JumpI (1100) | Jumps to Address at label |
| LoadI (1101) | Loads from Pointer |
| StoreI (1110) | Stores Pointer |

**Subroutines** or functions are called with the JNS statement and returned to with the JumpI statement. This works by storing the PC in the memory location defined by the JNS and returning to it with JumpI. This does however mean recursive functions don't work.

**Arrays** within MARIE the standard way to use arrays is to store adjacent data until a Decimal *0* terminator is read.
