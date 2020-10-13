---
Thread
---

# THREAD

flow of control within ps -> Context switch time

    1. User thread : 
      
      application level, easy, blocking 시에 모든 쓰레드중지
      
    2. Kernel thread : 
    
        OS, memory management, complicated, OS가 모든 쓰레드 스케줄링

# Multithreaded Programming 

    1. responsiveness to the user : allow a program to continue running
    
    2. resource sharing within the process
    
    3. economy
    
    4. scalability : running parallel on multiple cores


- Multicore programming

Multiple cores on CPU chips

```diff
+ Concurrency
```

# Amdahl's law
```
speedup <= 1/(S+(1-S)/N)
```

# Parallelism

  - Data
  - Task

# Multithreading models

Map User threads to kernel threads

```diff
+ concurrency 증가
```

- Many to one 
- One to one
- Many to many
- 2 level : many to many + one to one

# Implicit threading

  - Thread pool

  - OpenMP

# Threading issues

  - fork() & exec()
  
  - Signal handling
  
  - thread cancellation
  
  - thread local storage
  
  - Scheduler activation




