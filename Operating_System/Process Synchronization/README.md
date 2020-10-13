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
  * Race Condition
  
  - Critial Section
    ```c
    do{
      entry section
        # critial section
      exit section
        # remainder section
    }while(true);
    ```
# Critical Section Problem
  
  임계구역의 조건 
    1. **Mutual exclusion** : critical section에는 하나의 PS만 실행 가능
    2. **Progress** : 임계 구역 미사용중이면, 다음에 critial section에 들어갈 PS 결정
    3. **Bounded waiting** : 기다리는 횟수 제한, 같은 PS 독점 금지, 기아 방지

# Preemptive kernel

# Peterson's solution

# Mutex locks

# Semaphore

# Deadlocks

# 동기화 문제

# Monitor
