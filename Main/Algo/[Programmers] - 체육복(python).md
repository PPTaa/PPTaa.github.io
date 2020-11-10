# [Programmers] - 체육복(python)

### 문제 설명

점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다. 예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.

### 제한사항

- 전체 학생의 수는 2명 이상 30명 이하입니다.
- 체육복을 도난당한 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌의 체육복을 가져온 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌 체육복이 있는 학생만 다른 학생에게 체육복을 빌려줄 수 있습니다.
- 여벌 체육복을 가져온 학생이 체육복을 도난당했을 수 있습니다. 이때 이 학생은 체육복을 하나만 도난당했다고 가정하며, 남은 체육복이 하나이기에 다른 학생에게는 체육복을 빌려줄 수 없습니다.

### 입출력 예

| n    | lost   | reserve   | return |
| ---- | ------ | --------- | ------ |
| 5    | [2, 4] | [1, 3, 5] | 5      |
| 5    | [2, 4] | [3]       | 4      |
| 3    | [3]    | [1]       | 2      |



### 첫 풀이

학생들이 체육복이 모두 있다고 가정을 한 후에 lost의 값들을 하나하나 꺼내와서 lost-1번째의 학생들의 체육복 여부를 0으로 변환해준다.

그 lost의 값, +1, -1 값이 reserve에 있다면 학생들의 체육복여부를 다시 1로 변환해준다.

학생들의 체육복 여부가 담겨있는 리스트를 모두 더해주면 값이 나올것이라 생각했다.

````python
def solution(n, lost, reserve):
    student = [1 for i in range(n)]
    for i in lost:
        student[i-1] = 0
        if i in reserve:
            reserve.remove(i)
            student[i-1] = 1
        elif i-1 in reserve:
            reserve.remove(i-1)
            student[i-1] = 1
        elif i+1 in reserve:
            reserve.remove(i+1)
            student[i-1] = 1
    result = sum(student)
    print(student)
    return result
````

테스트케이스는 모두 통과 했지만 코드 채점에서 2~3 문제씩 실패가 나온다......

### 두번째 풀이

이유를 모르겠어서 마구잡이로 테스트케이스를 넣다가 

n = 6 , lost = [1,2,3] , reserve = [2,3,4] 를 넣으니 실패를 해서 살펴보았더니...

이경우에는 2,3 이 자신의 체육복을 잃어버려서 여벌의 자신의 것을 입고, 1은 빌릴사람이 없기 때문에 5명만 체육수업을 들을 수 있었지만

위의 코드는 1=2, 2=3, 3=4 로 빌려줘 버리니 6명이 모두 들을수 있다고 한것.

lost와 reserve에 같은 값이 있다면 두개의 리스트 에서 지워주기로 했다.

````python
def solution(n, lost, reserve):
    student = [1 for i in range(n)]
    for i in reserve:
        if i in lost:
            lost.remove(i)
            reserve.remove(i)
    for i in lost:
        student[i-1] = 0
        if i in reserve:
            reserve.remove(i)
            student[i-1] = 1
        elif i-1 in reserve:
            reserve.remove(i-1)
            student[i-1] = 1
        elif i+1 in reserve:
            reserve.remove(i+1)
            student[i-1] = 1
    result = sum(student)
    print(student)
    return result
````

 코드 채점을 통과했다~~