# 탐색 알고리즘 (Search Algorithms)
## 탐색 알고리즘이란
- 자료구조에서 원하는 조건에 맞는 자료를 찾는 것을 탐색 알고리즘이라 한다.
- 자료가 정렬되어 있는지 여부에 따라 크게 두 가지 방법으로 나뉜다.

## 선형 탐색 (Linear Search)
![linear search](https://github.com/ai-creatv/algorithm_nklcb1/raw/master/4_Algorithms/4_3_SearchAlgorithms/img/1.png)
- 순차 탐색(Sequential Search)라고도 부르며, 가장 단순한 탐색 알고리즘이다.
- 순서대로 하나씩 비교하여, 시간복잡도는 O(N)이다.

## 이분 탐색 (Binary Search)
![binary search](https://github.com/ai-creatv/algorithm_nklcb1/raw/master/4_Algorithms/4_3_SearchAlgorithms/img/2.png)
- 이진 탐색이라고도 부르며, 정렬된 자료의 탐색에 가장 많이 사용하는 알고리즘이다.
- 탐색 범위를 절반씩 줄여가며, 시간복잡도는 O(logN)이다.
- 이진 탐색 트리의 최선의 경우와 비슷하다.
- 방법1
```python
def solution(array, target_value):
    left, right = 0, len(array) - 1
    while left <= right:
        mid = (left + right) // 2
        if target_value < array[mid]:
            right = mid - 1
        elif target_value > array[mid]:
            left = mid + 1
        else:
            return mid  
    return -1
```
- 방법2(재귀)
```python
def solution(array, target_value, start, end):
    if start >= end:
        return
    mid = (start + end) // 2
    if target_value == array[mid]:
        return mid
    elif target_value < array[mid]:
        return solution(array, target_value, start, mid-1)
    else:
        return solution(array, target_value, mid + 1, end)
```


# 해싱(Hashing)
## 해시 기법이란?
![hash technique](https://github.com/ai-creatv/algorithm_nklcb1/raw/master/4_Algorithms/4_4_Hashing/img/1.png)
- 빠르게 계산할 수 있는 해시 함수(Hash Function)을 이용해 해시값으로 변환하는 기법
  - 일반적으로 입력의 범위보다 해시값의 범위는 감소한다.
- 해시 함수는 동일 입력에 대해서 동일 출력을 보장한다.
  - 다른 입력에 대해서 동일 출력이 발생할 수 있으며, 이것을 해시 충돌(Hash Collision)이라고 한다.
- 해시 함수의 선택에 따라 성능의 차이가 발생한다.
  - 해시 함수를 계산하는 데에 걸리는 시간에 크게 성능이 영향을 받는다.
  - 해시 충돌의 발생 확률에 따라 성능이 크게 영향을 받는다.
- 해시 범위와 충돌은 trade-off관계 => 비둘기집의 원리


## 해시 셋 (Hash Set)
![hash set](https://github.com/ai-creatv/algorithm_nklcb1/raw/master/4_Algorithms/4_4_Hashing/img/2.png)
- 집합을 구현하는 대표적인 자료구조. 파이썬에서는 set 자료형으로 구현되어 있다.
    - 해시 값을 인덱스로 하여 배열(Bucket)에 자료를 저장하는 자료구조이다.
        - 자료를 저장하는 인덱스는 `index = hash_value % bucket_size`로 정한다.
    - 자료의 중복을 혀용하지 않으며, 빠르게 자료를 탐색할 수 있다.
    - 해시 충돌이 가능할 경우 Chaning이나 Open Addressing 기법으로 처리한다.
- O(1)로 탐색하기 위해 그리고 O(N)으로 중복 제거하기 위해 쓰인다. 
