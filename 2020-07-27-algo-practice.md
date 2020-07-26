**스킬트리 조회 구현**  

**[문제]** 선행 스킬 순서 skill과 유저들이 만든 스킬트리를 담은 배열 skill_trees가 매개변수로 주어질 때, 가능한 스킬트리 개수를 return 하는 solution 함수를 작성  

​     

**[제한 조건]** 

- 스킬은 알파벳 대문자로 표기, 모든 문자열은 알파벳 대문자
- 스킬 순서와 스킬트리는 문자열로 표기
  - 예를 들어, `A → B → D` 라면 ABD로 표기
- 선행 스킬 순서 skill의 길이는 1 이상 26 이하이며, 스킬은 중복되지 않음
- skill_trees는 길이 1 이상 20 이하인 배열
- skill_trees의 원소는 스킬을 나타내는 문자열
  - skill_trees의 원소는 길이가 2 이상 26 이하인 문자열이며, 스킬은 중복되지 않음

​    

**[입출력 예시]**  

| skill   | skill_trees                         | return |
| ------- | ----------------------------------- | ------ |
| `"CBD"` | `["BACDE", "CBADF", "AECB", "BDA"]` | 2      |

#####     

**[입출력 예 설명]**

- BACDE: (불가능) B 스킬을 배우기 전에 C 스킬을 먼저 배워야 함
- CBADF: 가능
- AECB: 가능
- BDA: (불가능) B 스킬을 배우기 전에 C 스킬을 먼저 배워야 함

  

**[코드 구현]**

``` python
skill = "CBD"
skill_trees = ["BACDE", "CBADF", "AECB", "BDA","AQWER","DBC"]

def solution(skill, skill_trees):
    ans = 0 # 초기 ans
    skill_list = list(skill) #skill을 list형태로 저장
    
    for skill_t in skill_trees : # skill_tree안에 있는 각각의 skill_t에 대해서
        h = []

        for skill_item in skill_t: # skill_t의 스킬 하나하나씩 순회
            
            if skill_item in skill_list : # 만약 스킬리스트에 있는 스킬이라면
                h.append(skill_item) # h 에 하나씩 집어넣는다.

        if len(h) == 0 : # h의 길이가 0이라면 (스킬리스트에 있는 스킬이 없는 경우)
            print("skill_t doesn't have any skill's item")
            ans += 1

        elif h == skill_list[:len(h)]: # 순서가 같은지 확인
            print(str(skill_t) +"'s matched skill > "+ str(h))
            ans += 1

        else : pass
    return ans
```

``` python
solution(skill, skill_trees)
```

```
CBADF's matched skill > ['C', 'B', 'D']
AECB's matched skill > ['C', 'B']
skill_t doesn't have any skill's item
  
3
```

> 문제 출처 - [프로그래머스](https://programmers.co.kr/learn/courses/30/lessons/49993)

