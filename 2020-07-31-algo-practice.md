**\[문제 설명\]**

모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 스코빌 지수가 가장 낮은 두 개의 음식을 아래와 같이 만듦.

```
섞은 음식의 스코빌 지수 = 가장 맵지 않은 음식의 스코빌 지수 + (두 번째로 맵지 않은 음식의 스코빌 지수 * 2)
```

모든 음식의 스코빌 지수가 K 이상이 될 때까지 반복하여 섞음  
스코빌 지수를 담은 배열 scoville과 원하는 스코빌 지수 K가 주어질 때,

모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 섞어야 하는 최소 횟수를 return 하도록 solution 함수를 작성

**\[제한 사항\]**

-   scoville의 길이는 2 이상 1,000,000 이하
    
-   K는 0 이상 1,000,000,000 이하
    
-   scoville의 원소는 각각 0 이상 1,000,000 이하
    
-   모든 음식의 스코빌 지수를 K 이상으로 만들 수 없는 경우에는 -1을 return
    

**\[입출력 예\]**

<table style="letter-spacing: 0px; border-collapse: collapse; width: 64.3023%; height: 70px;" border="1"><tbody><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px;"><span>scoville</span></td><td style="width: 33.3333%; height: 19px;"><span>K</span></td><td style="width: 33.3333%; height: 19px;"><span>return</span></td></tr><tr style="height: 19px;"><td style="width: 33.3333%; height: 19px;"><span>[1, 2, 3, 9, 10, 12]</span></td><td style="width: 33.3333%; height: 19px;">7</td><td style="width: 33.3333%; height: 19px;">2</td></tr></tbody></table>

**\[입출력 예 설명\]**

1.  스코빌 지수가 1인 음식과 2인 음식을 섞으면,
    
    새로운 음식의 스코빌 지수 = 1 + (2 \* 2) = 5
    
    가진 음식의 스코빌 지수 = \[5, 3, 9, 10, 12\]
    
2.  스코빌 지수가 3인 음식과 5인 음식을 섞으면,
    
    새로운 음식의 스코빌 지수 = 3 + (5 \* 2) = 13
    
    가진 음식의 스코빌 지수 = \[13, 9, 10, 12\]
    

모든 음식의 스코빌 지수가 7 이상이, 이때 섞은 횟수는 2회

**\[코드 구현\]**

```python
import heapq
def solution(scoville, K):
    answer = 0 # 몇번 섞었는지 할당될 값
    heapq.heapify(scoville) # min heap형태로 만들기

    while True :
    # 중단 조건 (break)
    # 1) 모든 음식의 스코빌 지수가 K이상
    # 2) 음식이 하나도 안 남았는데 K에 이르지 못한 경우

        min1 = heapq.heappop(scoville) # 최소값을 min1에 할당
        if min1 >= K: # 최소값이 K보다 크면 중단
            break
        elif len(scoville) == 0: # 남은 음식이 하나도 없으면
            answer = -1 # k에 -1 할당하고 중단
            break
        min2 = heapq.heappop(scoville) # 두번째로 작은 값 min2에 할당
        new_scov = min1 + 2*min2 # 섞은 음식의 스코빌지수
        heapq.heappush(scoville, new_scov) #섞은 음식의 스코빌 지수를 scoville에 push
        answer += 1 # 섞은 횟수 1 증가

    return answer
```

> 출처: 프로그래머스 코딩 테스트 연습, [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)