Distributed computing is the coordination of computations across a network of systems. This is usually handled through [[Message Passing|message passing]], where computers, called **nodes**, complete computations across multiple locations. Distributed computers have to deal with topology of the system, failure tolerance, and the lack of a global [[CPU#Clocks|clock]].

**Clusters** are a group of general purpose processors connected through a fabric. They run cluster middle-ware that enables high-speed communication and coordination by running the same program to achieve parallelism.

**Grid computing** is an approach to parallelism through the use of grid middleware that distributed computers across networks.

# Fabrics
A fabric is an **interconnection network** used for communication between nodes. These fabrics are characterised by their topology which has the traits:
- *Network size*, number of nodes in the network.
- *Node degree*, number of I/O links per node.
- *Network diameter*, maximum number of hops to get from any node to another.
- *Bisection width*, minimum number of links broken to break network into 2 halfs.
- *Arc connectivity*, minimum number of arcs removed to break into two disconnected networks. Used for fault tolerance and contention.
- *Cost*, number of communication links in the network.

There are various possibly topology, with some including:
- *Linear array*, nodes are connected in a line.
- *Ring*, nodes are connected in a circle.
- *Star*, nodes are connected to a central node.
- *[[Tree Data Structures#Binary Tree|Binary tree]]*, nodes are connected in a tree structure.
- *Mesh*, nodes are connected in a square.
- *Torus*, nodes are kept in a [[Data Structures#Linked List|doubly linked list]], with them being arranged in a 2 or 3 dimensional orientation.
- *Hypercube*, a cube with eight edges, possibly connected to others cubs at scale.
- *Complete connection*, nodes are in a completed graph.

# Remote Procedure Call
Remote procedure calls (**RPC**) are function calls executed in a different [[Memory|address space]]. Any [[Processes#Inter-Process Communication|inter-process communication]] or server-side application is an example of this.

# Time Synchronisation Algorithms
Time synchronisation is a common issue with distributed 

# Election Algorithms
Election algorithms are a common method of concurrency control within distributed networks in cases where a node or process acts as a coordinator. They ensure that in the event of failure a new coordinator can be selected through an **election**. This election must be agreed upon by all processes.

## Bully Algorithm (Garcia-Molina)
The bully algorithm handles an election through an election message which is sent from one process to the rest, with processes possibly sending a message back. If no message is received that process becomes the new coordinator otherwise the process with the highest priority is selected. Once the election is decided a message is sent to all new processes.

## Ring Algorithm
The ring algorithm is used in cases where a ring topology is used. In this version the *election message* is passed between processes with each appending their priority until it returns to the original process. At this stage the message is changed to a *coordinator message* and sent around again. To handle dead nodes their usually is a timeout period for sent messages to ensure in the event of a failed message it can send to the next process in the ring.