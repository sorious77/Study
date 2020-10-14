## Tree

- 노드들로 이루어진 자료 구조로, 그래프의 한 종류

- 용어

  - 루트 노드 : 부모가 없는 노드, 트리는 하나의 루트 노드를 가짐
  - 리프 노드 : 자식이 없는 노드
  - 내부 노드 : 리프 노드가 아닌 노드
  - 형제 노드 : 같은 부모를 가지는 노드
  - 깊이(Depth) : 루트에서 해당 노드까지 도달하기 위해 거치는 간선의 수
  - 레벨(Level) : 특정 깊이를 가지는 노드의 집합
  - 차수(Degree) : 노드의 경우는 해당 노드가 가진 자식의 수를, 트리의 경우는 트리에서 가장 큰 차수를 의미
  - 간선(Edge) : 노드를 연결하는 선
  - 높이(Height) : 루트에서 가장 깊은 곳에 위치한 노드의 깊이

  <img src="https://user-images.githubusercontent.com/49060014/95410750-c107f780-095f-11eb-8ebe-6f8fb9e53c10.png">

- 표현 방법

  - N-Link

    - 노드는 N개의 자식을 가질 수 있음

    ```c++
    #include <iostream>
    
    using namespace std;
    
    #define N 3
    
    struct node {
    	int data;
    	node *child[N];
    };
    
    node* createNode(int data);
    void printTree(node* root);
    
    int main() {
    	node* root;
    
    	int index = 0;
    
    	root = createNode(0);
    
    	for (int i = 0; i < N; i++) {
    		root->child[i] = createNode(++index);
    	}
    
    	for (int i = 0; i < N; i++) {
    		for (int j = 0; j < N; j++) {
    			root->child[i]->child[j] = createNode(++index);
    		}
    	}
    
    	printTree(root);
    }
    
    node* createNode(int data) {
    	node* newNode = new node;
    	newNode->data = data;
    
    	for (int i = 0; i < N; i++) {
    		newNode->child[i] = NULL;
    	}
    
    	return newNode;
    }
    
    void printTree(node* root) {
    	if (!root) {
    		return;
    	}
    	cout << root->data << " ";
    
    	for (int i = 0; i < N; i++) {
    		printTree(root->child[i]);
    	}
    }
    ```

    <img src="https://user-images.githubusercontent.com/49060014/95415938-88224f80-096c-11eb-9b9d-123c056e7fd1.png">

  - Left Child-Right Sibling

    - 각 노드는 가장 왼쪽 자식과 오른쪽에 위치한 형제의 포인터 주소를 가지고 있음

    ```c++
    #include <iostream>
    
    using namespace std;
    
    struct node {
    	int data;
    	node* leftChild;
    	node *rightSibling;
    };
    
    node* createNode(int data);
    void insertNode(node* root, node* cur);
    void printTree(node* root);
    
    int main() {
    	node* root;
    
    	int index = 0;
    
    	root = createNode(0);
    
    	root->leftChild = createNode(1);
    	insertNode(root->leftChild, createNode(2));
    	insertNode(root->leftChild, createNode(3));
    
    	node* temp = root->leftChild;
    	temp->leftChild = createNode(4);
    	insertNode(temp->leftChild, createNode(5));
    	insertNode(temp->leftChild, createNode(6));
    
    	temp = temp->rightSibling;
    	temp->leftChild = createNode(7);
    	insertNode(temp->leftChild, createNode(8));
    	insertNode(temp->leftChild, createNode(9));
    
    	temp = temp->rightSibling;
    	temp->leftChild = createNode(10);
    	insertNode(temp->leftChild, createNode(11));
    	insertNode(temp->leftChild, createNode(12));
    
    	printTree(root);
    }
    
    node* createNode(int data) {
    	node* newNode = new node;
    	newNode->data = data;
    	newNode->leftChild = NULL;
    	newNode->rightSibling = NULL;
    
    	return newNode;
    }
    
    void insertNode(node* root, node* cur) {
    	node* temp = root;
    
    	while (temp->rightSibling) {
    		temp = temp->rightSibling;
    	}
    
    	temp->rightSibling = cur;
    }
    
    void printTree(node* root) {
    	if (!root) {
    		return;
    	}
    	cout << root->data << " ";
    
    	for (node* temp = root->leftChild; temp != NULL; temp = temp->rightSibling) {
    		printTree(temp);
    	}
    }
    ```

    <img src="https://user-images.githubusercontent.com/49060014/95416904-b43ed000-096e-11eb-932b-8884ba6ddd8c.png">



## 이진 트리(Binary Tree)

- 자식을 최대 2개까지 가지는 노드로 이루어진 트리

- 성질

  - 레벨 <i>i</i>에서 최대 노드 수는 2<i><sup>i-1</sup></i>(<i>i >= 1</i>)
  - 깊이가 <i>k</i>인 이진 트리의 최대 노드 수는 2<i><sup>k</sup></i>-1(<i>k</i> >= 1)

