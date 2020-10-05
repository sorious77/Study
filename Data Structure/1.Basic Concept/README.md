## Basic Concept

- Complexity

  - 컴퓨터의 자원(CPU, Memory)은 한정적이지만, 처리해야 하는 데이터의 양은 점점 늘어나고 있기 때문에 데이터를 다룰 효율적인 알고리즘의 선택이 필요함

    <table style="text-align:center">
        <thead>
            <tr>
                <td>Input Data</td>
                <td>Algorithm A(n<sup>2</sup>)</td>
                <td>Algorithm B(2<sup>n</sup>)</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>n = 6</td>
                <td>36 sec</td>
                <td>64 sec</td>
            </tr>
            <tr>
                <td>n = 10</td>
                <td>10,000 sec</td>
                <td>2<sup>100</sup> sec (= 4 * 10<sup>22</sup> year)</td>
            </tr>
        </tbody>
    </table>

    

  - 공간 복잡도(Space Complexity)

    - 알고리즘에 사용되는 저장 공간, 메모리의 크기

      ```c
      int sum(int a, int b, int c){ // 
          return a+b+c;
      }
      // 공간 복잡도 : 0
      
      int arraySum(int a[], int n){
          int result = 0;
          for(int i=0;i<n;i++){
              result += a[i];
          }
          return result;
      }
      // 공간 복잡도 : n+2(result, i, a 배열)
      ```

      

  - 시간 복잡도(Time Complexity)

    - 알고리즘에 사용되는 연산의 횟수(실행시간이 아님)
    - 직접 실행하지 않고 Pseudo Code를 이용해서도 계산이 가능

    - Big-O 표기법 사용

      ```c
      int sum(int a[], int n){
          int result = 0;
          for(int i=0;i<n;i++){
              result += a[i];
          }
          return result;
      }
      // 시간 복잡도 : O(n)
      
      void bubble_sort(int a[], int n){
          for(int i=0;i<n;i++){
              for(int j=0;j<n-(i+1);j++){
                  if(a[j] > a[j+1]){
                      SWAP(a[j], a[j+1]);
                  }
              }
          }
      }
      // 시간 복잡도 : O(n^2)
      ```

- 점근 표기법

|              | Expression | Meaning |   Example    |
| :----------: | :--------: | :-----: | :----------: |
|   O(Big-O)   |  f = O(g)  | f <= g  |  n ⊂ O(n^2)  |
| Ω(Big-Omega) |  f = Ω(g)  | f >= g  | n^3 ⊂ Ω(n^2) |
| Θ(Big-Theta) |  f = Θ(g)  |  f = g  |   Θ(n) = n   |

