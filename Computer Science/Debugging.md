A computer *bug* (also sometimes called a glitch) is an issue with a computer program or [[Algorithms|algorithm]] that results in incorrect execution. The process of finding these errors is referred to as **debugging**. To find a bug in a program it is common to check for errors in values, errors in loop invariants, and other logical issues. There are various methods of finding bugs within a program.

# Print Statement Debugging
**Print statement debugging** is the process of using a print function to check variables for issues. This is the simplest approach and is able to be done in nearly all programming languages. Despite this flexibility it lacks 

Another form of debugging which is similar are logs, which is information printed to a file such that it can be viewed later. These are common in programs which utilise an error system.

# REPL Debugging
A read-eval-print-loop or repl is a tool which allows for code to be ran in a small environment. This allows for functions to be tested with data allowing for debugging.

# Debugger
A debugger is a tool that is used for finding bugs within a program usually through sequential execution of instructions with memory readouts. A debugger works by stepping through either compiled or interpreted instructions, stopping a **break points** specified by the programmer. The **debugger adaptor protocol** (DAP) is standard way of implementing debuggers that allow for a wide variety of editors to easily connect to a debugger.

# Traces
There are a variety of tools which allow for traces of important function or [[Operating System#Kernel Mode & System Calls|system calls]]. A common example of this is within error logs which displays the functions calls which led to the error. System calls are another thing which can be tracked.

# Static Analysis
Static analysis is the process of examining source code to find potential issues. This is usually provided by a [[IDE#Language Server|LSP]], or linter. These tools find issues related to types, naming, and loops.