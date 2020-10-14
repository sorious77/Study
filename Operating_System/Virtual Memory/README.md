---
Virtual Memory
---

# Virtual Memory

- Logical / physical 메모리의 분리
- Dynamic memory allocation

```diff
+ RAM 의 부족한 용량 보완
```

**Frame**

​	물리 메모리를 사용하는 최소 크기 단위

**Page** 

​	가상 메모리 사용 최소 단위, 프로세스 구성 단위

# Demand Paging 

```diff
+ 다른 프로세스의 가각 페이지가 같은 프레임 가리키도록
+ 공유 메모리 사용 가능 
```



페이지 폴트 발생시 해당 페이지를 가상메모리에서 찾는 과정

페이지 폴트 해결하는 과정

- **Lazy swapper**

  요청 받기 전까지 메모리로 swap 하지 않음

  프로그램 실행중 요청(Demand) 받을 때 load pages

* **Swapper**

  물리 메모리에 동작하는 모든 프로세스를 로드하진 않는다.

* **Pager**

  프로세스의 모든 페이지를 물리메모리에 로드하지 않는다.

* **Page Fault**

  프로그램의 페이지가 물리 메모리에 부재하는 상황

* **Page Table**

  각 페이지가 저장된 주소값 저장

  Valid bit : 해당 페이지가 어느 메모리에 있는지 표시 가능

  ```diff
  + 가상메모리에서 페이지 쉽게 찾음
  ```

# Page replacement

1. 페이지 폴트이면 현 물리 메모리에 **비어있는 프레임**이 있는지 찾기
2. 비어있는 프레임에 해당 페이지 로드
3. 페이지 테이블 최신화
4. 중단된 CPU 다시 시작

물리 메모리에 비어있는 프레임이 없으면

희생 프레임을 골라서 가상 메모리에 저장

필요한 페이지 로드

1. FIFO : 가장 먼저 적재된 Page
2. LRU (Least Recent Used) : 가장 오랫동안 미사용인 page
3. LRU Approximation : LRU + Second chance( reference bit 사용 ) 
4. Counting : MFU, LFU

# Copy on Write ( 가상메모리 장점 )

부모 프로세스 clone 해 자식 프로세스 생성시

처음에는 같은 메모리 사용

그곳에 write 발생시 메모리 copy

같은 프레임 가리키도록 했다가 복사시에 새로운 프레임 할당

# Frame allocation

# Thrashing

실행 시간보다 페이지 교체 시간이 많아지는 현상

Locality 크기의 합 > 실제 메모리 크기

해결법

  - Working set model
  
  locality approximate한것으로 페이지 넘버로 관리
  
  working set > 실제 메모리 => 하나의 프로세스 종료
  
  - Page fault frequency

    한계점 넘어가면 프로세스 종료

- RAM 추가