- 종류

  - 포화 이진 트리(Full Binary Tree)

    - 리프 노드를 제외한 모든 노드가 2개의 자식을 가지고 있는 트리

    <img src="https://user-images.githubusercontent.com/49060014/95417814-ed783f80-0970-11eb-8c48-e1e7f395e91a.png">

  - 완전 이진 트리(Complete Binary Tree)

    - 리프 노드가 왼쪽부터 모두 쌓여있는 트리

    <img src="https://user-images.githubusercontent.com/49060014/95417835-fa952e80-0970-11eb-9e45-838d888d784e.png">

- 표현

  <img src="https://user-images.githubusercontent.com/49060014/95419438-9c6a4a80-0974-11eb-954a-5c3b37209efc.png">

  - 배열을 이용한 이진 트리

    - i번째 인덱스를 가진 노드의 자식은 각각 i\*2, (i\*2)+1을 인덱스로 가짐
    - 트리의 루트는 1을 인덱스로 가짐

    ```c++
    #include <iostream>
    
    using namespace std;
    
    void printTree(int* tree, int index);
    
    int main() {
    	int tree[100] = { 0, };
    
    	for (int i = 1; i <= 7; i++) {
    		tree[i] = i;
    	}
    	printTree(tree, 1);
    }
    
    void printTree(int* tree, int index) {
    	if (tree[index] == 0)
    		return;
    
    	cout << tree[index] << " ";
    	printTree(tree, index * 2);
    	printTree(tree, index * 2 + 1);
    }
    ```

    

  - 연결 리스트를 이용한 이진 트리

    - 노드는 구조체 형태를 지니며 데이터와 왼쪽/오른쪽 자식을 가짐

    ```c++
    #include <iostream>
    
    using namespace std;
    
    struct node {
    	int data;
    	node* leftChild;
    	node* rightChild;
    };
    
    node* createNode(int data);
    void printTree(node* root);
    
    int main() {
    	node* root;
    
    	root = createNode(1);
    	root->leftChild = createNode(2);
    	root->rightChild = createNode(3);
    
    	root->leftChild->leftChild = createNode(4);
    	root->leftChild->rightChild = createNode(5);
    
    	root->rightChild->leftChild = createNode(6);
    	root->rightChild->rightChild = createNode(7);
    
    	printTree(root);
    }
    
    node* createNode(int data) {
    	node* newNode = new node;
    	newNode->data = data;
    	newNode->leftChild = newNode->rightChild = NULL;
    
    	return newNode;
    }
    
    void printTree(node* root) {
    	if (root == NULL)
    		return;
    
    	cout << root->data << " ";
    	printTree(root->leftChild);
    	printTree(root->rightChild);
    }
    ```

    

- 탐색(Traversal)

  - 전위 순회(Preorder Traversal)

    - 루트 -> 왼쪽 자식 -> 오른쪽 자식 순으로 방문	

  - 중위 순회(Inorder Traversal)

    - 왼쪽 자식 -> 루트 -> 오른쪽 자식 순으로 방문

  - 후위 순회(Postorder Traversal)

    - 왼쪽 자식 -> 오른쪽 자식 -> 루트 순으로 방문

    <img src="https://user-images.githubusercontent.com/49060014/95419438-9c6a4a80-0974-11eb-954a-5c3b37209efc.png">

    ``` c++
    #include <iostream>
    
    using namespace std;
    
    struct node {
    	int data;
    	node* leftChild;
    	node* rightChild;
    };
    
    node* createNode(int data);
    void preorder(node* root);
    void inorder(node* root);
    void postorder(node* root);
    
    int main() {
    	node* root;
    
    	root = createNode(1);
    	root->leftChild = createNode(2);
    	root->rightChild = createNode(3);
    
    	root->leftChild->leftChild = createNode(4);
    	root->leftChild->rightChild = createNode(5);
    
    	root->rightChild->leftChild = createNode(6);
    	root->rightChild->rightChild = createNode(7);
    
    	cout << "Preorder : ";
    	preorder(root); // 1 2 4 5 3 6 7
    
    	cout << "\nInorder : ";
    	inorder(root); // 4 2 5 1 6 3 7
    
    	cout << "\nPostorder : ";
    	postorder(root); // 4 5 2 6 7 3 1
    }
    
    node* createNode(int data) {
    	node* newNode = new node;
    	newNode->data = data;
    	newNode->leftChild = newNode->rightChild = NULL;
    
    	return newNode;
    }
    
    void preorder(node* root) {
    	if (root == NULL)
    		return;
    
    	cout << root->data << " ";
    	preorder(root->leftChild);
    	preorder(root->rightChild);
    }
    
    void inorder(node* root) {
    	if (root == NULL)
    		return;
    
    	inorder(root->leftChild);
    	cout << root->data << " ";
    	inorder(root->rightChild);
    }
    
    void postorder(node* root) {
    	if (root == NULL)
    		return;
    
    	postorder(root->leftChild);
    	postorder(root->rightChild);
    	cout << root->data << " ";
    }
    ```



## PRACTICE

- 트리 순회 : [LINK](https://www.acmicpc.net/problem/1991)