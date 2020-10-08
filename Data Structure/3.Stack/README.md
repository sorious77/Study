## Stack

- 특징
  - 마지막에 삽입한 것이 가장 먼저 삭제되는 LIFO(Last In, First Out) 구조
  - 가장 위쪽에 있는 데이터(Top)에만 접근 가능
  - Push, Pop 연산 존재

- 활용
  - 깊이 우선 탐색(DFS)
  - 재귀 함수

<img src="https://user-images.githubusercontent.com/49060014/95403472-47ffa480-094d-11eb-9364-6bf4a335f46f.png">

## In C++

- 헤더 파일 \<stack> 선언 시 사용 가능

- 선언 방법 : stack\<자료형> 이름

  ``` c++
  #include <stack>
  
  stack<int> s;
  ```

- 라이브러리 함수

  - push() : 스택에 데이터를 삽입

  - pop() : 스택의 top을 삭제

  - top() : 현재 스택의 top에 있는 원소를 반환

  - empty() : 스택이 비어있는지를 반환

  - size() : 스택 내의 데이터 개수 반환

  - emplace() : 스택에 데이터를 삽입

  - swap() : 다른 스택과 데이터를 바꿈

    ```c++
    #include <iostream>
    #include <stack>
    
    using namespace std;
    
    int main(){
        stack<int> s;
        
        s.push(1); // 1
        s.push(2); // 2 1
        s.push(3); // 3 2 1
        s.pop(); // 2 1
        s.push(4); // 4 2 1
        
        cout << s.top() << "\n"; // print 4
        
        cout << s.empty() << "\n"; // false
        cout << s.size() << "\n"; // 3
        
        s.emplace(5); // 5 4 2 1
        
        stack<int> temp;
        
        s.swap(temp); // s : empty, temp : 5 4 2 1
        
        cout << s.empty() << "\n"; // true
        
        return 0;
    }
    ```

- <b>push vs emplace</b>

  - push와 emplace는 모두 stack에 데이터를 삽입하는 함수
  - 둘의 차이점은 push는 삽입하고자 하는 데이터의 복사본을 삽입하는 것이고, emplace는 새로운 데이터를 만드는 것이다.

## Practice

- 스택 : [LINK](https://www.acmicpc.net/problem/10828)

- 괄호 : [LINK](https://www.acmicpc.net/problem/9012)

- 후위 표기식 :  [LINK](https://www.acmicpc.net/problem/1918)

  