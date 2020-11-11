# [Programmers] - 완주하지 못한 선수(python) 

### 문제 설명

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

### 제한사항

- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

### 입출력 예

| participant                             | completion                       | return |
| --------------------------------------- | -------------------------------- | ------ |
| [leo, kiki, eden]                       | [eden, kiki]                     | leo    |
| [marina, josipa, nikola, vinko, filipa] | [josipa, filipa, marina, nikola] | vinko  |
| [mislav, stanko, mislav, ana]           | [stanko, ana, mislav]            | mislav |

[출처](http://hsin.hr/coci/archive/2014_2015/contest2_tasks.pdf): 프로그래머스

### 첫 풀이 

그냥 간단하게 for 문을 돌려서 풀면 되는 줄 알고 간단하게 participant 리스트에서 completion의 요소들을 모두 빼주기로 했다.

````python
def solution(participant, completion):
    for i in completion:
        participant.remove(i)   
    return participant[0]
````

하지만... 효율성테스트에서 모두다 시간초과를 하고 말았다... 

아마도 시간복잡도를 줄여야 할것 같다. 

현재는 O(n^2) (for문 O(N) * remove()함수 O(N))



### 두번째 풀이

찾아보니 collections 라이브러리에 Counter라는 함수가 있었는데 Counter Dictionary를 만들어주는 함수였다.

리스트를 Counter함수에 넣게되면 요소를 키값으로 사용하며 중복된 키값들이 여러개 있다면 중복되는 개수를 밸류값으로 보여준다.

````python
import collections

a = ["a","a","b","c","d","d","d"]
print(collections.Counter(a))
## 결과값 : Counter({'d': 3, 'a': 2, 'b': 1, 'c': 1})
````

심지어 Dictionary형태로 리턴이 되는데 이 값들은 같은 키값을 비교해서 연산이 가능하다.

```python
import collections

a1 = ["a","a","b","c","d","d","d"]
a2 = ["a","a","b","b","c","d","d","d","d"]
a1 = collections.Counter(a1)
a2 = collections.Counter(a2)
print(a2 - a1)
## 결과값 : Counter({'b': 1, 'd': 1})
```

이 라이브러리를 활용하여 문제를 풀이하면 간단하게 풀이 할 수 있다.



````python
from collections import Counter

def solution(participant, completion):
    answer = (Counter(participant) - Counter(completion))
    return list(answer)[0]
````

collections의 Counter함수는 시간복잡도가 O(N)으로 알려져 있고, 뺄셈 연산은 시간복잡도가 나오지않아 잘모르겠지만 최대 O(N) 이라도 두가지 연산이 따로 실행되기 때문에 전체적인 함수의 시간복잡도는 O(N) 이 되어 기존의 코드에 비해 시간복잡도가 낮아 해결이 가능했다.