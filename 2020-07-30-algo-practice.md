## 큰 수 만들기(탐욕법)

**\[문제\]**

_어떤 숫자에서 k개의 수를 제거했을 때 얻을 수 있는 가장 큰 숫자를 구함_

문자열 형식으로 숫자 number와 제거할 수의 개수 k가 solution 함수의 매개변수로 주어진다.

number에서 k 개의 수를 제거했을 때 만들 수 있는 수 중 가장 큰 숫자를 문자열 형태로 return

  

**\[제한 조건\]**

-   number는 1자리 이상, 1,000,000자리 이하인 숫자
    
-   k는 1 이상 `number의 자릿수` 미만인 자연수
    

  

**\[입출력 예\]**

<table style="border-collapse: collapse; width: 100%; height: 76px;" border="1"><tbody><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">number</span></p></td><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">k</span></p></td><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">return</span></p></td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">"1924"</span></p></td><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16">2</p></td><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">"94"</span></p></td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">"1231234"</span></p></td><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16">3</p></td><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">"3234"</span></p></td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16"><span style="color: #333333;">"4177252841"</span></p></td><td style="width: 33.3333%; height: 19px;"><p data-ke-size="size16">4</p></td><td style="width: 33.3333%; height: 19px;">&nbsp;</td></tr></tbody></table>

**\[코드 구현\]**

```python
def solution(number, k):
    collected = [] #하나씩 숫자를 모으는데 이용
    for i, num in enumerate(number) : #index와 숫자를 담는다.
        while len(collected) > 0 and collected[-1] < num and k > 0:
        # collected에 원소가 하나 이상 있음-마지막 원소를 고르기 위한 선행 조건으로 씀
        # collected의 마지막 원소가 지금 담으려는 num보다 작고, 그리고 k(빼낼 갯수)가 0보다 크면
            collected.pop() # collected에서 마지막 원소를 pop
            k -=1 # 빼내야할 갯수를 1 감소
        if k == 0:
            collected += list(number[i:]) # 빼낼 갯수를 모두 다 빼냈다면 남은 모든 숫자를 이어 붙인다.
            break
        collected.append(num) # 현재 num을 append

    collected = collected[:-k] if k > 0 else collected # 빼낼 갯수만큼 다 못뺀경우는 앞에부터 -k번째까지 자름
    answer = ''.join(collected) # 문자열로 이어붙임

    return answer
```



> 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)