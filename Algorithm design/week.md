# week2

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-1.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-1.png)

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-2.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-2.png)

- BFS : 너비 우선 탐색
- 시작점 S 노드 = Layer 0
    - 다음 레이어 = Layer 1 = a, b
    - Layer 2 = c, d
    - Laeyr 3 = e 라고 지칭
    - layer0부터 3까지 순서대로 노드에 방문하는 알고리즘
- 모든 노드들은 방향성을 가지고 있지 않음(양방향 이동 가능)
- 노드의 개수를 m, 모서리의 개수를 n이라고 했을 때 ,O(m+n)의 런타임을 가진다

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-3.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-3.png)

- 노드들이 주어져있는 그래프 G와 시작점 s가 주어져 있음
- FIFO 데이터 구조인 queue를 s로 시작
- 여러차례 탐색하는 것을 피하기 위해서 bool대수로 탐색 여부를 구분할 것임
- queue가 공집합이 될 때 까지 반복
    - 큐의 앞에서 노드 추출
    - 추출한 노드의 인접 노드에 방문
        - 방문한 노드는 탐색됨으로 처리
        - 큐의 끝에 추가
- s - a- b- c- d- e 순으로 탐색하게 됨

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-4.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-4.png)

- BFS의 특징
    - v노드가 탐색됨 = 시작점부타 v노드까지 연결되어있음을 의미
    - 런타임 = 노드 개수 + 엣지의 개수

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-5.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-5.png)

- BFS를 이용하여 s에서 v까지의 최단 거리를 구할 수 있음
- s=v일 때는 거리를 0으로 처리
- s≠v일 때는 거리를 무한대로 초기화
- BFS알고리즘대로 탐색이 안된 노드로 이동할 때 레이어 층 증가
- v까지의 거리가 i이면 v는 i번째 레이어에 있는것과 같으므로 최단거리 = i

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-6.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-6.png)

- 방향성의 유무는 외관상의 변화에 불과함
- 그래서 undirected graph에 대해서만 우선 소개하고자 함
- 오른쪽의 그래프를 보면 10개의 노드를 3개의 조각들로 나눌 수 있음을 알 수 있음
    - 여기서 연결된 것들을 connected components라고 할 것임
- 그러나 이를 좀 더 포멀하게 정의하고자 함
    - connected components

        =  equivalence class의 집합

        = undirected graph에서 연결 가능한 최대 영역

    - equivalence class = 연결 가능함 = 한 점에서 영역내의 모든 점으로 가는 경로가 존재
- 목표 = 모든 connected components를 찾는 것
    - 네트워크의 연결에서 단절된 부분을 찾는데 사용

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-7.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-bfs_typed-7.png)

- 실제로 계산하는 방법
- 모든 노드를 탐색하지 않은 상태로 초기화
- 각 노드의 이름을 배열의 위치에 대항하는 번호로 지칭
- 중복 탐색을 방지하기 위해서 탐색 여부를 판단
- 이후 BFS와 동일하게 인접 노드들을 탐색
- 최종적으론 1번노드와 연결된 모든 노드를 탐색 완료
- for루프로 돌아가서 2번 노드에 대하여 처리 → 미탐색된 상태이므로 2번 노드에 대해 BFS 처리
- 모든 노드에 대하여 탐색을 확인하므로 놓치는 노드는 없음
- 모든 노드에 대하여 초기화 = O(n)
- 모든 노드에 대하여 for loop = O(n)
- 노드간 연결 여부 탐색 = O(m)

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-1.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-1.png)

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-2.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-2.png)

- 깊이 우선 탐색
- 너비 우선 탐색에 비해 좀더 공격적인 탐색 방법
    - 너비 우선 탐색은 주변의 모든 길을 탐색하면서 나아가지만
    - 깊이 우선 탐색은 길을 하나 찾으면 그 끝까지 파고 듦
- 갈래길이 있을 때 순서대로 탐색 후 이미 지나간 노드면 pass 및 backtracking = 지나가지 않을 노드로 이동
- 런타임 = 노드의 개수 + 엣지의 개수

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-3.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-3.png)

