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
  * Race Condition 발생 -> critical section 해결책
  
  
# Critical Section Problem

- Critial Section
    ```c
    do{
      entry section
        # critial section
      exit section
        # remainder section
    }while(true);
    ```
  
  임계구역의 조건 
  
    1. **Mutual exclusion** : critical section에는 하나의 PS만 실행 가능
    
    2. **Progress** : 임계 구역 미사용중이면, 다음에 critial section에 들어갈 PS 결정
    
    3. **Bounded waiting** : 기다리는 횟수 제한, 같은 PS 독점 금지, 기아 방지

# Preemptive kernel
  - 커널 모드이어도 선점 가능함
  
  - 우선 순위 적용 가능
  
```diff
  + CPU 스케줄링
```

# Peterson's solution

```c
int turn # 임계구역으로 진입할 PS의 순번
boolean flag[2] # 특정 PS가 임계구역 진입 준비가 되었다.
```
를 이용한 소프트웨어 해결법


# Mutex locks

- lock 이 가용하면 acquire()

- lock 반환시 release()

```diff
  - CPU 낭비 = 바쁜 대기
  + Context Switch X

 ```c
 acquire(){
  while(!available); # busy wait -> CPU cycle 낭비
  available=false;
 }
 ```
 ```c
 release(){
  available=true;
 }
 ```
 ```c
 do{
  acquire lock
    critical section
  release lock
    remainder section
 }while(true);
 ```


# Semaphore
- 이진 세마포어 = 뮤텍스락

- Counting 세마포어 : S 가용한 자원으로 초기화
```c
wait(S){
  while(S <= 0); # busy wait
  S--;
}
```
```c
signal(S){
  S++;
}
```

# Deadlocks

# 동기화 문제

# Monitor
