## Problem Solved

[프로그래머스 Level 3까지 전체 문제 풀이](https://github.com/m1nnh/Problem-Solving/tree/master/Programmers)

## Algorithm QnA 

### Q. 시간복잡도 / 공간복잡도
A. 복잡도는 알고리즘의 성능을 나타내는 척도이다. 그중에서 시간복잡도는 특정한 크기의 입력에 대하여 알고리즘이 얼마나 오래 걸리는지를 의미한다. 공간복잡도는 특정한 크기의 입력에 대하여 알고리즘이 얼마나 많은 메모리를 차지하는지를 의미한다. 동일한 기능을 수행하는 알고리즘이 있다면 일반적으로 복잡도가 낮을수록 좋은 알고리즘이다.

### Q. 그리디 알고리즘
A. 그리디 알고리즘은 단어 그대로 번역하여 탐욕법이다. 단순 무식하게, 탐욕적으로 문제를 푸는 알고리즘이다. 여기서 탐욕적이라는 말은 현재 상황에서 지금 당장 좋은 것만 고르는 방법을 의미한다. 정렬과 최단 경로 알고리즘도 그리디 알고리즘에 속한다.

### Q. 구현
A. 구현이란 머릿속에 있는 알고리즘을 소스코드로 바꾸는 과정이다. 흔히 문제 해결 분야에서 구현 유형의 문제는 풀이를 떠올리는 것은 쉽지만 소스코드로 옮기기 어려운 문제를 의미한다. 

### Q. 재귀 함수 / 백트래킹
A. 재귀 함수란 함수 내에서 자기 자신을 호출하는 함수이다. 재귀 함수를 작성할 때는 함수 내에서 다시 자신을 호출한 후 그 함수가 끝날 때까지 함수 호출 이후의 명령문이 수행되지 않는다는 사실과 종료 조건이 꼭 포함되어야 한다는 부분을 인지하고 작성하면 무한 루프를 방지할 수 있다. 대표적인 예시로는 DFS가 있다.

백트래킹은 알고리즘 기법 중 하나로, 재귀적으로 문제를 하나씩 풀어나가되 현재 재귀를 통해 확인 중인 상태가 제한 조건에 위배되는지 판단하고 그러한 경우 해당 상태를 제외하고 다음 단계로 나아가는 방식이다. 일반적인 재귀와 분명하게 다른 점은, 특정 상태를 제외한다는 것이다. 백트래킹은 현재 상태에서 다음 상태로 나아갈 수 있는 모든 경우를 찾으며 그중 유망 하지 않다면 현재에서 더이상 나아가지 않고 이전의 상태로 돌아가 다음 상태를 검사한다. 여기서 더 이상 탐색할 필요가 없는 상태를 제외하는 것을 가지치기라고 한다.

### Q. DFS/BFS
A. DFS는 Depth-First Search, 깊이 우선 탐색이라고도 부르며, 그래프에서 깊은 부분을 우선적으로 탐색하는 알고리즘이다. 대부분 그래프 문제로 출제가 되는데, 그래프는 노드와 간선으로 표현되며 이때 노드를 정점이라고 한다. 프로그래밍에서 그래프는 크게 2가지 방식으로 표현할 수 있다. 2차원 배열로 그래프의 연결 관계를 표현하는 방식인 인접 행렬과, 리스트로 그래프의 연결 관계를 표현하는 방식인 인접 리스트로 표현할 수 있다.

BFS는 Breadth-First Search, 너비 우선 탐색이라는 의미를 가진다. 쉽게 말해 자신에 인접한 노드부터 방문하는 알고리즘이다. DFS는 루트 노드로부터 최대한 멀리 있는 노드를 우선으로 탐색하는 방식으로 동작한다면, BFS는 그에 반대이다. 대표적으로 queue를 이용하여 구현한다.

### Q. 버블 정렬
A. 버블 정렬은 서로 인접한 두 원소의 대소를 비교하고, 조건에 맞지 않다면 자리를 교환하며 정렬하는 알고리즘이다.

### Q. 선택 정렬
A. 선택 정렬은 해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘이다. 자릿 수마다 가장 최소 값을 찾아 해당하는 인덱스에 넣는다.

### Q. 삽입 정렬
A. 삽입 정렬은 2번째 원소부터 시작하여 그 앞의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입하여 정렬하는 알고리즘이다. 위의 두 정렬과는 다르게 최선의 경우 O(N)이라는 엄청나게 빠른 효율성을 가지고 있어, 다른 정렬 알고리즘의 일부로 사용될 만큼 좋은 정렬 알고리즘이다.

### Q. 퀵 정렬
A. 퀵 정렬은 피벗을 선택한 후, 오른쪽에서 왼쪽으로 가면서 피벗보다 작은 수를 찾고 왼쪽에서 오른쪽으로 가면서 피벗보다 큰 수를 찾아 두 원소를 교환한다. 이과정을 반복하다 보면 왼쪽엔 피벗보다 작은 값, 오른쪽엔 큰 값들만 존재하게 된다. 

### Q. 병합 정렬
A. 병합 정렬은 요소를 쪼갠 후, 다시 병합시키면서 정렬해 나가는 방식으로 퀵 정렬과 유사하다. 퀵 정렬은 피벗을 통해 영역을 쪼개지만, 병합 정렬은 영역을 쪼갤 수 있을 만큼 쪼갠 후에 정렬을 한다. 이미 병합의 대상이 되는 두 영역이 각 영역에 대해서 정렬이 되어있기 때문에 단순히 두 배열을 순차적으로 비교하면서 정렬할 수가 있다. 병합 정렬은 순차적인 비교로 정렬을 진행하므로, 링크드 리스트의 정렬이 필요할 때 사용하면 효율적이다.

### Q. 계수 정렬
A. 계수 정렬은 가장 큰 데이터와 가장 작은 데이터의 범위가 모두 담길 수 있도록 하나의 리스트를 생성하고, 데이터를 하나씩 확인하며 데이터의 값과 동일한 인덱스의 데이터를 1씩 증가시키는 정렬이다. 계수 정렬 알고리즘은 특정한 조건이 부합할 때만 사용할 수 있지만 매우 빠른 알고리즘이다.

### Q. 이진 탐색
A. 이진 탐색은 배열 내부의 데이터가 정렬되어 있어야만 사용할 수 있는 알고리즘이다. 이진 탐색은 위치를 나타내는 변수 3개를 사용하며, 탐색하고자 하는 범위의 시작점, 끝점, 그리고 중간점이다. 찾으려는 데이터와 중간점 위치에 있는 데이터를 반복적으로 비교해서 원하는 데이터를 찾는 것이 이진 탐색 과정이다.

### Q. 다이나믹 프로그래밍
A. 컴퓨터 연산 속도에 한계가 있고, 메모리 공간을 사용할 수 있는 데이터의 개수도 한정적이라는 점이 많은 제약을 발생시킨다. 그래서 연산 속도와 메모리 공간을 최대한으로 활용할 수 있는 효율적인 알고리즘을 작성해야 한다. 그런 방법이 다이나믹 프로그래밍이다.

### Q. 메모이제이션
A. 기본적으로 다이나믹 프로그래밍은 큰 문제를 작은 문제로 나눌 수 있으며, 작은 문제에서 구한 정답은 그것을 포함하는 큰 문제에서 동일하다는 조건을 가지고 있다. 따라서 한 번 구한 결과를 메모리 공간에 메모해두고 같은 식을 다시 호출하면서 메모한 결과를 그대로 가져오는 기법을 메모이제이션 즉 캐싱이라고도 부른다.

### Q. 다익스트라
A. 다익스트라 알고리즘은 최단 경로를 구할 때 사용한다. 그래프에서 여러 개의 노드가 있을 때, 특정 노드에서 출발하여 다른 노드로 가는 각각의 최단 경로를 구해주는 알고리즘이다. 단 음의 간선이 존재하지 않을 때 정상적으로 동작한다. 매번 가장 비용이 적은 노드를 선택하기 때문에 그리디 알고리즘으로도 분류되며, 우선순위 큐인 heapq를 이용해서 구현할 수 있다.

