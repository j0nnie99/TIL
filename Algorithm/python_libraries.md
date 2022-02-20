# 실전에서 유용한 표준 라이브러리
## 내장함수

- 기본 입출력 함수부터 정렬 함수까지 기본적인 함수 제공
- sum(), min(), max(), sorted(), sorted() with key
```python
#sum
result = sum([1, 2, 3, 4, 5])
print(result) #15

#min(), max()
min_result = min(7, 3, 5, 2)
max_result = max(7, 3, 5, 2)
print(min_result, max_result) #2 7

#eval(): 수식을 수 형태로 변환
result = eval("(3+5)*7")
print(result) #56

#sorted
result = sorted([9, 1, 8, 5, 4])
reverse_result = sorted([9, 1, 8, 5, 4], reverse=True)
****print(result) #[1, 4, 5, 8, 9]
print(reverse_result) #[9, 8, 5, 4, 1]

#sorted() with key (x[1]인 숫자를 기준으로 sort)
array = [('홍길동', 35), ('이순신', 75), ('아무개', 50)]
result = sorted(array, key = lambda x : x[1], reverse=True)
print(result) #[('이순신', 75), ('아무개', 50), ('홍길동', 35)]
```
---
## itertools

- 반복되는 형태의 데이터를 처리하기 위한 기능 제공
- 코딩 테스트에서 순열과 조합 라이브러리 자주 사용 → 모든 경우의 수가 총 얼마나 될 지를 짐작하여 문제를 풀기 위해 모든 경우의 수를 고려하는 방법이 통할지 안 통할 지를 짐작하는 방식을 사용
- 순열: 서로 다른 n개에서 서로 다른 r개를 선택하여 일렬로 나열하는 것
    - {’A’, ‘B’, ‘C’}에서 세 개를 선택하여 나열하는 경우: ‘ABC’, ‘ACB’, ‘’BAC, ’BCA’,  ‘CAB’, ‘CBA’
    ```python
    from itertools import permutations

    data = ['A', 'B', 'C'] #데이터 준비

    result = list(permutations(data, 3)) #모든 순열 구하기
    print(result)

    #[('A', 'B', 'C'), ('A', 'C', 'B'), ('B', 'A', 'C'), ('B', 'C', A'), ('C', 'A', 'B'), ('C', 'B', 'A')]
    ```
- 조합: 서로 다른 n개에서 순서에 상관 없이 서로 다른 r개를 선택하는 것
    - {’A’, ‘B’, ‘C’}에서 순서를 고려하지 않고 두 개를 뽑는 경우: ‘AB’, ‘AC’, ‘BC’
    ```python
    from itertools import combinations

    data = ['A', 'B', 'C'] #데이터 준비

    result = list(combinations(data, 2)) #2개를 뽑는 모든 조합 구하기
    print(result)

    #[('A', 'B'), ('A', 'C'), ('B', 'C')]
    ```
- **순열의 수**

    $nPr = n *(n-1)*(n-2)*... * (n-r+1)$

- **조합의 수**

    $nCr = n*(n-1)*(n-2)*...*(n-r+1) /r!$

- 중복 순열과 중복 조합
    ```python
    #중복 순열
    from itertools import product

    data = ['A', 'B', 'C']
    result = list(product(data, repeat=2)) #2개를 뽑는 모든 순열 구하기(중복 허용)
    print(result)

    #중복 조합
    from itertools import combinations_with_replacement

    data = ['A', 'B', 'C']
    result = list(combinations_with_replacement(data, 2)) #2개를 뽑는 모든 조합 구하기(중복 허용)
    print(result)
    ```
---
## heapq

- 힙(Heap) 자료구조 제공
- 일반적으로 우선순위 큐 기능을 구현하기 위해 사용
---
## bisect

- 이진 탐색(Binary Search) 기능 제공
---
## collections

- 덱(deque), 카운터(Counter) 등 유용한 자료구조 포함
- Counter
    - 등장 횟수를 세는 기능 제공
    - 리스트와 같이 반복 가능한(iterable) 객체가 주어졌을 때 내부의 원소가 몇 번씩 등장했는지 알려줌
    ```python
    from collections import Counter

    counter = Counter(['red', 'blue', 'red', 'green', 'blue', 'blue'])

    print(counter['blue']) #'blue'가 등장한 횟수 출력 
    print(counter['green']) #'green'이 등장한 횟수 출력
    print(dict(counter)) #사전 자료형으로 반환

    # 3
    # 1
    # {'red': 2, 'blue': 3, 'green': 1}
    ```
---
## math

- 필수적인 수학적 기능 제공
- 팩토리얼, 제곱근, 최대공약수(GCD), 삼각함수 관련 함수, 파이(pi)와 같은 상수
- gcd() 함수: 최대 공약수를 구할 때 사용
    ```python
    import math

    #최소 공배수(LCM)를 구하는 함수
    def lcm(a, b):
        return a * b // math.gcd(a, b)

    a = 21
    b = 14

    print(math.gcd(21, 14)) #최대 공약수(GCD) 계산
    print(lcm(21, 14)) #최소 공배수(LCM) 계산

    # 7
    # 42
    ```
    <br>
---

# 알아두면 편한 메서드

## isalpha()
- 알파벳인지 확인