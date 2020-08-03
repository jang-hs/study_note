여행경로(깊이/너비 우선 탐색)   
**\[문제 설명\]**  

주어진 항공권을 모두 이용하여 여행경로 짜기(항상 ICN 공항에서 출발)    

항공권 정보가 담긴 2차원 배열 tickets가 매개변수로 주어질 때, 방문하는 공항 경로를 배열에 담아 return 하도록 solution 함수를 작성  

**\[제한사항\]**  

- 모든 공항은 알파벳 대문자 3글자

- 주어진 공항 수는 3개 이상 10,000개 이하

- tickets의 각 행 [a, b]는 a 공항에서 b 공항으로 가는 항공권

- 주어진 항공권은 모두 사용

- 만일 가능한 경로가 2개 이상일 경우 알파벳 순서가 앞서는 경로를 return

- 모든 도시를 방문할 수 없는 경우는 주어지지 않는다

**\[입출력 예\]**

<table style="border-collapse: collapse; width: 100%;" border="1"><tbody><tr><td style="width: 33.333333333333336%;">tickets</td><td style="width: 33.333333333333336%;">return</td></tr><tr><td style="width: 33.333333333333336%;">[[ICN, JFK], [HND, IAD], [JFK, HND]]</td><td style="width: 33.333333333333336%;">[ICN, JFK, HND, IAD]</td></tr><tr><td style="width: 33.333333333333336%;">[[ICN, SFO], [ICN, ATL], [SFO, ATL], [ATL, ICN], [ATL,SFO]]</td><td style="width: 33.333333333333336%;">[ICN, ATL, ICN, SFO, ATL, SFO]</td></tr></tbody></table>

**\[입출력 예 설명\]**    

예제 #1  [ICN, JFK, HND, IAD] 순으로 방문    

예제 #2  [ICN, SFO, ATL, ICN, ATL, SFO] 순으로 방문할 수도 있지만 [ICN, ATL, ICN, SFO, ATL, SFO] 가 알파벳 순으로 앞선다.  

  

**[코드구현]**

```python
def solution(tickets):
    routes = {} #경로를 빈 사전으로 초기화
    for t in tickets: # tickets의 인자들을 꺼내서 사전을 채운다
        routes[t[0]] = routes.get(t[0], []) + [t[1]] # 출발공항 + 도착공항(리스트 병합)
    for r in routes : # 알파벳 역순으로 정렬
        routes[r].sort(reverse = True)
    
    stack = ["ICN"] #무조건 인천에서 시작하는 조건
    path = [] # list로 사용
    
    while len(stack) > 0 : # 스택에 있는 것이 다 없어질 때까지
        top = stack[-1] # 스택에 있는 제일 위 원소
        if top not in routes or len(routes[top]) ==0 :
        # top이 routes에 들어있지 않으면 or 다 써서 없는 경우
            path.append(stack.pop())
        else :
            stack.append(routes[top][-1]) #stack에 마지막원소(알파벳 역순)를 추가
            routes[top] = routes[top][:-1] #쓴 티켓을 경로에서 제거
            
    return path[::-1] # 방문하는 순서의 역순으로 있으니까 다시 바꿀 것
    
```

> 출처: 프로그래머스 코딩 테스트 연습,[https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
