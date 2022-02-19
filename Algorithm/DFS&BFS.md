# 그래프 탐색 알고리즘: DFS/BFS

- 탐색(Search): 많은 양의 데이터 중 **필요한** 데이터를 찾는 과정


<br> 

# 스택 자료구조

- 먼저 들어온 데이터가 나중에 나가는 형식(후입선출, LIFO)의 자료구조
- 입구와 출구가 동일한 형태로 스택을 시각화 가능 (ex. 박스 쌓기)
- 파이썬에서 스택 자료구조를 이용하려면 리스트 자료형을 이용하면 됨
    - 가장 오른쪽에 원소를 삽입하는 append()와 가장 오른쪽에서 원소를 꺼내는 pop()을 지원
    - append()와 pop()의 시간복잡도: O(1) → 스택 자료구조로 적합
    
    
## 스택 구현 예제

```python
stack = []

stack.append(5)
stack.append(2)
stack.append(3)
stack.append(7)
stack.pop()
stack.append(1)
stack.append(4)
stack.pop()

print(stack[::-1]) #최상단 원소부터 출력 -> [1, 3, 2, 5]
print(stack) #최하단 원소부터 출력 -> [5, 2, 3, 1]
```

<br>

# 큐 자료구조

- 먼저 들어온 데이터가 먼저나가는 형식(선입선출, FIFO)의 자료구조
- 입구와 출구가 모두 뚫려있는 터널같은 형태로 큐를 시각화 가능
- 파이썬에서 사용하기 위해 deque 라이브러리 사용
    - 리스트 자료형을 이용할 수도 있지만 시간 복잡도가 높아서 비효율적


## 큐 구현 예제

```python
from collections import deque

# 큐 구현을 위해 deque 라이브러리 사용
queue = deque()

queue.append(5) # 리스트의 append()와 동일: O(1)
queue.append(2)
queue.append(3)
queue.append(7)
queue.popleft() # 시간복잡도: O(1)
queue.append(1)
queue.append(4)
queue.popleft()

print(queue) # 먼저 들어온 순서대로 출력 -> deque([3, 7, 1, 4])
queue.reverse() # 역순으로 바꾸기
print(queue) # 나중에 들어온 원소부터 출력 -> deque([4, 1, 7, 3])
```

<br>

# 재귀함수

- 자기 자신을 다시 호출하는 함수
- 모든 재귀 함수는 반복문을 이용하여 동일한 기능 구현 가능
- 컴퓨터가 함수를 연속적으로 호출 →컴퓨터 메모리 내부의 스택 프레임에 쌓임 →스택 사용해야 할 때 구현상 스택 라이브러리 대신 재귀 함수 이용하는 경우가 많음
- 단순한 재귀 함수 예제
    - “재귀함수를 호출합니다” 문자열을 무한히 출력
    - 어느 정도 출력하다가 최대 재귀 깊이 초과 메시지가 출력됨
    
    ```python
    def recursive_function():
    	print("재귀함수를 호출합니다")
    	recursive_function()
    
    recursive_function()
    # RecursionError: maximum recursion depth exceeded while calling a Python object
    ```
    
- 재귀 함수를 문제 풀이에서 사용할 때는 반드시 재귀 함수의 종료 조건을 명시할 것
- 종료 조건을 명시하지 않으면 함수가 무한히 호출
    - 종료 조건을 포함한 재귀함수 예제
    
    ```python
    def recursive_function(i):
    	# 100번째 호출을 했을 때 종료되도록 종료 조건 명시
    	if i == 100:
    		return # return -> 아무것도 반환하지 않고 함수를 종료한다 
    	print(i, '번째 재귀함수에서', i+1, '번째 재귀함수를 호출합니다.')
    	recursive_function(i+1)
    	print(i, '번째 재귀함수를 종료합니다.')
    
    recursive_function(1)
    
    ```
    

## 팩토리얼 구현 예제

- $n! = 1*2*3*...*(n-1)*n$
- 0! = 1, 1! = 1

```python
# 반복적으로 구현한 n!
def factorial_iterative(n):
	result = 1
	# 1부터 n까지의 수를 차례대로 곱하기
	for i in range(1, n + 1):
		result *= i
	return result

# 재귀적으로 구현한 n!
def factorial_recursive(n):
	if n <= 1: # n이 1 이하인 경우 1을 반환
		return 1
	# n! = n * (n - 1)!를 그대로 코드로 작성하기
	return n * factorial_recursive(n - 1)

# 각각의 방식으로 구현한 n! 출력(n = 5)
print("반복적으로 구현: ", factorial_iterative(5))  # 반복적으로 구현: 120
print("재귀적으로 구현: ", factorial_recursive(5))  # 재귀적으로 구현: 120
```

## 최대공약수 계산(유클리드 호제법) 예제

- 유클리드 호제법: 두 개의 자연수에 대한 최대공약수를 구하는 대표적인 알고리즘
    - 두 자연수 A, B에 대하여 (A > B) A를 B로 나눈 나머지를 R이라고 한다
    - 이때 A와 B의 최대공약수는 B와 R의 최대공약수와 같다
- 유클리드 호제법의 아이디어를 그대로 재귀함수로 작성 가능
    - 예시: GCD(192, 162)
        
        나누어 떨어지면 종료
        
        | 단계 | A | B |
        | --- | --- | --- |
        | 1 | 192 | 162 |
        | 2 | 162 | 30 |
        | 3 | 30 | 12 |
        | 4 | 12 | 6 |
    
    ```python
    def gcd(a, b):
    	if a % b == 0:
    		return b
    	else:
    		return gcd(b, a % b)
    
    print(gcd(192, 162)) # gcd() 사용시 꼭 a, b(a>b) 순서 맞추지 않아도 가능 -> 6
    ```