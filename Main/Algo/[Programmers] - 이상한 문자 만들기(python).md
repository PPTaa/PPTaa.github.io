# [Programmers] - 이상한 문자 만들기(python)

### 문제 설명

문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

### 제한 사항

- 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
- 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.

### 입출력 예

| s               | return          |
| --------------- | --------------- |
| try hello world | TrY HeLlO WoRlD |



### 내 풀이 

띄어쓰기가 나올때 마다 부터 다시 시작해야 하기 때문에 count 변수를 두고 공백이 나올때 마다 0으로 초기화 시켜줬다.

띄어쓰기가 나온뒤 첫번째문자의 인덱스는 0 이지만 공백이 나오게 되면 count를 0으로 초기화 시키기 때문에 

count를 1로 시작하여 count가 홀수 일때마다 대문자로 변경 시키게 했고, count가 짝수일때 마다 소문자로 변경시켜 answer변수에 등록하도록 설계햇했다.

````python
def solution(s):
    answer = ''
    count = 1
    for i in range(len(s)):
        if s[i] == " ":
            count = 0
        if count%2 == 1:
            answer += s[i].upper()
        else:
            answer += s[i].lower()
        count += 1
    return answer
````

