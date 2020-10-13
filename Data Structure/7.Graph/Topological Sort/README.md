## Topological Sort

- 위상 정렬(Topological Sort)

  - 어떤 정점이 다른 정점과의 관계 속에서 가지는 위치를 기준으로 정렬을 수행
  - <b>방향성이 있어야하며, 싸이클이 없어야 함</b>

- 정렬 과정

  <img src="https://user-images.githubusercontent.com/49060014/95822252-7d016200-0d66-11eb-857e-9421ff0e8384.png">

  - 진입 간선이 없는 정점을 리스트에 추가하고, 해당 정점과 해당 정점의 진출 간선을 제거
  - 그래프에 더 이상 정점이 남아있지 않을 때까지 반복

- DFS를 이용한 정렬

  - 진입 간선이 없는 정점에 대해 DFS를 실행하고, 최고 깊이까지 탐색하면 해당 정점을 리스트의 헤드로 삽입
  - 위의 연산을 반복

- 참고 : [LINK](https://namnamseo.tistory.com/entry/Topological-Sort-위상정렬)