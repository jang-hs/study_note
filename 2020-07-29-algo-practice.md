**가장 큰 수 정렬 구현**  

**[문제]**   

*0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아낼 것*    

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성  

  

​     

**[제한 조건]** 

- numbers의 길이는 1 이상 100,000 이하
- numbers의 원소는 0 이상 1,000 이하
- 정답이 너무 클 수 있으니 문자열로 바꾸어 return

​      

**[입출력 예] **

| numbers           | return  |
| ----------------- | ------- |
| [6, 10, 2]        | 6210    |
| [3, 30, 34, 5, 9] | 9534330 |

  

**[코드 구현]**

``` python
def solution(numbers):
  numbers = [str(x) for x in numbers] # 문자열로 취급하기 위해서
  numbers.sort(key = lambda x : (x*4)[:4], reverse = True) 
  # 원소 최대길이가 4이므로 4번 반복한 후 크기를 비교하여 큰 수부터 나열(reverse)
  
  if numbers[0] == '0': # 모든 원소가 0인 경우
    answer = '0'
  else :
    anser = ''.join(numbers) #정렬된 숫자를 이어붙인다
    
  return answer
```

  

> 출처: 프로그래머스 코딩 테스트 연습, https://programmers.co.kr/learn/challenges
