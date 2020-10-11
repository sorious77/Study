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


----------------------------------------------------------------------------------------------------------------------------------------------------
- Scheduling
    1. short-term(하위스케줄링) ← ps scheduler : CPU 할당 시기와 특정 ps 지정, context-switching 
    2. mid : 어떤 ps 가 CPU를 할당받을것인지 결정, 프로세스 too many → 일시보류 후 활성화 ( 부하조절 )
    3. long(상위, job) : 자원차지할 ps 결정 후 ready queue로 보냄 ← job scheduler

- Context-switching

    I/O request

    time slice expired

    fork a child

    wiat for an interrupt...

    Context : ps state, register 

    하나의 프로세스를 실행하고 있는 상태에서

    interrupt 요청에 의해 다음 우선 순위의 프로세스가 실행되어야 할 때

    OS 스케줄러가

    기존의 프로세스의 상태 또는 레지스터 값(Context)을 저장하고 CPU가 다음 프로세스를 수행하도록 새로운 프로세스의 상태 또는 레지스터 값(Context)를 **교체하는 작업**

    In Multiprocess environment

- PCB

    ps state : new, ready, run, paused, terminated

    ps counter : the cmd address that will be running next

    register : stack, register

    ps number
