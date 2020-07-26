**다익스트라 알고리즘(Dijkstra algorithm) - 최단경로 탐색**

  

>  그래프 자료 구조에서 하나의 정점(vertex)에서 다른 정점까지의 최단 경로를 찾는 알고리즘

​    

1) 시작 정점에서 인점한 정점들 중 가장 가중치가 작은 정점 찾기  

2) 해당 정점에서 인접 정점까지 연결되는 간선의 가중치 조사 > 최단 경로를 수정  

3) 그래프 모든 정점에서 1, 2 반복  

4) 시작 정점에서 목표 정점까지 최단 경로 찾기  

  

```python
import heapq
```


```python
mygraph = {
    'A': {'B': 5, 'C': 2, 'D': 3},
    'B': {},
    'C': {'B': 7, 'D': 3},
    'D': {'E': 4, 'F': 5},
    'E': {'F': 2},
    'F': {'A': 5}
}
```


```python
start = 'C'

# 시작 정점에서 각 정점까지의 거리를 저장할 딕셔너리 생성 / 무한대로 초기화
distances = { vertex : float('inf') for vertex in mygraph}
distances[start] = 0
```


```python
# 모든 정점이 저장될 큐 생성
queue = []
for vertex, distance in distances.items():
    # 파이썬의 heapq 모듈을 사용하여 우선순위 큐로 저장
    heapq.heappush(queue, [vertex, distance])
```


```python
# 큐에 저장된 모든 정점에 대해서
while queue :
    
    # 정점을 하나씩 꺼내서 인접한 정점들의 가중치를 확인 -> 업데이트
    current_vertex, current_distance = heapq.heappop(queue)
    for adjacent, weight in mygraph[current_vertex].items() :
        distance = distances[current_vertex] + weight
        
        # 만약 시작 정점에서 인접 정점으로 바로 가는 것 보다 현재 정점을 거쳐서 가는것이 더 가까울 경우
        if distance < distances[adjacent]:
            # 거리 업데이트
            distances[adjacent] = distance
            
```


```python
distances
```


    {'A': 13, 'B': 7, 'C': 0, 'D': 3, 'E': 7, 'F': 8}

