Code profiling is the process of measuring and evaluating aspects of code to ensure optimisation. While [[Complexity Analysis|complexity analysis]] through big-O notation does enable a general prediction of code complexity it lacks the ability to map real-world conditions such as [[Cache|cache misses]], [[Memory|memory topology]], and [[Operating System|context switches]]. Therefore, to achieve better analysis various techniques and tools can be used to monitor code.

# Timing
The most basic approach to finding time taken by code is to measure the elapsed time for execution. There are three types of time which are commonly used:
- **Real-time** which is the total time taken including [[Operating System#Multitasking|multi-programming]] (waiting for other processes to execute), stalls from network or I/O, and any other additional time.
- **User-time** is the time the CPU spent running the code in user mode.
- **System-time** is the time spent running in kernel mode.

There are two main ways to time code, which are using a CLI application such as `time` or `perf` to monitor the time or using a timer function within the code to measure a specific part of the code.