---
Deadlock
---

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

# Resource Allocation Graph

- Vertex 정점  (P1,P2,... R1,R2..)
- Edge 간선 (자원요청, 자원할당)
- P 프로세스 집합
- R 자원타입 집합

# Deadlock solution

  - **Prevent**
    - 발생 가능성이 0이 되게한다
    - ***PS가 Resource 요구하는 방식에 제한***
  - **Avoid**
    - ***데드락 발생 가능성 여부가 있는지 계속 체크*** 
    - 가능성 있으면 조치
    - Resource 요청은 받지만 그 요청이 데드락 발생가능할 시 요구 거절
    - ***Safe / Unsafe state***
    - Safe sequence 가 하나라도 존재시, safe state
- **Detect & Recover**
  - **Ignore**

# Banker's Algorithm -*Avoid*

* Available : 이용가능한 자원
* Max : 각 프로세스별 최대 요구 자원수
* Allocation : 현 프로세스에 할당되어 있는 자원수
* Need: 실행 종료를 위해 필요한 남은 자원 수

Safe state 를 찾는 알고리즘

Safe면 프로세스에 자원할당

Unsafe면 프로세스는 대기하고 자원할당상태를 이전으로 복원

# Deadlock Detection -*Detect*

1. Single stance of each resource type

   Cycle 있을 경우 데드락

2. Instance 여러개

   데드락 탐색 ( 은행원 알고리즘과 비슷)

* 언제 호출할까?

  ​	데드락의 발생 빈도수, 데드락 발생시 영향을 받는 프로세스의 수에 따라

# Recovery from Deadlock

* Abort PS
  * 모든 데드락 PS들을 종료
  * 하나에 한번씩 종료, 데드락 풀리는지 check -> 오버헤드
* Preempt resource
  1. 어느 프로세스, 어느 자원을 뺏을지 결정 <- Cost 최소로
  2. Rollback : safe state로 롤백하고 나중에 재시작/ 처음 상태로 재시작
  3. Starvation : Cost factors에 Rollback 수 포함시켜 희생자 선택

