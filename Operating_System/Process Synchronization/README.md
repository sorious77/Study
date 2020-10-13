---
Process Synchronization
---

# PS 동기화

  - Cooperating PS

  - Producer-consumer problem
  ```c
  // Producer
  while(true){
    while(counter==BUFFER);
    
    buffer[in] = next_produced;
    in=(in+1) % BUFFER;
    counter++;
  }
  ```

  ```c
  // Consumer
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
        // critial section
      exit section
        // remainder section
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
int turn // 임계구역으로 진입할 PS의 순번
boolean flag[2] // 특정 PS가 임계구역 진입 준비가 되었다.
```
를 이용한 소프트웨어 해결법


# Mutex locks

- lock 이 가용하면 acquire()

- lock 반환시 release()

```diff
- CPU 낭비 = 바쁜 대기
+ Context Switch X
```

 ```c
 acquire(){
  while(!available); // busy wait -> CPU cycle 낭비
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
- **Counting 세마포어** : S 가용한 자원으로 초기화
```diff
- Timing error : difficult to detect
- 모든 프로세스는 critical section 실행전 반드시 wait(mutex);
- Deadlock 발생 위험
```



```c
wait(S){
  while(S <= 0); // busy wait
  S--;
}
```
```c
signal(S){
  S++;
}
```

## 우선순위 역전

- **공유 자원의 동기화**로 인해 발생 <- **세마포어**를 얻어야 공유자원 사용 가능
- 높은 순위 PS가 낮은 순위 PS로 인해 수행이 block 된 상태
- 우선순위가 높은 상이 실행 안되는 문제 : 프로세스 수가 많은 시스템에서 문제
- 세마포어가 필요한 작업에서 우선순위 **'하'인 프로세스가 세마포어를 가지고있음**

## 해결: 우선순위 계승 프로토콜 

- '상' 프로세스를 블록시키고 있는 '하'를 요청한 우선순위 '상'만큼 우선순위 높여줌
- '하' 가 세마포어 반환시 원래 우선순위로 돌아감
- '하'가 빨리 race condition 벗어나 세마포어 반납 = 우선순위 역전 시간 단축

# Deadlocks

하나의 PS 때문에 2개 이상의 PS가 무한 대기 상태



## Starvation

스케줄링, 상호배제 알고리즘에서 나온 에러에 의해 발생

세마포어에서 프로세스가 무한 대기 상태인 경우



## 용어

* Resource : 
* Instance :
* Request :
* Use : 
* Release : 

PS 는 자원 사용 전 반드시 요청하고 사용 후에는 자원을 반납

## 4 가지 조건

1. **Mutual Exclusion**

2. **Hold and Wait**

   특정 자원 소유한 상태에서 추가로 다른 자원 얻으려고 대기

3. **No preemption**

   *공유 자원(세마포어, lock ..)*에 대한 선점

   이미 다른 PS가 소유하고 있는 자원 강제로 뺏을수 없음

4. **Circular Wait **

   p1이 소유한 자원을 p2가 요구, p2가 소유한 자원 p1이 요구

## 교착상태의 표현

- Resource Allocation Graph
  - Vertex 정점  (P1,P2,... R1,R2..)
  - Edge 간선 (자원요청, 자원할당)
  - P 프로세스 집합
  - R 자원타입 집합

# 동기화 문제

## Bounded buffer probelm

- Producer & Consumer 

  ​	race condition 의 해결: ***Semaphore***

  ​	Bounded buffer 의 해결 : Circular array 로 구현 ( in, out 포인터 사용 )

## Readers Writers problem

하나의 DB 공유

- Writer : DB 수정
- Reader: DB 읽기

Exit section 

```c
if(read_count == 0) // critical section 머물러있는 reader가 하나도 없을때
  signal(rw_mutex) // writer가 공유 데이터에 접근 가능
```

```diff
- Writer 에 Starvation 문제 초래
```



## Dining philosopers problem

```c
semaphore chopstick[5]; // Binary semaphore
do{
  wait(chopstick[i]);
  wait(chopstick[(i+1)%5]);
  //Eating
  signal(chopstick[i]);
  signal(chopstick[(i+1)%5]);
  //Thinking
}while(true);
```

Deadlock

# Monitor

- ADT
- 모니터안에서 항상 하나의 프로세스만 Run
- 진입을 원하는 다른 프로세스는 entry queue
- Condition variable : running 중인 프로세스가 I/O 작업시, 시간 낭비 프로세스를 condition queue 에 넣어 재우다가 running 준비되면 깨워주기 전까지 보관 

```c
x.wait(); // 재우기
y.wait();
x.signal(); // 깨우기
y.signal();
```



```diff
+ No deadlock
- Starvation 위험 
```



# OpenMP

```c
#pragma omp critical
```

