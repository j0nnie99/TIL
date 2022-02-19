### 지수 표현 방식
- e나 E를 이용하여 가능
- 임의의 큰 숫자를 표현하기 위해 자주 사용
- 최단 경로 알고리즘에서 도달할 수 없는 노드에 대해 최단거리를 무한(INF)로 설정
- 이때 가능한 기댓값이 10억 미만이라면 무한(INF)의 값으로 1e9 사용
- 기본적으로 실수형으로 출력
```python
a = 1e9
print(a) #1,000,000,000 

b = 3954e-3
print(b) #3.954
```
---

### 실수형 오차로 인한 결과값 오류 해결 방법: round()
```python
round(123.456, 2) #123.46
```
---
### 나누기 연산자 주의사항
1. 파이썬 나누기 연산자(/)는 나눠진 결과를 **실수형**으로 반환
2. 나머지 연산(%) 활용 많음 ex) 홀수 짝수
3. 몫을 얻기 위해선 몫 연산자(//) 사용
4. 거듭제곱 연산자(**) → a**0.5 (제곱근 연산 가능)
---
### 리스트 초기화
- [] (대괄호)에 원소를 넣어 초기화,  , (쉼표)로 원소 구분
- 비어있는 리스트 선언
    
    list() or []
    ```python
    a = [1, 2, 3, 4, 5, 6, 7, 8, 9] #[1, 2, 3, 4, 5, 6, 7, 8, 9]

    print(a[3]) #4

    n = 10
    a = [0] * n #[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    
    ```

---
### 리스트 컴프리헨션

- 리스트를 초기화하는 방법 중 하나
- 대괄호 안에 조건문과 반복문을 사용하여 초기화 가능
- 2차원 리스트를 초기화할 때 (N x M) 효과적
```python
#0부터 9까지의 수를 초기화
array = [i for i in range(10)]
print(array) #[0,  1, 2, 3, 4, 5, 6, 7, 8, 9]

#0부터 19까지 중 홀수만 포함하는 리스트
array = [i for i in range(20) if i % 2 == 1]

#1부터 9까지의 수들의 제곱값을 포함하는 리스트
array = [i * i for i in range(1, 10)]

#2차원 리스트 초기화(Good Case)
array = [[0] * m for _ in range(n)]

#2차원 리스트 초기화(Bad Case)
array = [[0] * m] * n #전체 리스트 안에 포함된 각 리스트가 모두 같은 객체로 인식됨
```
---
### 언더바( _ )

- 반복을 수행하되 반복을 위한 변수의 값을 무시하고자 할 때 사용
```python
#code 1
summary = 0
for i in range(1, 10):
	summary += i
print(summary)

#code 2
for _ in range(5): #내부에서 변수 사용 없이 반복문만 수행하고자 할 때
	print("Hello World")
```
---
### 리스트 관련 기타 메서드
| 함수명 | 사용법 | 설명 | 시간 복잡도 |
| --- | --- | --- | --- |
| append() | 변수명.append() | 리스트에 원소를 하나 삽입할 때 사용 | O(1) |
| sort() | 변수명.sort() | 오름차순 정렬 | O(NlogN) |
|  | 변수명.sort(reverse = True) | 내림차순 정렬 | O(NlogN) |
| reverse() | 변수명.reverse() | 리스트의 원소 순서를 모두 뒤집음 | O(N) |
| insert() | insert(삽입할 위치 인덱스, 삽입할 값) | 특정 인덱스 위치에 원소 삽입 시 사용 | O(N) |
| count() | 변수명.count(특정 값) | 특정 값을 가지는 데이터의 개수를 구할 때 사용 | O(N) |
| remove() | 변수명.remove(특정 값) | 특정 값을 갖는 원소 제거. 여러 개일 경우 하나만 제거 | O(N) |


- 특정 값을 가지는 원소를 모두 제거하기

    ```python
    a = [1, 2, 3, 4, 5, 5, 5]
    remove_set = { 3, 5 } #집합 자료형

    #remove_list에 포함되지 않는 값만을 저장
    result = [i for i in a if i not in remove_set]
    print(result) #[1, 2, 4]
    ```
---
### 튜플을 사용하면 좋은 경우

1. 서로 다른 성질의 데이터를 묶어서 관리할 대
    - 최단경로 알고리즘에서는 (비용, 노드 번호)의 형태로 튜플 자료형 자주 사용
2. 데이터 나열을 **해싱(Hashing)의 키 값**으로 사용해야 할 때
    - 튜플은 변경이 불가능하여 리스트와 달리 키 값으로 사용 가능
3. 리스트보다 메모리를 효율적으로 사용해야 할 때
---
### 사전 자료형 관련 메서드
1. keys()
    
    : 키 데이터만 뽑아서 리스트로 이용할 때 사용
    
2. values()
    
    : 값 데이터만 뽑아서 리스트로 이용할 때 사용
    ```python
    #각 키에 따른 값을 하나씩 출력
    data = { '사과':'apple', '바나나':'banana'}
    key_list = data.keys #data는 사전 생성됨
    for key in key_list:
        print(data[key]) #apple banana
    ```
---
### 집합 자료형 관련 메서드

1. set()
    
    : 리스트 혹은 문자열을 이용하여 초기화할 때 사용
    ```python
    data = set([1, 2, 3]) 
    print(data) # {1, 2, 3}
    ```
2. add()
    
    : 새로운 원소 추가
    
3. update()
    
    : 새로운 원소 여러 개 추가
    
4. remove()
    
    : 특정한 값을 갖는 원소 삭제
---
### 자주 사용되는 표준 입력 방법

1. input()
    
    : 한 줄의 문자열을 입력받는 함수
    
2. map()
    
    : 리스트의 모든 원소에 각각 특정한 함수를 적용할 때 사용
```python
#공백을 기준으로 구분된 데이터를 입력받기
list(map(int, input().split()))

#공백을 기준으로 구분된 데이터의 개수가 많지 않다면 단순하게 사용 가능
a, b, c = map(int, input().split())
```
---
### 빠르게 입력을 받아야 할 때

- sys.stdin.readline() 메서드 이용
    - 단 입력 후 엔터가 줄 바꿈 기호로 입력되므로 rstrip() 메서드를 함께 사용
```python
import sys

data = sys.stdin.readline().rstrip()
print(data)
```
---
### f-string
- 문자열 앞에 접두사 ‘f’를 붙여 사용
- 중괄호 안에 변수명을 기입하여 간단히 문자열과 정수를 함께 넣을 수 있음
```python
answer = 7
print(f"정답은{answer}입니다.")
```
---
### pass 키워드

- 아무 것도 처리하고 싶지 않을 때 사용

    ex) 디버깅 과정에서 일단 조건문 형태만 만들고 조건문 처리하는 부분 비워놓고 싶은 경우
```python
score = 85

if score >= 80:
	pass #나중에 작성할 소스코드
else:
	print("성적이 80점 미만입니다.")

print("프로그램을 종료합니다.")

#프로그램을 종료합니다.
```
---
### global 키워드

- 함수 바깥에 선언된 변수를 참조할 때 사용
```python
a = 0

def func():
	global a
	a += 1

for i in range(10):
	func()

print(a) #10
```
---
### 람다 표현식

- 특정 기능을 수행하는 함수를 한 줄에 작성 가능
```python
def add(a,b):
	return a + b

#일반적인 add() 메서드 사용
print(add(3,7))

#람다 표현식으로 구현한 add() 메서드
print((lambda a, b: a + b)(3, 7))

#내장 함수에서 자주 사용되는 람다 함수
array = [('홍길동', 50), ('이순신', 32), ('아무개', 74)]

def my_key(x):
	return x[1]

print(sorted(array, key = my_key))
print(sorted(array, key = lambda x: x[1]))

#여러 개의 리스트에 적용
list1 = [1, 2, 3, 4, 5]
list2 = [6, 7, 8, 9, 10]
result = map(lambda a, b: a + b, list1, list2)
print(list(result)) #[7, 9, 11, 13, 15]
```

