# Introduction

## Operating system?

1. Resource allocator to manage the computer HW
- CPU time, memory, sortage, I/O devices...
2. provide an environment for application programs to run
- prevent errors
3. interface to the computer system provides to the user

## Computer System
1. CPU, Device controller
2. Memory controller

## Computer Operation
1. Bootstrap
- init computer
- load kernel
2. Start Kernel
- Handel I/O requests
3. System daemons
- Services for system, users ( network, security )
4. Handle Interrupts
- Interrupt vector

## Interrupt Handling by CPU
1. CPU can work user processes while I/O devices are working
2. Save the address of process worked 
3. Handle interrupt from I/O
4. Restore 

## Main memory

1. only processor can access directly 
2. arrays of bytes which have own address
3. volatile

- ROM (bootstrap)
- RAM (load/store)

## Secondary memory

1. nonvolatile
2. magnetic disk
3. holding large quantities of data (and programs)
4. Storage system organized in a hierarchy
  - cost per bit 반비례 access time

## I/O Structure
CPU - common bus - Device controller

1. Device controller
  - local buffer 
  - special purpose registers
2. Device driver
  - device controller 이헤
  - uniform interface to the device 

## Direct memory access (DMA)
1. tranfer an entire block of device data to memory **without CPU**


## Single-processor system
1. CPU: general-purpost instruction
2. Device controller: special purpost processor

## Multi-processor system

1. Sharing computer bus, physical memory, peripheral devices...

***장점***
1. throughput
  ~~N CPUs = N times throughput~~
2. 규모의 경제
  2.1 sharing resource
3. Reliability
  3.1 Grace degradation
  3.2 Fault tolerant System

  **- Symmetric multiprocessing (SMP) <-> ASMP (boss-worker)**
  
    1. multiprocessor design
    2. all processors are considered peers
    3. run independently of one another

  **- Clustered system**
  
    1. multiprocessor system
    2. consist of multiple computer systems connected by a local-area net

## Utilize the CPU

multiprogramming 

1. allows several jobs to be in memory at the same time
2. CPU always has a job to execute

Time-sharing system

1. extension of multiprogramming
2. CPU scheduling algorithms rapidly switch between jobs → illusion

## Correct operation

Dual more

1. hw has 2 modes ( user / kernel )

Privileged Instructions

1. Instruction ( I/O, halt ) are privileged and executed only in kernel mode

Memory protection

1. The memory be protected from modification by the user

Timer interrupt

1. Timer prevents infinite loops

## Process ( job )

fundamental unit of work 

- Process management
1. creat/delete/ processes
2. providing mechanisms for processes to communicate and synchronize with each other

- Memory management
1. keeping track of what parts of memory are being used and by whom
2. dynamically allocating
3. freeing memory space

- File system
1. represent files and dir
2. manage space on mass- storage devices

- Security
1. control the access of processes / user to the resources
    1. defending a computer system from external or internal attacks
    
---------------------------------------------------------------------------------------------------------------------------------------------

- multiprogramming & time-sharing environment

Stealing or copying one’s programs or data

Using system resources (CPU, memory, disk space, peripherals ) without proper accounting

- resource utilization

Mainframes : mem, CPU, storage, net bandwidth

Workstations : mem, CPU

Handheld : power consumption, mem

- Time-sharing system rather than PC, single-user
1. large task
2. fast hw
3. few other users

- Functionalities need to be supported by os

Batch programming ?

Virtual mem : handheld, real-time systems

Time sharing : real-time

- symmetric multiprocessing

treats all processors as equals

I/O on any CPU

- Asymmetric multiprocessing

one master CPU ← I/O

master distributes tasks among slaves

- Multiprocessors

save money

not duplicate power supplies

execute programs more quickly

reliability

more complex in both hw, sw

- Clustered system

combine multiple computers into single system

communicate using msg

if they cooperate to provide a highly available service

→ should be replicated 

→ one fail, the other take-over

- Multiprocessor

single physical entity comprising of multiple CPUs

communicate using shared mem

- Client-server

- Peer-to-peer
