## Graph

- 정점(Vertex)와 간선(Edge)로 구성된 집합

- 용어
  - 정점(Vertex) : 위치를 나타냄(Node라고도 부름)
  - 간선(Edge) : 정점을 잇는 선을 의미
  - 인접(Adjacent) : 간선으로 이어진 두 정점간의 관계
  - 경로(Path) : 인접한 정점들로 이루어진 집합
  - 단순 경로(Simple Path) : 경로 중에서 반복되는 정점이 없는 경우
  - 싸이클(Cycle) : 단순 경로에서 시작 정점과 종료 정점이 같은 경우
  - 오일러 경로(Eulerian Path) : 그래프 상의 모든 간선을 한 번씩 방문하는 경로(이 때, 시작과 끝이 같으면 오일러 회로(Circuit)이라고 부름)
  
- 구현

  - 인접 행렬(Adjacency Matrix)

    - N개의 정점을 가진 그래프
    - NXN 크기의 행렬을 이용하여 (x,y)가 연결되어 있다면 matrix[x,y]를 1로, 연결되어 있지 않다면 0으로 표기
    - (x,x)의 값이 항상 0
    - 방향이 없는 그래프의 경우 (x,x)를 기준으로 대칭을 이룸
    - 정점 간의 연결 여부를 쉽게 알 수 있음
    - 사용하는 메모리 양이 큼(정점의 크기 : N<sup>2</sup>)

    <img src="https://user-images.githubusercontent.com/49060014/95818708-74f1f400-0d5f-11eb-918c-20cf4802a56a.png">

    - 방향이 없는 그래프

    <img src="https://user-images.githubusercontent.com/49060014/95818743-84713d00-0d5f-11eb-8922-58cf35f821a4.png">

    - 방향이 있는 그래프

  - 인접 리스트

    - 해당 정점과 연결되어 있는 정점을 연결 리스트를 통해 저장
    - 연결 여부를 확인하기 위해 인접 리스트를 통한 순차 탐색이 필요
    - 정점과 간선의 삽입이 빠르고 메모리가 적게 소모됨

    <img src="https://user-images.githubusercontent.com/49060014/95819199-68ba6680-0d60-11eb-961d-5b09a4dc56ce.png">

  - 각각 장단점을 고려하여 사용하는 것이 중요!

- 그래프 순회

  - 깊이 우선 탐색(Depth First Search)

    - 더 나아갈 곳이 없을 때까지 깊이 들어간 후, 다시 돌아와 다른 정점을 방문

    - 스택이나 재귀 함수를 이용

    - 과정

      1. 해당 정점을 "방문"으로 표시
      2. 이웃 정점 중 방문하지 않은 정점을 방문, 더 이상 방문할 정점이 없을 때까지 1을 반복
      3. 해당 정점에서 더 이상 방문할 수 있는 정점이 없을 경우, 이전 정점으로 돌아가서 2를 반복
      4. 이전으로 돌아가도 방문할 수 있는 정점이 없을 경우, 탐색을 종료

      ```c++
      void dfs(vertex *v){
          edge *e = NULL;
          
          printf("%d ", v->data);
          
          v->visited = true;
          
          e = v->adjacencyList;
          
          while(e!=NULL){
              if(e->node != NULL && e->node->visited == false){
                  dfs(e->node);
              }
              
              e = e->link;
          }
      }
      ```

      

  - 너비 우선 탐색(Breadth First Search)

    - 같은 깊이에 있는 모든 정점을 방문하고, 다음 깊이를 방문
    - 큐를 이용

    - 과정

      1. 해당 정점을 "방문"으로 표시
      2. 큐에서 해당 정점을 삭제하고, 정점의 이웃 중 방문하지 않은 정점을 큐에 삽입
      3. 큐가 비면 탐색을 종료

      ```c++
      void bfs(vertex *v){
          queue<int> q;
          
          printf("%d ", v->data);
          v->visited = true;
          
          q.push(v);
          while(!q.empty()){
              vertex *temp = q.top();
              q.pop();
              
              edge *e = v->adjacencyList;
              
              while(e != NULL){
                  v = e->node;
                  if(v!=NULL && v->visited == false){
                      printf("%d ", v->data);
                      v->visited = true;
                      q.push(v);
                  }
                  e = e->link;
              }
          }
      }
      ```

## PRACTICE

- DFS와 BFS : [LINK](https://www.acmicpc.net/problem/1260)

  