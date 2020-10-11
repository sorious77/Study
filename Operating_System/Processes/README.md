---
Process
---
```diff
- text in red
+ text in green
! text in orange
# text in gray
```
- Process

    program in execution ← process's current activity

    the states : 
    ```diff
    # new, ready, running, waiting , terminated
    ```

- Process Control Block(PCB)
```diff
- ps state, ps number, program counter, register...
+ 목적: 스케줄링, 메모리, I/O 접근...
```

- Process Scheduling
```diff
+ 목적: maximizae the CPU utilization
```

- Queue

    **Waiting queue** : it is not executing

    **I/O request queue** :

    **Ready queue** : waiting for CPU && ready to execute

- Process

    I/O bound
    
    CPU-bound

- Scheduling

    1. Long term (JOB) : from job pool
    
    will be allowed to contend for the CPU ← Resource-allocation, Memory management
    
    2. Short term (CPU) : from ready queue
    
    3. Medium term : mix 1 & 2

- PS Swapping

    Medium term 스케줄러 
    
    잠시 메모리에서 PS 제거

- Context Switch 

   하나의 프로세스를 실행하고 있는 상태에서

    interrupt 요청에 의해 다음 우선 순위의 프로세스가 실행되어야 할 때

    OS 스케줄러가

    *기존의 프로세스의 상태 또는 레지스터 값(Context)을 저장*하고 CPU가 다음 프로세스를 수행하도록 *새로운 프로세스의 상태 또는 레지스터 값(Context)*를 **교체하는 작업**
    
    ```diff
    + state save/restore
    - pure overhead <- HW의 지원 필요
    ```

    In Multiprocess environment
    
    
    
- Parent/child mechanism

    concurrent execution → info sharing, computation speedup, modularity, convenience 
    
- PS Creation

    fork()
    
    child : pid = 0 (return 0)
    
    parent : pid > 0 (return pid)
    
- PS Termination

    exit()
    
    deallocate resources
    
    wait()
    
    parent: exit status 값 받기를 기다림
    
    - zombie
        자식이 부모의 wait 호출 전 종료됨, 자식의 상태 모름
    - orphan
        부모 종료

- Interprocess communication (IPC)

    Cooperating processes

    **1. message passing** : ← OS itself
        
        limited data size
        
        easier to implement
        
        ```diff
        - Blocking (syn) vs Nonblocking (asyn)
        -  Message queue 용량에 따른 Buffering
        ```

    
    **2. shared memory : **
    
        cache coherency issue
        
        faster
        
        exchange info through shared variables ← application programmers
        
        ```diff
        - Producer-Consumer Problem
        
    **3. Direct read and write operation   **  

    can be used simultaneously

- Communication in client-server system

    **1. Socket** : endpoint for communication 

     connection between a pair of application = pairs of sockets

    **2. RPC (Remote Procedure Call)** 

    on a remote application

    **3. Pipe** : simple 

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

    wait for an interrupt...
   
    ```diff
    - Context : ps state, register
    ```    

    하나의 프로세스를 실행하고 있는 상태에서

    interrupt 요청에 의해 다음 우선 순위의 프로세스가 실행되어야 할 때

    OS 스케줄러가

    *기존의 프로세스의 상태 또는 레지스터 값(Context)을 저장*하고 CPU가 다음 프로세스를 수행하도록 *새로운 프로세스의 상태 또는 레지스터 값(Context)*를 **교체하는 작업**

    In Multiprocess environment

- PCB

    ps state : new, ready, run, paused, terminated

    ps counter : the cmd address that will be running next

    register : stack, register

    ps number

