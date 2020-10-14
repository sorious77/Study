---
Main Memory
---

## Instruction Execution Cycle

1. Program 명령을 받아와 from memory
2. Save results into memory

CPU가 Main mem의 Instruction cycle 수행

Fetch -> Decode -> Fetch Operands -> Execute -> Store





```diff
- CPU 는 오직 Main Memory와 Register에만 접근 가능
```

## Main Memory

- General purpose storage
- Direct access storage device

## Memory Access

| Kernel |
| ------ |
| Stack  |
| \|     |
| Heap   |
| Text   |

```diff
+ User PS, User의 OS access를 보호
```

* Base 

  legal physical mem address 의 가장 작은 값 저장한 register

* Limit

  range의 size

* PS 구역 

  Base <= 구역 < limit

```diff
+ User mode 의 PS가 타 OS 나 타user PS의 메모리에 접근하려하면 trap 
```





## Speed & Protection

- OS를(혹은 다른 프로세스를) 사용자 프로세스부터 보호
- HW solution

## Kernel mode & User mode

## Address binding

프로세스의 address를 어느시점에 어떻게 할당해줄 것인지

Symbolic -> Logical -> Physical

1. Compile Time 

   컴파일해서 실행파일로 만들 때 주소 결정

   ```diff
   + 프로그램 내부에서 사용하는 주소(Logical주소) == physical 주소
   + Absolute code
   - 프로그램이 하나도 실행되고 있지 않을때만 가능한 방법 (임베디드 시스템)
   - 사전에 메모리 내용 다 알고, 어디서부터 할당해야 좋은지 파악된 상태에서만 가능
   - 멀티 프로그래밍 시스템에서 불가능
   ```

   

2. Load Time

   프로그램 실행 전 메모리에 올릴때 주소 결정

   ```diff
   - 논리적 주소는 사용되기 전 물리적 주소에 매핑되어야함 (매핑은 MMU이용해 처리)
   + 상대주소 가능
   + relocatable code
   + 멀티 프로그래밍 가능
   - 메모리 로딩시마다 로딩 시간 길다 -> 실제로 안 쓰임
   ```

   

3. Execution Time

   실행하는 순간에 주소 결정

   실행시에 MMU 이용해 더해줌

   **Contiguous Allocation**

   ​	base address 값을 더해서 실제 physical 주소 만드는 방법



## Absolute Code <-> Relocatable Code

어셈블리어가 정한 위치에 물리적으로 고정된 코드

## Physical <-> Logical Address

- Physical

  실질적 메모리 주소 레지스터에 로드되는 주소체계

- Logical

  CPU에 의해 생성되는 주소체계

## Linker & loader

## Memory Address space

* Logical
* physical

## Memory Management Unit

CPU 코어 안에 탑재되어 가상 주소를 실주소로 변환해주는 장치

연속적으로 더해줌

범위 안이 아니면 trap : 잘못된 메모리 번지를 참조하지 않도록 memory protection

## 

## Contiguous Memory Allocation

```diff
+ MMU 간단 
+ memory protection fault 체크 쉽다
+ 하드웨어 만들기 쉽다
- 현재 쓰이지 않음
- fragmentation
```

Logically contagious => Physically contiguous

- First fit, best fit, worst fit

- **External Fragmentation**

  총 공간 계산시 요청을 만족할만한 충분한 메모리가 있음에도 

  가능한 공간이 연속적이지 않을때 ( 작은 hole들로 조각나있을때 )

  ```diff
  - 쓸데없는 공간 많다
  ! 원인 <- 가변분할 : 프로세스별로 메모리 할당  
  ```

  

- **Compaction**

  프로세스를 이동시켜. 공간 확보 후 대기중인 프로세스 넣기

  ```diff
  - temp한 하드디스크로 메모리를 copy하는 과정에서 I/O 오버헤드
  + 페이징의 배경
  ```

  

## Memory protection

* **Paging (고정 분할)**

  프로세스를 일정크기 page로 잘라서 메모리에 적재

  메모리를 고정된 크기로 할당

* **Internal fragmentation** 내부단편화

  프로세스가 페이지 한블록 크기보다 작은 추가적인 크기 가질 경우

* Page mapping table

  여기저기 흩어진 page와 frame을 매핑시키고 linear하게 실행될수 있도록 관리하는 테이블 

## Fragmentation

- External
- Internal







## Dynamic Loading

## Dynamic Linking

## Swapping

## Memory Allocation

## Dynamic storage allocation





## 



## 





