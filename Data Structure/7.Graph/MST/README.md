## MST

- MST : Minimum Spanning Tree(최소 신장 트리)

  - 그래프의 간선에 가중치(Weight)를 추가

  - Tree인 이유 : 그래프에서 싸이클을 형성하는 간선을 제거하면 트리 구조와 같아지기 때문

- 프림 알고리즘(Prim's Algorithm)

  - 참고 : [LINK](https://www.weeklyps.com/entry/프림-알고리즘-Prims-algorithm)
  - 과정
    1. 임의의 정점을 루트로 선택
    2. MST에 속한 모든 정점들에서 가장 낮은 가중치를 가진 간선을 선택하여 MST에 추가(싸이클을 형성해서는 안 됨)
    3. 모든 정점을 연결할 때까지 반복
  - 최소 가중치를 선택하는 것이 힘듬

- 크루스칼 알고리즘(Kruskal's Algorithm)

  - 참고 : [LINK](https://www.weeklyps.com/entry/크루스칼-알고리즘-Kruskals-algorithm?category=797114)

  - 과정

    1. 그래프 내의 모든 간선을 가중치의 오름차순으로 정렬

    2. 정렬된 간선을 차례대로 선택하며, 선택한 간선이 연결되어 있지 않다면 MST에 추가하고 간선에 해당하는 두 정점을 연결(싸이클을 형성해서는 안 됨)

  - 싸이클을 형성하는지 확인하는 것이 힘들기 때문에 Union-Find 알고리즘 이용

  - Union-Find 알고리즘

    - 참고 : [LINK](https://gmlwjd9405.github.io/2018/08/31/algorithm-union-find.html)

## PRACTICE

- 최소 스패닝 트리 : [LINK](https://www.acmicpc.net/problem/1197)