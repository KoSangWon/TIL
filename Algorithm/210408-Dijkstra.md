# Dijkstra 알고리즘
## Dijkstra 알고리즘의 정의
![Dijkstra Algorithm](https://github.com/ai-creatv/algorithm_nklcb1/raw/master/4_Algorithms/4_7_DijkstraAlgorithm/img/1.png)

- Dijkstra 알고리즘은 노드 하나를 기준으로 다른 모든 노드까지 도달하는 최단 거리를 계산하는 알고리즘이다.
  - Vanila Dijkstra 알고리즘은 최단 거리만을 계산하며, 경로까지 알아내려면 추가 메모리 필요
  - path는 안찾아주지만 조금만 수정하면 path도 찾을 수 있다.


- Dijkstra 알고리즘을 적용하기 위해서는 아래 조건을 만족해야 한다.
  - 그래프의 내 간선(edge) 중 음수 값이 없을 때에 사용 가능
  - 그래프는 유향 그래프 또는 무향 그래프 모두 사용 가능


