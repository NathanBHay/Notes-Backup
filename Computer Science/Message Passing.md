Message passing is a technique of communication amongst [[Processes|processes]] or agents where messages are sent between routines. Message passing is important for the functioning of [[Operating System|operating systems]] and are a model of [[Parallelism|concurrency]]. Message passing can happen either on local systems through [[Processes|processes]] or on [[Distributed Computing|distributed systems]]. 

# Blocking
Blocking [[IO Devices|IO]], also called **synchronous message passing** occurs when process communication is handled through an interface which waits for a sender to send the message and the receiver to receive it. This ensures the program executes correctly as a message is waited for. Despite this it can result in a noticeable speed decrease as the program stalls.

# Non-Blocking
Non-blocking IO, also called **asynchronous message passing** doesn't wait for messages to be sent and received but rather uses intermediary software to handle the process. This can result in less stalls as processes don't need to wait.