- BFS와 동일하게 구현하는 대신 Queue 대신 Stack을 사용

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-4.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-4.png)

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-5.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-5.png)

- 위상 정렬
    - 방향성이 있는 그래프
- 각 노드에는 order가 존재 ⇒ order에 맞게 정렬해야함
    - 파란색과 초록색 두가지 경우의 수가 있으나 둘은 결국 동일한 그래프임
- 작업의 순서, 학습의 순서 처럼 일련의 과정을 순서에 맞게 정렬할 때 사용

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-6.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-6.png)

- 끝 노드가 없는 경우(더이상 이동할 엣지가 없는 노드가 없는 경우)

    = 이미 지나갔던 노드로 다시 돌아가는 싸이클이 생기는 경우가 있으면 안됨

    - 시작점이 존재하지 않기 때문에 정렬을 수행할 수 없음

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-7.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-dfs_typed-7.png)

- 위상 정렬을 위한 효율적인 알고리즘이 있지만 깊이 우선 탐색으로 먼저 해결해 볼 것임
- 첫번째 노드부터 시작하여 마지막 노드까지 이동
- 마지막 노드를 stack에 쌓음 → 그 이전노드를 순서대로 stack에 쌓는 방식
- DFS와 마찬가지로 노드의 개수 + 엣지의 개수만큼의 런타임이 소요됨

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-1.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-1.png)

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-2.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-2.png)

- 강하게 연결된 노드의 집합을 의미
    - 서로 긴밀하게 연결되어있다고 하여 강한이라는 표현을 사용
- 왼쪽의 핑크색 원을 보면 세 노드가 서로 강하게 연결되었다고 할 수 있음
    - 서로가 서로에게로 이동 가능하기 때문
    - 반면 그 밖의 노드와는 서로가 서로에게 갈 수 없기 때문에 강한 연결 요소라고 할 수 없음
- 방향이 있는 그래프에서만 의미가 있음 → undirected graph의 경우 서로 연결되어있기 때문에 의미가 없다

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-4.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-4.png)

- 노드 개수 + 엣지 개수 만큼의 러닝타임을 소요
- SCC에 해당하는 노드들은 서로가 서로에게로 이동할 수 있다는 싸이클 성질을 이용
    - 주어진 이동 방향을 바꿔도 서로가 서로에게 이동할 수 있으면 SCC라고 판단
- 총 두번의 DFS 탐색을 진행함
    - 첫번째 DFS에서 주어진 방향대로 탐색
    - 두번째 DFS에서 반대 방향으로 반전 후 탐색

![week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-5.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/slides_algo-graphs-scc_typed-5.png)

![week2%207cc9e908ce7c4c8ead7f815e989822b5/Untitled.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/Untitled.png)

- DFS를 이용한 탐색에서 더이상 갈 곳이 없으면 return 및 num값을 맵핑
- num이 높은 곳에서 낮은 곳으로 이동이 가능함

![week2%207cc9e908ce7c4c8ead7f815e989822b5/Untitled%201.png](week2%207cc9e908ce7c4c8ead7f815e989822b5/Untitled%201.png)

- 가장 큰 num값이 맵핑된 노드부터 DFS시작
    - DFS를 더이상 진행할 수 없는 노드까지가 SCC에 해당 됨
- 반전시킨 그래프에서도 num이 큰 값에서 작은값으로 이동이 가능하면 양방향 모두 이동 가능함을 의미
    - 첫번째 DFS에서의 가장 큰 값에서 시작 = 그보다 작은 값들로 정방향 이동이 가능함을 의미
    - 두번째 DFS = 역방향 이동이 가능한 노드를 찾는 과정
    - 따라서 두번째 DFS는 num이 더 큰 값부터의 정방향 이동이 가능한다는 것을 base로 하기 때문에 역방향 이동이 가능함을 보이기만 하면 SCC임을 밝힐 수 있음