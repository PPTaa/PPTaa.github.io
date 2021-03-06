# [백준] 1927번 - **최소 힙** (python)

## 문제

널리 잘 알려진 자료구조 중 최소 힙이라는 것이 있다. 최소 힙을 이용하여 다음과 같은 연산을 지원하는 프로그램을 작성하시오.

1. 배열에 자연수 x를 넣는다.
2. 배열에서 가장 작은 값을 출력하고, 그 값을 배열에서 제거한다.

프로그램은 처음에 비어있는 배열에서 시작하게 된다.

source : [문제링크 백준 - 1927](https://www.acmicpc.net/problem/1927)

## 내 코드

0 이 입력되었을 때 작은 값 부터 차례대로 출력되야 하기 때문에 heap 구조를 사용해야함

heap 구조를 구현시켜주는 파이썬 라이브러리 heapq를 사용하기로함 

```python
import heapq

n = int(input())
heap = []
result = []

for _ in range(n):
  data = int(input())
  # 입력값이 0 이라면
  if data == 0:
    # heap에 데이터가 있는지 확인
    if heap:
      # 있다면 heap의 데이터를 뽑아내서 result에 append
      result.append(heapq.heappop(heap))
    else:
      # 없다면 result에 0을 append
      result.append(0)
  # 입력값이 0 이 아닌 정수라면 heap에 데이터를 추가
  else:
    heapq.heappush(heap, data)
    
# 백준의 양식에 맞게 출력  
for data in result:
  print(data)
```

기본적인 힙의 구조를 숙지하면 간단하게 풀이할 수 있다~!
