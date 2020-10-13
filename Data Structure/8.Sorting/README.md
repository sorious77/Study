## Sorting

- 버블 정렬(Bubble Sort)
  - 인접한 두 개의 원소를 비교하여 자리를 교환하는 방식
  - 정렬이 이루어지는 과정이 거품이 올라오는 것과 비슷해 보여서 지어진 이름
  - 첫 번째 원소부터 마지막 원소까지 반복하며, 한 단계가 끝나면 가장 큰(작은) 원소가 마지막 자리에 위치하게 됨
  - 구현이 간단하며, 데이터를 하나씩 비교하기 때문에 정밀한 비교가 가능하지만 비교 횟수가 많아져 성능은 좋지 않음
- 삽입 정렬(Insertion Sort)
  - 이미 정렬이 되어 있는 데이터의 집합에서 위치를 찾아 새로운 원소를 <b>삽입</b>하는 방식
  - 정렬이 되어 있는 N개의 데이터의 가장 뒤 원소부터 비교해가며 위치를 찾음
  - 버블 정렬의 비교 횟수가 많다는 단점을 보완하기 위해 만들어짐
- 합병 정렬(Merge Sort)
  - Divide and Conquer(분할 정복)을 이용한 정렬 방식
  - 더 이상 쪼개지지 않을 때까지 분할을 반복한 후, <b>합병</b>을 수행
  - 각 부분 집합의 가장 첫 번째 원소부터 비교를 시작하여 병합함
- 선택 정렬(Selection Sort)
  - 전체 원소에서 해당 인덱스에 위치해야 하는 원소를 <b>선택</b>하여 자리를 교환하는 방식
  - 가장 작은 값을 첫 번째, 두번째로 작은 값을 두 번째, ... 반복
  - 정렬을 위한 비교 횟수는 많으나, 교환 횟수는 비교적 적음
  - 역순으로 정렬을 할 때 가장 적합함
- 퀵 정렬(Quick Sort)
  - Divide and Conquer(분할 정복)을 이용한 정렬 방식
  - Merge Sort는 동등한 크기로 분할을 하는 것에 비해, Quick Sort는 임의의 크기로 분할함
  - 임의의 원소(Pivot)을 기준으로 작은 값을 왼쪽으로, 큰 값을 오른쪽으로 옮긴 뒤, 각각을 다시 정렬하는 방식
  - 안정성이 없으며 가장 많이 사용됨
- 힙 정렬(Heap Sort)
  - 주어진 데이터를 이용하여 최대(최소)힙을 만든 후, Delete 과정을 거쳐 정렬하는 방식
  - 내림차순은 Max Heap, 오름차순은 Min Heap을 이용
- 기수 정렬(Radix Sort)
  - 자리수에 따라 정렬을 하는 방식
  - 1의 자리, 10의 자리, 100의 자리, ... 의 순으로, 각 자리의 값이 같은 원소끼리 부분집합을 만들어 정렬하는 방식



## Time Complexity

<table style="text-align:center">
    <thead>
        <th>Name</th>
        <th>Best</th>
        <th>Average</th>
        <th>Worst</th>
        <th>Run-time(sec)</th>
    </thead>
    <tbody>
        <tr>
            <td>Bubble Sort</td>
            <td>n<sup>2</sup></td>
            <td>n<sup>2</sup></td>
            <td>n<sup>2</sup></td>
            <td>22.894</td>
        </tr>
        <tr>
            <td>Selection Sort</td>
            <td>n<sup>2</sup></td>
            <td>n<sup>2</sup></td>
            <td>n<sup>2</sup></td>
            <td>10.842</td>
        </tr>
        <tr>
            <td>Insertion Sort</td>
            <td>n</td>
            <td>n<sup>2</sup></td>
            <td>n<sup>2</sup></td>
            <td>7.438</td>
        </tr>
        <tr>
            <td>Heap Sort</td>
            <td>nlog<sub>2</sub>n</td>
            <td>nlog<sub>2</sub>n</td>
            <td>nlog<sub>2</sub>n</td>
            <td>0.034</td>
        </tr>
        <tr>
            <td>Merge Sort</td>
            <td>nlog<sub>2</sub>n</td>
            <td>nlog<sub>2</sub>n</td>
            <td>nlog<sub>2</sub>n</td>
            <td>0.026</td>
        </tr>
        <tr>
            <td>Quick Sort</td>
            <td>nlog<sub>2</sub>n</td>
            <td>nlog<sub>2</sub>n</td>
            <td>n<sup>2</sup></td>
            <td>0.014</td>
        </tr>
        <tr>
            <td>Radix Sort</td>
            <td>d(자리수) * n</td>
            <td>d * n</td>
            <td>d * n</td>
            <td> </td>
        </tr>
    </tbody>
</table>

## Characteristic

