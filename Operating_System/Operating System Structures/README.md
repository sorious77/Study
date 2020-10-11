---
OS Structure
---

- Application programming interface (API)
    - portability
    - programmers' 편의

- System Calls ( lowest level )
    - running program to make requests from the os directly

- Command Interpreter / shell ( higher level )
    - provides mechanism for a user to issue a request without writing program

- Commands
    - come from files ( during batch mode execution )
    - come directly from terminal / desktop GUI ( in interactive / time - shared mode )

- System programs ( higher level )
    - satisfy common user requests

- Type of requests ← level
    1. System-call level : provide basic functions ( process control,  file, device manipulations )
    2. Command Interpreter / System programs : sequence of system calls
    3. System services : program control, status requests, I/O requests
    4. Program errors : implicit requests for services

- Design of OS
    1. set the goal of the system ← type of system
    2. algorithms and strategies

- Policy decisions from implementation detail (mechanisms)
    - allows max flexibility if policy are to be changed later

- Implementing OS

    written in higher level lang → improves implementation, maintenance, portability

- Modularity
    1. sequence of layers / microkernel
    2. dynamically loaded modules → adding functionality to an OS while it is executing
    3. hybrid approach : combines several different types of structures

- Debugging / Failures

    using tools analyze core dumps

    analyze production systems(DTrace) to find bottlenecks 

- OS for a particular machine configuration
    1. perform system generation
    2. CPU initialize and start executing the bootstrap program 
    3. bootstrap executes the OS directly 
    4. bootstrap completes a sequence in which it loads smarter programs 
    5. until OS itself is loaded into memory and executed
