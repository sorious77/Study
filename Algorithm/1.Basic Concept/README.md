## Basic Concept

- Algorithm

  > <i>"어떤 문제를 해결하기 위한 절차, 방법, 명령어들의 집합"</i>

  - 프로그래밍에서 알고리즘은 주어진 Input 값을 이용하여 올바른 Output 값을 얻는 계산 과정
  - <b>정확하고 효율적으로 결과를 얻기 위해 사용</b>

- 알고리즘의 조건
  - 입력(Input) : 연산을 수행하기 위해 0개 이상의 입력 값이 존재해야 함
  - 출력(Output) : 모든 입력에 동일한 출력이 나와서는 안 됨
  - 명확성(Clarity) : 연산 수행 과정은 명확해야 하며, 모호하지 않은 명령어로 구성되어야 함
  - 유한성(Finiteness) : 유한 번의 명령어를 수행하여 유한한 시간 내에 종료해야 함
  - 효율성(Efficiency) : 모든 연산 과정은 실행(또는 검증) 가능해야 함

- Time Complexity(시간 복잡도)
  - 문제를 해결하기 위해 걸리는 시간
  
  - <table style="text-align:center">
        <thead>
            <td>Time Complexity</td>
            <td>Description</td>
        </thead>
        <tbody>
            <tr>
                <td><i>O(1)</i></td>
                <td>상수 형태, n의 값과는 상관없이 일정한 양의 연산만 수행</td>
            </tr>
            <tr>
                <td><i>O(logn)</i></td>
                <td>로그 형태</td>
            </tr>
            <tr>
                <td><i>O(n)</i></td>
                <td>선형</td>
            </tr>
            <tr>
                <td><i>O(nlogn)</i></td>
                <td>선형 로그 형태</td>
            </tr>
            <tr>
                <td><i>O(n<sup>2</sup>), O(n<sup>3</sup>), ...</i></td>
                <td>다차 형태</td>
            </tr>
            <tr>
                <td><i>O(2<sup>n</sup>)</i></td>
                <td>지수 형태</td>
            </tr>
            <tr>
                <td><i>O(n!)</i></td>
                <td>팩토리얼 형태</td>
            </tr>
        </tbody>
    </table>
  
    - 아래로 갈수록 시간 복잡도가 커지며, 제한된 시간 내에 문제를 해결하기 위해서는 시간 복잡도를 낮춰야 함

- Data Structure(자료구조)
  - 데이터 사이의 관계를 반영한 저장 구조, 조작 방법
  - <img src="https://blog.yena.io/assets/post-img18/181114-04.png">
- 정렬
  - 오름차순, 내림차순 등의 기준에 맞춰 데이터를 정렬하는 것을 의미