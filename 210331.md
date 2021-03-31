# 정렬 알고리즘

## 심화 정렬 알고리즘

### 합병 정렬(Merge Sort)
- 알고리즘
  - 정렬되지 않은 리스트는 두 부분 리스트로 나눈다.
    - 길이가 1인 부분 리스트는 정렬된 부분 리스트로 본다.
  - 두 부분 리스트를 합병하여 정렬된 임시 배열에 저장한다.
  - 임시 배열에 저장된 결과를 원래 배열로 복사한다.

- 공간 복잡도 : O(n) 
- 시간 복잡도
  - 최악의 경우: O(nlogn)
  - 최선의 경우: O(nlogn)
  - 평균적인 경우: O(nlogn)
 

### 퀵 정렬(Quick Sort)
- 속도가 빠름에도 stable정렬 알고리즘이다. 실제 알고리즘을 구현해서 쓸 때 유용함.
- 알고리즘
  - 리스트에서 하나의 Pivot을 선택한다.
    - pivot이 중앙값일때 best case
    - pivot이 가장 작은 값일 때, left는 없고 right만 있을 것이다. worst case는 selection sort와 같다. 반반씩 줄이고 싶었는데 하나씩만 줄어들게 됨. 
    - 따라서 pivot에 따라 최선, 최악, 평균이 결정된다.
    - 일상생활에서는 정렬은 되어 있지만, 조금의 noise가 섞여있다고 가정하여서 pivot으로 보통 중앙값을 선택한다.
  - pivot을 기준으로 좌측에 더 작은 값을, 우측에 더 큰 값을 배치한다.
  - pivot 좌측과 우측에 대해서 재귀적으로 반복한다.

- 공간 복잡도 : O(logn)
- 시간 복잡도
  - 최악의 경우: O(n^2)
  - 최선의 경우: O(nlogn)
  - 평균적인 경우: O(nlogn)


## 하이브리드 정렬 알고리즘

### 팀소트(Timsort)
- Java SE 7, Android, GNU Octave, Chrome V8, Swift, Rust, Python 등에 적용된 정렬 알고리즘
- Insertion Sort와 Merge Sort를 결합하여 만든 알고리즘
  - 작은 영역에서는 Insertion Sort를 수행하고, 이것을 Merge Sort하여 최적화
    - n이 작으면 locality(지역성)이라는 것이 있다. cache에 hit이 많이 발생하는 것. n이 작으면 insertion sort이 유리.

- 공간복잡도: O(n) (Merge sort 때문에 O(n))
- 시간복잡도
  - 최악의 경우: O(nlogn)
  - 최선의 경우: O(n) (이미 sorting이 되어 있는 경우 insertion sort는 O(n)이고 그 경우가 최선이다.)
  - 최악의 경우: O(nlogn)



# 재귀 호출과 반복(Recursive Calls & Iterations)
## 재귀 호출이란?
- 함수가 자기 자신을 호출하는 것을 재귀 호출이라 한다.
- 분할 정복(Divid & Conquer), 점화식 등을 구현하는 데에 많이 사용된다.
- 재귀 구현은 항상 반복(Iteration) 구현으로 변환될 수 있다.

## 점화식
- 재귀식(Recursion relation)이라고도 부르며, 수열의 항 사이의 관계를 나타낸다.
- 일부 점화식은 일반식으로 풀이할 수 있다. 수열을 n에 대한 식으로 표현하는 것을 '풀이한다'고 한다.
- 점화식의 예
  - 피보나치 수열: f(n) = f(n-1) + f(n-2)
  - 팩토리얼: f(n) = n * f(n-1)
  - 등차 수열: f(n) - f(n-1) = d
  - 등비 수열: f(n) / f(n-1) = r

## 재귀 호출
- 재귀 호출을 할 때에는 반드시 '탈출 조건'이 필요하다.
  - 탈출 조건이 없으면, 재귀 호출은 무한히 계속된다.

- 점화식에 의거하여 재귀 호출을 수행한다.
  - 입력 파라미터를 달리하여, 결국 탈출 조건에 도달할 수 있게 한다.

```python
def fibonacci(n):
  if n < 2: # 탈출 조건
    return n
  return fibonacci(n - 1) + fibonacci(n - 2) # 재귀 호출(점화식 구현)
```

## 분할 정복
- 재귀 호출을 이용하여 큰 문제를 작은 문제로 나누어 해결
  - 재귀 호출을 이용해 Top-Down 형식으로 구현
    - Top-Down 재귀 호출은 가장 큰 문제가 호출이 되면 더 작은 문제를 호출하고..
    - Bottom-Up 문제를 다 쪼개놓고 시작.. 
  - trivial 하다.
  - tidious 하다.

- ex. quick sort(O(logN))
```python
def quick_sort(x):
    if len(x) < 2: # 종료 조건
        return x

    left = []
    right = []
    pivot = x[len(x) // 2]

    for el in x:
        if el < pivot:
            left.append(el)
        else:
            right.append(el)
    
    return quick_sort(left) + [pivot] + quick_sort(right) # 분할 정복
```

## 재귀 호출의 한계
- 여러번 재귀 호출이 발생하는 경우, 기하급수적으로 호출 횟수가 증가한다.
  - 함수 호출 스택(Function call stack)의 크기에 제한이 있어, 일정 횟수 이상 호출이 불가하다.
- 실질적인 계산에 필요한 연산보다, 함수 호출에 의한 Overhead가 발생한다.

## 반복 구현
- 종료 조건을 초기값(initial value)으로 하여, Bottom-Up으로 구현한다. 
- Top-Down은 탈출 조건이 있었다. Bottom-Up에서는 초기값 설정을 해준다.
```python
def fibonacci(n): # O(n)
    fn_1, fn = 0, 1  # 초기값 설정
    
    if n == 0:
        return fn_1
    if n == 1:
        return fn
    
    for i in range(2, n + 1):  # 반복문 구현
        fn_1, fn = fn, fn_1 + fn # 2개 보고 더한거 쓰고 반복
    
    return fn
```

## Tail Recursion
- 재귀 함수에서, 재귀 호출이 마지막에 단 한번 수행되는 것을 의미한다.(마지막에 딱 한번만 Recursion이 있어야한다.)
- 재귀 호출이 여러번 발생하는 경우, Tail Recursion 기법으로 재귀 횟수를 줄일 수 있다.
- 코드 위로 다시 돌아올 필요가 없다. 함수 콜 스택을 재활용할 수 있고, 재귀지만 반복문처럼 동작한다.
- 컴파일러에서 Tail Recursion 최적화를 지원하는 경우, 함수 호출 스택을 낭비하지 않을 수 있다.
  - 재귀 호출 이후에는 함수에서 할 일이 남아있지 않으므로, 함수 호출 스택을 재활용한다.
  - 컴파일러에서 최적화를 지원하지 않으면 적용되지 않는다는 한계점이 있다.(Python은 미지원)

```python
def fibonacci(n, a=0, b=1):
    if n == 0:
        return a
    if n == 1:
        return b
    
    return fibonacci(n-1, b, a+b)
```
