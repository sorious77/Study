## Heap

- 완전 이진 트리(CBT)의 구조를 가짐
- Max Heap : 각 노드는 하위에 있는 모든 노드보다 큰 값을 가짐
- Min Heap : 각 노드는 하위에 있는 모든 노드보다  작은 값을 가짐
- 우선순위 큐(Priority Queue)를 구현할 때 주로 사용

<img src="https://user-images.githubusercontent.com/49060014/95425473-4bac1f00-097f-11eb-8875-3b22aed4de4c.png">

- 연산

  - 삽입
    1. 완전 이진 트리를 만족할 수 있는 리프 노드의 위치에 새로운 데이터 값을 가진 노드 삽입
    2. 부모 노드와 비교하며 삽입 위치를 찾음 
  - 삭제
    1. 루트 노드의 데이터를 삭제하고, 가장 끝의 데이터를 루트 노드 자리로 이동
    2. 자식 노드와 비교하며 삽입 위치를 찾음(둘 다 힙 규칙을 위반한다면, Min Heap은 더 작은 값과 교환하고 Max Heap은 더 큰 값과 교환)

- 구현

  - 주로 배열을 이용하여 구현하며, 시작 인덱스는 1을 사용

  ```c++
  #include <iostream>
  using namespace std;
  
    void insertHeap(int* heap, int num, int *index); // heap에 num을 삽입하는 함수
    int deleteHeap(int* heap, int* index);
  
    int main() {
    	int maxHeap[100] = { 0, };
  
    	int index = 0;
  
    	insertHeap(maxHeap, 1, &index); // 1
    	insertHeap(maxHeap, 2, &index); // 2 1
    	insertHeap(maxHeap, 3, &index); // 3 1 2
    	insertHeap(maxHeap, 4, &index); // 4 3 2 1
  
  
    	cout << deleteHeap(maxHeap, &index) << "\n"; // 3 1 2
    	cout << deleteHeap(maxHeap, &index) << "\n"; // 2 1
    	cout << deleteHeap(maxHeap, &index) << "\n"; // 1
    	cout << deleteHeap(maxHeap, &index) << "\n"; // empty
    }
  
    void insertHeap(int* heap, int num, int *index) { // index 자리에 num을 삽입하는 함수
    	if (*index == 0) {
    		heap[++(*index)] = num;
    		return;
    	}
  
    	(*index)++;
  
    	int temp = *index;
  
    	while (true) {
    		if (temp <= 1)
    			break;
  
    		if (heap[temp / 2] > num) {
    			heap[temp] = num;
    			break;
    		}
  
    		heap[temp] = heap[temp / 2];
    		temp /= 2;
    	}
  
    	if (temp == 1)
    		heap[temp] = num;
    }
  
    int deleteHeap(int* heap, int* index) {
    	int data = heap[1]; // heap의 루트 노드를 반환
  
    	heap[1] = heap[*index];
    	heap[(*index)--] = 0;
  
    	int cur = 1;
    	int temp = heap[1];
  
    	while (true) {
    		if (heap[cur * 2] == 0) // 리프 노드인 경우
    			break;
  
    		int next;
  
    		if (heap[cur * 2 + 1] == 0) // 자식이 하나인 경우, 다음에 비교할 자식은 왼쪽 자식
    			next = cur * 2;
    		else {
                // 자식이 두개인 경우, 더 큰 값을 가진 자식과 비교
    			next = heap[cur * 2] > heap[cur * 2 + 1] ? cur * 2 : cur * 2 + 1;
    		}
  
    		if (temp < heap[next]) { // 자식과 자리를 바꿔야할 경우
    			heap[cur] = heap[next];
    			cur = next;
    		}
    		else {
    			heap[cur] = temp;
    			break;
    		}
    	}
  
    	heap[cur] = temp;
  
    	return data;
    }
  ```