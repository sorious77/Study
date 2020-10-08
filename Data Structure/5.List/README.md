## List

- 배열과 같이 데이터를 선형적으로 저장하는 자료구조로, 크기가 가변적
- 주로 연결 리스트(Linked List)를 사용



### Linked List

- 리스트 내의 각 요소인 노드(Node)와 데이터(Data)로 구성

  <img src="https://user-images.githubusercontent.com/49060014/95408985-b0ee1900-095b-11eb-9225-f5c89a076101.png">

- 주요 연산

  - 생성
  - 추가
  - 탐색
  - 삭제

  ``` c++
  #include <iostream>
  
  using namespace std;
  
  struct node {
  	int data;
  	node* link;
  };
  
  node* createNode(int data); // 새로운 노드 생성
  void insertNode(node** head, node* newNode); // 노드를 리스트의 가장 뒤에 삽입
  node* find(node* head, int data); // 해당 값이 리스트 내에 존재하는지 탐색
  void deleteNode(node** head, int data); // 해당 값을 가진 노드가 있다면 삭제
  void printList(node* head); // 전체 리스트를 출력
  
  int main() {
  	node* head = NULL;
  
  	insertNode(&head, createNode(1));
  	insertNode(&head, createNode(2));
  	insertNode(&head, createNode(3));
  	printList(head);
  
  	node* temp = find(head, 5);
  	if (temp != NULL) {
  		cout << "5 exists in the list\n";
  	}
  	else {
  		cout << "5 doesn't exist in the list\n";
  	}
  
  	deleteNode(&head, 4);
  
  	deleteNode(&head, 2);
  	printList(head);
  }
  
  node* createNode(int data) {
  	node* newNode = new node;
  	newNode->data = data;
  	newNode->link = NULL;
  
  	return newNode;
  }
  
  void insertNode(node** head, node* newNode) {
  
  	if (*head == NULL) {
  		*head = newNode;
  	}
  	else {
  		node* temp = *head;
  		while (temp->link) {
  			temp = temp->link;
  		}
  		temp->link = newNode;
  	}
  }
  
  node* find(node* head, int data) {
  	for (node* temp = head; temp != NULL; temp = temp->link) {
  		if (temp->data == data) {
  			return temp;
  		}
  	}
  	return NULL;
  }
  
  void deleteNode(node** head, int data) {
  	node* location = find(*head, data);
  
  	if (location == NULL) {
  		printf("%d doesn't exist in the List... Cannot delete\n", data);
  	}
  	else {
  		if (location == *head) {
  			*head = (*head)->link;
  		}
  		else {
  			node* temp = *head;
  
  			while (temp->link != location) {
  				temp = temp->link;
  			}
  			temp->link = location->link;
  			free(location);
  		}
  	}
  }
  
  void printList(node* head) {
  	cout << "Print List\n";
  	for (node* temp = head; temp != NULL; temp = temp->link) {
  		cout << temp->data << " ";
  	}
  	cout << "\n";
  }
  ```

  - 앞, 뒤 노드의 정보를 모두 가지고 있는 더블 링크드 리스트도 존재



## In C++

- 헤더 파일 \<list> 선언 시 사용 가능

- 선언 방법 : list\<자료형> 이름

  ```c++
  #include <list>
  
  list<int> l;
  ```

- 라이브러리 함수 : [LINK](https://hyeonstorage.tistory.com/326)

  - push_back() : 리스트의 마지막에 데이터를 삽입
  - push_front() : 리스트의 처음에 데이터를 삽입
  - pop_back() : 리스트의 마지막 데이터를 삭제
  - pop_front() : 리스트의 처음 데이터를 삭제
  - size() : 리스트 내 데이터 개수 반환
  - reverse() : 리스트의 순서를 뒤집음
  - front() : 리스트의 처음 원소 반환
  - back() : 리스트의 마지막 원소 반환
  - empty() : 리스트가 비어있는지를 반환

  ```c++
  #include <iostream>
  #include <list>
  
  using namespace std;
  
  int main(){
      list<int> l;
      
      l.push_front(2); // 2
      l.push_front(1); // 1 2
      
      l.push_back(3); // 1 2 3
      l.push_back(4); // 1 2 3 4
      
      cout << l.front() << "\n"; // print 1
      cout << l.back() << "\n"; // print 4
      
      cout << l.size() << "\n"; //4
      
      l.reverse(); // 4 3 2 1
      
      l.pop_front(); // 3 2 1
      l.pop_back(); // 3 2
      
   	return 0;
  }
  ```

- Deque와 비교 : [LINK](http://egloos.zum.com/sweeper/v/2817817)



## PRACTICE

- 요세푸스 문제 : [LINK](https://www.acmicpc.net/problem/1158)
- 에디터 : [LINK](https://www.acmicpc.net/submit/1406/19336658)