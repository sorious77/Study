---
Process
---

- Process

    program in execution ← process's current activity

    the states : new, ready, running, waiting , terminated

- PCB

- Queue

    Waiting queue : it is not executing

    I/O request queue :

    Ready queue : waiting for CPU && ready to execute

- Scheduling
    1. Long term (JOB) : will be allowed to contend for the CPU ← Resource-allocation, Memory management
    2. Short term (CPU) : from ready queue

- Parent/child mechanism

    concurrent execution → info sharing, computation speedup, modularity, convenience 

- Cooperating processes

    interprocess communication mechanism

    1. shared memory : exchange info through shared variables ← application programmers
    2. message passing : ← OS itself

    can be used simultaneously

- Communication in client-server system
    1. Socket : endpoint for communication 

     connection between a pair of application = pairs of sockets

    1. RPC (Remote Procedure Call) 

    on a remote application

    1. Pipe : simple 

    between parent & child ps

