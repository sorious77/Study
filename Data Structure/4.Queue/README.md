## Queue

- 특징

  - 먼저 삽입한 것이 먼저 삭제되는 FIFO(First In, First Out) 구조
  - 가장 앞에 있는(가장 먼저 삽입한) 데이터(Front)에만 접근 가능
  - 삽입이 일어나는 쪽을 Rear, 삭제가 일어나는 쪽을 Front라고 부름
  - Push(Enqueue), Pop(Dequeue) 연산 존재

-  활용

  - 버퍼(Buffer)

  - 너비 우선 탐색(BFS)
  - CPU Scheduling
  - 원형 큐(Circular Queue)
  - 우선순위 큐(Priority Queue)
  - 데크(Deque, Double Ended Queue)

<img src="https://user-images.githubusercontent.com/49060014/95403478-4afa9500-094d-11eb-8ce2-a7bcff5e46dc.png">

## In C++

- 헤더 파일 \<queue> 선언 시 사용 가능

- 선언 방법 : queue\<자료형> 이름

  ```c++
  #include <queue>
  
  queue<int> q;
  ```

- 라이브러리 함수

  - push() : 큐에 데이터를 삽입

  - pop() : 큐의 Front를 삭제

  - front() : 현재 큐의 Front에 있는 원소를 반환

  - empty() : 큐가 비어있는지를 반환

  - size() : 큐 내의 데이터 개수 반환

  - emplace() : 큐에 데이터를 삽입

  - swap() : 다른 큐와 데이터를 바꿈

  - back() : C++에서 지원하는 함수로, 큐의 Rear에 있는 원소를 반환

    ```c++
    #include <iostream>
    #include <queue>
    
    using namespace std;
    
    int main(){
        queue<int> q;
        
        q.push(1); // 1
        q.push(2); // 1 2
        q.push(3); // 1 2 3
        q.pop(); // 2 3
        q.push(4); // 2 3 4
        
        cout << q.front() << "\n"; // print 2
        cout << q.back() << "\n"; // print 4
        
        cout << q.empty() << "\n"; // false
        cout << q.size() << "\n"; // 3
        
        q.emplace(5); // 2 3 4 5
        
        queue<int> temp;
        
        q.swap(temp); // q : empty, temp : 2 3 4 5
        
        cout << q.empty() << "\n"; // true
        
        return 0;
    }
    ```



## Practice

- 큐 : [LINK](https://www.acmicpc.net/problem/10845)
- 프린터 큐 : [LINK](https://www.acmicpc.net/problem/1966)

## 우선순위 큐(Priority Queue)

- 원래 큐는 들어간 순서에 따라 데이터의 삭제가 이뤄지지만, 우선순위 큐는 데이터의 삽입 순서와는 관계 없이 우선 순위에 따라 데이터의 삭제가 이루어짐

- 주로 힙(Tree 단원 참고)을 이용해서 구현

- C++에서는 \<queue> 헤더 파일 선언 시 사용 가능하며, priority_queue<자료형, 컨테이너, 비교 함수>와 같이 선언

  - 라이브러리 함수는 [스택](https://github.com/sorious77/Study/tree/master/Data%20Structure/3.Stack)과 동일

  ``` c++
  #include <iostream>
  #include <queue>
  
  using namespace std;
  
  int main(){
      priority_queue<int, vector<int>, less<int>> pq; // or priority_queue<int> pq;
      // 내림차순의 우선순위 큐 선언
      // 오름차순의 경우는 priority_queue<int, vector<int>, greater<int>> pq; 와 같이 선언
      
      pq.push(123);
      pq.push(345);
      pq.push(45);
      pq.push(777);
      
      while(!pq.empty()){
          cout << pq.top() << "\n";
          pq.pop();
      }
      // print 777 345 123 45
      
      return 0;
  }
  ```



## 데크(덱, Deque)

- 일반적인 큐는 FIFO 형식을 사용하는 것에 비해, 데크는 양쪽에서 삽입과 삭제가 모두 가능함(스택+큐)

- 크기가 가변적이며, 앞뒤의 삽입/삭제는 편하지만 중간에 데이터를 삽입하는 것은 어려움

- 구현이 어렵기 때문에 주로 이중 연결 리스트(Doubly Linked List)를 사용해서 구현

  <img src="https://user-images.githubusercontent.com/49060014/95405050-ad559480-0951-11eb-858a-4f19cc74b0ed.png">

  ``` c++
  #include <iostream>
  #include <deque> // deque를 사용하기 위한 헤더 파일
  
  using namespace std;
  
  int main() {
      deque<int> dq; // deque<데이터 타입> 이름 으로 선언
  
      dq.push_back(1); // 1
      dq.push_back(2); // 1 2
  
      dq.push_front(0); // 0 1 2
      dq.push_front(-1); // -1 0 1 2
  
      cout << dq.front() << "\n"; // print -1
      cout << dq.back() << "\n"; // print 2
  
      dq.pop_front(); // 0 1 2
      dq.pop_back(); // 0 1
  
      cout << dq.size(); // 2
  
      return 0;
  }
  ```

  - 라이브러리 함수 :  [LINK](https://hyeonstorage.tistory.com/325)
  - [큐2](https://www.acmicpc.net/problem/18258)