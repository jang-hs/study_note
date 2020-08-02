N으로 표현   
**\[문제 설명\]**

아래와 같이 5와 사칙연산만으로 12를 표현할 수 있다.  
`12 = 5 + 5 + (5 / 5) + (5 / 5)`  
`12 = 55 / 5 + 5 / 5`  
`12 = (55 + 5) / 5`  
5를 사용한 횟수는 각각 6,5,4 이고, 가장 작은 경우는 4  
N과 사칙연산만 사용해서 표현 할 수 있는 방법 중 N 사용횟수의 최솟값을 return 하도록 solution 함수를 작성

**\[제한사항\]**  
N: 1 이상 9 이하  
number: 1 이상 32,000 이하  
수식에는 괄호와 사칙연산만 가능하며 나누기 연산에서 나머지는 무시  
최솟값이 8보다 크면 -1을 return

**\[입출력 예\]**

<table style="border-collapse: collapse; width: 100%;" border="1"><tbody><tr><td style="width: 33.333333333333336%;">N</td><td style="width: 33.333333333333336%;">number</td><td style="width: 33.333333333333336%;">return</td></tr><tr><td style="width: 33.333333333333336%;">5</td><td style="width: 33.333333333333336%;">12</td><td style="width: 33.333333333333336%;">4</td></tr><tr><td style="width: 33.333333333333336%;">2</td><td style="width: 33.333333333333336%;">11</td><td style="width: 33.333333333333336%;">3</td></tr></tbody></table>

**\[입출력 예 설명\]**  
예제 #1: 문제에 나온 예와 같음  
예제 #2: 11 = 22 / 2와 같이 2를 3번만 사용하여 표현가능

```
def solution(N, number):
    # 8개의 set이 만들어지게 초기화
    s = [set() for x in range(8)]
    for i, x in enumerate(s, start = 1) : # 시작이 1부터 하게
        x.add(int(str(N)*i)) # 각각의 set에 해당 숫자를 연달아 적는 것을 i번 반복한 것을 생성

    for i in range(1, len(s)) :
        for j in range(i):
            for op1 in s[j]:
                for op2 in s[i-j-1]:
                    s[i].add(op1 + op2)
                    s[i].add(op1 - op2)
                    s[i].add(op1 * op2)
                    if op2 != 0 :
                        s[i].add(op1//op2)
        if number in s[i]:
            answer = i+1
            break
    else :
        answer = -1 #해당 숫자가 없는 경우


    return answer
```

> 출처: 프로그래머스 코딩 테스트 연습,[https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
