---
Process Synchronization
---

# PS 동기화

  - Cooperating PS

  - Producer-consumer problem
  ```c
  # Producer
  while(true){
    while(counter==BUFFER);
    
    buffer[in] = next_produced;
    in=(in+1) % BUFFER;
    counter++;
  }
  ```
  
  ```c
  # Consumer
  while(true){
    while(counter==0);
    
    next_consumed= buffer[out];
    out= (out+1) % BUFFER;
    counter--;
  }
  ```
  
  - Critial section


# Preemptive kernel

# Peterson's solution

# Mutex locks

# Semaphore

# Deadlocks

# 동기화 문제

# Monitor
